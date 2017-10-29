+++
date = "2016-08-31"
title = "Bridging Rhizome over HF"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1076246796460985677" itemprop="description articleBody">
I'm currently up at Pacific Endeavour in Brisbane, which is a multi-national defence and civilian humanitarian and disaster response interoperability exercise, attended by, among others, the military of 22 nations around the Pacific basin.<br/>
<br/>
We have been talking with <a href="http://www.codanradio.com/">Codan</a> for a while about integrating Serval with their HF radios to allow Rhizome-based services over HF distances.  The goal is to allow MeshMS and our (still being written) Mesh-based social media applications to be carried over HF-distances (kilometres to hundreds of kilometres) between more localised concentrations of Mesh Extenders equiped with Wi-Fi and UHF packet radios.<br/>
<br/>
This is of direct interest for our AusAID/DFAT grant to pilot Serval in the Pacific, where the beneficiary nations typically have small populations on islands separated by tens to hundreds of kilometres.   If we can link distant islands, then we can provide national and regional level communications, subject to the limitations of HF radio bandwidth (typically in the bytes to tens of bytes per second, although hundreds of bytes per second is possible in principle).<br/>
<br/>
As part of the Pacific Endeavour, exercise the folks from <a href="http://www.codanradio.com/">Codan</a>, <a href="http://www.barrettcommunications.com.au/">Barrett</a> and the other HF radio vendors are here.  The folks from Codan and Barrett in particular have been super helpful and enthusiastic as I have been explaining to them what we are trying to do, and how, to me at least, it seems to create the potential for new markets for HF radios. <br/>
<br/>
They have kindly provided me with access to radios and documentation that they have with them, so that I can attempt a code sprint to establish two-way packet communications between their radios. That is, my goal is not just to prove that Serval Rhizome can run over HF radio, but that we can do it between what I understand are the two largest vendors in the humanitarian and disaster HF radio space.  Here is my setup with the Barrett radio (the black one on the desk) and the Codan radio (on the floor next to me):<br/>
<br/>

<a href="https://3.bp.blogspot.com/-dp7U8P2sOzw/V8eV0AFwAwI/AAAAAAAAF74/3YXA7t7rNiAEb9zjIHMcrhS72RUNt6JgwCLcB/s1600/IMG_20160831_190209.jpg"><img src="https://3.bp.blogspot.com/-dp7U8P2sOzw/V8eV0AFwAwI/AAAAAAAAF74/3YXA7t7rNiAEb9zjIHMcrhS72RUNt6JgwCLcB/s640/IMG_20160831_190209.jpg"/></a>
<br/>
<br/>
After some false starts with having the correct firmware on one of the radios, I was pleasantly surprised to find that I was able to establish basic packet communications after only about ten hours of work.  Here you can see a packet being received, and a peer being detected by LBARD (the Serval Mesh program for handling slow radio links):<br/>
<br/>

<br/>
<br/>

<a href="https://4.bp.blogspot.com/-G9hsrrJZdzY/V8eRtuh6__I/AAAAAAAAF7c/O5NnWPofqjYCIQNYwrQVggRymlkJCpRDgCLcB/s1600/TerminalScreenSnapz007.png"><img src="https://4.bp.blogspot.com/-G9hsrrJZdzY/V8eRtuh6__I/AAAAAAAAF7c/O5NnWPofqjYCIQNYwrQVggRymlkJCpRDgCLcB/s640/TerminalScreenSnapz007.png"/></a>
<br/>

As the messages above show, LBARD knows what brand the radios are.  

<br/>

This is partly out of necessity, because the serial control interface is quite different on the two radios, but also because we know if we are linking radios produced by the same vendor, that we have the potential to use higher-speed communications options.  

<br/>

