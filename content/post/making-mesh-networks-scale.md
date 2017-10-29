+++
date = "2011-08-28"
title = "Making Mesh Networks Scale"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6688718813183338319" itemprop="description articleBody">
Mesh networks have great potential to create sustainable, resilient and low-cost communications capabilities.  This is why we are passionate about mesh networking at <a href="http://servalproject.org/">Serval Project</a>.<br/>
<br/>
However, the mesh routing protocols that I have seen to date almost all have a scalability ceiling.  This is because if you have 10 devices all talking to each other you get 100 messages, but if you have 1,000 devices all talking to each other you get 1,000,000 messages in the same time.  In computer science we would say that a mesh network has a complexity of O(N^2), because the mesh traffic scales with the square of the number of devices.<br/>
<br/>
Eventually, not matter how fast the links on the mesh, the capacity gets used up. <br/>
<br/>
Even on a "quiet" mesh where most of the devices aren't saying much, they still have to share O(N^2) information, and so the mesh just existing eventually causes it to collapse under its own weight.<br/>
<br/>
What would be nice is a more graceful degradation, so that even in a mesh of say, 7 billion devices, that each local pool of devices could talk to one another, even though it would be impossible to allow all 7 billion to talk to each other.<br/>
<br/>
It might seem pointless to allow a device to see only a few thousand nearby devices, as that represents only about 0.00001% of the devices on such a global mesh.<br/>
<br/>
However, for telephony at least, it turns out that most phone calls are at most a few kilo-metres away, and thus would be possible over such a "local patch" on the global mesh.<br/>
<br/>
So this is something that Serval is planning to do over the next few months. <br/>
<br/>
We are going to take the BATMAN mesh routing protocol and modify it so that it can keep track of "near by" devices on the mesh without being swamped by location information from devices on the other side of the world (which from my perspective is probably you, because I live in Australia, which is on the other side of the world from most other places ;).
<div></div>
</div>