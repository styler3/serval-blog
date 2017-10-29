+++
date = "2013-04-13"
title = "Root-free operation of the Serval Mesh"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8434815707967540008" itemprop="description articleBody">
We have known from the beginning that expecting people to root their Android phones to use the mesh was not the ideal solution.  This is why we have put effort into liaising with the IEEE 802.11 committee, as well as encouraging Google to fix <a href="https://code.google.com/p/android/issues/detail?id=82">bug 82</a>.<br/>
<br/>
Bug 82 is the bug that describes the lack of ad-hoc Wi-Fi support in Android, and was filed back in January 2008, and at the time of writing is the fourth most starred bug in the Android bug tracker.  You can see it and vote for it <a href="https://code.google.com/p/android/issues/list?can=2&amp;q=&amp;colspec=ID+Type+Status+Owner+Summary+Stars&amp;cells=tiles">here</a>.  To vote for it, just click on the star next to the issue.<br/>
<br/>
While we hope that this will be fixed one day, and ad-hoc Wi-Fi will be easily available on all Android phones, we have put considerable effort into a work-around. <br/>
<br/>
That work-around is to alternate Wi-Fi on a phone between Access Point and Client modes. Combined with the Serval Rhizome store-and-forward protocol, this allows data to move from phone to phone.  The downside is that you can't have an end-to-end connection over many hops. Nonetheless, we have created text messaging and file sharing applications, amongst others, over Rhizome and using this step-by-step approach to moving data by Wi-Fi.<br/>
<br/>
More recently, we have sought to mature this ability to operate without root access so that the Serval Mesh software assumes that there is no root access, and to operate as best it can in that situation. This functionality is now more or less complete, and is expected to appear in Serval Mesh 0.91 in the next while.  You can try it out by downloading and building the development branch of the Serval Mesh at <a href="http://github.com/servalproject/batphone">http://github.com/servalproject/batphone</a>.<br/>
<br/>
To give an idea of how this works in practice, I made a few screenshots of a nightly build of Serval Mesh 0.91-pre:<br/>
<br/>
First, here is the new home screen.  The main difference is that the "Switch on/Switch off" button is now called "Connect".  This name might change before 0.91 is released.<br/>
<br/>

<a href="http://1.bp.blogspot.com/-jIDo16Ck4u4/UWopK4rEMzI/AAAAAAAAA40/H8cbY8ZaFWM/s1600/device-2013-04-14-131055.png"><img src="http://1.bp.blogspot.com/-jIDo16Ck4u4/UWopK4rEMzI/AAAAAAAAA40/H8cbY8ZaFWM/s320/device-2013-04-14-131055.png"/></a>

<span><br/></span>

<span>Instead of just starting or stopping the mesh, it now takes you to a list of available networks:</span>

<a href="http://4.bp.blogspot.com/-ksY8QaDpcpA/UWops6Q-bLI/AAAAAAAAA5U/-Nsp52TBFIE/s1600/device-2013-04-14-132933.png"><img src="http://4.bp.blogspot.com/-ksY8QaDpcpA/UWops6Q-bLI/AAAAAAAAA5U/-Nsp52TBFIE/s320/device-2013-04-14-132933.png"/></a>

The operation of the mesh software on the phone itself is now controlled by ticking or unticking "Enable Services". Again, the label may change and indeed we expect to make this whole display much more visually appealing. 

<br/>

The Wi-Fi networks that are available or might be available are listed below.  Selecting "Auto Cycle" is still an option to get the mostly-automatic behaviour of previous versions.  But it is now much easier to pick a particular Wi-Fi network.

<br/>

Note also that ad-hoc shows up, even though this is on an unrooted phone.  However, it won't be used without user intervention.  

<br/>

To attempt to use ad-hoc mode you touch the "Adhoc" item.  It then asks if you would like to try to setup ad-hoc mode, and reminds you that this requires root access, and might not be supported on all phones.

<br/>
<br/>

<a href="http://2.bp.blogspot.com/-iA3n7eCHufU/UWopLIMrQsI/AAAAAAAAA44/m3wE5N9ugPY/s1600/device-2013-04-14-131125.png"><img src="http://2.bp.blogspot.com/-iA3n7eCHufU/UWopLIMrQsI/AAAAAAAAA44/m3wE5N9ugPY/s320/device-2013-04-14-131125.png"/></a>
<br/>
If you respond with "Test", then it tries to get root access and enable ad-hoc Wi-Fi:<br/>
<br/>

<a href="http://1.bp.blogspot.com/-j8IiSKtm1bM/UWopLoMi0BI/AAAAAAAAA5M/B9F4rRSmPhs/s1600/device-2013-04-14-131140.png"><img src="http://1.bp.blogspot.com/-j8IiSKtm1bM/UWopLoMi0BI/AAAAAAAAA5M/B9F4rRSmPhs/s320/device-2013-04-14-131140.png"/></a>

<br/>

In the case of this phone, it fails of course, because it is not rooted.  But I can of course choose to join another Wi-Fi network, or just enable Auto Cycle mode, and any collection of phones running the Serval Mesh should then connect to one another or other networks when available:

<br/>

<a href="http://1.bp.blogspot.com/-_QwKkRZsO28/UWopK955h1I/AAAAAAAAA48/H2piFeVM7sI/s1600/device-2013-04-14-131115.png"><img src="http://1.bp.blogspot.com/-_QwKkRZsO28/UWopK955h1I/AAAAAAAAA48/H2piFeVM7sI/s320/device-2013-04-14-131115.png"/></a>
<br/>
So while there is some refinement to go, the Serval Mesh software is now able to work easily without root access, and does not try to get root access without asking the user first.
<div></div>
</div>