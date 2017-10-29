+++
date = "2015-08-31"
title = "Simple CSMA firmware for RFD900 radios"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6163365751387882887" itemprop="description articleBody">
I have been continuing to work on getting multiple Mesh Extenders communicating nicely via the RFD900 radio.  <br/>
<br/>
As I have previously mentioned, the challenge with this is that the frequency hopping firmware that they normally run cannot work with multiple radios without a defined network controller.  This just isn't possible with Mesh Extenders, where we expect nodes to wander in and out of coverage on a regular basis.<br/>
<br/>
Fortunately, it is allowable to use the ISM915 band in Australia, the USA, New Zealand and a few others without frequency hopping.  To do this, you must however use very wide channels, or limit your transmit power to not more than 3mW EIRP.  Fortunately, as described in my last post, the RFD900 can still transmit a long way on a couple of milli-Watts EIRP.  While at Arkaroola, we can of course transmit at upto 1W EIRP under our scientific spectrum license.  In the longer term, the next model of radio from RFDesign will allow the use of very wide channels, so the scientific license is really just an interim solution. Anyway, enough of the spectrum regulation side of things ...<br/>
<br/>
The normal RFD900 firmware's frequency hopper uses a Time Division Multiplexing (TDM) scheme, which is great for a pair of radios, or a small group with a defined controller, who can control who has what slice of time.  But as mentioned, that doesn't make sense for Mesh Extenders.<br/>
<br/>
Instead, we need a simple CSMA (Carrier Sense Multiple Access) or similar scheme that allows disorganised radios to communicate with each other on a transient and dynamic basis. The downside to this is that the effective bandwidth will be probably less than 1/3 of what can be achieved using TDM (which is part of why the original firmware uses TDM).<br/>
<br/>
Because we can now also have potentially a lot of radios talking, we need a clear way to mark packet boundaries in the serial stream -- for both transmit and receive -- so that we can reliably send and receive whole packets.<br/>
<br/>
To this end, I have culled all the TDM code out of the RFD900 firmware, and implemented some simple packet framing. <br/>
<br/>
The framing on the receive side we had already implemented for the Mesh Extenders. This just puts a simple prefix on each received packet in the serial buffer. That prefix contains a magic value, as well as some useful statistics, mostly signal strength.<br/>
<br/>
For the transmit side, I have changed the firmware so that it holds onto bytes in the TX buffer until it sees "!!".  To include a ! in the packet it must be escaped as "!.".<br/>
<br/>
After a bit of fiddling around, I was able to get all this working fairly nicely.<br/>
<br/>
The only other piece was to add a simple Listen Before Talk (LBT) function that holds off sending a packet until the ambient noise drops below a threshold.  This is to stop us talking over the top of other stations.  This is vital now that we no longer have TDM to keep the radios from talking over the top of each other.  For now I have a hard-wired threshold, but I will make this configurable soon, and if I can think of a good approach, I will make it dynamic based on the background noise on the channel, so that it doesn't stop transmission in busy urban areas, but still stops talking over the top of distant stations when in low-noise environments.<br/>
<br/>
(In fact, this whole effort was triggered by problems using the existing LBT code in version 1.6 of the RFD900 firmware, on which our Mesh Extender version is based. Basically if you set the LBT register on that firmware, the radio stops responding.  This may well have been fixed in later versions of the firmware.)<br/>
<br/>
Anyway, while there is more work to be done, you can see the work so far at <a href="https://github.com/gardners/SiK/tree/csma-packetised">https://github.com/gardners/SiK/tree/csma-packetised</a>.
<div></div>
</div>