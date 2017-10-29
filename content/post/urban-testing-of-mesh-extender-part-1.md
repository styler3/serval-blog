+++
date = "2013-05-01"
title = "Urban testing of Mesh Extender - Part 1"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-2732276867659392926" itemprop="description articleBody">
Yesterday we finally got around to performing an urban test of the Mesh Extender prototypes.<br/>
<br/>
<div>
<div>
<object class="BLOGGER-picasa-video" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,40,0" data-thumbnail-src="https://lh6.googleusercontent.com/-wzPjusibKjE/UYHyEgHKxeI/AAAAAAAAA7w/zaQfmrRmF3s/s1600/Mesh%2BExtender%2BIndoor%2BUrban%2BTest.mp4"><param name="movie" value="http://video.google.com/googleplayer.swf?videoUrl=http%3A%2F%2Fredirector.googlevideo.com%2Fvideoplayback%3Fid%3D08d5896b274bdfa8%26itag%3D18%26source%3Dpicasa%26cmo%3Dsensitive_content%253Dyes%26ip%3D0.0.0.0%26ipbits%3D0%26expire%3D1370062611%26sparams%3Did%2Citag%2Csource%2Cip%2Cipbits%2Cexpire%26signature%3D387678F6681D9B8AB664976E83A7C03FBCC74525.2EB3741D8970B3A4E6E0DFF6D7BBEDD59DA95A78%26key%3Dlh1"></param><param name="bgcolor" value="#FFFFFF"></param><param name="allowFullScreen" value="true"></param><embed allowfullscreen="true" src="http://video.google.com/googleplayer.swf?videoUrl=http%3A%2F%2Fredirector.googlevideo.com%2Fvideoplayback%3Fid%3D08d5896b274bdfa8%26itag%3D18%26source%3Dpicasa%26cmo%3Dsensitive_content%253Dyes%26ip%3D0.0.0.0%26ipbits%3D0%26expire%3D1370062611%26sparams%3Did%2Citag%2Csource%2Cip%2Cipbits%2Cexpire%26signature%3D387678F6681D9B8AB664976E83A7C03FBCC74525.2EB3741D8970B3A4E6E0DFF6D7BBEDD59DA95A78%26key%3Dlh1" type="application/x-shockwave-flash"></embed></object></div>
</div>
<br/>
To make this a realistic test, we have one Mesh Extender just sitting inside my house on a cupboard.  There was no antenna aiming. It was not up high. It was inside a double-brick house, placed no better than you could expect an uninformed user to place it.<br/>
<br/>
We know that in similar circumstances that Wi-Fi has a range of about one house, i.e., you can often see your immediate neighbours Wi-Fi, but not any further.<br/>
<br/>
We wanted to see how much further we could cover with the Mesh Extender's 915MHz packet radio.<br/>
<br/>
The first part of the test consisted of walking around the block where we live.  This block has 11 houses in a row along its length, with us on one end (the green marker on the map).  From where we placed the Extender to the far corner on the footpath is about 192 metres as the photon flies. Transmit power was +24dBm (250mW) and air bit rate was 128kbit.<br/>
<br/>

<a href="http://1.bp.blogspot.com/-bDElWjhVoIo/UYG5MYAFviI/AAAAAAAAA6M/VoMB59nCZNg/s1600/Google+ChromeScreenSnapz094.png"><img src="http://1.bp.blogspot.com/-bDElWjhVoIo/UYG5MYAFviI/AAAAAAAAA6M/VoMB59nCZNg/s1600/Google+ChromeScreenSnapz094.png"/></a>

We were able to maintain link all the way around the block, without it dropping even once.  This is very encouraging, as it suggests that anyone on our block would be able to put a Mesh Extender in their house, and we would have digital communications between them. Again, contrast this with Wi-Fi where if you are lucky you can see your next-door neighbours Wi-Fi.

<br/>

<br/>

