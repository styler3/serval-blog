+++
date = "2015-08-28"
title = "Testing RFD900 radio at Arkaroola"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3399080488084494402" itemprop="description articleBody">
Last week I was up at Arkaroola for Science Week, and took the opportunity to test the RFD900 radios up there in preparation for some upcoming Mesh Extender testing there.<br/>
<br/>
The idea of the tests was to try the RFD900s out in single-channel (non-hopping) mode, now that we have an experimental spectrum license issued for Arkaroola.  This means that we can run the RFD900 at full power, without frequency hopping enabled, as a precursor to the new radio the RFDesign folks are working on, that can be operated in an equivalent mode without the special spectrum license. <br/>
<br/>
The benefit of all this is that we can completely avoid the synchronisation issue between Mesh Extenders, and thus allow more than just pairs of Mesh Extenders to communicate. This is a big step forward, and one that has been a long time coming!<br/>
<br/>
So, I configured the radios down here in Adelaide, but set to 1mW, so that we would not be in breach of the LIPD Class License under which the RFD900 is typically operated.  This let me confirm that I had them setup properly.<br/>
<br/>
Then, up at Arkaroola, I put one radio in the window of one of the buildings in the Arkaroola Village, and drove up towards Coulthard's Lookout, about 4 - 5km away, to confirm that we could get that kind of range.  We were not expecting any problems, but just wanted to make sure that they worked in the rocky terrain that is full of iron and odd shaped rocks on the ground that can mess with radio propagation.<br/>
<br/>
A little way before Coulthard's Lookout there is a ridge that has excellent line of sight back to the village, and is almost 4km from the village.  So we stopped there to test performance, which confirmed that we were losing only a small percentage of packets.  We did also discover that horizontal polarisation was pretty much useless, and that it was the vertical polarisation that was doing all the work.<br/>
<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><a href="http://2.bp.blogspot.com/-MDMIWNtUjNw/VeDXs41H0xI/AAAAAAAAFm0/m8ZBwPJ3IaM/s1600/P1010446-PGS-Radio-Testing-on-Ridge.JPG"><img src="http://2.bp.blogspot.com/-MDMIWNtUjNw/VeDXs41H0xI/AAAAAAAAFm0/m8ZBwPJ3IaM/s640/P1010446-PGS-Radio-Testing-on-Ridge.JPG"/></a></td></tr>
<tr><td class="tr-caption">Here I am in my "other" office. The village is just visible in the distance.</td></tr>
</tbody></table>
<br/>
We then went up to Coulthard's Lookout, and were receiving only perhaps 50% of packets, which rather surprised us, as we had expected better performance, however, it was adequate.  It was only the next morning driving home that I realised that I had left the radio set to 1mW !  So the RFD900 was still getting 50% of packets through at 1/500th the TX power that we could use. <br/>
<br/>
Given that every 4x increase should double the range, this means that we should expect 50% packet throughput at a range more like 85km -- and this is with both radios on the ground. Previous tests indicating ~80km range of the RFD900 has involved one radio being in the air on a UAV.<br/>
<br/>
Part of the reason for the great performance (apart from the great design and implementation of the RFD900) is the REALLY low level of background noise at Arkaroola.  Based on the RSSI indications of the RFD900 it is probably 10 - 20dB lower than in Adelaide.  But this isn't news to us, as we know from previous work that the noise floor at 2.4GHz - 5GHz is around -100dBm, compared with around -80dBm here in Adelaide.<br/>
<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><a href="http://2.bp.blogspot.com/-TZ6WvVJ3MuQ/VeDYTTNw1gI/AAAAAAAAFm8/7nbntHKWqQQ/s1600/P1010355.JPG"><img src="http://2.bp.blogspot.com/-TZ6WvVJ3MuQ/VeDYTTNw1gI/AAAAAAAAFm8/7nbntHKWqQQ/s640/P1010355.JPG"/></a></td></tr>
<tr><td class="tr-caption">Apparently it was family day in the office.</td></tr>
</tbody></table>
<br/>
<div></div>
</div>