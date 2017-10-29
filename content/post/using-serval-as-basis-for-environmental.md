+++
date = "2012-10-08"
title = "Using Serval as a Basis for Environmental Monitoring"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3916681083124717182" itemprop="description articleBody">
One of our developers, Corey Wallis, is in the midst of a project with some of the other researchers in the Flinders University Disaster Research Centre (DRC) where they are creating a system to acquire temperature and humidity data from mass gathering events, such as concerts and sports events. <br/>
<br/>
This involves both fixed and mobile devices with sensors continuously collecting data for analysis both at the event and on-line.<br/>
<br/>
One of the tricks is that we can't rely on cellular service being available at these events.  Also, we want all of the field teams who are gathering data to also be able to visualise and act on the data, so we need a many-to-many distribution scheme.<br/>
<br/>
These features make it an good fit for Serval Rhizome, our store-and-forward/Delay Tolerant Networking (DTN) system, that is able to handle both of these requirements, and will result in a very versatile system that can be used anywhere in the world.<br/>
<br/>
Corey has made some good progress on the hardware and software for the data gathering, as can be seen in this blog post:<br/>
<br/>
<a href="http://magdaaproject.org/2012/10/08/mobile-environment-monitoring-software-update/">http://magdaaproject.org/2012/10/08/mobile-environment-monitoring-software-update/</a><br/>
<br/>
Among the next steps are to actually integrate it with the Serval Mesh software so that the data can be shared among the field teams and analysis staff.
<div></div>
</div>