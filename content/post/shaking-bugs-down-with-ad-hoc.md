+++
date = "2015-09-20"
title = "Shaking the bugs down with ad-hoc communications via RFD900"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3191174196714730550" itemprop="description articleBody">
Last week I was up at Arkaroola again working on getting the Mesh Extenders to communicate via the RFD900 radios running my new CSMA firmware using our new spectrum license that allows us to avoid frequency hopping at (relatively) high power levels.<br/>
<br/>
The CSMA firmware itself had very few problems to be solved.  The main change I made was introduce a couple of escape sequences to allow setting the power level of each packet to either low (requiring no spectrum license) or high (requiring a spectrum license).<br/>
<br/>
This was part of a general effort to make the power level easily controllable so that I could set the Mesh Extenders to either "normal" or "Arkaroola" mode, without having to reflash them.<br/>
<br/>
In the end, I implemented two tests that the Mesh Extenders perform before sending a packet at high power: First, the file "HIPOWER.EN" must exist on the USB memory stick on the FAT32 partition, and second, the slider switch on the MR3020 PCB must be set to the middle position. If either of those are not set correctly, then packets will be transmitted at low power.  Thus I can either replace the contents of the USB memory stick, or slide the switch to disable hi-power mode when I return from Arkaroola.  Ideally I should modify the lid design of the 3D-printed case so that I can access the slider switch without unscrewing it, but that's really just a matter of convenience.<br/>
<br/>
So after fixing that, and having a frustrating day while I realised I was using the wrong binary for the RFD900 radios, I managed to send a MeshMS message between a pair of Mesh Extenders operating in this way.  There are still some scheduling bugs in LBARD that prevented the confirmation reply from getting back to the sending phone. I also have a list of other relatively minor issues to work through to get it all operating stably, all of which I hope to work through this week ready for the next trip to Arkaroola, where I hope to be able to operate 8 or more Mesh Extenders together using the RFD900 in this ad-hoc mode, and to be able to send and receive MeshMS messages over a fairly large area.  This will be very satisfying and a significant step forward if I can achieve it.
<div></div>
</div>