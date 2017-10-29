+++
date = "2013-02-26"
title = "3KM Mesh link using Mesh Helper Prototypes"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1331728048369071704" itemprop="description articleBody">

After the short-range testing of the mesh helpers, we then set about creating a longer-range test so that we could determine the maximum useful range.  

<br/>

As part of the exercise, a VHF repeater was located on a prominent ridge, and this seemed like a good place to put a mesh helper to give us the chance to setup some long-range links.

<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><a href="http://1.bp.blogspot.com/-KWNMehkUVvk/USxw9KWrXjI/AAAAAAAAAwI/ah_fKCfKTzY/s1600/20130226_154012.jpg"><img src="http://1.bp.blogspot.com/-KWNMehkUVvk/USxw9KWrXjI/AAAAAAAAAwI/ah_fKCfKTzY/s400/20130226_154012.jpg"/></a></td></tr>
<tr><td class="tr-caption">The VHF repeater is on the left, and our mesh helper is hiding under the plastic bag on the right to keep out of the sun.</td></tr>
</tbody></table>

<a href="http://4.bp.blogspot.com/-PXXQ7G0gEBA/USx5shWonSI/AAAAAAAAAw0/Wa6qh7SBrQA/s1600/20130226_152935.jpg"><img src="http://4.bp.blogspot.com/-PXXQ7G0gEBA/USx5shWonSI/AAAAAAAAAw0/Wa6qh7SBrQA/s400/20130226_152935.jpg"/></a>
Here is a closer view of the mesh helper lashed to the fence post before receiving the plastic bag.  You can get an idea of the kind of vantage point where the gear was placed.<br/>
<br/>



We then proceeded to drive along the road towards Pongaroa with one of the mesh helpers in the car with us.  Monitoring of link budget was using the built-in diagnostic webpage that we incorporated into servald.  

<br/>

That web page provides continuous link budget, calculated as difference between RSSI and noise-floor recalibrated into dB. I am not completely confident in the reading from this, but it is a good general guide.  

<br/>

For those interested, the radios we are using are transmitting at +30dBm, and using +3db antennae, that are admittedly poorly placed next to a large LiFePO4 battery and other gear in the buckets. Receiver sensitivity is around -121dB @ 1200bps, and so should be expected to be around -100dB @ 128kbps, giving a link budget of around 133dB.

<br/>

Earlier, we had setup a second site nearer to the cottage, the results from which are marked as "site 2" in the following table.  The primary site by the repeater is approximately 1km from the cottage, almost in the opposite direction from the road we travelled along, so the distances here are underestimates of the actual distances.  The 2.65km and 2.68km records almost certainly correspond to actual distances of &gt;3km.

<br/>

