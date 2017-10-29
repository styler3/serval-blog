+++
date = "2011-09-12"
title = "Why User-Land Mesh Networks Are Necessary For Heterogeneous WiFi Mesh Networks"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-5155843293206904401" itemprop="description articleBody">
The normal approach to creating a mesh network is to write a program that does some tricky stuff to work out how to get from node A to node Z via whatever nodes might be in the middle, and then tell this to the operating system so that packets get routed according to these instructions.<br/>
<br/>
We are doing something different for Serval, in that we are having the program that does all that tricky stuff carry the messages between nodes, instead of asking the operating system to help out.<br/>
<br/>
This has some disadvantages and some advantages.<br/>
<br/>
First, the disadvantages, and why we think that they aren't such a problem for our application. <br/>
<br/>
1. Such "user-land" overlay networks suffer from an inefficiency known as "double-copy", where every packet sent or received ends up getting copied not once by the kernel, but twice, once by the kernel, and once by the overlay program.  This is bad if you are processing lots of data.  But on a mesh network the actual throughput of data tends to be fairly low (it is one of the well known problems with mesh networks).  So this problem is kept under control.<br/>
<br/>
2. Programs that want to know about the mesh network need to know about the overlay and have to use special calls to talk to the mesh.  This is bad if your primary goal is allowing people to run BitTorrent, SSH, for example, because you need to modify each of those programs to support the new network, and without operating system cooperation that can get a little messier than you might like.<br/>
<br/>
However, for a mesh telephony platform, and where we know that bandwidth starvation is one of the greatest potential problems, there is actually merit in requiring people to go to some effort before they enable their application to consume the limited resources of the mesh.  We will be adding the support to the initial core applications we intend to run over the mesh, so this isn't really a big deal.<br/>
<br/>
Now for some advantages:<br/>
<br/>
1. We don't need operating system cooperation.  This makes it easier to port the mesh to all operating systems, both desktop and mobile.  It is especially important because the need to fiddle with routing tables requires root/administrative access on most platforms.<br/>
<br/>
For mobile platforms, this is certainly true on Android, and I believe iOS, with together constitute the majority of smart phones.  This alone means that we have to take this path. <br/>
<br/>
But it also gives us some additional upside here, in that it means we could make a USB key loaded with Serval mesh software that could be run on any desktop computer, and without administrative access or being "installed" could enable that computer to participate in the mesh.  In fact, it could probably even be an HTML5 application running in a web browser.<br/>
<br/>
2. It separates us from the underlying network addressing. Many devices and networks only support IPv4, but there aren't enough IPv4 addresses to go around. But by pushing our mesh network addressing into a dedicated addressing layer we can solve this problem. <br/>
<br/>
We use 256bit Elliptic Curve cryptography keys as the basis for our address<br/>
<br/>
In fact, using this approach it is possible for every single Serval enabled device on a mesh to all have the same IPv4 address, provided we use only broadcast traffic, which we do for a very important reason:<br/>
<br/>
Broadcast traffic is the only traffic which WiFi ad-hoc can reliably carry between devices with incompatible or buggy ad-hoc implementations.  For example, we cannot get unicast traffic to flow reliably between Mesh Potatoes and Huawei IDEOS U8150/U8180 phones.  However, we can get unicast traffic to flow between Mesh Potatoes and the original Android G1 developer phones, and between the G1 and the U8150/U8180 phones. <br/>
<br/>
Unfortunately mesh routing protocols all tend to use broadcast traffic to discover available routes, and thus the routes choose the impossible Mesh Potato-U8150/U8180 links, which is very bad indeed.  But by making the mesh traffic itself broadcast we ensure that what the mesh routing protocol and what we are trying to do is the same, instead of merely similar.<br/>
<br/>
Taking this a little further, by transporting the mesh topology management information in the same packets as the data we can directly measure the performance of the mesh delivering the traffic we really care about, rather than using different packets as an indirect measure -- especially since the distribution of packet sizes can otherwise be very different, and WiFi packet losses are not insensitive to packet length or differentiation between broadcast and unicast traffic.<br/>
<br/>
Implementing this is of course a significant undertaking, and I have already spent a few weeks programming away.  But the effort is beginning to yield results.  Today for the first time I have the new overlay mesh detecting nodes and building the in-memory route table. You can see a screen grab here:<br/>
<br/>
<a href="http://4.bp.blogspot.com/-Gxgilgn8CSI/Tm4K9Ji4zvI/AAAAAAAAAC0/EFgHl5Y4axE/s1600/TerminalScreenSnapz001.png"><img src="http://4.bp.blogspot.com/-Gxgilgn8CSI/Tm4K9Ji4zvI/AAAAAAAAAC0/EFgHl5Y4axE/s640/TerminalScreenSnapz001.png"/></a><br/>
So here you can see some debug output from a Serval DNA node running in overlay mode using a file called dummy0 as a dummy network interface.<br/>
<br/>
I realised early in the development of the overlay network that I would need some convenient simulation tools to make it easier to debug the behaviour of the mesh.  I decided the best way to do this was to make the software itself also a network simulator.  So I added support to pretend an ordinary file is a network interface.  Any instances of the overlay pointed to the same file would all append their "packets" to the end of the file, and remember where they had got up to reading from the file, and keep an eye out for any packets deposited by other nodes. <br/>
<br/>
Each packet also has a header that has space for location information, transmission power, time, node velocity and heading and a whole pile of other information that can be used to drop packets that are deemed to have been sent from too far away, or suffering collision during reception and so on.<br/>
<br/>
The file then also represent a log of all activity on the mesh which has already proven very helpful for debugging.  I will also create a tool that allows for the creation of visualisations of the mesh in action to help understand why things go wrong, and to explain the operation of the mesh.  I will post such animations here once I get that far.<br/>
<br/>
Back to the trace, the error messages are mostly information for me for development (although there is on link-list bug that I can see I will need to fix to avoid a memory leak).<br/>
<br/>
There are a few 256bit addresses that can be seen.  The all-f's is the mesh broadcast address, while the one that starts with 9d5f is the address of a node on the mesh. <br/>
<br/>
These addresses are really big, and so I have already implemented a variety of mechanisms for abbreviating the addresses. <br/>
<br/>
For example, the broadcast address is used so often, that it has a one-byte abbreviation (0x0f).  For other addresses, we only need to transmit as much of the address is required for the receiver to discriminate it from all other nodes.  The birthday paradox comes into play here, and means that we typically need about twice the number of bits as the base-2 log of the number of nodes on the network.  For a small network of a few hundred nodes 24 bits (3 bytes) of address is a pleasant over-kill.  Even at a global scale, we need to accomodate around 10 billion addresses = ~2^34 addresses, and so about 70 bits (7 bytes) should be enough.<br/>
<br/>
We also have abbreviation strategies where neighbouring nodes that talk with each other a lot can allocate a one-byte short code for each other, however, as you might be able to guess from the trace that abbreviation method is temporarily disabled in the code to keep my life a little simpler at present -- which is a good move because of the density of new features in the code.<br/>
<br/>
At the end of the trace we see a summary of the overlay routing table which shows 7-digit address prefixes for all know nodes on this network, and the link-scores to each via the various routes known to each.<br/>
<br/>
The scores have two components. The first being a BATMAN-like score derived from beacon counting, although we take into account that the remote node might have different interfaces running at different beacon rates.  The second part is the number of Serval gateways that are on the path. <br/>
<br/>
This gateway count is there to prevent routing loops and other nasties in meshes where the overlay has managed to infer some hierarchy, or where inter-mesh links have been purposely provisioned.<br/>
<br/>
I'll talk about inferred hierarchy in another post, but it is one of several measures we are taking to ensure that a Serval mesh can scale beyond the normal bandwidth-starvation limit imposed by all nodes trying to know about all other nodes all of the time.<br/>
<br/>
Our premise is that you need frequent information for nearby nodes because their "bearing" can change wildly over short time frames, but that for more distant nodes their "bearing" on the mesh should change much more slowly, and so we should be able to cope with less frequent updates about the position of such distant nodes.<br/>
<br/>
But meanwhile, as you can see we are making good progress, and the Serval DNA overlay mesh is beginning to come together.
<div></div>
</div>