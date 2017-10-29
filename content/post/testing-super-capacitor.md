+++
date = "2017-01-17"
title = "Testing the Super-Capacitor"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6433512852106919745" itemprop="description articleBody">
We have included a 1F 5.5V super-capacitor on the new Mesh Extender board. <br/>
<br/>
The idea of this is so that when power is lost, the unit has a couple of seconds to stop writing to the microSD card, and perhaps tidy things up to ensure a clean boot next time.<br/>
<br/>
However, we haven't managed to get it to work properly yet.<br/>
<br/>
The boards have a 20 Ohm resister in-line with the super-cap, so that there is no unmanaged in-rush current when charging the capacitor from empty.<br/>
<br/>
The capacitor takes a few minutes to fully charge to about 4.8V (5V - the voltage of the zener diode that forms part of the power loss detection circuit).<br/>
<br/>
At this point, it should be possible to then remove the power source, and have the unit operate powered solely by the super-capacitor, until its voltage level drops below about 3.3V.<br/>
<br/>
GPIO24 is the line that reads our input-power-available signal (effectively the input power before passing through a zener diode, after which it charges both the super-capacitor, as well as powering the rest of the board.  To test the system, I configured that GPIO line for input, and had a little shell script that sits in a loop reading from it. <br/>
<br/>
<div class="p1">
<span class="s1">root@OpenWrt:/# cd /sys/class/gpio</span></div>
<div class="p1">
<span class="s1">root@OpenWrt:/sys/class/gpio# echo 24 &gt; export</span></div>
<div class="p1">
<span class="s1">root@OpenWrt:/sys/class/gpio# cd gpio24</span></div>
<div class="p1">
<span>root@OpenWrt:/sys/devices/virtual/gpio/gpio24# while [ true ]; do cat value; don</span></div>
<style type="text/css">
p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 15.0px 'Andale Mono'; color: #28fe14; background-color: #000000; background-color: rgba(0, 0, 0, 0.9)}
span.s1 {font-variant-ligatures: no-common-ligatures}
</style>
<br/>
<div class="p1">
<span class="s1">e</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">...</span></div>
<br/>
It reports 1 when there is an input power supply (other than USB, which is another little problem we need to solve), and 0 when there is no input power supply, but is running on the super-capacitor.  At least that is the theory.<br/>
<br/>
However, with the 20 Ohm resister, the voltage on the low-side is only about 2.2V, much too low to be useful.  Thus I tried putting a 10 Ohm resister in parallel, dropping the combined resistance to about 6.7 Ohms.  That still wasn't enough. <br/>
<br/>
Then I tried bridging the resister by using a multi-meter in current measuring mode after having already charged the capacitor.  This gives effectively 0 Ohms, and provides an upper bound of what is possible with this super-capacitor.  With that configuration, things were more promising, as I saw u-boot try to boot, but as can be seen, as soon as it tried using the DDR RAM, it would reset, as presumably the DDR RAM draws too much power for the super-cap to sustain the supply above 3.3V:<br/>
<br/>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p1">
<span class="s1">1</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p1">
<span class="s1">*        U-Boot 1.1.4  (Jun  6 2015)        *</span></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">AP121 (AR9331) U-Boot for DOMINO v1</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">DRAM:   </span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p1">
<span class="s1">*        U-Boot 1.1.4  (Jun  6 2015)        *</span></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">AP121 (AR9331) U-Boot for DOMINO v1</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">DRAM:</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p1">
<span class="s1">*        U-Boot 1.1.4  (Jun  6 2015)        *</span></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">AP121 (AR9331) U-Boot for DOMINO v1</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">D?</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p1">
<span class="s1">*        U-Boot 1.1.4  (Jun  6 2015)        *</span></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">AP121 (AR9331) U-Boot for DOMINO v1</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p1">
<span class="s1">*        U-Boot 1.1.4  (Jun  6 2015)        *</span></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">AP121 (AR9331) U-Boot for DOMINO v1</span></div>
<div class="p1">
<span class="s1">?</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p1">
<span class="s1">*        U-Boot 1.1.4  (Jun  6 2015)        *</span></div>
<div class="p1">
<span class="s1">*********************************************</span></div>
<div class="p2">
<span class="s1"></span><br/></div>
<div class="p1">
<span class="s1">AP121 (AR9331) U-Boot for DOMINO v1</span></div>
<style type="text/css">
p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 15.0px 'Andale Mono'; color: #28fe14; background-color: #000000; background-color: rgba(0, 0, 0, 0.9)}
p.p2 {margin: 0.0px 0.0px 0.0px 0.0px; font: 15.0px 'Andale Mono'; color: #28fe14; background-color: #000000; background-color: rgba(0, 0, 0, 0.9); min-height: 17.0px}
span.s1 {font-variant-ligatures: no-common-ligatures}
</style>
<br/>
<div class="p1">
<span class="s1">?</span></div>
<div>
<br/></div>
<div>
As can be seen above, there is no line with 0, before it hits the u-boot reboot loop, indicating that the board does not operate on the super-capacitor,  even for just a few milliseconds.</div>
<div>
<br/></div>
<div>
We'll have to think of an appropriate solution to this problem, but first we need to understand the situation more completely.  </div>
<div>
<br/></div>
<div>
Is the capacitor unable to provide enough current for the DDR RAM?</div>
<div>
<br/></div>
<div>
Is the capacitor too small?</div>
<div>
<br/></div>
<div>
Also, only one of three super-capacitors seemed to work.  The other two might have been damaged at some point in the process, but having 2/3 faulty makes me think that we shouldn't be relying on them.</div>
<div></div>
</div>