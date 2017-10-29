+++
date = "2014-05-28"
title = "Tunnelling IP traffic over the Serval Overlay Mesh"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3079450175848578256" itemprop="description articleBody">

We have been asked a number of times over the past few years if it is possible to carry IP traffic over a Serval Mesh network.  

<br/>

Our answer has always been along the lines of "yes, you could in principle tunnel it, but we haven't added support for it, and we have other tasks higher on our priority list."  Thanks to a research agreement with the New America Foundation's Commotion Wireless project, and a lot of excellent work by Jeremy, this has now changed.  

<br/>

We are now able to tunnel IP traffic over the newly implemented Mesh Streaming Protocol (MSP).  MSP is kind of like TCP for Serval Mesh, in that it provides reliable in-order delivery of a data stream.  It isn't exactly like TCP, however.  For example, we intend to add a kind of hybrid mode where it tries to reliably deliver traffic, but is okay with missing the occasional packet if it will delay the whole stream too much.  That sort of feature is good for streaming live audio, for example.

<br/>

To tunnel IP traffic over a mesh we need more than just MSP, we need some sort of port-forwarding between IP and MSP, in other words a protocol converter.  We also need a proxy server, and ideally, some sort of access control mechanism to decide who can use the service.  It would also be great to have an automatic service discovery mechanism.

<br/>

Jeremy has implemented all of these things, as can be seen in the video below.

<br/>

<iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/4Kmh8Wiix0o?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe>
<br/>
Talking about the access control, one of the nice things about the Serval overlay mesh protocols is that node addresses are public keys.  This means that you can reliably limit services to a particular node, just by filtering on network address, because no one can spoof the network address of any other party.<br/>
<br/>
Another happy side effect is that all traffic over the tunnel is automatically end-to-end encrypted.  As can be seen in the video, there is nothing the user needs to do in order to get the encryption.<br/>
<br/>
<br/>
<div></div>
</div>