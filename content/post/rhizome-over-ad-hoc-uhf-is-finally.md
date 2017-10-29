+++
date = "2016-06-15"
title = "Rhizome over ad-hoc UHF is FINALLY working"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1580010935622136704" itemprop="description articleBody">

<br/>
 As many of you will already know, we have been working away in the background on getting the RFD900 radios working in something that approximates ad-hoc mode on Wi-Fi, but using the ISM 915 MHz band, so that we can have Mesh Extenders communicate over long distance, without any limit on the number of Mesh Extenders, and without them having to be in specially paired groups.<br/>
<br/>
FINALLY at 4am this morning I fixed the remaining bugs that were stopping this from working in most cases.  There are still a few little niggly issues of course, but it is now working.<br/>
<br/>
Together with some work-experience students, we have tested the units in and around the lab today.<br/>
<br/>
First, we set one unit up on the bench in our lab on the fourth floor, together with an Android tablet running Serval Mesh that could receive MeshMS messages, and therefore cause automatic delivery acknowledgements to be pushed back to the message sender.<br/>
<br/>

<a href="https://2.bp.blogspot.com/-NMxX36xT1Gw/V2IpyXmJThI/AAAAAAAAF2Q/ZSK3tCh6XYkeYp8VsduK7QGhQk62VWXYwCLcB/s1600/P1000106.JPG"><img src="https://2.bp.blogspot.com/-NMxX36xT1Gw/V2IpyXmJThI/AAAAAAAAF2Q/ZSK3tCh6XYkeYp8VsduK7QGhQk62VWXYwCLcB/s320/P1000106.JPG"/></a>
<br/>
We then went for a wander with another Mesh Extender and a phone, and sent messages to the tablet, and waited for delivery confirmation to come through.  This typically took a couple of minutes, although in many cases the MeshMS text message itself is delivered in about 15 seconds.<br/>
<br/>
Here we are one floor down from the lab:<br/>
<br/>

<a href="https://3.bp.blogspot.com/-en_vhT0XQdA/V2IpybrjtUI/AAAAAAAAF2I/1HjT9Y7lsw8gaiuQYyA_HAWflgNfYI-FACLcB/s1600/P1000107.JPG"><img src="https://3.bp.blogspot.com/-en_vhT0XQdA/V2IpybrjtUI/AAAAAAAAF2I/1HjT9Y7lsw8gaiuQYyA_HAWflgNfYI-FACLcB/s320/P1000107.JPG"/></a>
<br/>
And then two floors down.  Note that our building has 1/2 metre thick concrete floor decks.<br/>
<br/>

<a href="https://1.bp.blogspot.com/-lWuJtSeylrE/V2Ipz2PFwBI/AAAAAAAAF2k/6NG8giLgywEzF8F3toXhwzXA8GRW30pAQCLcB/s1600/P1000108.JPG"><img src="https://1.bp.blogspot.com/-lWuJtSeylrE/V2Ipz2PFwBI/AAAAAAAAF2k/6NG8giLgywEzF8F3toXhwzXA8GRW30pAQCLcB/s320/P1000108.JPG"/></a>
<br/>
And yet another floor down:<br/>
<br/>

<a href="https://3.bp.blogspot.com/-xdzrWfRlkm4/V2Ipz2bMYPI/AAAAAAAAF2g/n1-RQhKkyWYxKEWSY9LIjq1JXM7WQN3jwCLcB/s1600/P1000109.JPG"><img src="https://3.bp.blogspot.com/-xdzrWfRlkm4/V2Ipz2bMYPI/AAAAAAAAF2g/n1-RQhKkyWYxKEWSY9LIjq1JXM7WQN3jwCLcB/s320/P1000109.JPG"/></a>
 And a bit closer in on the same floor:<br/>
<br/>

<a href="https://4.bp.blogspot.com/-9V_T9vsCI40/V2Ip03C8HcI/AAAAAAAAF20/rrJG0euNO1MTrY8p_gDcbGRS4II5Z1HIACLcB/s1600/P1000111.JPG"><img src="https://4.bp.blogspot.com/-9V_T9vsCI40/V2Ip03C8HcI/AAAAAAAAF20/rrJG0euNO1MTrY8p_gDcbGRS4II5Z1HIACLcB/s320/P1000111.JPG"/></a>
<br/>
And then down on the first floor -- with three thick floor decks between us and the Mesh Extender.<br/>
<br/>

<a href="https://2.bp.blogspot.com/-IKcTz-4DunI/V2Ip0xg_peI/AAAAAAAAF24/iYMJC95cw_8GZp3_00VWkKsai8DvQCftgCLcB/s1600/P1000112.JPG"><img src="https://2.bp.blogspot.com/-IKcTz-4DunI/V2Ip0xg_peI/AAAAAAAAF24/iYMJC95cw_8GZp3_00VWkKsai8DvQCftgCLcB/s320/P1000112.JPG"/></a>

<br/>

We also went outside on the ground floor under the metal main assembly building roof, and saw radio packets, and the units attempting to transfer messages, but no messages came through.  We think that the bundle synchronisation process needs a bit of help when faced with &gt;50% packet loss.  This should be quite possible to achieve.

<br/>

Then we went to a local supermarket to buy lunch, and took the Mesh Extenders with us.  One stayed in the car in the underground car park, and the other we took with us into the shopping centre.  Here is our Mesh Extender in its special shopping centre disguise vehicle:
<br/>

<a href="https://3.bp.blogspot.com/-C7lYNMH-u_o/V2Ip1Tb6TGI/AAAAAAAAF3A/KV2O50HkO4Y8WFNjvm3NSzfQkYjQ0DJ3gCLcB/s1600/P1000113.JPG"><img src="https://3.bp.blogspot.com/-C7lYNMH-u_o/V2Ip1Tb6TGI/AAAAAAAAF3A/KV2O50HkO4Y8WFNjvm3NSzfQkYjQ0DJ3gCLcB/s320/P1000113.JPG"/></a>
<br/>

<a href="https://2.bp.blogspot.com/-nmVCw5cOfqU/V2Ip2Ms6yuI/AAAAAAAAF3M/UMS-zX-Ha9MC3p_e-0Axk-AEmRsKta3oACLcB/s1600/P1000115.JPG"><img src="https://2.bp.blogspot.com/-nmVCw5cOfqU/V2Ip2Ms6yuI/AAAAAAAAF3M/UMS-zX-Ha9MC3p_e-0Axk-AEmRsKta3oACLcB/s320/P1000115.JPG"/></a>
<br/>

This was quite nice, with one of our work experience students sending text messages down to the car park, and receiving delivery confirmations in the supermarket.

<br/>

So, in other words, it lives!  Hopefully we will have more updates soon, as we start testing the resulting capabilities more thoroughly and in different contexts, particularly outdoors.
<br/>
<div></div>
</div>