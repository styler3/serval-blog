+++
date = "2013-04-10"
title = "\"Multi-threaded radio\" for the ISM915 band for fun and profit"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-835861524670314555" itemprop="description articleBody">
This is some ideas that I plan to implement that I wanted to capture somewhere public before I forget.  I plan to implement this in the RFD900 firmware for the Mesh Extenders.<br/>
<br/>
---<br/>
<br/>
The ISM915 band requires frequency hopping in most countries where it is proclaimed.<br/>
<br/>
This is a bit of a pain, because the frequency hopping means that we need to synchronise all the nodes in a mesh such that they are all listening and talking on the same frequency at the same time. That is, they need to be on the same "virtual channel".<br/>
<br/>
The virtual channel is really just a hopping pattern, and knowing your position in the pattern.<br/>
<br/>
It occurred to me some time ago that this imposition actually creates some interesting opportunities that we might not have otherwise considered for cooperative shared use of a block of spectrum.<br/>
<br/>
The first step is to use a fairly fast frequency hopping pattern, hopping perhaps every 1ms - 2ms.<br/>
<br/>
This hopping time is <i>purposely</i> shorter than the time it takes to send a whole packet.<br/>
<br/>
The second step is to have each station only listen on a fraction of slots.  For example:<br/>
<br/>
<ol>
<li>Define a bundle to be a fixed number of, say, 10 consecutive slots.</li>
<li>Each station listens on exactly one of those slots, based, for example, on the last three bits of its' network address.</li>
<li>The remaining two slots are a double-sized slot for broadcast packets. All stations should listen during this slot.</li>
<li>This means that while the logical hopping rate might be 1000Hz, the effective rate for each station is reduced to two hops per slot bundle, i.e., twice every 100Hz, i.e., 200Hz.</li>
</ol>
<div>
This reduces the number of hopping actions for each station, and to some extent allows for a little slop in the synchronisation. </div>
<div>
<br/></div>
<div>
When a station sends a packet to another station, it can predict which time slot to send in, because the receiving stations listen slots can be determined from its network address.  </div>
<div>
<br/></div>
<div>
The sender then switches to the appropriate channel at the appropriate time, and sends the entire packet, even though it might take many slots to do so.</div>
<div>
<br/></div>
<div>
In effect, the transmitter and receiver switch from the shared virtual channel to another channel.  </div>
<div>
<br/></div>
<div>
This means that each packet transfer "forks" off from the main channel, hence my calling it "multi-threaded radio".</div>
<div>
<br/></div>
<div>
This means that as many packets can be in flight as there are real channels in the hopping pattern, and that they can all be used at the same time, <i>but not by the same stations</i>. That is, it has an intrinsic fair-share mechanism built in.</div>
<div>
<br/></div>
<div>
In terms of aggregate bandwidth, the result is potentially very pleasing.  </div>
<div>
<br/></div>
<div>
A 50 channel 128kbit hopping scheme such as we use on the RFD900 radio goes from being 128kbit/second throughput to potentially 50x128kbit = 6.4Mbit/second!</div>
<div>
<br/></div>
<div>
Yet, without the range reduction and increased receiver power consumption that Wi-Fi suffers by trying to make all that bandwidth available to a single station.</div>
<div>
<br/></div>
<div>
Anyway, I need to implement it to see how it works in reality, and whether the accurate synchronisation is possible on a completely distributed network with no external clock.</div>
<div></div>
</div>
