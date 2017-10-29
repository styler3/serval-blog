+++
date = "2013-05-30"
title = "Range Testing Mesh Extenders in Boston & at the MIT Media Lab"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-676431279549589093" itemprop="description articleBody">
<div>
While here in Boston with the <a href="http://shuttleworthfoundation.org/">Shuttleworth Foundation</a>, I decided to take the opportunity to see what kind of coverage we can obtain with a Mesh Extender in my hotel room.  </div>
<div>
<br/></div>
<div>
My room is on the 7th floor of the Kendall Hotel in Cambridge, which provides a good vantage point in amongst buildings that are often 10 - 20 floors.  I put the Mesh Extender on top of the wardrobe in my room, and set about walking around the local area to see how far the signal would reach.</div>
<div>
<br/></div>
<div>
You can get an idea of the coverage in the map below, generated using the coverage mapping tool written by Loïc, one of our students.  This tool reads the signal strength directly from Mesh Extender via the ServalD HTTP interface, and merging it with a GPS fix from the phone.  The resulting trace is processed with some scripts to produce an HTML page that overlays the data points on Google Maps.</div>
<div>
We expect to release the mapping tool in the next few weeks. </div>
<div>
<br/></div>
<div>
You can see that coverage in this case extends one to two blocks. Not surprisingly, range is shortest when faced with the tallest buildings, e.g., through the Boston Marriot Hotel.  Nonetheless, the signal almost always appears to penetrate through an entire building, and is usable on the other side.  </div>
<div>
<br/></div>
<div>
Basically, whereas Wi-Fi can punch through about one wall before fading out, the UHF packet radio link can punch through something like 10 walls before fading out.</div>
<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><a href="http://3.bp.blogspot.com/-5rVSXXU6Zus/UaY_-EmKq1I/AAAAAAAABGs/rH-QU2MEIa8/s1600/Google+ChromeScreenSnapz106.png"><img src="http://3.bp.blogspot.com/-5rVSXXU6Zus/UaY_-EmKq1I/AAAAAAAABGs/rH-QU2MEIa8/s640/Google+ChromeScreenSnapz106.png"/></a></td></tr>
<tr><td class="tr-caption">Points with confirmed coverage back to my hotel room. Actual coverage is somewhat better, but the collection tool needs tweaking to show spots with good link below 10dB.</td></tr>
</tbody></table>
<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><div>
The keen eye will notice that this area is right next to MIT, and indeed we have coverage right around the MIT Media Lab where we are having our Shuttleworth Foundation meetings.  So one morning I decided to see if we could establish a mesh between my hotel room and the room we were in the Media Lab building.  </div>
<div>
<br/></div>
<div>
That room faces the away from the hotel, so the signal would have to punch through the Media Lab building, as well as the MIT Health Services building which is in between the lab and the hotel.  In the image below the room in the media lab where we were meeting is roughly indicated by the arrow near the bottom of the image.  </div>
<div>
<br/></div>

<a href="http://4.bp.blogspot.com/-f1aZpvr-tYE/UacuCIfyWHI/AAAAAAAABHQ/p_ppe8HOi4w/s1600/Google+ChromeScreenSnapz107.png"><img src="http://4.bp.blogspot.com/-f1aZpvr-tYE/UacuCIfyWHI/AAAAAAAABHQ/p_ppe8HOi4w/s640/Google+ChromeScreenSnapz107.png"/></a>
<div>
<br/></div>
<div>
<br/></div>
<div>
As the link was from the top floor of one building to the top floor of another building it is likely that some signal followed a free space path outside of the buildings, but there is certainly no line-of-sight path.</div>
<div>
<br/></div>
<div>
The link frustratingly dropped out once we were inside the building with the Mesh Extender. However, we did find that by placing the Mesh Extender out on the deck outside that we had a steady link back to the hotel room.  So while we couldn't have the Mesh Extender inside the room, it was possible to have a mesh phone inside the room, talking to the Mesh Extender outside on the deck, and from there back to the hotel. In the image below you can see that the phone could see both Mesh Extenders, as well as the other phone in my pocket.  The Mesh Extender is visible out on the deck in the background.</div>
<br/>
<a href="http://1.bp.blogspot.com/-cGlunnjuRyA/UaZkC5ZDQcI/AAAAAAAABHA/MZNOJDDj47Y/s1600/20130527_225340.jpg"><img src="http://1.bp.blogspot.com/-cGlunnjuRyA/UaZkC5ZDQcI/AAAAAAAABHA/MZNOJDDj47Y/s400/20130527_225340.jpg"/></a></td></tr>
<tr><td class="tr-caption">In the MIT Media Lab with link back to the hotel via the Mesh Extender on the balcony.</td></tr>
</tbody></table>
So while it would have been nice if link could be sustained inside the building, it was still pretty easy to establish a link between two buildings a couple of hundred metres apart in a built-up urban area, with one of the Mesh Extenders indoors.
<div></div>
</div>