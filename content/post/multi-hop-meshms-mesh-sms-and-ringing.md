+++
date = "2013-05-08"
title = "Multi-Hop MeshMS (Mesh SMS) and Ringing Phones via Mesh Extender"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8764824083823320133" itemprop="description articleBody">
Today we did some more testing with the prototype Mesh Extenders, and finally got around to filming the Mesh Extenders actually relaying mesh data, rather than just reporting link quality figures. <br/>
<br/>
As a side effect, we also ended up testing some of Jeremy's new mesh routing code.<br/>
<br/>
The topology we used was two un-rooted Android phones and two Mesh Extenders. Each phone was connected to one of the Mesh Extenders as a Wi-Fi client.  The Mesh Extenders used their Wi-Fi and UHF packet radios to connect to each other.  Thus there were three hops from one phone to the other, as shown in the peer list screen grab below:<br/>
<br/>

<a href="http://1.bp.blogspot.com/-heR9UtNU_vU/UYo_QjSWMcI/AAAAAAAABBI/IxOnPJ9JyP4/s1600/MeshExtenders-facilitating-3hop-network.png"><img src="http://1.bp.blogspot.com/-heR9UtNU_vU/UYo_QjSWMcI/AAAAAAAABBI/IxOnPJ9JyP4/s400/MeshExtenders-facilitating-3hop-network.png"/></a>
Jeremy added the nice routing information to the peer list recently, so that you can see the number of hops to get to a peer, including the route taken.  This makes it much easier for us to debug multi-hop paths.<br/>
<br/>
We then put one of the Mesh Extenders on a bench by a window in the lab, and left Jeremy next to it with one of the phones:<br/>
<br/>

<a href="http://3.bp.blogspot.com/-URn-dE3BaXY/UYpEQSl0YwI/AAAAAAAABCw/Q8hYWWoyBVg/s1600/20130508_163736.jpg"><img src="http://3.bp.blogspot.com/-URn-dE3BaXY/UYpEQSl0YwI/AAAAAAAABCw/Q8hYWWoyBVg/s400/20130508_163736.jpg"/></a>
<br/>
<br/>
I took the other Mesh Extender walk-about and in the RV Bakfiets to see how far we could go, sending and receiving text messages and making the phones ring at each location.  An actual voice call over the limited bandwidth of the Mesh Extenders will not be possible until we add support for CODEC2 into batphone. What was encouraging was we did hear pops of audio when we placed calls, indicating that it was only the bandwidth starvation that was stopping us from having voice calls.<br/>
<br/>
The idea was to test reachability, rather than probe the exact limits of range.  We are planning a little phone app that will log signal strength and GPS location to help map the limits of range more exactly, but that will be another day. A couple of locations were of the menu today:<br/>
<br/>
First, in the bush behind the University.  There the challenges are vegetation and undulating land.  The near edge of the bush land where I went was visible through the lab window where the Mesh Extender was sitting, with the building not getting in the way.  Here I am in the bush with the Mest Extender and phone after doing the test there:<br/>

<br/>

<a href="http://4.bp.blogspot.com/-5fCMg1tz0P8/UYpEPgnTBfI/AAAAAAAABCk/zJiBSnuIb-k/s1600/20130508_154426.jpg"><img src="http://4.bp.blogspot.com/-5fCMg1tz0P8/UYpEPgnTBfI/AAAAAAAABCk/zJiBSnuIb-k/s400/20130508_154426.jpg"/></a>
 Here is a map showing approximately where we were.  The lab is the green spot, and we were about where the red spot is. We had about +13dB link margin, which is ample.<br/>
<br/>
Here you can see me send and receive text messages, asking Jeremy to call my phone, which he does:<br/>

