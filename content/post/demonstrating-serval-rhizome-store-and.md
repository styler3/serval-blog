+++
date = "2011-11-22"
title = "Demonstrating the Serval Rhizome Store-and-Forward MeshMS SMS Service"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7836560133251563692" itemprop="description articleBody">
(Please take a look at our crowd-funding campaign at <a href="http://igg.me/at/speakfreely">igg.me/at/speakfreely</a>.)<br/>
<br/>
Update: We <a href="http://servalpaul.blogspot.com.au/2012/03/kiwiex-2012-installing-and-updating.html">trialled Rhizome on a training exercise in New Zealand</a> recently.  Follow the link to read the blog post about it.<br/>
<br/>
SMS messages on a cellular network get delivered via the cell towers and message centre infrastructure.<br/>
<br/>
On a mesh, it is possible for us to deliver messages to other phones that are reachable on the mesh at the same time.  This works great, and we have had this capability in the Serval BatPhone software for a while now. <br/>
<br/>
However, it does have some limitations, in particular, if there is no link all the way from the sender to the receiver on the mesh at the instant the message is sent.  This is rather unfortunate, as we usually think of SMS as being the most reliable fall-back on a mobile communications network. <br/>
<br/>
So we set about replicating this resilience by creating a store-and-forward SMS-like service on top of the Serval Rhizome mesh file distribution framework.  We call this MeshMS, for Mesh Message Service.<br/>
<br/>
This service uses direct mesh links if they are available by making use of the existing SMS capability in the Serval BatPhone software.  However, if there is no direct link, then it uses a store-and-forward scheme, that asks any passing phones to copy the message and distribute it to other phones on the mesh, until it (hopefully) eventually reaches its intended destination.  The cartoon below shows how this works. <br/>
<br/>

<a href="https://3.bp.blogspot.com/-F2IB6rfYS20/TsuZlnZAHMI/AAAAAAAAAIY/IvSqEpH2ADg/s1600/store-and-forward-cartoon.png"><img src="https://3.bp.blogspot.com/-F2IB6rfYS20/TsuZlnZAHMI/AAAAAAAAAIY/IvSqEpH2ADg/s640/store-and-forward-cartoon.png"/></a>
<br/>
<br/>
The man wishes to send the message "Prepare the Zeppelin" to his hench-person, but there is no direct mesh link at that time due to the challenging topology.  The message gets picked up (stored) by the compatible phone in the pram, without any action on the part of the woman.  The woman then keeps walking along, and eventually the phone in the pram is able to automatically deliver (forward) the message to the ultimate destination, whereupon the minion knows to ready his master's zeppelin, to do the weekly grocery shopping, one trusts. Of course, there could be many intermediate steps, instead of just the one shown here.<br/>
<br/>
The great thing about this approach is that it doesn't require a complete path to the destination at the time of sending, but can propagate progressively across the mesh as it is able, and can make use of nodes that move between otherwise isolated mesh networks, creating an asynchronous link between them where it would not otherwise be possible.<br/>
<br/>
While the delay in such a service is huge, the bandwidth is also great, as potentially gigabytes of data can be transferred between nodes.  One side use of this protocol that we intend to exploit is to provide an efficient means of distributing updates to the Serval software suite, so that field updates can occur without dependence on infrastructure, and with much greater aggregate bandwidth than any single-cast cellular or wireless approach.  In fact, this will even allow the update of software, maps and other resources during a disaster.<br/>
<br/>
We have even demonstrated it to deliver an SMS message between South Africa and Australia, using nothing but compatible phones to carry the message more than 10,000km:<br/>
<br/>

<iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/KDhJcwsnxf0?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe>
<br/>
<br/>
This feature has profound utility in allowing the exchange of messages, files, and all manner of data in what are otherwise very difficult settings. <br/>
<br/>
It also provides the capabilities required to enable disadvantaged communities, perhaps in remote locations, war zones or informal settlements, to create their own infrastructure, carrier and cost-free SMS networks using compatible handsets, so that they can enjoy the benefits of digital communications that many of us take for granted.
<div></div>
</div>