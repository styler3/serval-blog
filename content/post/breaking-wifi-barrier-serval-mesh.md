+++
date = "2013-02-05"
title = "Breaking the WiFi Barrier - The Serval Mesh Helper Packet-Radio Prototyping (Part 1)"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-5960274984668218143" itemprop="description articleBody">
From the outset the Serval Project has been using WiFi in mobile phones to form the mesh network, because that was the easiest radio to make use of in the phone.<br/>
<br/>
However, WiFi has a lot of problems for meshing, especially on Android phones where you need to "root" the phone to even be able to use WiFi in the meshing ad-hoc mode.  Ad-hoc WiFi also has a lot of interoperability issues, power consumption issues, as well as some scaling and mobility problems due to the relatively under-developed standard that underpins it.<br/>
<br/>
But most of all, even if we solve all of those problems, WiFi has limited range. Typically mobile cannot communicate by WiFi over distances greater than 150m, and that's outdoors and without obstructions.  Indoors it can be as bad as 10m, especially when there are walls and fences and other substantial obstructions.<br/>
<br/>
This is why we have been thinking for a long time now about a pocket-sided "Mesh Helper" that will do the ad-hoc WiFi, so your phone doesn't need to be rooted, and won't go flat nearly so fast.  But most importantly, we can put additional radios on the helper, so that we can form useful mesh networks over much greater distances. <br/>
<br/>
A nice side effect of the mesh helper design is that anyone within WiFi range of the mesh helper can join the mesh, so you don't necessarily need one per person.  Also, it means that people can keep on using whatever mobile phone they like, and upgrading it as often as they like, without worrying about mesh compatibility or losing the long-range communications capability.<br/>
<br/>
We have some funding from the <a href="http://nlnet.nl/">NLnet Foundation</a> to explore prototyping the mesh helper device at present, so we have been working on the hardware and software needed to do this.<br/>
<br/>
For a while we had our eyes on the HopeRF RFM23BP 1W ISM 915MHz band radio modules that are  very small and cheap (about $10 in sample quantities), and fairly easy to program.  That said, when you are talking about implementing the kind of frequency hopping required to use the ISM 915MHz band in Australia and the USA, "fairly easy to program" is a bit euphemistic for "not strictly impossible to achieve".<br/>
<br/>
Fortunately, we have been following the progress of Andrew Tridgell (of Samba fame) with long-range telemetry radios for auto-piloting radio controlled model planes or UAVs.  Andrew has been very patient with my frequent probing at Linux Conf AU (LCA) events where I have quizzed him on the current state of the radio equipment they are using, to determine the feasibility of using it to prototype our Mesh Helper device.<br/>
<br/>
This year at LCA, it became clear that there was an excellent radio and firmware combination that would allow us to rapidly advance the prototype to a functional state. The only major trade-off would be that the prototype would feature a point-to-point radio link instead of a true mesh link, so only a pair of Mesh Helpers could operate in an area at a given time.  This is totally acceptable for the prototyping stage.  Also, the radio firmware has been largely written by Andrew, and is open-source, making it an excellent starting point for us to generalise the point-to-point link into a mesh link.<br/>
<br/>
So we ordered a pair of the <a href="http://rfdesign.com.au/index.php/rfd900">RFD900 radio modules</a> from <a href="http://rfdesign.com.au/">RFDesign</a>, which arrived on Monday.  A testament to the quality of the radios and firmware is that by yesterday afternoon we had Serval Mesh traffic flowing over them! <br/>
<br/>
This was tested with a modified version of our servald software (currently living in the "serial" branch of <a href="http://github.com/servalproject/serval-dna">github.com/servalproject/serval-dna</a>, but soon to move into the "development" branch).  The radios were plugged into my mac, and I had a separate instance of servald talk to each, and configured so that they could only communicate with each other via the radios, thus testing the full radio communication path.<br/>
<br/>
After a few glitches with my SLIP-style encapsulation of packets in the serial data link, all was working, as the following video shows.<br/>
<br/>

<iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/n2jEfWh10K8?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe>
<br/>
I did try to grab a couple of screenshots, but they seem to have disappeared into the ether, perhaps during one of the several times that my mac froze hard while talking to the radios.  I need to look into the cause of that, which I suspect may be related to either the FTDI USB to TTL serial port driver or excess current draw by the radios over the USB port (however, the problem still occurred when transmitting at only +10dBm (10mW), which should have been well within the capability of the USB ports).<br/>
<br/>
We also did a couple of indoor/urban tests with the radios. In both cases, a radio was left plugged into a mac either in my house just sitting on the lounge, or on a desk in our lab at work.  We then wandered around with a 2nd computer with the other radio and kept an eye on the link quality to see how far away we could wander.<br/>
<br/>
For the uban test, with the radio indoors, I then wandered outside and proceeded to walk around the block. Our block is about 75m wide and 200m long, with lots of solid brick homes and steel fences between houses.  The radio was sitting only about 0.8m above ground level, well below fence level. The link was sustained almost the whole way around the block, up to about 150m - 200m <i>through all the houses, walls, fences and other obstructions</i>. In other words, if almost any two people on our block were using Mesh Helper devices, they could have easily communicated. In contrast with WiFi <i>everyone</i> on the block would have needed to be part of the mesh.  This is exactly the kind of result we were hoping for. Also, when I got home I realised I didn't have the radios at full power, so it might even have been possible to get right around the block.<br/>
<br/>
For the office test, we walked around inside the building from the 4th floor where our lab is, down to the 3rd and 2nd floors, all the way to the tea room (an important communications destination for us), and were able to maintain link most of the time, including while in the tearoom.  It is worth noting that our building has thick concrete floors and is built into the side of a hill, so there were substantial barriers.  We are not even certain if there is line of sight from the tea room to our lab above the soil of the hill side.<br/>
<br/>
In the process of this, we have discovered that the full link budget (of up to about 125dB at typical noise levels) does not seem usable without some refinement of the forward error correction. This is something that we will look into when we have the opportunity, because it could potentially extend the maximum range in certain situations, where the loss of link is not due to complete obstruction of signal.
<div></div>
</div>