+++
date = "2017-10-17"
title = "Setting up Mesh Extender capability within NZ Red Cross"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1025734472203374582" itemprop="description articleBody">
I am briefly in Wellington, NZ, visiting NZ Red Cross on my way to the Global Humanitarian Technology Conference where we have a bunch of papers to present at the end of the week.<br/>
<br/>
One purpose of the visit was to update the firmware on the Mesh Extenders we had previously provided NZ Red Cross with, and to transfer the knowledge of how to flash the Mesh Extenders to their IT &amp; Telecomms Emergency Response Unit (IT&amp;T ERU), so that they can do it themselves in the future.<br/>
<br/>
As the ERU does not normally carry laptops running Linux, we found an old disused laptop, and installed Ubuntu on it, and replicated the build and flashing environment from my laptop.<br/>
<br/>
The important parts were to setup a TFTP server on the laptop, copy the firmware files in there, and clone the <a href="https://github.com/servalproject/openwrt-packages/">Mesh Extender openwrt-packages repository from github</a>, checkout the MeshExtender2.0 branch, compile the auto-flash program.<br/>
<br/>
After that, it is just a case of running the auto-flash program with a USB to serial adapter connected to a specially made adapter cable, and connecting the Mesh Extenders and watching the output of auto-flash to see when a unit has been flashed.<br/>
<br/>
Natalie from the ERU was super-helpful being our guinnea pig, and also in documenting the process.  Hopefully we will get the documentation up on the wiki in the near future, at which point I will link to it from this post.<br/>
<br/>
But in the meantime, the following photo shows the completed kit, with the USB serial adapter cable, ethernet cable for TFTP, USB memory stick with Ubuntu so that it can be cloned to other laptops in the future, all in a fashionable marigold laptop case.  <a href="https://en.wikipedia.org/wiki/Cat_(Red_Dwarf)">The Cat</a> may object wearing gold and marigold at the same time, but we are quite happy with the result for now.<br/>
<br/>
<br/>
<br/>

<a href="https://2.bp.blogspot.com/-0Lnox1a9bwc/WeaSHf1A3xI/AAAAAAAAGjw/9u8UB8zfKLU0wY8JmXuChqPvrqNYlOYdACLcBGAs/s1600/IMG_20171018_105157-NZRC-ERU-MeshExtender-Flashing-Kit.jpg"><img src="https://2.bp.blogspot.com/-0Lnox1a9bwc/WeaSHf1A3xI/AAAAAAAAGjw/9u8UB8zfKLU0wY8JmXuChqPvrqNYlOYdACLcBGAs/s400/IMG_20171018_105157-NZRC-ERU-MeshExtender-Flashing-Kit.jpg"/></a>
<br/>
<div></div>
</div>
