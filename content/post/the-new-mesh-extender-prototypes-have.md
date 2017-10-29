+++
date = "2016-12-06"
title = "The new Mesh Extender Prototypes have arrived!"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-5405109950103305727" itemprop="description articleBody">
After DHL claiming that they couldn't deliver the parcel to our address here in Germany for "technical reasons," we finally have the two prototypes of the new Mesh Extender design.<br/>
<br/>
As a reminder, this design is required for our AusAID grant to pilot Serval in the Pacific.  The new board is much easier to manufacture, and is designed to fit in a custom-designed housing designed to meet the IP65 or IP66 standard.  This is all being done on a shoe-string budget, in part because hardware always costs more to design than you expect.<br/>

<a href="https://3.bp.blogspot.com/-KK6HFBrgmHE/WEbXxsw3xRI/AAAAAAAAGA8/MOnpwbrS7SUAbu1Wb4B0FZhCDSyupHfjACLcB/s1600/IMG_20161206_132645_MeshExtenderPrototype.jpg"><img src="https://3.bp.blogspot.com/-KK6HFBrgmHE/WEbXxsw3xRI/AAAAAAAAGA8/MOnpwbrS7SUAbu1Wb4B0FZhCDSyupHfjACLcB/s640/IMG_20161206_132645_MeshExtenderPrototype.jpg"/></a>

<br/>
<br/>
Here is the side that accepts an RFD900 or RFD868 packet UHF radio, if it is being optionally included, which will be the normal situation.  The round thing is a 1F super-cap, so that the unit can shut itself down gracefully if the battery/solar power supply fails.  <br/>
<br/>
You can tell it's a prototype by the yellow tape over one of the ethernet connector's pins, where we hadn't thought too hard about where the antenna cables would end up.  Also, the D-Sub 15 is on the opposite side of the PCB to the D-Sub 25 connector, when they should probably be on the same side. Hopefully these will be the worst issues we have to deal with.<br/>
<br/>
You can also see the internal USB connector for holding a memory stick, or something else if you want.  We actually hope to not use the USB port, because of the myriad problems we have had using USB memory sticks on battery-powered Mesh Extenders.  Basically the power consumption is too high, the performance is horrible, and the memory sticks get easily corrupted, or even die, if they lose power at the wrong time.<br/>
<br/>
Below you can see both sides of the PCB.  Here the two internal ethernet jacks can be seen, which face downwards, so that cables can be routed inside the water-proof case.  We won't by default be providing external routing for those cables, as they are not normally needed in a Mesh Extender.  We figure that people will just drill holes in the cases in convenient locations if they need ethernet.  Not ideal, but given our extremely limited budget, it was the best we could manage.<br/>
<br/>

<a href="https://4.bp.blogspot.com/-xTsF2A2M54E/WEbXxr6mvCI/AAAAAAAAGBA/ceGbOAAcS8E1xMkgVVj2Phc9GU93tB6dwCLcB/s1600/IMG_20161206_132612_MeshExtenderPrototype.jpg"><img src="https://4.bp.blogspot.com/-xTsF2A2M54E/WEbXxr6mvCI/AAAAAAAAGBA/ceGbOAAcS8E1xMkgVVj2Phc9GU93tB6dwCLcB/s640/IMG_20161206_132612_MeshExtenderPrototype.jpg"/></a>
<br/>

<br/>

The D-Sub 25 connector has 5V in, as well as 9-26ishV input, which can come from a car or truck plug, or from a solar panel.  That is, you can connect one of these to a suitable naked solar panel, without needing any interface circuitry.  Similarly, there are three pins for connecting a 2-cell LiFePO4, LiPo or sealed lead-acid battery.  The multi-chemistry battery charger is included in the unit.  

<br/>
<h3>
Dealing with EU Directive 2015/53/EU and potential unhelpful FCC rules</h3>

<br/>

The D-Sub 25 also has device identification pins that are intended to allow the unit to work out which countries regulations apply, to control allowed transmission frequencies, and if required by FCC rules or EU directives to prevent the installation of third party firmware, that this can be done without any DRM locks. That is, by building a "research and development cable," the device will always be able to accept 3rd-party firmware, but when used with the default cable for a country that requires it, will only accept firmware updates that we have signed.  

<br/>

We have talked about this solution to mis-regulation in a few different places, and understand that it isn't perfect, however, given our pragmatic requirements, it seems the least-bad option available to us.  We are always interested to hear people's thoughts on how we can improve on this, and of course people are always free to make their own firmware that follows their own policy, instead of this one.

<br/>

This issue might become more important in the near future, if low-cost wireless routers start coming firmware locked due to these counter-productive regulations.
<h3>
Getting down to business</h3>

<br/>

So now I need to start qualifying these boards, so that we can confirm to our design and manufacture friends when it is safe to finalise the design, and manufacture the units we need for our pilot in the pacific.

<br/>

There are a number of steps that we need to cover here, and that I would welcome assistance with, including:

<br/>

1. Bringing the units up for the first time

<br/>

2. Making the microSD slots work

<br/>

The boards have two microSDs, because we don't know which method will work with the Ath9k chipset. One is connected to an SPI bus, which would be the preferred option, but may require some careful control of that bus, as it may have other devices connected. The other is connected via GPIOs to the Core Domino module, which should be fairly easily supportable by the Linux GPIO SPI/SD card kernel driver, although performance is likely to be poor.  We are <i>very</i> keen to get at least one of these options working, so that we can avoid all the horrors of using USB that I have described previously.

<br/>

3. Building Serval Mesh and Mesh Extender packages for the Core Domino, and testing.

<br/>

4. Porting our firmware patches for the RFD900 radio to the European version, the RFD868.

<br/>

5. Testing the solar and battery controller interfaces.

<br/>

6. Testing the ethernet interfaces.

<br/>

7. Building and testing power cables, including the region identification and regulatory satisfaction functions.
<br/>
8. Adding support for the super-cap to cleanly shut the thing down when power is lost, and characterising the super-caps performance. Added bonus: Abort shut down when power is restored during the shutdown process.<br/>
<br/>
9. General integration testing for the whole Mesh Extender software suite<br/>
<br/>
10. Help us develop the remaining functions required for the AusAID Pacific Pilot.<br/>
<br/>
Anyone who is willing and able to contribute to these efforts would be greatly appreciated. <br/>
<br/>
There is the practical limitation that we have only two prototypes, and that they need to stay with me here in Darmstadt, Germany. <br/>
<br/>
That said, if anyone is interested in buying their own prototypes to assist in the process, I would be happy to facilitate this, however we don't have funds to subsidise this process at the moment, and because they are being built as prototypes, we would expect that they will be relatively expensive.  However, if we get enough orders to get a batch made at once, we can look into that.<br/>
<br/>
Related to that, at this stage it would seem reasonable to expect that the prototype boards will be able to fit into the final custom injection-moulded cases that we are getting designed, to allow use of the prototypes outdoors in the future -- although nothing is certain until it happens.
<div></div>
</div>