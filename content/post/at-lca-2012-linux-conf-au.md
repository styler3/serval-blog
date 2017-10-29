+++
date = "2012-01-19"
title = "At LCA 2012 (Linux Conf AU)"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-2932773905002375758" itemprop="description articleBody">
<br/>
<div>
This year I was not expecting to be
heading to Linux Conference Australia (LCA), as two of the Serval
Project team were expecting to be there, and I am already looking at
the likelihood of somewhere north of six bouts of international
travel this year, on top of a very full itinerary for myself in our
software development program, especially in the first half of the
year.</div>
<div>
<br/></div>
<div>
However, circumstances changed just
before <a href="http://linux.conf.au/">LCA2012</a> with one of our team unable to travel due to health, and
another being overseas at an IEEE 802.11 meeting as part of our
effort to get the ad-hoc WiFi standard improved.  So I found myself
flying in for just over 24 hours to present one of the talks.</div>
<div>
<br/></div>
<div>
The two Serval Project talks this year
were covering Serval Rhizome, our store-and-forward message and file
distribution system, and the Serval Mapping Service, an
infrastructure-free map and crowd-sourced information gathering and
visualisation platform that is something like a cross between <a href="http://google.com.au/maps">GoogleMaps</a>, <a href="http://ushahidi.org/">Ushahidi</a> and <a href="http://twitter.com/">Twitter</a>.<br/>
<br/>
Update: Here are the videos of the talks.  The authorships are wrong way around, however:<br/>
<br/>

<iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/u-v4yhTyP_c?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe>

<br/>

