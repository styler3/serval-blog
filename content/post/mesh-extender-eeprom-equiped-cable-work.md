+++
date = "2017-02-21"
title = "Mesh Extender EEPROM-equiped cable work"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-4236579809828015034" itemprop="description articleBody">
One of the novel features of the new Mesh Extender, is that the national radio regulatory parameters will not be stored in the main unit, but rather in the power cable, as I have described previously.<br/>
<br/>
This means that we can, the theory at least, have bunches of Mesh Extenders pre-positioned regionally (or even globally), without having to configure them for each country in which they will be used. Instead, we just need to have batches of country-specific power cables for them, or similarly, program sets of power cables for them, and then send those to the relevant country/countries.<br/>
<br/>
It also means that we can deal with unfortunate regulations that require firmware be locked in some countries, by having the firmware lock encoded on the power cable as well.<br/>
<br/>
To implement all this, we are using 2KB I2C EEPROMs, so that we can have quite a bit of information stored, and also re-program the cables from one country to another when the need arises.<br/>
<br/>
We want the RFD900/RFD868 radio to read this information directly when they power up, so that they can set their radio frequency and TX power levels appropriately.  This means it makes sense to have the RFD radio talk directly to the I2C EEPROM, rather than via the Ath9k CPU.  A second reason for doing it this way is that we don't have enough GPIOs left on the Ath9k module we are using.<br/>
<br/>
All this means that I needed to implement an I2C library in the RFD900 firmware, and as mentioned in the previous post, implement the SHA-3 hash function, so that we can validate that the parameters are intact, and have not been corrupted by problems with the I2C EEPROM. <br/>
<br/>
I found some nice reference information about I2C, and apart from some challenges at getting the timing and protocol right, it only took a few days work to get to the point where I can now reliably and quickly read and write the EEPROM.  This meant spending a lot of time staring at oscilloscope displays like this one.<br/>
<br/>

<a href="https://2.bp.blogspot.com/-0s7YAQfx63E/WK0cLZfOx7I/AAAAAAAAGFU/fTyWUwoxniwtfRRvNcynZPsflmhFWVf2QCLcB/s1600/IMG_20170217_141925.jpg"><img src="https://2.bp.blogspot.com/-0s7YAQfx63E/WK0cLZfOx7I/AAAAAAAAGFU/fTyWUwoxniwtfRRvNcynZPsflmhFWVf2QCLcB/s320/IMG_20170217_141925.jpg"/></a>
<br/>

<a href="https://2.bp.blogspot.com/-5NOyd7wuwD8/WK0cLQ8AGxI/AAAAAAAAGFQ/vyPYCEI23lAxtuakXL_mIaVZMh1vWApFgCLcB/s1600/IMG_20170217_143506.jpg"><img src="https://2.bp.blogspot.com/-5NOyd7wuwD8/WK0cLQ8AGxI/AAAAAAAAGFQ/vyPYCEI23lAxtuakXL_mIaVZMh1vWApFgCLcB/s320/IMG_20170217_143506.jpg"/></a>
<br/>
<br/>
For development, I wired up a little board with one of the EEPROMs to an RFD900, to simulate the wiring for the cable.<br/>
<br/>

<a href="https://4.bp.blogspot.com/-MtCGJo36MrA/WK0cMScCLcI/AAAAAAAAGFk/L1LJzseZ54A_9xK9GFyX9M-mPWeZpKwwwCLcB/s1600/IMG_20170217_164530.jpg"><img src="https://4.bp.blogspot.com/-MtCGJo36MrA/WK0cMScCLcI/AAAAAAAAGFk/L1LJzseZ54A_9xK9GFyX9M-mPWeZpKwwwCLcB/s320/IMG_20170217_164530.jpg"/></a>
<br/>

<a href="https://3.bp.blogspot.com/-DQUUcoejK84/WK0cMR0AvFI/AAAAAAAAGFc/p-5fMd2jWswCIg8i_GxgXgeAkEfevgV5ACLcB/s1600/IMG_20170220_122038.jpg"><img src="https://3.bp.blogspot.com/-DQUUcoejK84/WK0cMR0AvFI/AAAAAAAAGFc/p-5fMd2jWswCIg8i_GxgXgeAkEfevgV5ACLcB/s320/IMG_20170220_122038.jpg"/></a>
<br/>
One nice little trick that we do to save power consumption, is that the EEPROM is powered directly from one of the GPIOs on the RFD900.  If we turn that GPIO off, then the EEPROM is physically switched off, saving a (very) little bit of power.<br/>
<br/>
For the actual cables, we have the pinout planned such that the EEPROM can be soldered directly onto the relevant pins of the D-SUB 25 connector, to simplify assembly and avoid the cost of a little PCB, something like this:<br/>
<br/>

