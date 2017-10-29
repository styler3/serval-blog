+++
date = "2012-03-29"
title = "Serval Overlay Mesh Can Now Ping"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1480853366854862279" itemprop="description articleBody">
Okay, so it is one small step, but for us it is a significant one: the Serval Overlay Mesh can now ping nodes, simply using the Serval network identifiers (that are really stand-alone public keys in the NaCl CryptoBox key space):<br/>
<br/>

<a href="http://3.bp.blogspot.com/-dLo0jvJ3hSQ/T3RQbHtnvBI/AAAAAAAAAMg/YDBkVNw_KKQ/s1600/mdp-ping.png"><img src="http://3.bp.blogspot.com/-dLo0jvJ3hSQ/T3RQbHtnvBI/AAAAAAAAAMg/YDBkVNw_KKQ/s640/mdp-ping.png"/></a>
<br/>
It looks just like normal ping, except for those really long addresses (256 bits).  What is important for us, is that behind the scenes we have the Mesh Datagram Protocol (MDP) working, and all of the supporting infrastructure that goes behind it. <br/>
<br/>
This means we are getting closer to carrying phone calls over MDP, and that <i>is</i> significant, because it lets us enjoy great transparent super-strong cryptography to protect the privacy of people making calls on a Serval phone.<br/>
<br/>
It also lets us use non-IP based transports to carry the data, such as UHF and VHF radio based long-range mesh technologies that we are working on.  We are having some really encouraging conversations with one phone manufacturer about including UHF long-range meshing into their phones, which would be great, as it would provide hundreds of metres range indoors and potentially one to a few kilometres outdoors under ideal conditions. <br/>
<br/>
Such improved range compared with WiFi makes mesh telephony much more useful, as it means that fewer mesh phones are needed in an area to allow communications to occur.  With WiFi you need someone in just about every house with a mesh node if you want to connect a community, because the range is about one house.  But the long-range meshing would increase that range to perhaps a 5 to 10 house radius.  In that context only a few percent of homes need mesh devices, which is much easier to achieve.<br/>
<br/>
Meanwhile, I should get some sleep and then get back to writing software.
<div></div>
</div>