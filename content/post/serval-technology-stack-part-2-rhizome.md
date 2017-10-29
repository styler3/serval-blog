+++
date = "2013-01-24"
title = "Serval Technology Stack (Part 2) - Rhizome"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6054561120782271630" itemprop="description articleBody">
In a previous post, I began to discuss the Serval Technology stack, and gave a high-level overview of the lowest layers, upto the Serval Overlay Mesh (SOM), and the real-time Mesh Datagram Protocol (MDP), and protocols and services that sit above it.  In this post I want to give an overview of the Rhizome store-and-forward or Delay Tolerant Networking (DTN)  and the protocols and services that depend on it.<br/>
<br/>

<a href="http://3.bp.blogspot.com/-DW88SrDWEbI/UHBNesqUYpI/AAAAAAAAAjk/0zFVfCFSzxc/s1600/serval-technology-stack.png"><img src="http://3.bp.blogspot.com/-DW88SrDWEbI/UHBNesqUYpI/AAAAAAAAAjk/0zFVfCFSzxc/s640/serval-technology-stack.png"/></a>
<br/>
Rhizome sits over the Serval Overlay Mesh (SOM) layer, and uses the same public key identity system when required.<br/>
<br/>
Rhizome itself is a bundle-based network protocol, where arbitrarily large bundles of data (often files, or compressed archives of files) are the basic unit of transport.<br/>
<br/>
Each bundle of data is associated with a manifest which contains meta-data about the bundle, such as the name of the bundle, a SHA512 hash of the file so that reception of the file can be verified, and sender and recipient details where that makes sense.<br/>
<br/>
Each manifest also contains a Bundle ID (BID), which is the public key in a CryptoSign key space. The BID is the unique identifier of the bundle. Each manifest is also signed using the private key corresponding to the BID, thus allowing detection and rejection of manifests that have been tampered with by a 3rd party. <br/>
<br/>
It is also envisaged that manifests will later be signed by multiple keys, allowing filtering and grouping of bundles based on attesting authorities.  This will be used as part of an overall system that will allow updating of Serval Mesh software via Rhizome over the Serval Mesh itself.<br/>
<br/>
Where bundles are addressed to a particular party, the sender and recipient SID/ServalIDs (which are public keys of the sender and recipient, as discussed in <a href="http://servalpaul.blogspot.com.au/2012/10/the-serval-technology-stack.html">a previous post on this blog</a>. <br/>
<br/>
This has the advantage that Diffie-Hellman style shared secret calculation can be performed to produce a cipher stream that can be XORed with the data in the bundle, ensuring that it can be encrypted/decrypted only by the intended recipient. The nature of a Diffie-Hellman shared secret calculation means that it can also be encrypted/decrypted by the sender, which provides repudiability, which is a valuable property for use in sensitive environments.<br/>
<br/>
In a similar way, the private key corresponding to the BID can be stored in the manifest, allowing the recipient to update the manifest, e.g., to remove the file, once they have received it.  This allows the bundle to be removed from the network.  This ability to scrub stale content is an important property, because Rhizome is a store-and-forward based protocol, and thus each bundle may end up being replicated on every node in the network.<br/>
<br/>
Rhizome itself provides a very flexible service that can be used to enable a wide variety of applications that depend on the resilient secure replication, and hence transport, of data from one node to another.<br/>
<br/>
For example, MeshMS, which is our SMS-like service on the mesh uses Rhizome to distribute messages, even in the face of acute and chronic partitioning or islanding of the mesh.  We have used this property in the past to <a href="http://servalpaul.blogspot.com.au/2011/11/demonstrating-serval-rhizome-store-and.html">send MeshMS from Africa to Australia, without depending on any telecommunications infrastructure</a>.<br/>
<br/>
We have also built, and are planning to build other services on top of Rhizome, such as voice mail (which is really just a variation on MeshMS), Serval Maps, our off-line collaborative mapping and situation awareness application, and of course general file distribution.<br/>
<br/>
You can read more about Rhizome, MeshMS in:<br/>
<br/>
<a href="http://www.scirp.org/journal/PaperDownload.aspx?FileName=IJCNS20120800007_49141839.pdf&amp;paperID=21934">Gardner-Stephen, Paul, Jeremy Lakeman, Romana Challans, Corey Wallis, Ariel Stulman, and Yoram Haddad. "MeshMS: Ad Hoc Data Transfer within Mesh Network." (2012).</a>.
<div></div>
</div>