<object class="BLOGGER-picasa-video" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0" data-thumbnail-src="https://lh4.googleusercontent.com/-ECq2_70k6Xo/UYpH_wM6tWI/AAAAAAAABD4/pbhc6MS6JIg/s1600/GOPR0035.MP4"><param name="movie" value="http://video.google.com/googleplayer.swf?videoUrl=http%3A%2F%2Fredirector.googlevideo.com%2Fvideoplayback%3Fid%3D18b128ae1d014e15%26itag%3D18%26source%3Dpicasa%26cmo%3Dsensitive_content%253Dyes%26ip%3D0.0.0.0%26ipbits%3D0%26expire%3D1370608896%26sparams%3Did%2Citag%2Csource%2Cip%2Cipbits%2Cexpire%26signature%3D11FD15F5FE96BE741490CD2AA8E0BA3679A5D9B4.299128BB0A4BAC1BD0D57301435632654762BC5B%26key%3Dlh1"></param><param name="bgcolor" value="#FFFFFF"></param><param name="allowFullScreen" value="true"></param><embed allowfullscreen="true" src="http://video.google.com/googleplayer.swf?videoUrl=http%3A%2F%2Fredirector.googlevideo.com%2Fvideoplayback%3Fid%3D18b128ae1d014e15%26itag%3D18%26source%3Dpicasa%26cmo%3Dsensitive_content%253Dyes%26ip%3D0.0.0.0%26ipbits%3D0%26expire%3D1370608896%26sparams%3Did%2Citag%2Csource%2Cip%2Cipbits%2Cexpire%26signature%3D11FD15F5FE96BE741490CD2AA8E0BA3679A5D9B4.299128BB0A4BAC1BD0D57301435632654762BC5B%26key%3Dlh1" type="application/x-shockwave-flash"></embed></object>
<br/>
<br/>

<a href="http://1.bp.blogspot.com/-O8hhRmByPf0/UYpAv9MjK4I/AAAAAAAABBU/Spp_QxZJCeM/s1600/Google+ChromeScreenSnapz102.png"><img src="http://1.bp.blogspot.com/-O8hhRmByPf0/UYpAv9MjK4I/AAAAAAAABBU/Spp_QxZJCeM/s640/Google+ChromeScreenSnapz102.png"/></a>

Total distance was about 315m, which was pretty nice, given all the trees in the way, and the there are some low rises in the path as well.  Also, the car park was full of cars, so the path wasn't as clear as the satellite image suggests.

<br/>

Then later in the afternoon I needed to head down to the plaza in the central part of the campus.  Discussion in the lab was not very positive about getting to the plaza in one hop.

<br/>

I rode my bakfiets down, with the Mesh Extender in the box. The first view is roughly in the direction of the lab -- through a pile of trees, and up the hill, and through the entire Engineering building -- there was no good line of sight for this one, just a strong elevated position.

<br/>


<br/>

<a href="http://1.bp.blogspot.com/-5c4qqhnkdk4/UYpEPzb-9PI/AAAAAAAABCs/OjCruoA7eCY/s1600/20130508_161949.jpg"><img src="http://1.bp.blogspot.com/-5c4qqhnkdk4/UYpEPzb-9PI/AAAAAAAABCs/OjCruoA7eCY/s320/20130508_161949.jpg"/></a>
<br/>
 This is the view across the plaza, with a number of people enjoying the unseasonably warm weather this week (28c just three weeks out from winter):<br/>
<br/>



<a href="http://1.bp.blogspot.com/-RXa4zTvH-3Y/UYpEOhrwHeI/AAAAAAAABCc/9ElRs5suAbY/s1600/20130508_161940.jpg"><img src="http://1.bp.blogspot.com/-RXa4zTvH-3Y/UYpEOhrwHeI/AAAAAAAABCc/9ElRs5suAbY/s320/20130508_161940.jpg"/></a>

<br/>

Here I call Jeremy's phone and receive a message from Jeremy while on the plaza:

