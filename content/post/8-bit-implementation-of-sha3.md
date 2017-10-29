+++
date = "2017-02-21"
title = "8-bit implementation of SHA3"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7856980764600970696" itemprop="description articleBody">
We have need of a hash function in the Mesh Extender for the RFD900 radio to verify that the radio regulatory parameters it is loading from the serial EEPROM in the power cable have not been corrupted.<br/>
<br/>
Taking a look at the current major families of hash functions, SHA-1, 2 and 3, it looks like SHA-3 is the best.  This is not just because it is the newest (incorporating the latest advances in cryptography against known attacks, compared with SHA-1, which is <a href="https://www.schneier.com/blog/archives/2005/02/sha1_broken.html">showing signs of vulnerability</a>), but because it is also relatively computationally efficient (compared with SHA-2, for example), and friendly for running on simple hardware.<br/>
<br/>
I found a nice public domain implementation of SHA-3, and tried to pull that into the RFD900 firmware.  However, it upset the compiler in a variety of ways.  In short, the SDCC compiler really doesn't like 64-bit data types, and does horribly inefficient (and incorrect) things with them.<br/>
<br/>
Result: I have worked through the implementation converting it to a byte-oriented implementation of the full SHA-3 hash.  It correctly calculates the hashes of various test-vectors I have fed it.  What is nice, is that the implementation is now quite a bit shorter and simpler, because I have removed some optimisations for 64-bit machines from the code.  You can see the code here:<br/>
<br/>
https://github.com/gardners/SiK/blob/MeshExtender2.0/Firmware/radio/sha3.c<br/>
https://github.com/gardners/SiK/blob/MeshExtender2.0/Firmware/radio/sha3.h<br/>
<br/>
For very short input texts, I can calculate a SHA-3 hash in under a second, which isn't too bad, given the little 8051 CPU on the RFD900 board.
<div></div>
</div>