+++
date = "2016-02-24"
title = "TP-Link Firmware Lockdown and Alternative (Better!) Hardware for Mesh Extenders"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6048851427625794110" itemprop="description articleBody">
TP-LINK are starting to lock down the firmware on their routers.  This is a bad idea, because it means that there will be more and more routers out there that have horribly out of date and vulnerable firmware, that cannot be updated and secured by end-users, or in our case, re-purposed to meet their individual and/or humanitarian needs.  This is rather sad.<br/>
<br/>
Fortunately, there are manufacturers making what are basically souped up clones of the cheap TP-LINK routers, such as the WR703N and MR3020 that we have been using for the Mesh Extender prototypes.<br/>
<br/>
One that has caught our eye is this one:<br/>
<br/>
<a href="https://wiki.openwrt.org/toh/gl-inet/gl-ar150">https://wiki.openwrt.org/toh/gl-inet/gl-ar150</a><br/>
<br/>
Which you can buy from places like this:<br/>
<br/>
<a href="http://www.aliexpress.com/item/GL-iNet-6416A-150Mbps-802-11g-b-n-SMART-Mini-WiFi-Wireless-Router-OPENWRT-ENGLISH-Firmware/32273181856.html">http://www.aliexpress.com/item/GL-iNet-6416A-150Mbps-802-11g-b-n-SMART-Mini-WiFi-Wireless-Router-OPENWRT-ENGLISH-Firmware/32273181856.html</a><br/>
<a href="http://www.aliexpress.com/item/GL-iNet-AR-150-150Mbps-OPENWRT-Firmware-Mini-Routers-Wi-Fi-Router-WiFi-Repeater-Booster-Extender/32464052719.html">http://www.aliexpress.com/item/GL-iNet-AR-150-150Mbps-OPENWRT-Firmware-Mini-Routers-Wi-Fi-Router-WiFi-Repeater-Booster-Extender/32464052719.html</a><br/>
<br/>
It comes with OpenWRT DD 14.07 pre-installed, has 64MB RAM (instead of 32MB in the MR3020) and 16MB FLASH (instead of the tiny 4MB on the MR3020), has the serial port already with a header on it (unlike the fiddly soldering process on the MR3020), and also has a few GPIOs on the same header (none on the MR3020), and has two ethernet ports (instead of one on the MR3020).   Oh yes, and if you don't mind paying an extra US$5, <b><i>which still brings the price to only almost what an MR3020 costs</i></b>), you can have an external Wi-Fi antenna, which will be sure to increase the range compared with the PCB antennae on the MR3020 (which we hope to verify soon).<br/>
<br/>
In short, it is at least as good, if not better, on every technical measure when compared with the MR3020 and WR703N, and they are also cheaper! In fact, <b>we can get the external antenna version express international couriered via DHL from China for less than we have to pay for an MR3020 via ebay in Australia</b>!<br/>
<br/>
Further, with the extra flash, we should be able to make a Mesh Extender install package set that can just be installed on it, because there is actually enough room in the flash for servald, lbard and the various scripts and things we need. Combine that with the fact that we have a real physical header that we can use to connect between the RFD900 radio and the router PCB, avoiding the need for any soldering at all*, the physical assembly process is now greatly simplified. This makes us very happy about the prospect of making Mesh Extenders easier to build and provision, including for people who aren't big on soldering.<br/>
<br/>
All we will need to have is some special little cable made that goes between the headers on the PCB, and the RFD900 radio, and an updated case design.<br/>
<br/>
Now, about that little * about "no soldering", the only problem we have remaining is that the headers which come on the board don't have a 5V line populated, so we will still need to solder a header on, assuming that the Power-Over-Ethernet header has access to the 5V rail, which seems like a reasonable prospect.  We will take a look at this when the 5 units that we have ordered have arrived. In any case, soldering on just a header is not a big problem, and we might even be able to ask the manufacturer to prepare a batch with the header fully populated.  Likewise, we can probably ask some company in China to make up the little adapter cables that we will want to go between the radio and PCB.<br/>
<br/>
We wouldn't have found these units if TP-LINK weren't being unhelpful with their firmware lockdown policy, so in this particular case it is a clear example where being unfriendly to the open-source will result in<br/>
<br/>
<div></div>
</div>