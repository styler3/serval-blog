+++
date = "2013-11-19"
title = "Don't Panic, it's a Serval Mesh Extender"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3941652092800042254" itemprop="description articleBody">
I have been working on the firmware for the Mesh Extenders the last couple of weeks.<br/>
<br/>
This has involved combining a few features to make a 0.01 release that can go out on the perk Mesh Extenders, as well as some WR703N-based mesh extenders we are preparing for a monastery (more on that in a later post). <br/>
<br/>
I wanted the firmware to support updating of the servald binary and config file, as well as preventing login as root in normal operation, and operating a captive portal so that people connecting to a mesh extender get some idea of what is going on. It also needs to support the different hardware types we are using.<br/>
<br/>
This is all finally coming together as the following image shows.   The captive portal automatically pops up on my Mac if I associate with a mesh extender by Wi-Fi.<br/>
<br/>

<a href="http://3.bp.blogspot.com/-w2s_QBvW7A0/UoxdMjNKhfI/AAAAAAAABjo/bpGyVV3wVIk/s1600/Captive+Network+AssistantScreenSnapz001.png"><img src="http://3.bp.blogspot.com/-w2s_QBvW7A0/UoxdMjNKhfI/AAAAAAAABjo/bpGyVV3wVIk/s640/Captive+Network+AssistantScreenSnapz001.png"/></a>
<br/>
I'll talk more about the firmware structure later, and document it on the wiki.  Anyone wanting to take an early look can checkout the <a href="http://github.com/gardners/mesh-extender">source code</a> and look in the somewhat erroneously named mr3020 directory.<br/>
<br/>
But for now, I am happy that we have the main functions of the mesh extender firmware functioning.
<div></div>
</div>