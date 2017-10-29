+++
date = "2012-06-27"
title = "Serval Project Quarterly Update 2012Q2"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6994527119873027665" itemprop="description articleBody">
The last quarter has been quite an exciting one from our perspective, although much of the excitement has not been externally visible.  So here are some of the highlights that you may or may not already be aware of.<br/>
<h3>

Version 0.08 Released</h3>
The most notable visible progress has been the release today (27 June 2012) of <a href="http://servalpaul.blogspot.com.au/2012/06/serval-meshbatphone-008-release.html">version 0.08</a> of Serval Mesh to the Android Market / Google Play.  This is primarily a bug-fix and minor-enhancement release while we finish drawing together a whole pile of work that has been going on behind-the-scenes that will show up in the next version, version 0.90.  The jump in version numbers should give you a clue as to how significant we think the next version will be, so lets have a look at the contrast and what is being planned.<br/>
<h3>

Preparations for Version 0.90 - Switching From Architecting To Integration</h3>
Version 0.08 is a direct descendent of the initial proof-of-concept that launched the Serval Project back in mid-2010.  The bulk of the work in this past quarter has been preparing the reengineered "production" functionality of Serval.  In the last week or so we have reached the point where the bulk of effort is now going into integration of the various components, shaking out the bugs and finding the outstanding tasks that need to be done to make it all work seamlessly together.  This is a very encouraging and exciting stage for the team as we see the hard work over the past year or so come together to make something that we think will be compellingly useful for many people.<br/>
<br/>
To get an idea of the scope of work that has been undertaken, let us summarise a number of the properties of version 0.08 (the most recent proof-of-concept derived release), and then compare this with the reengineered work.  First, version 0.08:<br/>
<br/>
<ul>
<li><span>It requires root permissions to operate, because it needs ad-hoc WiFi to provide end-to-end network paths for the mesh routing protocols. </span></li>
<li><span>It relies on BATMAN or OLSRd for mesh routing over ad-hoc WiFi. </span></li>
<li><span>It has no encryption or authentication of calls.</span></li>
<li><span>It includes a complete installation of Asterisk to do the PBX/VoIP call routing. </span></li>
<li><span>It includes an entire SIP client that talks to the Asterisk installation.  </span></li>
<li><span>It can only operate on IP networks. </span></li>
<li><span>It has only a prototype of the Rhizome store-and-forward mesh file sharing service. </span></li>
<li><span>It relies on 3rd-party applications to send or receive MeshMS (SMS) messages over the mesh.</span></li>
<li><span>It has a rather awkward user interface.</span></li>
<li><span>It has no APIs for interaction with other applications.</span></li>
</ul>
<br/>
In contrast, Version 0.90 will include a pile of reimplemented and new functionality that will make for a  totally transformed product and experience:<br/>
<br/>
<ul>
<li>It will not require root permissions, removing the single greatest barrier to adoption.</li>
<li>It will include its' own mesh routing engine that can operate over access-point and client mode WiFi, and deliver MeshMS and files even under highly partitioned network conditions.</li>
<li>It will offer <a href="http://servalpaul.blogspot.com.au/2012/04/making-security-simple.html">robust end-to-end encryption</a> of voice, MeshMS and, later, of files over the mesh. A later version will also include simple and effective protection against man-in-the-middle attacks.</li>
<li>It will include its own VoIP over Mesh protocol (VoMP), that is light weight and avoids the need to include Asterisk and a SIP client.  This has allowed us to shave 60% off the application size (about 2MB instead of 5MB), and increase responsiveness and speed significantly, even while adding in end-to-end encryption.</li>
<li>It will be able to use non-IP transports, e.g., packet radio, carrier pigeons carrying memory sticks and almost any other digital data carrier to synchronise data between meshes.</li>
<li>It will include the new low-latency and auto-prioritising reimplementation of the Rhizome store-and-forward data distribution service.</li>
<li>It includes it's own MeshMS client, removing the need for external SMS handling applications: one APK provides all services.</li>
<li>It will include a completely redesigned and reimplemented user-interface.</li>
<li>It will include APIs to allow interaction with the mesh, and use of mesh services by other applications.</li>
</ul>
All of these features are nearing completion and being integrated ready for release as version 0.90 sometime in the coming quarter.  Significant and intense progress has been made, and the various features are now beginning to come together, and the work is increasingly focussing on integration and whole-of-system behaviour, rather than on completing the individual components.<br/>
<br/>
Together, they constitute a useful product, one that we will be able to demonstrate to various potential partners and even paying customers who are looking for custom mesh services, making Serval well and away the clear leader in mesh telephony.<br/>
<h3>
Continued Interaction With New Zealand Red Cross</h3>
Following <a href="http://servalpaul.blogspot.com.au/2012/03/kiwiex-2012-installing-and-updating.html">our participation as observers at KiwiEx 2012</a>, we have continued to nurture and develop our relationship with the New Zealand Red Cross IT&amp;Telecommunications Emergency Response Unit (IT&amp;T ERU).  As a result we are addressing the specific requirements and refinements that they have identified as being necessary to make Serval useful for themselves and the broader humanitarian and emergency response sector. <br/>
<h3>
Presentation to UN Working Group on Emergency Telecommunications (UN WGET)</h3>
<div>
During the past quarter our existing relationship with New Zealand Red Cross gave us the opportunity to present not only to NZ Red Cross, but also to IT representatives from the Internatational Federation of the Red Cross/Crescent (IFRC), Internation Committee of the Red Cross/Crescent (ICRC), the World Health Organisation (UN WHO), UNHCR and several other major international humanitarian and emergency response organisations.</div>
<div>
<br/></div>
<div>
This was a tremendously positive day, with considerable interest expressed in what we are doing, and how it might be able to help meet various needs among those organisations. As a result of that meeting we are anticipating further engagement with those organisations and WGET as a whole, and are preparing to submit a proposal to them relating to field data collection.</div>
<h3>

On-Going Work With OTI/Commotion Project</h3>
<div>
The other major activity during the quarter has been continuing the work on integrating Serval with the Open Technology Initiative's Commotion project.  This will allow OpenBTS-based portable GSM cellular networks to interoperate with Serval mesh telephones in a seamless manner.  The first tangible result of this will be the use of Serval's Distributed Numbering Architecture (Serval DNA) to allow meshed OpenBTS units to route calls amongst themselves.  This should be functional within the next few weeks.</div>
<div>
<br/></div>
<div></div>
</div>