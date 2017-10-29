+++
date = "2012-10-06"
title = "The Serval Technology Stack"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-171716253014922197" itemprop="description articleBody">
Back when we started with the Serval Project we were focussed on creating a proof-of-concept that showed the potential of the concept of enabling mobile telephones to communicate directly, and allow people to communicate in difficult situations.<br/>
<br/>
As a result of that approach, we took largely existing VoIP and mesh routing technologies and fitting them into a mobile telephone.<br/>
<br/>
We already had ideas at the time that there was a better approach. This was reinforced by our early experience where we found that the combination of SIP was very sensitive to packet loss during call setup.<br/>
<br/>
To cut a long story short, we decided to implement our own suite of mobile mesh oriented protocols overlay network, and mesh oriented protocols and technologies to replicate the core functionality, not just of SIP/VoIP, but also UDP-style datagram services, file distribution, SMS-like services and more.<br/>
<br/>
Today I presented at <a href="http://wirelesssummit.org/">#IS4CWN</a> describing this new technology stack and explained a lot of our reasoning behind it.  I have been meaning to document some of this for a while, and now it has finally happened.  Now that I have some diagrams and slides, my intention is to write a series of posts explaining the various parts of the new Serval technology stack.<br/>
<br/>
For this post I want to start with an overview of the new technology stack, which I will then expand on each part in future posts.<br/>
<br/>

<a href="https://3.bp.blogspot.com/-DW88SrDWEbI/UHBNesqUYpI/AAAAAAAAAjk/0zFVfCFSzxc/s1600/serval-technology-stack.png"><img src="https://3.bp.blogspot.com/-DW88SrDWEbI/UHBNesqUYpI/AAAAAAAAAjk/0zFVfCFSzxc/s640/serval-technology-stack.png"/></a>
<br/>
Starting at the bottom, we have the various base layers that the Serval Mesh protocols all might be encapsulated in.  While the current implementation is an overlay encapsulated in IPv4 UDP packets, the overlay was designed to allow the kind of flexibility reflected here, with digital packet radio and other transports being anticipated from the outset. <br/>
<br/>
The trained squirrels is somewhat tongue-in-cheek, but serves to represent that we are thinking broadly about the form of possible transports.  It is hard to write kernel drivers that can expose a fleet of trained squirrels as a first-class network interface on a variety of operating systems, and the same goes for packet radio and other interfaces. <br/>
<br/>
This is a good reason for us to pursue an overlay network approach, because it avoids the need for kernel cooperation, even if using strange transports.  It also allows us to step back from some of the overheads and anachronisms of IP networking that are not appropriate for low-bandwidth or high-latency links, such as packet radio.<br/>
<br/>
This naturally leads into explaining the nature of the Serval Overlay Mesh protocols itself.  As mentioned, one reason for pursuing the an overlay model is to allow the use of non-conventional packet transports.  Another reason is to avoid the pain of IP address allocations.  IPv4 doesn't have enough address space to allow random self-allocation of addresses at a global scale.  It also turns out that IPv6 doesn't either, because there are only 64 host address bits, and there are more than 2^(64/2) people and devices in the world, which is the practical limit for random address allocation.  Structured address allocation is not feasible for mobile mesh networks that are intended to provide resilient communications.  Further, not all mobile phone platforms support IPv6. <br/>
<br/>
So our view is that IPv6 doesn't really offer any compelling advantage for our use-case.  Our approach was to instead use 256-bit Elliptic Curve Cryptography public keys as network addresses.  This also makes end-to-end encryption of communications between nodes trivial, because a Diffie-Hellman shared secret agreement process can be used to facilitate the use of a stream cipher.  And this is exactly what we have implemented for our Mesh Datagram Protocol (MDP), which is otherwise very much like UDP.<br/>
<br/>
The transparent encryption offered by MDP is used to host our Voice over Mesh Protocol, which then benefits from this.  Of course security isn't just encryption, and there are authentication and man-in-the-middle attack issues to be considered.  But I will leave that discussion for a future post.<br/>
<br/>
So that covers the right hand side of our protocol stack, which is all the real-time protocols.<br/>
<br/>
The left hand side covers the Rhizome store-and-forward or Delay Tolerant Networking (DTN) protocol and applications layered on top of that.  Full explanation of that will also be the subject of a future post.
<div></div>
</div>