<object class="BLOGGER-picasa-video" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0" data-thumbnail-src="https://lh6.googleusercontent.com/-Ml4Orn5eR9U/UYpIFV1SxhI/AAAAAAAABDk/kVrxqg_A9Jo/s1600/GOPR0036.MP4"><param name="movie" value="http://video.google.com/googleplayer.swf?videoUrl=http%3A%2F%2Fredirector.googlevideo.com%2Fvideoplayback%3Fid%3D996facca39d248de%26itag%3D18%26source%3Dpicasa%26cmo%3Dsensitive_content%253Dyes%26ip%3D0.0.0.0%26ipbits%3D0%26expire%3D1370608918%26sparams%3Did%2Citag%2Csource%2Cip%2Cipbits%2Cexpire%26signature%3D66999E92A1D99C37C653661B317BB29A2D2662AF.B76E6853EB729DBEAAD0BB991272CE412387610C%26key%3Dlh1"></param><param name="bgcolor" value="#FFFFFF"></param><param name="allowFullScreen" value="true"></param><embed allowfullscreen="true" src="http://video.google.com/googleplayer.swf?videoUrl=http%3A%2F%2Fredirector.googlevideo.com%2Fvideoplayback%3Fid%3D996facca39d248de%26itag%3D18%26source%3Dpicasa%26cmo%3Dsensitive_content%253Dyes%26ip%3D0.0.0.0%26ipbits%3D0%26expire%3D1370608918%26sparams%3Did%2Citag%2Csource%2Cip%2Cipbits%2Cexpire%26signature%3D66999E92A1D99C37C653661B317BB29A2D2662AF.B76E6853EB729DBEAAD0BB991272CE412387610C%26key%3Dlh1" type="application/x-shockwave-flash"></embed></object>

<br/>

The distance was about 415m, with +12dB link margin.  Riding around the plaza the signal was fine unless I ventured too far East (right on the map) towards the buildings, in which case the obstructions were just too much. 

<br/>

<a href="http://1.bp.blogspot.com/-56IJLQohnM8/UYpAwCE7XRI/AAAAAAAABBg/yIoN1kTO6hk/s1600/Google+ChromeScreenSnapz101.png"><img src="http://1.bp.blogspot.com/-56IJLQohnM8/UYpAwCE7XRI/AAAAAAAABBg/yIoN1kTO6hk/s640/Google+ChromeScreenSnapz101.png"/></a>

<br/>
As with the other recent tests of the Mesh Extenders, we continue to see that the distance between each hop can be something like 10x that of Wi-Fi, and hence cover 100x the area, whether in urban areas, open country, vegetated areas or otherwise.  The following list of posts is a summary of some of the tests we have performed so far, all lending support to this premise:<br/>
<br/>
<a href="http://servalpaul.blogspot.com/2013/05/urban-testing-of-mesh-extender-part-1.html">http://servalpaul.blogspot.com/2013/05/urban-testing-of-mesh-extender-part-1.html</a><br/>
<a href="http://servalpaul.blogspot.com/2013/05/urban-testing-of-mesh-extender-part-2.html">http://servalpaul.blogspot.com/2013/05/urban-testing-of-mesh-extender-part-2.html</a><br/>
<a href="http://servalpaul.blogspot.com/2013/03/testing-serval-mesh-helper-prototypes.html">http://servalpaul.blogspot.com/2013/03/testing-serval-mesh-helper-prototypes.html</a><br/>
<a href="http://servalpaul.blogspot.com/2013/02/3km-mesh-link-using-mesh-helper.html">http://servalpaul.blogspot.com/2013/02/3km-mesh-link-using-mesh-helper.html</a><br/>
<a href="http://servalpaul.blogspot.com/2013/02/mesh-link-using-our-prototype-mesh.html">http://servalpaul.blogspot.com/2013/02/mesh-link-using-our-prototype-mesh.html</a><br/>
<br/>
This is quite important, because the human voice has roughly the same propagation characteristics as Wi-Fi, that is, you can typically shout at someone if they are in Wi-Fi range, which means that prior to the Mesh Extender, single-hop mesh communications were basically no further than you could shout at someone. <br/>
<br/>
But now are consistently facilitating communications an order of magnitude further, to a distance that is more like that of a hand-held CB radio in a single hop.  But unlike a CB radio, we have rich digital services, and once we complete the firmware rewrite we will be able to carry services over many Mesh Extender hops, thus also eclipsing the range of ordinary CB radio. <br/>
<br/>
So perhaps we should be marketing Serval as something like "Digital CB" rather than just as "mobile mesh telephony"...
<div></div>
</div>