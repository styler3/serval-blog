+++
date = "2013-02-12"
title = "Building Serval Mesh Helper Device Prototypes"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1321077374062219513" itemprop="description articleBody">
We finally have all the bits and pieces we need to assemble three prototype Serval Mesh Helper (SMH) devices, that under ideal conditions should be able to support links over tens of kilometres, instead of the tens of metres that WiFi is capable of.  
<a href="http://1.bp.blogspot.com/-TuZhdYr6Atc/URrrbUq6qGI/AAAAAAAAAu4/23iIEhckWFc/s1600/20130213_111906.jpg"><img src="http://1.bp.blogspot.com/-TuZhdYr6Atc/URrrbUq6qGI/AAAAAAAAAu4/23iIEhckWFc/s320/20130213_111906.jpg"/></a>
<div>
<br/><div>
<br/></div>
<div>
The SMH has an embedded router (TP-LINK WR703Ns running OpenWRT -- see <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:meshhelper:prototyping_on_mp2&amp;#etc_config_wireless">http://developer.servalproject.org/dokuwiki/doku.php?id=content:meshhelper:prototyping_on_mp2&amp;#etc_config_wireless</a> for more information) running the Serval Mesh software with 802.11n WiFi  running in ad-hoc mode so that the SMH's can mesh with each other.  They will simultaneously run in access-point mode so that phones can connect to them as WiFi clients, and hence not need to be rooted or otherwise able to do ad-hoc mode. This is the core functionality of the helper device.</div>
<div>
<br/></div>
<div>
The other capability in the helper is a long-range UHF radio operating in an appropriate ISM band, so that the mesh helpers can communicate over long distances. We are using RFD900 radios from <a href="http://rfdesign.com.au/">rfdesign.com.au</a>.</div>
<div>
<br/></div>
<div>
The fundamental components draw less than 1W sustained, and it can probably be optimised down to somewhere around 0.3W on average.</div>
<div>
<br/></div>
<div>
Here are some pictures of the assembly of these units.</div>
<div>
<br/></div>
<div>
First, for the power supply for the radio and RFD900s, we are using UBECs (little 5v switch-mode power supplies that are great for running from batteries).  The RFD900s can be powered from USB to TTL serial cables (we are using FTDI ones at the moment), but at full power it is a bit too much for the WR703N's to pass through, so we are powering them separated. </div>
<div>
<br/></div>
<div>
This entailed soldering up a power connector that can plug into the UBEC and provide the correct power outlets for the WR703N and the RFD900 radio.</div>
 <br/>

<a href="http://4.bp.blogspot.com/-haOcyyRtX1I/URrrVYHf-cI/AAAAAAAAAt8/04HWieXFaj8/s1600/20130212_145558.jpg"><img src="http://4.bp.blogspot.com/-haOcyyRtX1I/URrrVYHf-cI/AAAAAAAAAt8/04HWieXFaj8/s320/20130212_145558.jpg"/></a>

<br/>

<a href="http://2.bp.blogspot.com/-2GJ8CTB4diU/URrrUwXAdrI/AAAAAAAAAtw/VN0sBRMlgp8/s1600/20130212_145929.jpg"><img src="http://2.bp.blogspot.com/-2GJ8CTB4diU/URrrUwXAdrI/AAAAAAAAAtw/VN0sBRMlgp8/s320/20130212_145929.jpg"/></a>
<br/>
Then it was a case of plugging all the bits together.  The following shot shows the connections to the radio modules:<br/>
<br/>

<a href="http://3.bp.blogspot.com/-qdFWS5AEWjo/URrrbjw-6rI/AAAAAAAAAu8/q0M7JVJ9ZuY/s1600/20130213_111916.jpg"><img src="http://3.bp.blogspot.com/-qdFWS5AEWjo/URrrbjw-6rI/AAAAAAAAAu8/q0M7JVJ9ZuY/s320/20130213_111916.jpg"/></a>

Basically the black wires go on the left-hand edge, with the serial cable underneath, and the power connector on top.
<br/>
<br/>
We need a USB memory stick for extra storage (the WR703N has only 4MB flash, much too small for a Serval Rhizome node that might want to cache giga-bytes of data), which entailed adding a passive USB hub so that both the radio and memory stick could share the single USB port on the WR703N.<br/>
<br/>
We are powering the components from large 120Wh LiFePO4 batteries, that should be able to run these units for close to a week.  We opted for using car accessory power connectors as vehicle power is the most likely backup power source we expect to encounter:<br/>
<br/>

<a href="http://1.bp.blogspot.com/-TuZhdYr6Atc/URrrbUq6qGI/AAAAAAAAAu4/23iIEhckWFc/s1600/20130213_111906.jpg"><img src="http://1.bp.blogspot.com/-TuZhdYr6Atc/URrrbUq6qGI/AAAAAAAAAu4/23iIEhckWFc/s320/20130213_111906.jpg"/></a>
<div>
</div>

<br/>

One of the (many) nice things about the RFD900 radios is that they support antenna diversity.  We take advantage of this by plugging in two antennae on perpendicular axes, so that we get horizontal and vertical polarisation (assuming we hang them vertically in the box).  We also have some +6db yagis for when the need arises.

<br/>
 On the charging side of the batteries we used some nice connectors that we also fitted to our RedArc solar regulator, so that we can charge the batteries easily, including while using them to run the helper devices. <br/>
<br/>
With such large batteries it is really important to make sure you have everything fused and protected against short-circuit, especially since we will be flying with these and don't want to accidently melt a hole in a plane.<br/>
<br/>

<a href="http://4.bp.blogspot.com/-PaeiT3JTG7o/URrrXxmyipI/AAAAAAAAAuQ/knldDtiHlMk/s1600/20130212_154706.jpg"><img src="http://4.bp.blogspot.com/-PaeiT3JTG7o/URrrXxmyipI/AAAAAAAAAuQ/knldDtiHlMk/s320/20130212_154706.jpg"/></a>
<br/>
Then it was time to think about a convenient container that would fit everything, be easy to carry around, and be weather proof enough for use at KiwiEx 2013 in a couple of weeks time.  Some $10 storage tubs did the trick.  We will put a small bag of rice in each when we take them on field to absorb any condensation in the tubs.  You can see everything in there happily running:<br/>

<a href="http://1.bp.blogspot.com/-MUVpBkChkkQ/URrrYwx7mTI/AAAAAAAAAuc/L_Oqgd10RLs/s1600/20130213_111334.jpg"><img src="http://1.bp.blogspot.com/-MUVpBkChkkQ/URrrYwx7mTI/AAAAAAAAAuc/L_Oqgd10RLs/s320/20130213_111334.jpg"/></a>
<br/>

<a href="http://4.bp.blogspot.com/-opNoXRyiXpQ/URrrZncURfI/AAAAAAAAAuk/8f1Yfvnbf_o/s1600/20130213_111342.jpg"><img src="http://4.bp.blogspot.com/-opNoXRyiXpQ/URrrZncURfI/AAAAAAAAAuk/8f1Yfvnbf_o/s320/20130213_111342.jpg"/></a>
<br/>

<a href="http://3.bp.blogspot.com/-zod6yswM5Kg/URrrZiEj5PI/AAAAAAAAAuo/nvXAjZf_pKA/s1600/20130213_111359.jpg"><img src="http://3.bp.blogspot.com/-zod6yswM5Kg/URrrZiEj5PI/AAAAAAAAAuo/nvXAjZf_pKA/s320/20130213_111359.jpg"/></a>
<br/>
</div>
<div></div>
</div>