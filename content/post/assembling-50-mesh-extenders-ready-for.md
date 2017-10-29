+++
date = "2017-08-28"
title = "Assembling 50 Mesh Extenders ready for Vanuatu"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3410278511997051987" itemprop="description articleBody">
Tomorrow we fly out to Vanuatu for our third visit. <br/>
<br/>
This means we need to have several dozen Mesh Extenders ready to take with us, to hopefully begin deploying in Port Vila between various government and NGO sites, and assuming we get the final authorities through, to also connect a couple of outlying villages.<br/>
<br/>
From a practical stand point, this means flashing 50 Mesh Extender boards, 50 RFD900+ radios, 50 boot loaders, and pre-formatting and putting the default files on 50 USB memory sticks, and then assembling the boards in their cases.<br/>
<br/>
Flashing the radios is fairly simple, and can be done using an FTDI USB serial cable in about a minute.  I did those last night while sitting at the computer after the kids went to bed.<br/>
<br/>
For the boot loaders and OpenWRT firmware, <a href="https://github.com/servalproject/openwrt-packages/tree/MeshExtender2.0/auto-flash">I wrote a simple program</a> today that listens on a serial port for the uboot boot loader, and then directly issues the commands to flash first the boot loader, and then the firmware.  When it has finished, it runs vlc and plays an MP3 file to alert me that it is ready for the next board, thus saving lots of dead time between flashing boards.  It went smoother with the team in the lab when I stopped playing the <a href="https://www.youtube.com/watch?v=xxhP6vD3unY">music from Wizball</a>, and switched to <a href="https://ia800208.us.archive.org/33/items/ClassicalGuitar-Greensleeves/Greensleeves__Sir_John.mp3">Greensleves</a>.<br/>
<br/>
Apart from some niggly problems with the USB serial adapter drivers causing the port to stop reading data, the while process takes only a minute or two.  This is allowing us to plough through flashing the boards much faster than expected, which is good (I have been interrupted by VLC playing Greensleves at me several times while writing this post).<br/>
<br/>
Here is my bench setup, as I flash a board.  Firmware and boot loader updates are loaded via ethernet from a tftp server on my laptop. Commands are via serial through an adapter on the radio/power connector on the Mesh Extender, and power for the Mesh Extender comes via the micro-USB connector on the Mesh Extender board which exists for that single purpose (it doesn't actually provide an USB data signals):<br/>
<br/>

<a href="https://4.bp.blogspot.com/-Dl4HCY-PgAM/WaTftQMs3iI/AAAAAAAAGdQ/qYDzzOrLfgkgHLew6ZPQoniGxODHrq5YwCLcBGAs/s1600/IMG_20170829_114229.jpg"><img src="https://4.bp.blogspot.com/-Dl4HCY-PgAM/WaTftQMs3iI/AAAAAAAAGdQ/qYDzzOrLfgkgHLew6ZPQoniGxODHrq5YwCLcBGAs/s400/IMG_20170829_114229.jpg"/></a>
<br/>
The harder part is the assembly.  You can see three of our great students who are helping with the assembly:<br/>
<br/>
<br/>

<a href="https://2.bp.blogspot.com/-T6lLaeB7_b8/WaTftcw14LI/AAAAAAAAGdM/GPeYtfKm3hkm9qjqafTV-DqGPDwAgP_kgCLcBGAs/s1600/IMG_20170829_114243.jpg"><img src="https://2.bp.blogspot.com/-T6lLaeB7_b8/WaTftcw14LI/AAAAAAAAGdM/GPeYtfKm3hkm9qjqafTV-DqGPDwAgP_kgCLcBGAs/s400/IMG_20170829_114243.jpg"/></a>
<br/>
Ryan is checking that the boards have correctly flashed and boot and begin transmitting via the UHF packet radio.<br/>
<br/>
Then we have to get the boards into their cases. This is the fun part, because this revision of the PCBs has the wrong D-SUB 25 connector compared to what we wanted, but due to time constraints we are stuck with them for this batch.  The problem is that the D-SUB connectors have holes for screws, but are not threaded.  This means we have to put washers and nuts on the back of the connectors, which are frustratingly located in rather awkward locations, as shown here marked by the yellow arrows.  <br/>
<br/>

<a href="https://3.bp.blogspot.com/-LhRAlBb1590/WaTiH9nraPI/AAAAAAAAGdc/Il9ZgIsCmTINttuys5M-a0tUe8X1-Y9WACLcBGAs/s1600/IMG_20170829_130624.jpg"><img src="https://3.bp.blogspot.com/-LhRAlBb1590/WaTiH9nraPI/AAAAAAAAGdc/Il9ZgIsCmTINttuys5M-a0tUe8X1-Y9WACLcBGAs/s400/IMG_20170829_130624.jpg"/></a>
<br/>
Those locations are right in the bottom of the shell, about 55mm down. 
For the one on the left, the super-capacitor is in the way, all making 
it rather difficult to get in there to install the washer and nut on 
each.  <i>Very</i> annoying. Our current least-bad solution is to use some <a href="http://au.element14.com/duratool/cl5045/seizer-straight/dp/1421548?MER=bn_level5_5NP_EngagementRecSingleItem_1">seizers</a>. <br/>
<br/>
So that's our afternoon today, basically getting enough of these assembled, ready to go, as well as getting everything packed in the big case ready to fly out tomorrow.
<div></div>
</div>