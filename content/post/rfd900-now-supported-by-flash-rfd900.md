+++
date = "2015-11-25"
title = "RFD900+ now supported by flash-rfd900 utility"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3454223521083704849" itemprop="description articleBody">
We have a bunch of the newer RFD900+ radios, which have 1 - 2 dB better receive sensitivity than the older RFD900/900a (no plus) versions of the radio. <br/>
<br/>
However, we were previously unable to use these in Mesh Extenders, because we couldn't flash them using our little C utility that we wrote for flashing them on Mesh Extenders. <br/>
<br/>
Using the officially supported flash utility was not an attractive option for us for a couple of reasons: (1) it requires all sorts of dependencies, like python, that ended up adding something like 200MB to the Mesh Extender image, which is normally ~50MB; and (2) it wasn't as fast as we would like.<br/>
<br/>
Our flash-rfd900 utility (<a href="https://github.com/servalproject/flash-rfd900">https://github.com/servalproject/flash-rfd900</a>) worked fine on the old RFD900 / RFD900a radios, but seemed to brick the 900+ radios.  Some very helpful insights from the folks at RFDesign revealed that the new radio uses 24-bit addresses in the bootloader, instead of 16-bit ones.   The intel hex program file can also contain type-04 records in addition to the usual type-00 records that contain the actual data. Type-04 records indicate which 64KB bank is being addressed, and are necessary for the RFD900+ which has an upgraded micro-controller that has 128KB of program flash, and twice the RAM resources of the older radios.<br/>
<br/>
Adding support for these two features was fairly simple, and after that flash-rfd900 is now working for the RFD900+ radios, so we can finish getting the Mesh Extender firmware image to work with that model of radio.
<div></div>
</div>