+++
date = "2017-01-16"
title = "Mesh Extender 2.0 second revision prototype boards"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7696116202547419334" itemprop="description articleBody">
The second revision of the Mesh Extender 2.0 (ME2.0) PCBs have arrived.  These were manufactured at almost miraculous speed by RF Design ahead of the Christmas break.  They contain fixes for three of the main problems we encountered with the first revision, fixing problems with both the ethernet and serial level-converter interfaces, as well as the bootstrap pull-up and pull-down on the Domino Core Atheros 9k module.  Here is the new PCBs:<br/>
<br/>
Ethernet - both ethernet ports now work nicely.  One is capable of giga-bit, but sometimes it only connects at 100mbit/sec.  We need to understand what is going on there.<br/>

<a href="https://3.bp.blogspot.com/-YYPfyr_MTSQ/WHy6bjHEkuI/AAAAAAAAGDM/lOts8jGaHmkFneZg2baZgz3dzwhOmMtfwCLcB/s1600/IMG_20170116_131210.jpg"><img src="https://3.bp.blogspot.com/-YYPfyr_MTSQ/WHy6bjHEkuI/AAAAAAAAGDM/lOts8jGaHmkFneZg2baZgz3dzwhOmMtfwCLcB/s640/IMG_20170116_131210.jpg"/></a>
<br/>

<br/>
Serial port - the serial port now works without problem, since we have switched to a well-known MAXIM part, instead of the TI level converter, that although in principle capable of level-converting serial lines, turns out to be much too glitchy in our situation.  Other people have had similar problems.<br/>
<br/>
The pull-up registers are now correctly set, although we did still have a problem with one of them apparently not being pulled up hard enough, so we have had to install a single resister to ensure that the Ath9k knows to boot from the 16MB flash, instead of from its internal ROM.  This resister can be seen in the photo below:<br/>
<br/>

<a href="https://2.bp.blogspot.com/-KSD-ZRvYszc/WHy6bqMHN2I/AAAAAAAAGDI/UEnnvmkOCasg-mTVWuTfd2TA2kXaSiZiACLcB/s1600/IMG_20170116_131226.jpg"><img src="https://2.bp.blogspot.com/-KSD-ZRvYszc/WHy6bqMHN2I/AAAAAAAAGDI/UEnnvmkOCasg-mTVWuTfd2TA2kXaSiZiACLcB/s640/IMG_20170116_131226.jpg"/></a>
<br/>
We now also have both D-SUB connectors on the same side of the PCB, but having double checked with the 3D-printed case prototype, they are both on the wrong side now, so we will have to fix that in the next revision:<br/>
<br/>

<a href="https://4.bp.blogspot.com/-79qBewOn5pM/WHy6bjBXROI/AAAAAAAAGDQ/6G_Pig4VzMseTD0X0VNaLWlZqV_0VDPnQCLcB/s1600/IMG_20170116_131243.jpg"><img src="https://4.bp.blogspot.com/-79qBewOn5pM/WHy6bjBXROI/AAAAAAAAGDQ/6G_Pig4VzMseTD0X0VNaLWlZqV_0VDPnQCLcB/s640/IMG_20170116_131243.jpg"/></a>
<br/>
We are currently working on building firmware images for this board, so that we can test other functions, which I'll report on in a separate post.
<div></div>
</div>