<br/><iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/bIVtXkDAIQ8?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe>
<br/></div>
<div>
<br/></div>
<div>
The talks were well attended and many
people asked a wide variety of questions.  Several themes that
emerged in the question time were that we should think about how we
might interface our work with that of the ham radio community, and a
general discussion of the <a href="http://openstreetmaps.org/">Open Street Maps</a> project that we use to
supply the cacheable maps for the Serval Mapping Service. Questions
were also asked about whether we were looking to branch out from
Android to other platforms, including low-cost “feature phones”,
which are common in the developing world.  We have been targeting the
Symbian/Belle S60 platform for a long time now.  We also explained
how we intend to seek the manufacture of custom feature and smart
phones that contain a pluggable extra radio for mesh communications. 
</div>
<div>
<br/></div>
<div>
This goal received a substantial boost
when we discovered that Andrew Tridgell (of SAMBA fame) has already
written <a href="https://github.com/tridge/SiK">frequency-hopping firmware</a> for HopeRF radio modules similar to the ones we are intending to use.  This will likely save us months of effort,
and also enabled us to learn from Andrew's experience about what the
realistic capabilities of the modules are.  The firmware and adapter
boards that Andrew has created will also make it much easier for us
to quantify the transmission range that we can achieve with these
devices in practise, rather than relying on fairly simplistic
link-budget calculations.</div>
<div>
<br/></div>
<div>
Also from talking with Andrew we have
begun to look more seriously about using small model drone aircraft
to loft mesh repeaters (possibly just mesh-enabled Android phones)
and have them loiter over an area to provide significant coverage
where it would otherwise be possible.</div>
<div>
<br/></div>
<div>
The combination of the longer-range
radios and an established ability to loft mesh devices each have the
potential to greatly increase the utility of our technology in a
variety of settings, including disaster response and in both built-up
areas and open country where either obstacles or low population
density make WiFi meshing difficult.</div>
<div>
<br/></div>
<div>
It was also great to hear about David
Rowe's continuing progress on his open-source codec, called <a href="http://www.rowetel.com/blog/?p=2255">Codec2</a>,
which while still alpha, already is able to demonstrate <a href="http://www.rowetel.com/blog/?p=2255">veryacceptable performance at 2500bps and 1400bps</a>, i.e., as low as 175
bytes per second for speech of a quality that is more than acceptable
for a phone call, and is substantially better than the now rather
aged GSM codec that requires almost 10x the bandwidth.  The challenge
is how to make effective use of such a low bit-rate coded, since as
David pointed out during his talk, the IP, UDP and RTP headers in a
typical VoIP application would consume probably 5x more bandwidth
than the voice stream itself.  
</div>
<div>
<br/></div>
<div>
This is a welcome problem we have been
anticipating for some time now, and have some thoughts on how we
might address it.  First, once we get our new overlay mesh operating,
we will use packet aggregation to defray some of the headers. 
Second, we will setup pseudo virtual circuits between nodes that will
allow the voice to be directed using one-byte channel identifiers
that are local to each node-pair.  Third, we can build more efficient
transport structures once we branch out to custom radio interfaces,
such as in the ISM915 band building on the work that Andrew Tridgell
described earlier in this post.  
</div>
<div>
<br/></div>
<div>
For example, we could use a one-byte
packet type identifier plus the one-byte channel identifier described
to provide an overall header size of just two bytes.  Add to this 
perhaps 2 more bytes of synchronisation data for the cryptography
layer, and the total overhead is 4 bytes per 40ms, for a total of 100
bytes of overhead, and a total data requirement in each direction of
275 bytes per second, or just under 2400bps.  Allowing for guard
bands and the like on the radio interface, we should be able to
easily accommodate a full duplex voice call over a 5kbs – 10kbs
radio channel, and multi-hop voice calls over perhaps 20kbs –
30kbs*.  Such a low bit rate, as I have explained previously, offers
the potential of very long range compared with WiFi, probably
hundreds of metres per hop in built-up urban areas, and perhaps a few
kilo-metres in open country, and even better with an elevated
transmitter.  We do hope to quantify these range figures in some
realistic situations over coming months.</div>
<div>
<br/></div>
<div>
(* Each channel into and out of each
node requires about 2400bps.  In a multi-hop network, we do not want
any two adjacent, two-hop or three-hop neighbours transmitting at the
same, as they will cause interference to each others (the
interference range is typically about double the effective
transmission range, so one node talking can be heard by its immediate
neighbours, and cause interference to it's two-hop neighbours). 
Also, we have two voice streams, one each way, so we need to schedule
this in an appropriate manner.  Let us explore how this might work if
we have four nodes, A, B, C and D, involved as successive hops in a
multi-hop call.  
</div>
<div>
<br/></div>
<div>
At time 0 transmits to B (A → B), so
B must be listening, and C cannot talk, else it would interfere with
B's reception of A's transmission.  In fact, even D cannot talk, for
fear of interfering with B's reception of A's transmission, as B may
be in the interference range of D. Thus in this entire system of four
nodes to maximise range we need to have only one of the four nodes
talking at any time.  As it takes three hops to carry the audio in
each direction, we need six time slices.  Some savings can, however,
be gained by having B talk to A and C at the same time with a
double-length frame, and similarly C talk to B and D with a double
length frame, thus saving two guard bands.  Thus we need two 2400bps
channels and two 4800bps channels (a total of 14400bps), plus four
guard bands.  At 20kps this would leave approximately 25% of air time
available, including for use guard bands, or to allow for the
occasional carriage of additional data. 
</div>
<div>
<br/></div>
<div>
At 30kps fully half of air time would
be available, which would also allow for some forward error
correction, and a more realistic allowance for additional data,
especially if some creative time slicing and signalling is employed.
For calls with more than four hops, additional bandwidth is not
required, as nodes more than three hops from one another have
reasonable prognosis (though no guarantee) of not interfering with
one another.)</div>
<div>
<br/></div>
<div>
Meanwhile, also at LCA, we have been
demonstrating the ability of the Serval software to share itself via
bluetooth and WiFi to other phones, thus simulating deployment in a
disaster zone or rural/remote context where internet access is not
available.  While there have been some issues, it has been tremendous
to see many people install and try our software.  It seems that
practically everyone at LCA this year is aware of Serval and what we
are trying to do.</div>
<div>
<br/></div>
<div>
As part of my talking about the Serval
Mapping Service, Jeremy and I setup a “scavenger hunt” using the
Serval Mapping Service to place geotagged pins on the map and Serval
Rhizome to distribute photographs of the location of each small 2.5cm
square cardboard token that we hid around the sprawling Ballarat
University Campus.  Similar to geocaching, the tokens were placed so
as to be near impossible to find without knowing their location.  LCA
attendees can use the Mapping and Rhizome software to locate the
tokens and return them to Jeremy. Each token is redeemable for two
free coffee vouchers to help encourage participation.  Apart from a
bit of fun, we hope that this will provide us with some real-life
experience and feedback on the use of these technologies.</div>
<div>
<br/></div>
<div>
Jeremy also succeeded in setting up an
configuration-free gateway between Serval Mesh phones and a free SIP
to PSTN service that is running at the conference, and left some
voice mail on my cell phone to prove it.</div>
<div>
<br/></div>
<div>
We also had some interesting contact
with several businesses that may be able to make use of our
technology.  
</div>
<div>
<br/></div>
<div>
Much credit must go to Jeremy for
getting the software together, and engaging in many of the
conversations that have enabled us to have such a successful time at
LCA so far.  Also Rob Thomas has been a tireless advocate of Serval
at LCA and elsewhere, and together with Jeremy have helped many
people to install our software on their phones at the conference this
year.</div>
<div>
<br/></div>
<div>
Thus, while I was not expecting to
attend LCA this year, I am very glad that I managed to get there.</div>
<div></div>
</div>