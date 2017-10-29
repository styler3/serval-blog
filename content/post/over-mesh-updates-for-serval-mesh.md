+++
date = "2013-08-27"
title = "Over-the-Mesh Updates for Serval Mesh Extender Prototypes"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-12742596189962214" itemprop="description articleBody">
I have just spent the day working on field upgradability for the serval mesh extender prototypes.<br/>
<br/>
Note that the following is how updates for the prototypes work at present. We expect that this may change over time, and is likely to be different in the final products.<br/>
<br/>
Updates to servald will be supported in two different ways.<br/>
<br/>
First, it will be possible to pull the USB memory stick from the unit and copy the new servald binary onto the stick.<br/>
<br/>
Second, if there is no servald binary on the USB memory stick, then it will look for an update via Rhizome.  If there is an update, it will install it.  As with all Rhizome files, the updates are cryptographically protected so that only genuine updates will be accepted.<br/>
<br/>
None of the update functions are automatic, because we want to place updates entirely under user control, as a partial protection against network poisoning attacks.<br/>
<br/>
To effect an update (or to restart the servald on a mesh extender without turning it off and on again), just press the WPS button on the MR3020 router.<br/>
<br/>
Of course, if something stuffs up, for example you have a bad update on the USB memory stick, then hold the WPS button down for 10 seconds and it will "factory reset" back to the original servald that shipped with it.<br/>
<br/>
More as we develop it.
<div></div>
</div>