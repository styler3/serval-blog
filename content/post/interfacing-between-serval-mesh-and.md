+++
date = "2013-03-27"
title = "Interfacing between the Serval Mesh and Cellular Networks (Part 1)"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-987811616351456761" itemprop="description articleBody">
A number of people now have asked whether a Serval Mesh can be connected to the cellular network, e.g., to allow people living just beyond the range of cellular service to be able to make and receive mobile telephone calls.<br/>
<br/>
This would be best done using a cellular modem and a bit of software integration to make use of it, so that the cellular audio can be passed through digitally.  However, most people who have asked about GSM/mesh gateways have indicated strongly that the solution must use only Android phones, and not require any soldering.<br/>
<br/>
This is not unexpected, since it is hard to get new equipment into areas where disaster, rural, remote or poverty are at play. The same goes for areas impacted by war or unrest.<br/>
<br/>
So we started thinking about how we can do this.<br/>
<br/>
Unfortunately, most models of Android phone don't let you access the audio from the cellular call directly, which rules out the easy option of writing some clever software that can run on a phone.<br/>
<br/>
However, all is not lost.  We can use two phones, with one making the cellular end of the call, and the other handling the mesh end of the call.  Then by using headsets to do some good old-fashioned acoustic coupling, we can record the cellular audio through the microphone of the mesh-connected phone, and play the audio out the speaker of the mesh-connected phone and into the microphone of the cellular-connected phone.  A picture should help illustrate how this would be arranged in practice:<br/>
<br/>

<a href="https://2.bp.blogspot.com/-8HvG7jJZdbU/UVPG2ZCctqI/AAAAAAAAA4M/lP5fuF_eBWU/s1600/20130328_172543.jpg"><img src="https://2.bp.blogspot.com/-8HvG7jJZdbU/UVPG2ZCctqI/AAAAAAAAA4M/lP5fuF_eBWU/s320/20130328_172543.jpg"/></a>

<br/>

Yes, it really is that simple. And that ugly.  

<br/>

For extra simple and ugly, you could just tape the two phones together with one upside down so that the speaker and microphones are close enough to couple the audio.

<br/>

Of course it has some drawbacks, notably the need for two phones instead of one, and the degredation in audio quality that is almost certain to occur.  However, initial tests reveal that the audio quality is better than might be expected, and quite likely to be very usable.

<br/>

Where we are up to now is that we have a student working on prototyping this.  He has got to the point where a call from on the mesh can trigger an outbound call to the cellular network, and has the two ends of the audio playing.  You can see this in the video below:


<div>
<br/></div>
<div>
<iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/e-CRKFDlaJg?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe></div>
<br/>

<br/>

The next step, and the one that will get us to a complete usable prototype for mesh to cellular calls (the other way around is a bit trickier) is to make the Serval Mesh software know about wired headsets so that it can route the audio through that path.
<br/>
<div></div>
</div>