But between vendors, we currently have to use only inter-operable standards, which when it comes to HF radio means the older version of the <a href="https://en.wikipedia.org/wiki/Automatic_link_establishment">Automatic Link Establishment protocol</a>.  This is a bit unfortunate, because the interoperable ALE 2G standard is really slow.  The native data rate of ALE 2G is only 375 bits per second to begin with.  There is some protocol overhead, which reduces that somewhat.  Then we discovered that some radios don't support the full ASCII-64 restricted character set specified by the ALE 2G standard, and as their documentation claims. In particular, most of the punctuation characters in the ASCII-64 character set actually cause the message to be truncated on some of the radios.  This means that we can only use hex encoding, which means that we are consuming 2x 6-bit characters to encode each byte, i.e., 12 bits per byte. This reduced bandwidth by a further third.  Then there are a number of other losses relating to slow turn-around from TX to RX and back again, the need to fragment messages into 43 byte pieces to fit into the short ALE 2G AMD message limitations, all of which together reduce the effective bandwidth to perhaps 10 bytes per second.  Fortunately LBARD was designed to handle such slow links.
<br/>
(We also found that some versions of firmware on some of the radios wouldn't receive ALE AMD messages sent by the opposite vendor, although we think that particular problem has been corrected in the latest version of firmware, so the problem is manageable.)<br/>
<br/>
Naturally, we would much prefer to have higher speed connections, including the ALE 3G standard, that allows for up to 1KB/sec under ideal conditions, and without the need to fragment packets, which further saves on the TX/RX/TX turnaround cycle.  Unfortunately not all HF radios support ALE 3G.  That said, we will add support for radios that have it, and thus need to know if the remote radio also supports it -- thus another reason to know the vendor and model of the remote radio.<br/>
<br/>
Higher-speed HF modems are also available, but are rather expensive.  Thus we are contemplating designing a low-cost HF radio using a cheap Spartan 3 or 6 FPGA for DSP, and attempt to implement something compatible with one of the existing HF modem standards (since they have done the hard work of knowing which modulation schemes are actually sensible on HF), that can be part of a Serval Mesh Extender HF adapter, to allow similar practical performance to the way that we are using the RFD900 UHF packet radios.    The RFD900 is actually much faster natively, but we are using it in an ad-hoc manner to allow many radios to be in range of each other, thus limiting each transmitter to ~0.25 - 1KB/sec.  For HF links, we are using 1:1 direct links, so that the best channel and modulation can be used, and thus we can use a simple TDM or equivalent scheme, that allows us to utilise a channel fully.<br/>
<br/>
After getting everything working on ALE 2G, here is our Codan / Rhizome gateway (running from my laptop), and using this Codan "manpack" radio:<br/>
<br/>

<a href="https://3.bp.blogspot.com/-W2ZgxpHTqGE/V8eV3tO4hqI/AAAAAAAAF8A/NupksQo3Q4kqHKimE9vnVb1r0c8JdMfrwCLcB/s1600/IMG_20160901_115833.jpg"><img src="https://3.bp.blogspot.com/-W2ZgxpHTqGE/V8eV3tO4hqI/AAAAAAAAF8A/NupksQo3Q4kqHKimE9vnVb1r0c8JdMfrwCLcB/s640/IMG_20160901_115833.jpg"/></a>
<br/>
And the Barrett / Rhizome gateway, which I have yet to setup for the demo, will use this radio, a Barrett 2050:<br/>
<br/>

<a href="https://1.bp.blogspot.com/-Kid9bQWcpzc/V8eXjQWb8II/AAAAAAAAF8M/KDFApLu8vRM0c2W2oEkLyWkUmnHKzpo8QCLcB/s1600/IMG_20160901_124850.jpg"><img src="https://1.bp.blogspot.com/-Kid9bQWcpzc/V8eXjQWb8II/AAAAAAAAF8M/KDFApLu8vRM0c2W2oEkLyWkUmnHKzpo8QCLcB/s640/IMG_20160901_124850.jpg"/></a>
<br/>

So now I just need to update the version of OSX on the 2nd-hand Mac I just bought down the street, so that I can run this updated version of LBARD on it, and show it all running during the demo session this afternoon.  

<br/>

But in the end, we have reached a significant milestone in that we have a proof-of-concept of near-real-time Serval communications over hundreds of kilometres, by using HF radios.
<div></div>
</div>