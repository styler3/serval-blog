+++
date = "2017-02-21"
title = "SPI microSD card on Atheros 9k"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7992527150472118270" itemprop="description articleBody">
For the new Mesh Extenders, we want to use a microSD card for bulk storage, instead of a USB memory stick.  This is in part because USB draws a lot of power just to run the bus (about 10% - 20% of the total power consumption of a Mesh Extender), but also because we have had a lot of reliability problems with USB memory sticks in Mesh Extender prototypes. Basically, they don't like being shut down suddenly.<br/>
<br/>
Our preferred solution was to add a microSD slot to the Ath9k modules we are using (the Core Domino).  However, we could not find any good sources on how to do this. First, we tried using the bit-bashing driver, which we did get working, however it was horribly slow (about 10KB/sec), and would routinely freeze or reset the Ath9k (possibly due to watchdog timeouts?).<br/>
<br/>
The Atheros 9k does have an SPI interface which is compatible with microSD cards, however, after searching for people having used it, I couldn't find anything sensible.  The main problem is that the 16MB FLASH that boots the Mesh Extender is also attached to the SPI bus, and so there is a need to arbitrate between that, and our microSD card.<br/>
<br/>
After I had given up hope and was trying to make the bit-bash driver work, I accidentally found a page that described exactly what I wanted to do, and had some simple patches for OpenWRT CC to implement it.  You just had to assign a GPIO to be the chip-select for the microSD slot, and all would be well.  Unfortunately I had no spare GPIOs. <br/>
<br/>
What I did have, however, was the chip-select line for the 16MB FLASH.  Since I had only two devices, I suspected that I could just invert that signal, and feed it as the chip-select to the microSD slot.  As hoped, this worked just fine.<br/>
<br/>
The total changes were very small:<br/>
<br/>
https://github.com/servalproject/openwrt/commit/1cfb77ccaf4fd6a5ef345ba599534a5ae26114df<br/>
https://github.com/servalproject/openwrt/commit/3133e6ed935bc4d7705f72e639519e39cafa711d<br/>
https://github.com/servalproject/openwrt/commit/034daf1f4c63c90b079e40da3f8529288ddc1a79<br/>
<br/>
Note that while I didn't have a spare GPIO, this approach still requires that you assign some GPIO to be the chip-select line. I chose a GPIO that was not exposed on the board I was using.  For many low-cost wireless routers, like the TP-LINK WR703N and friends, there are plenty of such blind GPIOs to choose from.  Indeed, this microSD hack should be fairly easily adaptable to the 703N, MR3020, MR3040 and many other cheap Atheros 9331 (or similar Atheros parts) wireless routers, such as the very nice GL-AR150 and related family.<br/>
<br/>
Update: I have spoken to the nice people who make the GL-AR150 and related devices, and they are taking a look at this for evaluation.
<div></div>
</div>