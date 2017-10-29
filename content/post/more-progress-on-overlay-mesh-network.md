+++
date = "2011-09-12"
title = "More progress on the overlay mesh network"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-2034500735029328850" itemprop="description articleBody">
It is 5:58am and dawn is just beginning.<br/>
<br/>
I have been up all night making the best of the need of an overnight sleep study for our son, which requires an adult to perform a specific function every 15 minutes throughout the night.<br/>
<br/>
Programming in these little pieces feels a bit like the software development version of watching commercial television; just as you think you are about to witness something really interesting there is an interruption.<br/>
<br/>
Nonetheless, I have made significant progress getting the overlay mesh to send and receive advertisements of a different kind; notices by one node that they can reach another node.<br/>
<br/>
There are plenty of bugs that I know about, without even thinking about the ones that I don't know about, and also some code that is still plain old missing.  But even so, I have got the code forming a multi-hop mesh and keeping track of the routes to them.<br/>
<br/>
I ran two nodes connected to two separate dummy networks, so that they couldn't see each other.  Then I connected an extra node in the middle that bridged the two networks, and after a short delay, viola, the nodes could all see each other.  The image shows the routing table from one of the nodes with only one network interface.<br/>
<br/>
<a href="http://3.bp.blogspot.com/-oZy5XwwsEg0/Tm5tiYd96DI/AAAAAAAAAC4/23LmE0HO2_A/s1600/TerminalScreenSnapz002.png"><img src="http://3.bp.blogspot.com/-oZy5XwwsEg0/Tm5tiYd96DI/AAAAAAAAAC4/23LmE0HO2_A/s640/TerminalScreenSnapz002.png"/></a><br/>
The 0000000* addresses in the neighbour table are clear evidence of some of those bugs I mentioned, as is the crazily large age field for one of those. <br/>
<br/>
The FDB3BA1*, D64CEB4* and B167503* addresses are nodes that I had temporarily added to the mesh, and then removed again fairly recently, so the routes were (correctly) still hanging around with their link scores steadily dropping.<br/>
<br/>
The important part is the route to D6850E3*, the node on the other network, for which the current route is via 30464E5*, which is the node bridging the two networks.  30464E5* was a node that I had previously bridging the networks just a short while earlier, and we can see the lingering route as it decays.<br/>
<br/>
B167503* is the node currently bridging the link, and it's score is still climbing, and is about to overtake the recently removed node and become the route of choice.<br/>
<br/>
So while I have a lot more work to do, the basic function of the mesh to discover multi-hop paths and switch routes based on appropriately calculated scores.<br/>
<br/>
But right now, I am going to bed.
<div></div>
</div>