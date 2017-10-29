+++
date = "2013-01-22"
title = "Serval Mesh 0.90 Release Candidate 1 is Out"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8531557971011178735" itemprop="description articleBody">
The past year and a half we have put a large amount of effort into rebuilding the Serval Mesh application from the inside out, to include end-to-end encryption, integrated short-messaging and resilient file sharing, all made much, much more useful by a completely overhauled user interface.<br/>
<br/>
Therefore it is with great pleasure that I announce our first release candidate for version 0.90 of the Serval Mesh. <br/>
<br/>
This has only been possible due to the outstanding efforts, including during some difficult times, of our core team (in alphabetic order): Andrew Bettison, Romana Challans, Jeremy Lakeman and Corey Wallis.<br/>
<br/>
To get an idea of the extent of changes, take a look at the <a href="https://github.com/servalproject/batphone/blob/release-0.90/CURRENT-RELEASE.md">release notes</a> and related documents. Changes include:<br/>
<br/>
<span><span>If you have used </span><a href="https://github.com/servalproject/batphone/blob/release-0.90/doc/RELEASE-0.08.md">version 0.08</a><span>, you will notice these changes:</span></span><br/>
<br/>
<ul>
<li><div>
<span>A completely redesigned human interface.</span></div>
</li>
<li><div>
<span>A much smaller APK; faster to download and install.</span></div>
</li>
<li><div>
<span>No need for third-party apps like SMSDroid or WebSMS.</span></div>
</li>
</ul>
<div>
<span>The main screen now presents nine buttons:</span></div>
<ul>
<li><span><em>Call</em> to make voice calls</span></li>
<li><span><em>Messages</em> to compose and view messages</span></li>
<li><span><em>Contacts</em> to discover nearby phones on the Mesh and show your Contact List</span></li>
<li><span><em>Maps</em> calls up the Serval Maps interface (if installed)</span></li>
<li><span><em>Share files</em> to send files via the Rhizome file-distribution system, list and view received files, see how much storage you are using</span></li>
<li><span><em>Share Us</em> to give the Serval Mesh software to other users with compatible Android devices</span></li>
<li><span><em>Settings</em> to adjust settings (see below)</span></li>
<li><span><em>Switch Off(On)</em> to stop or start Serval Mesh</span></li>
<li><span><em>Help</em> for instructions and information</span></li>
</ul>
<div>
<span>The help system is more detailed and complete:</span></div>
<ul>
<li><span><em>Guide To Interface</em> explains the buttons on the main screen</span></li>
<li><span><em>Accounts &amp; Contacts</em> explains how Serval Mesh identifies you and other users to each other</span></li>
<li><span><em>Licence</em> is the full text of the software licence</span></li>
<li><span><em>Serval Security</em> describes Serval's security features, Android permissions used, and the Privacy Policy</span></li>
<li><span><em>About</em> introduces the Serval Project and leads to the Donate button</span></li>
<li><span><em>Quick Links</em> contains some useful links for further reading</span></li>
<li><span><em>Serval Version</em> is the full text of these release notes</span></li>
</ul>
<div>
<span>The Settings menu has been overhauled:</span></div>
<ul>
<li><span><em>Wifi Settings</em> lets you examine and change Wi-Fi settings</span></li>
<li><span><em>Accounts Management</em> lets you change your Serval Mesh phone number and name</span></li>
<li><span><em>View Logs</em> shows a log of recent software activity</span></li>
<li><span><em>Redetect Wifi</em> redetects the device's Wi-Fi chipset</span></li>
</ul>
<div>
<span>There have been enormous changes under the hood:</span></div>
<ul>
<li><div>
<span>The foundations of the <a href="https://github.com/servalproject/serval-docs/blob/master/serval-security-framework/ServalSecurityFramework.odt">Serval Security Framework</a> are now in place. <a href="http://nacl.cr.yp.to/">Elliptic curve cryptography</a> is used for identifying, protecting and authenticating subscribers and mesh network traffic.</span></div>
</li>
<li><div>
<span>All Serval-to-Serval traffic (except Rhizome transfers) is now encapsulated in Serval's new, secure <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:technologies:mdp">Mesh Datagram Protocol</a>, implemented as an overlay network on standard <a href="http://en.wikipedia.org/wiki/Internet_Protocol">IP</a> over <a href="http://en.wikipedia.org/wiki/Wi-Fi">Wi-Fi</a>.</span></div>
</li>
<li><div>
<span>The original Java implementation of the <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:technologies:rhizome">Rhizome</a> file sharing system has been superseded by a new implementation in C within the <a href="https://github.com/servalproject/serval-dna">serval-dna</a> component, using <a href="http://www.sqlite.org/">SQLite</a> as the local storage engine.</span></div>
</li>
<li><div>
<span>Voice calls are now carried over the mesh using Serval's own <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:technologies:vomp">Voice over Mesh Protocol</a>, which has been designed to replace <a href="http://en.wikipedia.org/wiki/Session_Initiation_Protocol">SIP</a>and <a href="http://en.wikipedia.org/wiki/Real-time_Transport_Protocol">RTP</a>. As a result, call quality and latency have improved.</span></div>
</li>
<li><div>
<span><a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:technologies:meshms">MeshMS</a> (Serval's SMS-like service) now uses <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:technologies:rhizome">Rhizome</a> as its transport.</span></div>
</li>
<li><div>
<span>Improved stability and responsiveness.</span></div>
</li>
</ul>
<span>Version 0.90 is still considered experimental software, and there are a number of features and improvements that we intend to implement in releases between versions 0.90 and 1.00.</span><br/>
<span><br/></span>
<span>What we need now is for people to <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:software:techroadmap:releases:version090">download</a> and test this release candidate, and <a href="https://github.com/servalproject/batphone/issues">report any issues</a> they encounter.</span><br/>
<br/>
For more information, visit the <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:software:techroadmap:releases:version090">Serval wiki page for this release candidate</a>.<br/>
<br/>
Update: see a video of us using 0.90RC1 <a href="serval-mesh-090-rc1-demo.html">here</a>.
<div></div>
</div>