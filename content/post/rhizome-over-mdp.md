+++
date = "2012-12-03"
title = "Rhizome over MDP"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8471451619871888837" itemprop="description articleBody">
The Serval Mesh uses our own overlay network, rather than relying solely on any underlying IP network.  This decision was made for several reasons. <br/>
<br/>
First, we knew that IP over ad-hoc WiFi has a number of problems, many of which are a direct result of interoperability problems among and within ad-hoc WiFi implementations.  Such interoperability issues could manifest as, among other things, an inability to deliver unicast IP packets, but allowing broadcast IP packets to be delivered just fine.<br/>
<br/>
Second, we have planned from the outset to diversify our radio options beyond WiFi and other traditional wireless-IP based solutions. In particular, we have had our eye on low-bandwidth communications in the ISM bands.  At low bandwidth IP encapsulation would incur unnecessary overheads. Also, allowing compatibility with IP would mean that any such mesh would soon be drowned out by the general IP chatter of hosts, because most modern software is no longer designed with dialup and sub-dialup speeds in mind.<br/>
<br/>
Third, it allows us to use public keys as network identifiers, and so gain some very nice security characteristics for free.<br/>
<br/>
So we created the Serval Overlay Mesh (SOM) and Mesh Datagram Protocol (MDP) as our solution to this. We have already implemented encrypted voice calls and Serval DNA resolution over MDP. <br/>
<br/>
That left the Rhizome store-and-forward file and data distribution system as the sole part of the Serval Mesh dependent on IP networking and unicast packets.<br/>
<br/>
So this week I finally got around to implementing Rhizome over MDP, using a protocol similar to TFTP, but with each request asking for up to 32 packets at a time to improve throughput.  We also have some ideas for buffering and handling packet loss and out-of-order delivery, which we hope to implement soon. <br/>
<br/>
In the process we also revamped Rhizome transfers to stream directly into the database, instead of having to be written to temporary files first.  We also hash the files as we receive them, so that there is no big time hit at the end of reception.  This is important for slow devices, large file transfers and situations where servald's responsiveness is important, such as when carrying a voice call.<br/>
<br/>
But for now, we are happy that we can transfer arbitrarily large files using only broadcast IP packets, which makes it much easier to create useful mesh networks using existing ad-hoc WiFi capable equipement.<br/>
<br/>
The image below shows servald running on a Dragino, and me poking it to see if a file has been received.  The file "foo" is duly received after a short while.<br/>
<br/>

<a href="http://1.bp.blogspot.com/-Il5nNF0uCzk/UL1pfVDTMyI/AAAAAAAAAnY/53oDbx5p8xs/s1600/TerminalScreenSnapz004.png"><img src="http://1.bp.blogspot.com/-Il5nNF0uCzk/UL1pfVDTMyI/AAAAAAAAAnY/53oDbx5p8xs/s640/TerminalScreenSnapz004.png"/></a>
<br/>
<div></div>
</div>