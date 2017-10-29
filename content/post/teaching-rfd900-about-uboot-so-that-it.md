+++
date = "2017-03-28"
title = "Teaching the RFD900 about uboot, so that it doesn't interrupt the Mesh Extender boot process"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7156703050541181963" itemprop="description articleBody">
The Serval Mesh Extenders logically consist of a CPU with a serial port, and an RFD900 radio.  Our RFD900 firmware provides a regular heart-beat. <br/>
<br/>
This all means that the RFD900 radio, as soon as it powers on, begins sending heart-beat messages.<br/>
<br/>
This ordinarily wouldn't be a problem, except that the CPU modules we are using have only one serial port, so the serial boot loader is listening on the serial port when the system first powers up, and whenever it resets. <br/>
<br/>
This means that if uboot sees a heartbeat, it will interpret it as the user wishing to interrupt the boot process to interact with the boot loader.  Following Murphey's Law, this is assured to happen on every boot.<br/>
<br/>
We can't get rid of uboot, as it is important to have a way to reflash the devices (especially while we are still developing the software for them).<br/>
<br/>
The remaining solution is to teach the RFD900 to notice when uboot is active.<br/>
<br/>
In theory, this would just take a simple little finite state machine to notice the uboot banner, and then make sure it doesn't send any characters for a while, to allow uboot to boot normally.<br/>
<br/>
There are, however, two complications.<br/>
<br/>
1. We have to stay silent for long enough that we don't interfere with OpenWRT's fail-safe boot mode, which just means staying silent for longer.<br/>
<br/>
and<br/>
<br/>
2. The RFD900 is set to 230400bps for talking to LBARD, while uboot uses the serial port at 115200.<br/>
<br/>
It is this last problem that makes life more interesting, because we can't just watch for the characters of the uboot banner. Instead, we need to look for a character sequence at 230400bps that is what you would see if you send the uboot banner at 115200bps.<br/>
<br/>
As uboot is working at 1/2 the baud rate that the RFD900 is using, every serial bit received from uboot will be interpreted as two bits. Thus each uboot serial character should be able to be reliably received as two characters by the RFD900. We're lucky it isn't the other way around, as then the bits would be only half as wide, and there would be some uncertainty about how the bits would be read.<br/>
<br/>
In the process, I also had to clean up a few other spots where our RFD900 firmware was causing other characters to be emitted immediately on power-up.<br/>
<br/>
So after a few frustrating hours of debugging the finer points, I can now reliably boot a uboot-based system with an RFD900 running our packet radio firmware permanently attached to the serial port.<br/>
<br/>
<br/>
<br/>
<br/>
<div></div>
</div>