+++
date = "2013-02-26"
title = "Mesh link using our prototype Mesh Helper through ~200m of forest"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6496331819326643285" itemprop="description articleBody">

Yesterday we setup a test link between two buildings here on the field exercise.  The distance between the points was about 300m -- in theory short enough for a good WiFi link, like between a pair of Mesh Potatoes.  However, mobile phone WiFi has poorer range for a variety of reasons.  Also, there was 200m or so of damp forest in between, so any WiFi link would be likely to have problems.  You can see the situation here:

<a href="http://4.bp.blogspot.com/-Te4XjZWFtzI/US0RN-EOYPI/AAAAAAAAAxg/IUq3LD8bVbc/s1600/20130224_164304-marked-cropped.png"><img src="http://4.bp.blogspot.com/-Te4XjZWFtzI/US0RN-EOYPI/AAAAAAAAAxg/IUq3LD8bVbc/s400/20130224_164304-marked-cropped.png"/></a>

<br/>

A perfect chance to try out our prototype <a href="http://servalpaul.blogspot.co.nz/2013/02/building-serval-mesh-helper-device.html">Mesh Helper devices</a> with their UHF packet radios. Basically they look like this, with a OpenWRT router, UHF packet radio and a big LiFePO4 rechargeable battery in a plastic lunch bucket:

<br/>

<a href="http://4.bp.blogspot.com/-opNoXRyiXpQ/URrrZncURfI/AAAAAAAAAuk/8f1Yfvnbf_o/s1600/20130213_111342.jpg"><img src="http://4.bp.blogspot.com/-opNoXRyiXpQ/URrrZncURfI/AAAAAAAAAuk/8f1Yfvnbf_o/s320/20130213_111342.jpg"/></a>

<br/>

<br/>

So we put one mesh helper at the wool-shed (the building on the left of the image above).  The landing of the wool-shed was ideally situated, a bit elevated and facing towards the other building:

<br/>



<a href="http://4.bp.blogspot.com/-z-zGNVNDzVE/USx6CyWFtiI/AAAAAAAAAxE/rdukj6KQbsQ/s1600/20130225_180545.jpg"><img src="http://4.bp.blogspot.com/-z-zGNVNDzVE/USx6CyWFtiI/AAAAAAAAAxE/rdukj6KQbsQ/s320/20130225_180545.jpg"/></a>
<div>
<br/></div>
<div>
You can see the whole of the front of the wool-shed here.  The large antenna mast is a HF radio link that is part of the exercise.</div>
<div>
<a href="http://4.bp.blogspot.com/-i7_30qZG2Dc/USxxBeipq_I/AAAAAAAAAwQ/1fDkGTZxSpk/s1600/20130225_180620.jpg"><img src="http://4.bp.blogspot.com/-i7_30qZG2Dc/USxxBeipq_I/AAAAAAAAAwQ/1fDkGTZxSpk/s320/20130225_180620.jpg"/></a></div>
<div>
<br/></div>
<div>
At the other end, we tried placing the other mesh helper on the roof of one of the out buildings where it was close enough to provide WiFi coverage for nearby phones, but hopefully provide a link to the wool-shed.  </div>

<a href="http://4.bp.blogspot.com/-PZwfFWcdMNs/USx6MM28xeI/AAAAAAAAAxM/e5qV8Tgp3tU/s1600/20130225_094702.jpg"><img src="http://4.bp.blogspot.com/-PZwfFWcdMNs/USx6MM28xeI/AAAAAAAAAxM/e5qV8Tgp3tU/s320/20130225_094702.jpg"/></a>
<div>
<br/></div>
<br/>
Unfortunately the roof was almost completely blocking signal, and so we didn't quite get link to the wool-shed from there.  But by moving the mesh helper to the back of an adjacent building we got a strong signal (indicated by the RSSI and link-lock from the radios), although I forgot to write down exactly what the link budget was.<br/>
<br/>

<a href="http://2.bp.blogspot.com/-LAVmsE0YvoM/USxxI1PunSI/AAAAAAAAAwY/fm2pcL9LfHo/s1600/20130225_193345.jpg"><img src="http://2.bp.blogspot.com/-LAVmsE0YvoM/USxxI1PunSI/AAAAAAAAAwY/fm2pcL9LfHo/s320/20130225_193345.jpg"/></a>
<br/>
We then sent a message from the wool-shed back to the operations room near the other mesh helper device, which was successfully received:<br/>
<br/>

<a href="http://3.bp.blogspot.com/-l8xXC5merms/US0wKiO2HrI/AAAAAAAAAyA/jmd1duuAEWY/s1600/20130227_103933-cropped.jpg"><img src="http://3.bp.blogspot.com/-l8xXC5merms/US0wKiO2HrI/AAAAAAAAAyA/jmd1duuAEWY/s320/20130227_103933-cropped.jpg"/></a>

<br/>
<br/>
What is nice is that all we have to do is to place the boxes, and everything connects automatically, keeping with our zero-configuration ideal for Serval Mesh networks.<br/>
<br/>
The next step is to do some longer-range tests with one of the units on a good vantage point, so that we can get an idea of the maximum range possible with the current configuration.
<div></div>
</div>