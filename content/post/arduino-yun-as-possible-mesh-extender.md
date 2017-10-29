+++
date = "2013-10-10"
title = "Arduino Yun as a possible Mesh Extender Platform"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8494518260872658842" itemprop="description articleBody">
<div>
Regular readers of this blog will know
that we have been looking at a variety of hardware options for the
Serval Mesh Extender.</div>
<div>
<br/>
</div>
<div>
The <a href="http://servalpaul.blogspot.com.au/2013/07/smaller-more-elegant-mesh-extender.html">Serval Mesh Extender</a> is a device
that combines ad-hoc WiFi meshing with long-range license-free UHF
packet radio to allow the easy formation of mesh networks spanning
useful distances.  Typically the UHF packet radio has a range about
ten times greater than WiFi. This means that in ordinary suburban and
urban areas we get a range of a block or two, and in open rural areas
the range can be in the kilometres.</div>
<div>
<br/>
</div>
<div>
We run our <a href="http://thetechchallenge.org/winners/communicate.html">award winning</a> Serval Mesh
software over the top, providing an easy to use communications system
that lets you use your cell phone without cellular coverage, for
example, during a disaster, or when you and your friends are near one
another outside of the range of your native network.  For example, if
you are at an international gathering and don't want to pay $4 a
minute for the privilege of calling someone a few hundred metres
away.</div>
<div>
<br/>
</div>
<div>
The challenge with the Mesh Extender
design is that we haven't had the budget to design our own device
from the ground up.  As a result we have been using existing hardware
platforms, and trying to adapt them to accept the excellent <a href="http://rfdesign.com.au/index.php/rfd900">RFD900</a>
UHF packet radios we source from RFDesign (their link margin is
probably about 10dB better than competing radios that we are aware
of).</div>
<div>
<br/>
</div>
<div>
This means that we have been doing
things like <a href="http://servalpaul.blogspot.com.au/2013/09/mesh-extender-assembly.html">modifying TP-LINK MR3020 wireless routers</a> to build
prototypes.  While it works, the process is far from satisfactory,
and the physical steps take a couple of hours per unit, which makes
the effective unit price very high, despite the low cost of the
MR3020 unit itself.</div>
<div>
<br/>
</div>
<div>
This is where the <a href="http://arduino.cc/en/Main/ArduinoBoardYun?from=Main.ArduinoYUN">Arduino Yun</a> is very exciting
for us.  It has all of the functionality of the MR3020 in the form of
the mesh-friendly Atheros processor and WiFi system-on-a-chip running Linux, and of
course being an Arduino it has plenty of connectivity options for us
to connect to the RFD900, which just uses RS232 serial.  As an added
bonus the Yun has a microsd slot, so we don't need to use a USB
memory stick for mass storage, which actually makes a noticable impact on power consumption.  The larger flash on the Yun is also
welcome, as the 4MB flash on the MR3020 is, frankly, a pain to work
with.</div>
<div>
<br/>
</div>
<div>
While we are still working on the
integration, the prospect is there for the Yun to save us a lot of
time, and hence cost, in making future prototypes, and the Yun board
itself could be the basis for a customised PCB that exactly meets our
needs, and allows us to just plug the radio module directly onto the
PCB.  Here you can see the Yun connected to an RFD900 radio ready for integration testing:</div>
<div>
<br/></div>


<br/>

<a href="http://2.bp.blogspot.com/-z8aFvRHbOCE/UleT-MwqxWI/AAAAAAAABZ8/dIO1Nz-EAII/s1600/20131011_145442.jpg"><img src="http://2.bp.blogspot.com/-z8aFvRHbOCE/UleT-MwqxWI/AAAAAAAABZ8/dIO1Nz-EAII/s400/20131011_145442.jpg"/></a>
<div>
<br/></div>
<div>
<br/>
</div>
<br/>
<div>
In short, the Yun is opening a new
opportunity for us to innovate faster, more affordably, and with a
better result.</div>
<div></div>
</div>