Encouraged by the success of this, we decided to see if we could get a link from my house to the local super-market.  The Mesh Extender remained where it was, and we walked around to the super-market. The idea was to push as far as we could until link was lost.
<br/>

<a href="http://1.bp.blogspot.com/-kbknTdIDn2g/UYG5Me7ej5I/AAAAAAAAA6I/72lcaYKDKG0/s1600/Google+ChromeScreenSnapz096.png"><img src="http://1.bp.blogspot.com/-kbknTdIDn2g/UYG5Me7ej5I/AAAAAAAAA6I/72lcaYKDKG0/s1600/Google+ChromeScreenSnapz096.png"/></a>

We took the route along Minchinbury Terrace, and then across to the bottom-right corner of the shopping complex, and then walked towards the red mark on the map.  The link became intermittent once we were on Chambers Street, and was only reestablished intermittently at the shopping centre.  The maximum distance where we had link, in the foyer of Coles, was about 262m.  

<br/>

Remember that these units were only metre or so off the ground, and one was inside a double-walled brick house, and that there were a number of similarly constructed dwellings and large trees in the way. This is really quite a hostile environment, and is certainly not unreasonably optimistic compared with expected real-world deployment in urban areas.

<br/>

As mentioned above, Wi-Fi range of about 1 house means that forming a suburban Wi-Fi mesh requires almost 100% of homes to participate.  In contrast, if we draw a circle around the 192m range where we had solid link, and the 192m-262m range where a link might be possible, the story is <i>very</i> different:

<br/>

<a href="http://4.bp.blogspot.com/-7tvHALuaZyM/UYHAEy7NdNI/AAAAAAAAA6g/pDfOfNU5LkQ/s1600/mesh-extender-range-from-inside-number10.png"><img src="http://4.bp.blogspot.com/-7tvHALuaZyM/UYHAEy7NdNI/AAAAAAAAA6g/pDfOfNU5LkQ/s1600/mesh-extender-range-from-inside-number10.png"/></a>
<br/>
The solid range area includes about 90 separate homes, and that ignores that a few of those are blocks of units.  This means that an adoption rate of 2/90 = about 2% would be sufficient to almost guarantee the formation of a continuous mesh, <i>with people just placing the Mesh Extenders in a convenient location <b>inside</b> their home</i>. <br/>
<br/>
If we assume that half the homes in the 192m - 262m range can establish a link, then that adds another 25 houses (not even counting the ones that didn't fit in the image).  In fact, in most realistic urban or suburban deployments then dwellings are likely to be packed more closely.<br/>
<br/>
But most importantly, if even a few Mesh Extenders are placed in better vantage points, perhaps on a roof, or even on the top of a book case, then it is possible that the range will be extended even further. Radio range is typically proportional to the square root of the height of the transmitter above ground level, so doubling the height of the radio from ~1m to ~2m could increase the range by about 71%, which would double the number of houses in range. Double the height at <i>both</i> ends, and the effect is combined, and the range would be doubled. <br/>
<br/>
Placing units 4m or so off the ground, e.g., on the roof of a house would likely extend the range much more, as in addition to the 2x range due to increased height, the obstruction of the house and other objects near ground level would be greatly reduced, and distances in the kilo-metres should be achievable in favourable conditions.  It seems quite feasible that well placed units could reach potentially thousands to tens of thousands of other homes.  This is something that we may try to test in the next few days.<br/>
<br/>
This is the kind of capability that makes mobile mesh telephony able to cover very large areas, and connect whole communities, and without requiring wide-spread adoption to begin forming the network. <br/>
<br/>
And I again emphasise that this is without any aiming or special skills on the part of the people "installing" the Mesh Extenders.<br/>
<br/>
To achieve this we have some hardware design work to do, as well as some interesting work on improving the packet radio firmware.  If anyone would like to pitch in and help, we'd love to hear about it.
<div></div>
</div>