The road varied in altitude, and had a lot of road-side vegetation and forest in places, as well as hills completely occluding line-of-sight to the sites where the other mesh helpers were located.  This is reflected in the varying link budgets as we travelled along the road.
<br/>
<table bordercolor="#0033FF" cellpadding="3" cellspacing="3">
<caption><b>Link Margin versus Distance</b></caption>
<tbody>
<tr>
<th>Link Margin</th>
<th>Distance to Cottage<br/>
<br/></th>
<th>Notes</th>
</tr>
<tr>
<td>11dB</td>
<td>0.36km</td>
<td>Adjacent to the bridge</td>
</tr>
<tr>
<td>6dB</td>
<td>0.75km</td>
<td>road side</td>
</tr>
<tr>
<td>30dB to site 2</td>
<td>0.76km</td>
<td>road side</td>
</tr>
<tr>
<td>13dB to site 2</td>
<td>1.00km</td>
<td>road side</td>
</tr>
<tr>
<td>12dB</td>
<td>1.19km</td>
<td>On the hill side</td>
</tr>
<tr>
<td>18dB</td>
<td>1.33km</td>
<td>hill side</td>
</tr>
<tr>
<td>21dB</td>
<td>1.38km</td>
<td>track</td>
</tr>
<tr>
<td>10dB</td>
<td>1.48km</td>
<td>Side of road, next to a gate</td>
</tr>
<tr>
<td>2dB</td>
<td>1.63km</td>
<td>road side</td>
</tr>
<tr>
<td>13dB</td>
<td>2.00km</td>
<td>road side</td>
</tr>
<tr>
<td>23dB</td>
<td>2.00km</td>
<td>parked, antenna vertical</td>
</tr>
<tr>
<td>20dB to site 2</td>
<td>2.19km</td>
<td>road side</td>
</tr>
<tr class="”alt”">
<td>10dB</td>
<td>2.5km</td>
<td>While driving</td>
</tr>
<tr>
<td>22dB to site 2</td>
<td>2.65km</td>
<td>road</td>
</tr>
<tr>
<td>3dB to site 2</td>
<td>2.68km</td>
<td></td>
</tr>
<tr>
<td>14dB</td>
<td>26.02km</td>
<td>Steady 14db margin, but no lock/link.</td>
</tr>
</tbody></table>
<br/>
<div>
It is nice to know that we could maintain a link over distances of around 3km. There were of course spots along the way where link was not possible due to vegetation, hills and other obstacles getting in the way.</div>
<div>
<br/></div>
<div>
Between 3km and the 26km there were hills blocking any line-of-sight, and so measurements were not possible there, except in one place at around 12km, where we could not detect signal.</div>
<div>
<br/></div>
<div>
3KM is way short of what we believe these radios to be capable of, as reflected by the strong link budget (22dB) at around that range. Certainly 12km should be plausible, if not possible.</div>
<div>
<br/></div>
<div>
We are exploring a number of possible reasons why we were not able to obtain links at these distances.</div>
<div>
<br/></div>
<div>
One of the main culprits we are exploring is the forward error correction on the radios.  Currently they can detect and correct 25% BER in every 12 bits.  However, there is no block code or convolution code to allow graceful handling of bursts of errors. The addition of such a code should allow links at greater distances. The 14db reading at 26km, which was steady over several minutes, offers tantalising hope that with improved error correction links over such distances may be possible.  It is also possible that the number of black spots nearer might be reduced by such improvements in forward error correction.  </div>
<div>
<br/></div>
<div>
Something like Turbo Codes would be ideal, but are too complex to implement in the radios, but could be implemented in the wireless router.</div>
<div>
<br/></div>
<div>
Another source of trouble is the prototype units themselves, where all the components are sitting together in a plastic bucket.  There is almost certainly interference, occlusion and other problems occurring as a result.</div>
<div>
<br/></div>
<div>
It is nice to know that several kilometres is possible, and that there are some obvious areas we can work on to improve the range further.</div>
<div>
<br/></div>
<div>
What is significant is that the mesh helpers extend the range to useful distances, compared with the native WiFi capability of smartphones, as the following table summarising our experience shows.<br/>
<br/></div>
<div>
<table bordercolor="#0033FF" cellpadding="3" cellspacing="3">
<caption><b>Link Margin versus Distance <br/>(with omnidirectional antennae)</b></caption>
<tbody>
<tr>
</tr>
<tr><th>Setting</th><th>SmartPhone WiFi</th><th>Mesh Helper</th></tr>
<tr>
<td>Urban, through dwellings</td><td>~20m</td><td>~200m</td></tr>
<tr><td>Vegetation</td><td>~20m</td><td>&gt;300m</td></tr>
<tr><td>Rural</td><td>~200m</td><td>&gt;3KM</td></tr>
</tbody></table>
<br/>Note that we are concentrating on omnidirectional antennae here, because our focus is on networks that are easy for normal people to setup, without having to aim antennae or have significant radio experience.<br/>
<br/>
The Mesh Helper takes the range from being about one house to potentially tens of houses in distance, depending on the setting. <br/>
<br/>
Thanks to the square rule, this means that instead of covering perhaps just one house, this means that we can cover potentially hundreds of dwellings with one unit, thus reducing the density of units required to establish a network -- which is precisely what we set out to achieve.<br/>
<div>
<br/>
If it turns out that with improved forward error correction we can push those ranges out further, then the benefit will be even greater.<br/>
<br/>
One of the next steps will be to reduce the size of the mesh helpers to mobile-phone size, to make them truly portable, which is entirely feasible as the core electronics are already small enough.</div>
</div>
<div></div>
</div>