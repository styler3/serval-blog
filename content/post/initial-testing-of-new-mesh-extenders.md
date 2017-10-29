+++
date = "2017-06-01"
title = "Initial testing of the new Mesh Extenders with NZ Red Cross in Dunedin"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3443145620407169155" itemprop="description articleBody">

As I have hinted at previously, I went to Dunedin with NZ Red Cross last month to participate in their field exercise there, and to bring the new Mesh Extender prototypes with me for initial socialisation and testing with the NZ RC IT&amp;Telecommunications Emergency Response Unit.

<br/>

The exercise was run over a weekend, with myself and the ERU arriving a couple of days in advance to establish VHF communications and internet access in advance for them.  Here is the white board listing the task list.  Serval Mesh and RAMP+ (another project we have with NZ RC) are on the list! (I'll talk a bit more about RAMP+ later in this post).

<br/>

<a href="https://2.bp.blogspot.com/-8o4-pvh7iog/WTDyvUkThQI/AAAAAAAAGNk/EUIJw2kKeSw6MmdaGp_v6bWEr6QLMkT4gCLcB/s1600/2017-04-28%2B22.31.44.jpg"><img src="https://2.bp.blogspot.com/-8o4-pvh7iog/WTDyvUkThQI/AAAAAAAAGNk/EUIJw2kKeSw6MmdaGp_v6bWEr6QLMkT4gCLcB/s400/2017-04-28%2B22.31.44.jpg"/></a>
<br/>
To give a feel for the exercise, here are some shots from around the Emergency Operations Centre (EOC), which was located in a Scout camp site near Dunedin.<br/>
<br/>
First, internet from two places, the satellite dish in the foreground providing VSAT internet, and the ubiquiti router (easier to see in the second image below) pulling in internet from a nearby wireless ISP.  The ISP link required activating and a fair bit of work to get going.  The ERU folks then setup an automatic fail-over between them.  The mast in the field to the right was for VHF radio. They also setup a couple of repeaters on nearby hills.<br/>
<br/>

<a href="https://4.bp.blogspot.com/-oHJFIOaIYWs/WTDysoSNQZI/AAAAAAAAGNg/WqQsNMS-SVE468ZpY13Lcl2Xt1amhfoBQCLcB/s1600/2017-04-28%2B14.25.47.jpg"><img src="https://4.bp.blogspot.com/-oHJFIOaIYWs/WTDysoSNQZI/AAAAAAAAGNg/WqQsNMS-SVE468ZpY13Lcl2Xt1amhfoBQCLcB/s320/2017-04-28%2B14.25.47.jpg"/></a>
<br/>

<a href="https://2.bp.blogspot.com/-PigdjQEsCLI/WTDysm3k-PI/AAAAAAAAGNc/mCgzpvs0K9w6Ac81R95-r007WrvLm1vEwCLcB/s1600/2017-04-28%2B14.26.01.jpg"><img src="https://2.bp.blogspot.com/-PigdjQEsCLI/WTDysm3k-PI/AAAAAAAAGNc/mCgzpvs0K9w6Ac81R95-r007WrvLm1vEwCLcB/s320/2017-04-28%2B14.26.01.jpg"/></a>
<br/>
Here is the communications desk in the EOC itself, staffed by the wonderful ERU folks in their very nice new jackets that <a href="http://www.kathmandu.co.nz/">Kathmandu</a> kindly donated:<br/>
<br/>

<a href="https://2.bp.blogspot.com/-7jZg4cOPXfg/WTDy36Su-mI/AAAAAAAAGNo/bCFoQS909Yw5bfiE3bTHbOB6KW9eN7umQCLcB/s1600/20170429_081327.jpg"><img src="https://2.bp.blogspot.com/-7jZg4cOPXfg/WTDy36Su-mI/AAAAAAAAGNo/bCFoQS909Yw5bfiE3bTHbOB6KW9eN7umQCLcB/s400/20170429_081327.jpg"/></a>
<br/>
Then here I am sitting down trying to flash and debug some teething problems on the Mesh Extenders with Steve from the ERU to the left:<br/>
<br/>

<a href="https://4.bp.blogspot.com/-9BJyf8Vay5g/WTDy83vLtCI/AAAAAAAAGNs/d4dlJw-Xb4cktrh6opWcoiVdqhMhJirKACLcB/s1600/20170429_081528.jpg"><img src="https://4.bp.blogspot.com/-9BJyf8Vay5g/WTDy83vLtCI/AAAAAAAAGNs/d4dlJw-Xb4cktrh6opWcoiVdqhMhJirKACLcB/s400/20170429_081528.jpg"/></a>
<br/>
Here is Andrew from the ERU taking a Mesh Extender and battery pack walk-about as part of a multi-hop over UHF test.<br/>

<a href="https://3.bp.blogspot.com/-ATInv783f-4/WTDzGErbZzI/AAAAAAAAGN0/CaYTB5_PKl8mhCn2U7yLo9NEU8YHK9cAwCLcB/s1600/IMG_1220.jpg"><img src="https://3.bp.blogspot.com/-ATInv783f-4/WTDzGErbZzI/AAAAAAAAGN0/CaYTB5_PKl8mhCn2U7yLo9NEU8YHK9cAwCLcB/s400/IMG_1220.jpg"/></a>
<br/>
And another of the ERU out during the exercise collecting data using RAMP+, which is a combination of <a href="http://magpi.com/">Magpi.com</a> and the Succinct Data extreme compression and satellite uplink tool designed and built by Matthew Lloyd and ourselves, which can exceed 99% compression when uploading the XML records for Magpi, making satellite SMS practical as a transport.<br/>
<br/>

<a href="https://2.bp.blogspot.com/-VJcW0SNM6ZU/WTDzJ0d2gJI/AAAAAAAAGN4/v8677nLja-MHpdxrNKzIkgKQItxTWYtQACLcB/s1600/IMG_3111.JPG"><img src="https://2.bp.blogspot.com/-VJcW0SNM6ZU/WTDzJ0d2gJI/AAAAAAAAGN4/v8677nLja-MHpdxrNKzIkgKQItxTWYtQACLcB/s400/IMG_3111.JPG"/></a>
<br/>
The week turned out to be extremely busy for me, as the Mesh Extender prototypes were still very new, and I only managed to get them packed in time, and the firmware was very raw, and required considerable work to get to the point of having the Mesh Extenders booting quickly and reliably, including formatting their microSD cards.<br/>
<br/>
This was complicated by problems we encountered with RAMP+, where the interface between the Succinct Data application on the tablets and the Garmin inReaches would break if tracking were enabled. Used separately, both work fine, but together a bug in the inReach communications library for Android gets tickled, causing an uncatchable force-quit.  This combined with a minor comedy of errors in trying to get access to the Succinct Data server back home at the University (it was now after close of business in Australia on the Friday), culminating in completely reimplementing the Succinct Data server on Amazon Web Services (for which it is much the better) from in the field, consuming a valuable 36 hour period, which I really needed to use to get the Mesh Extender firmware shaken down.<br/>
<br/>
The result was that we got RAMP+ mostly operational, but the Mesh Extenders had a couple of firmware issues that prevented us from completing any multi-hop UHF tests, which was disappointing.  We also quickly discovered a critical bug in the new Serval Chat application for Android, which rendered the application unresponsive on first load in certain circumstances.  This was of course rather disappointing for myself and the ERU team, as we had hoped to be able to carry out more sophisticated and extensive tests.<br/>
<br/>
The good news is that we have since isolated and corrected the faults that we encountered in both the Mesh Extenders and Serval Chat, and are now gearing up to making an updated firmware image in preparation for the next visit to Vanuatu, and, hopefully, with enough time before landing to perform more extensive testing (in the process we now have more extensive test cases for the firmware image, which means that we are able to automate regression testing of the faults we encountered in NZ).  But before I do that, I need to write about the first visit to Vanuatu...
<div></div>
</div>