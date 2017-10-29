+++
date = "2015-08-13"
title = "Working on the Mesh Extender UHF Radios and other things"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8357602998804227399" itemprop="description articleBody">
It's been a while since the last post, but we have been busy in the background on some exciting things:<br/>
<br/>
With the help of the NLnet Foundation, we are making the first steps towards an iOS port of the Serval Mesh.<br/>
<br/>
With the help of USAID, we are working on "slow-media transports" for Android, in particular using Bluetooth device names, and hopefully, Wi-Fi Direct service discovery information, to carry mesh traffic. This is really significant, because it allows carriage of ad-hoc communications on non-rooted devices.  The trade-off is that it is much slower than ad-hoc Wi-Fi.<br/>
<br/>
The third thing we are working on at the moment is making Mesh Extenders work in groups of more than two units. <br/>
<br/>
Historically we have been stuck with pairs because the radios we are using are required to frequency hop when using the ISM 915MHz band available here in Australia, New Zealand and the USA.<br/>
<br/>
We are now actively working to remove this limitation, using the new radios that RFDesign are creating that allow broader spectrum occupancy that will allow them to qualify as spread spectrum devices under the relevant FCC and ACMA rules (LIPD class 45 for the ACMA rules).  This means that we can drop the frequency hopping that causes all the synchronisation issues for ad-hoc and transient groups of Mesh Extenders that currently exist.<br/>
<br/>
In other words, this will allow people to carry a Mesh Extender, and for it to automatically mesh with any other Mesh Extenders that come into range from time to time.  The practical limit will probably be 5 - 25 Mesh Extenders in range at any one time -- something I hope to quantify better in the near future.<br/>
<br/>
Now, the only trouble is that those radios are not yet finished and available.<br/>
<br/>
So we have embarked on an interim solution, by obtaining a spectrum license from ACMA that will allow us to operate the RFD900 radios without frequency hopping at upto 1W EIRP in our favourite piece of Outback, the Arkaroola Wilderness Sanctuary. <br/>
<span><br/></span>
<span>Our <a href="http://web.acma.gov.au/pls/radcom/assignment_search.lookup?pACCESS_ID=1848560&amp;pDEVICE_ID=2269298">scientific spectrum license</a> which was granted earlier in the week allows us use of 915MHz - 928MHz at upto 1W anywhere within 130km of <span>29'52"35S, </span><span>138'52"25E, which is great because this affords us great flexibility for testing in a variety of settings.  </span></span><br/>
<span><span><br/></span></span>
<span><span>The license stands for the next 12 months, which will hopefully be time enough for us to transition to the new RFDesign radios.</span></span><br/>
<span><span><br/></span></span>
<span><span>We are also open to making use of this license open to other people who would like to experiment in similar ways in that area (but note that it is really quite remote, 400km from the nearest large town, and centred about 130km from the nearest settlements with any facilities).  We would also need to make sure that ACMA and the University are comfortable with such an arrangement, but I am happy to explore this if anyone is interested.</span></span><br/>
<span><span><br/></span></span>
<span><span>Meanwhile, I hope to modify the configuration of some radios, and put the latest servald on a couple of Mesh Extenders and, all things going well, to perform some rudimentary testing at Arkaroola this coming week.</span></span><br/>
<span><span><br/></span></span>
<span><span>Update: <a href="https://www.google.com/maps/d/edit?mid=zaLUdkTbCPF0.kP6eCcsnp8wo&amp;usp=sharing">This map</a> shows the approximate area of the license.</span></span>
<div></div>
</div>