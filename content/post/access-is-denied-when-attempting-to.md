+++
date = "2013-04-23"
title = "Access is Denied when attempting to install drivers on Windows 7"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7790485738266791000" itemprop="description articleBody">

This is just a quick post to share a problem I had while trying to update the firmware on an MK808B recently, and the solution I came up with.  The problem was trivial, but none of the suggested solutions that I found online were appropriate, so I am sharing what happened here to save other people the same issue.

<br/>

I downloaded the USB drivers for a device, connected the device, and waited for Windows to ask about drivers for it. I had the drivers downloaded and extracted ready for installation.

<br/>

When I selected the folder with the drivers, Windows proceeded to try to install the drivers, but then very quickly reported "Access is denied".

<br/>

The same happened if I tried to update driver from in Device Manager.

<br/>

The problem was caused by the folder containing the drivers being read-only, and I think, encrypted (but I am a bit fuzzy on what the Encrypted attribute really does on Windows 7).

<br/>

I solved the problem by right-clicking on the folder, and unticking "read-only" and "encrypted" and applying that to the entire folder and its contents.  This took a few seconds for Windows to fix the attributes on all the files.

<br/>

After that I was able to install the driver without incident.

<br/>

Hopefully this helps save someone else some hassle.

<br/>

[Update: If you are running Windows 8.1 there is a related problem where you basically can't use unsigned drivers anymore.  That's a separate issue.]
<div></div>
</div>
