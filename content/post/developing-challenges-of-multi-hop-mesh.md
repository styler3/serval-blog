+++
date = "2012-02-06"
title = "Developing Challenges of Multi-Hop Mesh Telephony on Android"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6886221887208707380" itemprop="description articleBody">
If you are reading this blog, you probably know that the <a href="http://servalproject.org/">Serval Project</a> is all about making mesh telephony practical, so that people can communicate anywhere, any time.<br/>
<br/>
For regular Android software development, it is often practical to use the Android emulator to reduce the time between updating source code and seeing the effect of the change.<br/>
<br/>
For Serval, this isn't really an option, because we work below the Android API layer, and much of the software development challenge is related to making the WiFi chipsets do what we want.  We also have a fair amount of native code to do the mesh routing and telephony functions.  In fact, we currently have an entire distribution of Asterisk in the Serval Mesh software, which must be decompressed and installed when the Serval Mesh APK is installed or updated. <br/>
<br/>
Together, these contribute to an update process that can take several minutes to between modifying a line of code and seeing it on an Android device, especially on the low-cost devices that are our primary targets, and when using the debug option in eclipse.<br/>
<br/>
Those minutes add up over time, and so I decided to minimise the install time as much as possible, and also address another problem with developing our software, that is detecting when you have an actual multi-hop network.<br/>
<br/>
To reduce the install time, I started looking at the Asterisk installation to see what we could safely throw out.  I managed to get rid of about half of the loadable modules, several utilities and all of the speech files that Asterisk comes bundled with.  This reduced the size of the APK by a little over 1MB, down to just under 5MB, and cut down the install time by about 15%.  Further savings came from removing unused audio codecs in our SIPDroid-derived SIP client, saving another 0.4MB, and getting the whole thing down to less than 4.5MB and installing about 25% faster than previously.<br/>
<br/>
The bulk of the remaining time is about evenly split between installing Asterisk and testing that the WiFi control works properly.  For development, it probably makes sense to separate out the Asterisk installation from the other files we need to deploy on installation, as we really don't modify the Asterisk files between builds.  This shouldn't be too hard to do, but I have run out of time tonight.<br/>
<br/>
Also, for our target handsets, we really don't need to test the WiFi control every time we update, so we should be able to set a flag to tell the software that we are in development mode, and just assume that the WiFi control works.  This now works by checking if a file called <span>/sdcard/serval/developer-mode/fast-wifi</span> exists, and if so, bypassing those tests, and thus saving about 15 seconds.<br/>
<br/>
So over all the minimum time from hitting "run" in Eclipse to getting the software ready has been reduced from 85 seconds down to 48 seconds (without debugging).<br/>
<br/>
The over significant development convenience task I have worked on in the last few days is one that is probably of more general interest.  The peer list now shows the number of hops to each of the nodes that your phone knows about, as shown in the image below.  This was produced by having two phones at opposite ends of my house, and having the phone shown here with me out on the street.<br/>
<br/>

<a href="http://4.bp.blogspot.com/-fjjD53rd-b4/Ty-t5cAVRaI/AAAAAAAAAJw/daWBb3wYnFo/s1600/2-hop-peerlist"><img src="http://4.bp.blogspot.com/-fjjD53rd-b4/Ty-t5cAVRaI/AAAAAAAAAJw/daWBb3wYnFo/s1600/2-hop-peerlist"/></a>

<br/>
Each row of the peer list now shows the telephone number, e.g., 5550344, the batman link score, e.g., 243, the ping time to the peer, e.g., 19 milli-seconds, and either "direct" for nodes we can reach directly, or the number of hops to reach the node, e.g., 2 hop. <br/>
<br/>
Importantly for debugging, this displays doesn't ask BATMAN how far to the node in question, but actually enquires of the time-to-live (TTL) field in the IP header, and thus returns the true distance from your phone to the phone in question (the return path might be a different length, though). <br/>
<br/>
Actually, because of limitations with the Java UDP programming interface, the TTL field is read by the Serval DNA daemon (which is written in C), and included in the returned UDP packet to the requesting client.<br/>
<br/>
This means that we can just look at the interface on the screen (and so can all of you who have been asking us for this feature) and see what is happening to routes, instead of having to connect to the phone with a USB cable and enter all sorts of commands to ask BATMAN and the operating system what <i>might</i> be happening.<br/>
<br/>
So all in all we now have a slightly faster and easier development process, that I am sure will more than save the couple of person days of effort that they took to develop, and thus enable us to work faster instead of harder.
<div></div>
</div>