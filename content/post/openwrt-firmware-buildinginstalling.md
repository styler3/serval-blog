+++
date = "2017-07-30"
title = "OpenWRT firmware building/installing problem"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6241182735065877903" itemprop="description articleBody">
I'm currently working on the firmware for the Mesh Extenders, and have hit an unexpected problem:<br/>
<br/>
Whereas we have previously been able to easily build and flash OpenWRT firmware images onto the Domino Core modules (Atheros 71xx based, Chaos Chalmer derived firmware), it has suddenly stopped working with nasty errors from uboot, like this:<br/>
<br/>
<span>uboot&gt; boot<br/>Booting image at: 0x9F050000<br/><br/>   Image name:   MIPS OpenWrt Linux-3.18.45<br/>   Created:      2017-07-10  23:59:50 UTC<br/>   Image type:   MIPS Linux Kernel Image (lzma compressed)<br/>   Data size:    5328879 Bytes = 5.1 MB<br/>   Load address: 0x80060000<br/>   Entry point:  0x80060000<br/><br/>Uncompressing kernel image... ## Error: LZMA error num: 1<br/>uboot&gt; </span><br/>
Anyone who can provide some assistance or suggestions as to how to go about tracking the problem down and fixing it would be greatly appreciated.<br/>
<br/>
Some clues so far:<br/>
<br/>
1. The firmware file from <a href="http://www.gl-inet.com/firmware/domino/v1/openwrt-domino-2.261.bin">http://www.gl-inet.com/firmware/domino/v1/openwrt-domino-2.261.bin</a>, and that works, so I presume that both uboot and the hardware are working.<br/>
<br/>
2. We used to build and flash firmware from an Ubuntu VM in a Mac.  This problem has come about since moving to a native Ubuntu 16.04 based machine.<br/>
<br/>
3. Firmware built on the Mac, which we believe used to work, doesn't seem to worrk now.<br/>
<br/>
4. When this first occurred, it looked like we might have had a problem with a USB power plug, so we have ditched that, and are now running the boards from a USB port on the laptop.  It is in this configuration that we have successfully installed the firmware file mentioned in (1).<br/>
<br/>
5. I *did* manage to build some working firmware images on Friday with the Linux laptop, and apart from using old versions of Serval packages, they seemed to work, before putting updated versions on stopped working.<br/>
<br/>
I'll likely update this post with progress of things as I try them.<br/>
<br/>
<b>UPDATE 01AUG17:</b> It looks like the problem is that we can't flash from uboot while a microSD card is inserted. <br/>
<h2>
Works</h2>
<h3>
1. gl-inet openwrt-domino-2.261.bin installed from Linux laptop via "run lf" + tftp</h3>
<h3>
2. Freshly built openwrt image built from Linux laptop without Mesh Extender package, and on an older test board, that was never powered by the presumed faulty USB power plug, and with no microSD card inserted. [01AUG17]</h3>
<h3>
3. Freshly built openwrt image built from Linux laptop without Mesh 
Extender package, on one previously powered by 
the presumed faulty USB power plug, and without a microSD card inserted. [01AUG17]</h3>
<h2>
Doesn't Work</h2>
<h3>
1. openwrt-ar71xx-generic-uImage-initramfs-lzma.bin built on Ubuntu 16.04 laptop from github.com/servalproject/openwrt</h3>
<h3>
</h3>
<h3>
2. Freshly built openwrt image built from Linux laptop without Mesh 
Extender package, on one previously powered by 
the presumed faulty USB power plug, and with a microSD card inserted. [01AUG17]</h3>
<h2>
</h2>
<div></div>
</div>