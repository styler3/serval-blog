+++
date = "2017-01-16"
title = "OpenWRT doesn't see packages from custom feed"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-237264863543303442" itemprop="description articleBody">
Just a quick post to document a problem we encountered with adding a feed to an OpenWRT build process for the Serval Mesh Extender, and how we fixed it.<br/>
<br/>
We followed the process in <a href="https://wiki.openwrt.org/doc/devel/feeds">https://wiki.openwrt.org/doc/devel/feeds</a> to add a new feed, by:<br/>
<br/>
1. Modifying feeds.conf (copying feeds.conf.default, if required)<br/>
2. Running <span>./scripts/feeds update customfeed</span>, with customfeed replaced with the name of the new feed.<br/>
3. Running <span>./scripts/feeds install -p customfeed</span>,  again with customfeed replaced by the name of the new feed.<br/>
<br/>
However, when we did this, and then ran <span>make menuconfig</span>, our new packages were nowhere to be seen.<br/>
<br/>
We solved this by running the following additional command:<br/>
<br/>
<span>./scripts/feeds install -a customfeed</span>
<div></div>
</div>