+++
date = "2011-10-05"
title = "Photos and Update from Nigeria - and introduction to Rhizome"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3107391259810830422" itemprop="description articleBody">
We have a partner organisation working in Nigeria looking at citizen-sourced journalism and using our mesh network as the connectivity among a number of camera-equipped cell phones, so that citizen journalists there can make a short video or news piece and then have it distribute automatically over the mesh using our Rhizome protocol.<br/>
<br/>
Rhizome is our mesh file distribution protocol that allows user-created content and software updates to spread hop-by-hop over the mesh.  This hop-by-hop approach elegantly solves many of the problems with mesh-wide file transfer, in particular bandwidth starvation and instability of long links.<br/>
<br/>
We have called it rhizome because it is like the <a href="http://en.wikipedia.org/wiki/Rhizome">vegetable reproductive process</a> of the same name, because we think it is a good analogy for the way that Rhizome allows data to spread by small hops, but such that over time it can spread over great distances.<br/>
<br/>
We are busy working on making Rhizome do all that the team in Nigeria needs, but in the meantime, the team in Nigeria have sent us some photos showing the mesh in action.<br/>
<br/>
First, they sent photographic evidence of 10 IDEOS U8150 phones forming a mesh with our software:<br/>
<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><a href="https://3.bp.blogspot.com/-m1I9RxIslJA/TozkmVFAyYI/AAAAAAAAAC8/TY1hQ8YCoF8/s1600/DSCF0827.JPG"><img src="https://3.bp.blogspot.com/-m1I9RxIslJA/TozkmVFAyYI/AAAAAAAAAC8/TY1hQ8YCoF8/s400/DSCF0827.JPG"/></a></td></tr>
<tr><td class="tr-caption">10 Serval BatPhones on the mesh (and a call in progress!)</td></tr>
</tbody></table>They also sent us this picture which I really love, because it shows a community getting started with out technology thousands of kilometres from where we are writing the software here in Australia.  This is what it is all about, people using and benefiting from the software that we are creating and releasing.<br/>
<br/>
<a href="https://4.bp.blogspot.com/-68qzyeZ0S-0/TozlXkzJzMI/AAAAAAAAADE/yuLhP7x9mXs/s1600/DSCF0829.JPG"><img src="https://4.bp.blogspot.com/-68qzyeZ0S-0/TozlXkzJzMI/AAAAAAAAADE/yuLhP7x9mXs/s400/DSCF0829.JPG"/></a><br/>
<br/>
Finally, just a week after they got 10 phones on the mesh, they sent this shot showing 15 phones on the mesh.  This was just a case of them getting 15 phones within range, as the underlying BATMAN mesh protocol should be able to handle a couple of hundred devices without any difficulty:<a href="https://1.bp.blogspot.com/-CFJEHgPWBwo/TozlQAScItI/AAAAAAAAADA/UMnBQ9Ohfio/s1600/DSCF0864.JPG"><img src="https://1.bp.blogspot.com/-CFJEHgPWBwo/TozlQAScItI/AAAAAAAAADA/UMnBQ9Ohfio/s400/DSCF0864.JPG"/></a><br/>
One of the challenges we are looking at solving with this group is auto-update of the mesh software, over the mesh.  That is, we want to be able to load a signed software update onto any one of the phones on the mesh, and have the phones on the mesh share it automatically with one another.<br/>
<br/>
This is a great idea, and the Rhizome protocol will allow us to do this, however it introduces some security challenges.<br/>
<br/>
In particular, we don't want someone or some party seizing or cracking our signing key, and then being able to spread a trojan update that destroys the Serval mesh.<br/>
<br/>
One approach we are looking at is making the update require that the new version be signed by a majority of keys from a pool, where each key would be held by a different mesh-friendly organisation.   The pool of trusted keys could then be similarly updated by a majority vote of existing trusted keys.<br/>
<br/>
This will allow us to spread the keys among countries and jurisdictions and provide the kind of distributed resilience that the Serval Project is predicated on, and even allows the software to continue to be refined and distributed if the Serval Project as an organisation ceases to exist.<br/>
<br/>
If you think that your organisation might like to be one of our key custodians, let me know.
<div></div>
</div>