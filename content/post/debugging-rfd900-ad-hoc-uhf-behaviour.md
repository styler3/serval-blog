+++
date = "2015-10-21"
title = "Debugging RFD900 Ad-Hoc UHF behaviour"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-2821876179137443684" itemprop="description articleBody">
So I am getting closer to having working ad-hoc UHF communications between Mesh Extenders with RFD900 family radios running our custom CSMA firmware (not that for now you need a spectrum license from your local regulator to do this at &gt;3mW in most countries).<br/>
<br/>
Now I am debugging why MeshMS messages are not being delivered in reasonable time. It seems that lbard is not making the most sensible choices in terms of which piece of which bundle to transmit. <br/>
<br/>
However, I need a nice way to see what it thinks it is transmitting, without having to stop lbard and run it in debug mode, which of course loses the accumulated state in lbard, and thus might cause the bug to disappear.<br/>
<br/>
To address this, I am implementing a function to dump the current state of lbard in HTML so that it can be read wirelessly using the web server on the Mesh Extender to serve it up.  This will show the calculated priority of the bundles on each node, as well as their information about neighbours and in-progress transfers from neighbours.  Hopefully with that I will be able to track down the remaining priority bugs quite quickly.
<div></div>
</div>