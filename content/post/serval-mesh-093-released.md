+++
date = "2016-06-01"
title = "Serval Mesh 0.93 Released"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-2134345875366978910" itemprop="description articleBody">
<span>After much too long, the next official release of the Serval Mesh app for Android has been released on Google Play.</span><br/>
<span><br/></span>
<span>This includes many, many bug fixes incorporated during that time, and also the following major improvements:</span><br/>
<ul>
<li><div>
<span>Greatly reduced power usage, particularly when no peers are present. In previous versions of the software, a CPU lock would be held whenever the software was enabled and connected to a viable Wi-Fi network. This would completely prevent the CPU from suspending, draining the battery in a matter of hours. In this release, Android alarms are used to wake up the CPU, holding a CPU lock for only a short time. While there are still improvements to be made in this area, the software may be able to remain enabled and connected to a Wi-Fi network without significantly impacting battery life.</span></div>
</li>
<li><div>
<span>Bluetooth has been added as a usable network transport. The addition of bluetooth support has the potential to greatly simplify the process of discovering and connecting to other phones.</span></div>
</li>
<li><div>
<span>Better support for more recent versions of Android. Android 5.0 requires that native binaries are compiled in a way that isn't supported on version before 4.1. So we must now include 2 sets of compiled binaries.</span></div>
</li>
<li><div>
<span>Improved user feedback while networks are turning on and off.</span></div>
</li>
</ul>
<span><br/></span>
<span>You can read full release notes at:</span><br/>
<span><br/></span>
<span> <a href="https://github.com/servalproject/batphone/blob/master/CURRENT-RELEASE.md">https://github.com/servalproject/batphone/blob/master/CURRENT-RELEASE.md</a>,</span><br/>
<span><br/></span>
<span>and get the app itself at:</span><br/>
<span><br/></span>
<span> <a href="https://play.google.com/store/apps/details?id=org.servalproject">https://play.google.com/store/apps/details?id=org.servalproject</a></span><br/>
<br/>
<div></div>
</div>