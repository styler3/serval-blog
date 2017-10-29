+++
date = "2013-07-12"
title = "Smaller, more elegant Mesh Extender prototype"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1462316316398133658" itemprop="description articleBody">
(Please check out our crowd-funding campaign at <a href="http://igg.me/at/speakfreely">http://igg.me/at/speakfreely</a> to help us turn the Mesh Extender into a product that can be used to help people communicate in difficult circumstances.)<br/>
<br/>
There is nothing like being busy to increase the incentive to just get something done in spite of the things that make it impossible. <br/>
<br/>
So today I decided that I would actually get around to making a Mesh Extender prototype out of a TP-Link MR3020 wireless router.<br/>
<br/>
These have an Atheros 9k chipset, so they have the good Wi-Fi chip that we need, which is usually the tricky bit. They have a USB port for the mass storage that Rhizome needs to run.  So far so good.<br/>
<br/>
The previous TP-Link (WR703N) routers we used didn't have an easily accessible serial port -- they just had a couple of tiny points on the PCB you could solder to.<br/>
<br/>
In contrast, the MR3020 has real hole-through pins that can take a standard 0.1" single-inline header, and some of the earlier builds actually have the connector installed.<br/>
<br/>
With the help of a work-experience student we put OpenWRT on several of the MR3020s and got them about half-way to working as Mesh Extenders, able to mesh over Wi-Fi.<br/>
<br/>
That just left the serial connection to the UHF packet radio, which is what I attacked today.<br/>
<br/>
The serial port normally has a login and is used to log kernel messages.  After figuring out how to turn off as much of that as possible short of recompiling the kernel, I then set about connecting up one of the packet radio modules and getting some holes drilled so that we could put the RFD900 packet radio in the little case.  Well, mostly in the case, because the heat-sink sticks out a bit. <br/>
<br/>
The following pictures show how this makes a neat little unit:<br/>
<br/>

<a href="https://1.bp.blogspot.com/-jkmw1l92E0s/Ud-r1QqKvKI/AAAAAAAABLs/kno1pgluGzE/s1600/MeshExtender-Prototype-CloseUp.jpg"><img src="https://1.bp.blogspot.com/-jkmw1l92E0s/Ud-r1QqKvKI/AAAAAAAABLs/kno1pgluGzE/s320/MeshExtender-Prototype-CloseUp.jpg"/></a>
<br/>
<br/>

<a href="https://1.bp.blogspot.com/-oFjXQeboUjM/Ud-r02PT4zI/AAAAAAAABLg/CiAm-Ppb0wQ/s1600/MeshExtender-Prototype-InHand.jpg"><img src="https://1.bp.blogspot.com/-oFjXQeboUjM/Ud-r02PT4zI/AAAAAAAABLg/CiAm-Ppb0wQ/s320/MeshExtender-Prototype-InHand.jpg"/></a>
<br/>

<a href="https://2.bp.blogspot.com/-QkzDuQEthxU/Ud-r0w27MxI/AAAAAAAABLk/lo-h6XX2bx4/s1600/MeshExtender-Prototype-Oblique.jpg"><img src="https://2.bp.blogspot.com/-QkzDuQEthxU/Ud-r0w27MxI/AAAAAAAABLk/lo-h6XX2bx4/s320/MeshExtender-Prototype-Oblique.jpg"/></a>
<br/>
We have some Verbatim nano USB memory sticks on order so that we can replace the big USB drive on the side with a little tiny bump, which will further stream line the shape.<br/>
<br/>
That leaves only the battery to consider, and we have a few options for those.<br/>
<br/>
Importantly, we have shed the USB hub and USB to serial adapter, which between them were consuming perhaps 20% of the total power budget, and made the resulting prototypes frustratingly large. <br/>
<br/>
Indeed, compare the images below of the older prototypes to the images above, where the only missing component is a battery connected to the USB port of the MR3020.<br/>
<br/>

<a href="https://1.bp.blogspot.com/-TuZhdYr6Atc/URrrbUq6qGI/AAAAAAAAAu4/23iIEhckWFc/s1600/20130213_111906.jpg"><img src="https://1.bp.blogspot.com/-TuZhdYr6Atc/URrrbUq6qGI/AAAAAAAAAu4/23iIEhckWFc/s320/20130213_111906.jpg"/></a>
<br/>

<a href="https://3.bp.blogspot.com/-zod6yswM5Kg/URrrZiEj5PI/AAAAAAAAAuo/nvXAjZf_pKA/s1600/20130213_111359.jpg"><img src="https://3.bp.blogspot.com/-zod6yswM5Kg/URrrZiEj5PI/AAAAAAAAAuo/nvXAjZf_pKA/s320/20130213_111359.jpg"/></a>
<br/>
<br/>
Once we cut a hole for the heat-sink and get the lid fitting back on, and install the nano USB sticks, we should have a nice pocket-sized prototyping platform from which to refine.<br/>
<br/>
<div></div>
</div>