<a href="https://2.bp.blogspot.com/-16tYamCLhVQ/WK0cMeRK6sI/AAAAAAAAGFg/aCitHmuibTwq8q4CTLBIi-kiWm4mcxcCQCLcB/s1600/IMG_20170222_135636.jpg"><img src="https://2.bp.blogspot.com/-16tYamCLhVQ/WK0cMeRK6sI/AAAAAAAAGFg/aCitHmuibTwq8q4CTLBIi-kiWm4mcxcCQCLcB/s320/IMG_20170222_135636.jpg"/></a>
<br/>

<a href="https://4.bp.blogspot.com/-aC3JADY8ufc/WK0cNNXiHgI/AAAAAAAAGFo/CieyVR2f3ugrJ3izLbC0VM9YKdp19Ku5QCLcB/s1600/IMG_20170222_135659.jpg"><img src="https://4.bp.blogspot.com/-aC3JADY8ufc/WK0cNNXiHgI/AAAAAAAAGFo/CieyVR2f3ugrJ3izLbC0VM9YKdp19Ku5QCLcB/s320/IMG_20170222_135659.jpg"/></a>
<br/>
Bending the pins the right amount was a bit more work than hoped, but with practice (or a little jig) could be done quite quickly. This is mainly because the chip is quite a bit fatter than the pitch between the rows of pins.  The pins are the same pitch as the pins within a row on the connector, however, so that aspect is fine.<br/>
<br/>
This theme of simplifying assembly is, I am finding, a recurring one as I plan how to make something that can actually be manufactured, even in modest quantities.  All manual steps need to minimised so far as possible.  This means actually trying to do things, rather than just designing them.  So half way through writing this post, I wandered downstairs and tried to solder one of these cables together. I succeeded eventually, more or less, but in the process realised that to just fit the chip onto the back of the D-SUB connector, two pins needed to be swapped around.  For now, I have soldered it up with the temporary fix, until we can get this pin change made on the next revision of PCBs (which fortunately haven't been fabricated yet). You can see the resulting mess here:<br/>
<br/>
<br/>

<a href="https://3.bp.blogspot.com/-RWz8n_lBEsc/WK0cNYGkNbI/AAAAAAAAGFs/xxWzcysrJtwJ7yZQdy9hFgtRpQiWQ-87QCLcB/s1600/IMG_20170222_152058.jpg"><img src="https://3.bp.blogspot.com/-RWz8n_lBEsc/WK0cNYGkNbI/AAAAAAAAGFs/xxWzcysrJtwJ7yZQdy9hFgtRpQiWQ-87QCLcB/s320/IMG_20170222_152058.jpg"/></a>
<br/>

<a href="https://1.bp.blogspot.com/-u_XP0xaWdQ0/WK0cOPVXZfI/AAAAAAAAGF0/WpXqBQcPIvod_h1rCC3EkQK1Z6kfyEc-gCLcB/s1600/IMG_20170222_152150.jpg"><img src="https://1.bp.blogspot.com/-u_XP0xaWdQ0/WK0cOPVXZfI/AAAAAAAAGF0/WpXqBQcPIvod_h1rCC3EkQK1Z6kfyEc-gCLcB/s320/IMG_20170222_152150.jpg"/></a>

<br/>

Here is the whole thing with the nice $1.35 a piece IP65-rated connectors I found recently:

<br/>

<a href="https://2.bp.blogspot.com/-k6I6cFaOs8E/WK0cNDxXqnI/AAAAAAAAGFw/g-IZDxOZFLMKesfBuKwuYW2L6q4uoV3uQCLcB/s1600/IMG_20170222_152048.jpg"><img src="https://2.bp.blogspot.com/-k6I6cFaOs8E/WK0cNDxXqnI/AAAAAAAAGFw/g-IZDxOZFLMKesfBuKwuYW2L6q4uoV3uQCLcB/s320/IMG_20170222_152048.jpg"/></a>

<br/>

Apart from the pinout problem, it wasn't too hard to assemble, really, so I am encouraged that this could still work.  I won't stop thinking about how I can further optimise the process, however.

<br/>

What I haven't covered above is how I am going to protect the cable head, so that it is sealed etc.  For that, I have been talking to the plastics manufacturing people who are helping us with the injection-moulded housing design.  They have suggested we could fairly cheaply produce a tool for low-pressure plastic encapsulation of the cable, similar to what is used to produce serial and printer cable ends.  Because it is low pressure, it is possible to use aluminium for the tool, rather than the hard tool steel that is required for the injection-moulded housing.  Because aluminium is so much softer, it is quicker (and thus cheaper) to machine.
<div></div>
</div>