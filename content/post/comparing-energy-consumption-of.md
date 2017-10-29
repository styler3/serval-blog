+++
date = "2013-04-24"
title = "Comparing energy consumption of candidate Mesh Extender components"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3761757827202525779" itemprop="description articleBody">
I am trying to design the 2nd generation Mesh Extender prototypes.  These will still be prototypes, and budgetary and time constraints mean that we will need to use off-the-shelf hardware for the most part.<br/>
<br/>
Two of the goals are to reduce the size from bucket sized to book-sized, and to weigh less than a kilo-gram, while still preserving at least 24 hours of run-time. A third goal is to use a much faster CPU so that verifying signatures on Rhizome bundles no longer takes tens of milliseconds.<br/>
<br/>
This introduces a tension on the battery size.  The 120WH batteries we have been using would be great, if only they were smaller and lighter. We could of course go for a very small and light battery, but then the Mesh Extender wouldn't be able to run for 24 hours between recharges. <br/>
<br/>
To know just how small we can make the battery, we need to know what our power budget is, and this is what I set about determining today.  You can see the test rig in the picture. Basically I measured the current consumed by the USB lead that I was using to power everything, and varied what I plugged in the end.<br/>
<br/>

<a href="http://1.bp.blogspot.com/-2QzyLFuUQ8k/UXfAMQ_f4dI/AAAAAAAAA5k/XA_sftyom8k/s1600/20130424_144652.jpg"><img src="http://1.bp.blogspot.com/-2QzyLFuUQ8k/UXfAMQ_f4dI/AAAAAAAAA5k/XA_sftyom8k/s640/20130424_144652.jpg"/></a>

<br/>
The display on the TV is the HDMI output of the MK808B which is plugged in out of view behind the TV.  The MK802ii is visible just to the left of the Mac, and one of the RFD900 radios connected to an FTDI USB2serial adapter is currently plugged into the USB lead that is powered by the desk supply on the left, and is consuming 0.091A @ 4.995V DC, which implies power consumption of around 0.46W at that particular instant.<br/>
<br/>
I used the TP-LINK WR703N based Mesh Extender prototypes as a base-line, and compared that against MK802ii and MK808B Android "Stick PCs".  I also separately measured the power consumption of the USB to serial adapters, and tried to get an idea of the power consumption of the RFD900 radios as well.  The raw measurements I made are available <a href="http://developer.servalproject.org/dokuwiki/doku.php?id=content:meshhelper:prototyping_on_mk808&amp;#comparing_power_consumption_of_the_various_devices">here</a>.<br/>
<br/>
The summary of what I discovered is:<br/>
<br/>
<table cellpadding="2">
<tbody>
<tr><th>Device</th><th>Feature</th><th>Energy Consumption</th>
</tr>
<tr>
<td>TP-LINK WR703N</td>
<td>Base power consumption</td><td>0.50W - 0.55W</td>
</tr>
<tr>
<td></td><td>Wi-Fi (Access Point Mode + Ad-Hoc Mode)<br/>
+ USB hub + memory stick + running servald</td><td>0.46W - 0.50W</td>
</tr>
<tr>
<td></td><td>Base + Wi-Fi + servald</td><td>0.96W - 1.05W</td>
</tr>
<tr>
<td>MK802ii</td>
<td>Base + Wi-Fi Client Mode + HDMI display</td><td>1.05W - 1.5W</td>
</tr>
<tr>
<td></td>
<td>Base + Wi-Fi Client Mode</td><td>1.0W - 1.50W</td>
</tr>
<tr>
<td>MK808B</td>
<td>Base power consumption</td><td>0.51W - 0.52W</td>
</tr>
<tr>
<td></td><td>HDMI Display Connected</td><td>0.21W - 0.22W</td>
</tr>
<tr>
<td></td><td>Wi-Fi (Client Mode)</td><td>0.21W - 0.25W*</td>
</tr>
<tr>
<td></td><td>Wi-Fi (Access Point Mode)</td><td>0.21W - 0.27W*</td>
</tr>
<tr>
<td></td><td>Base + Wi-Fi</td><td>0.73W - 0.79W</td>
</tr>
<tr>
<td>CP210x USB2Serial</td><td></td><td>0.13W - 0.14W</td>
</tr>
<tr>
<td>FTDI USB2Serial</td><td></td><td>0.11W</td>
</tr>
<tr><td>RFD900</td>
<td>TX power set to 250mW</td><td>0.09W - &gt;0.49W*</td></tr>
</tbody></table>
<br/>
<br/>
Entries marked with an asterisk probably underestimate the peak power consumption, because the bench top supply I was using did not have (or probably I didn't know how to use) hold peak current mode that would let me see what the peak current consumption was.  Instead, I sat and watched the display and tried to read the lowest and highest numbers off to provide estimated power consumption ranges. <br/>
<br/>
This was mostly a problem with the RFD900 radios where RX and TX power consumption differ significantly, compounded by the radio switching rapidly between the modes.<br/>
<br/>
The results were a pleasant surprise over all, because I had been led to believe that the MK808B used somewhat more than 1W when idle, so to find that it used only about three-quarters of a watt was a pleasing.  A significant contributor of this efficiency seems to come from the ability of the MK8080B ROM that I used to disable the HDMI output, saving a fifth of a watt.  This doesn't seem to be part of the ROM on the MK802ii that I have here.<br/>
<br/>
When booting or doing heavy CPU load the power consumption of all three devices was substantially higher, as these embedded platform all use a variety of tricks to minimise power consumption.<br/>
<br/>
I was surprised to discover that the MK808B might in fact use less energy than the WR703N, provided that running servald on it doesn't use more than a quarter of a watt.  The cores in the MK808B apparently throttle down to 265MHz when there is nothing to do, which should be enough to run servald, so it might be that the energy consumption increases only very slightly under typical loads. <br/>
<br/>
I started to look into measuring servald's power consumption on the MK808B, but ran out of time when I hit an odd problem with the serial connect to the radio on the MK808B, perhaps related to the CP210x adapter.  I will revisit this in the next week or so.<br/>
<br/>
So provided the servald energy consumption comes in okay, it looks like the MK808B is a good contender for the next model of Mesh Extender prototype. The main caveat is the lack of simultaneous access point and ad-hoc Wi-Fi, which means that the Mesh Extenders will only be able to talk to each other via packet radio, instead of being able to use Wi-Fi when in close proximity.<br/>
<br/>
All up, it looks like our continuous energy budget, averaging out RFD900 RX and TX consumption @ 250mW (+20dBm) will probably be around 1.3W or so.  Allowing for an 80% efficient supply from battery, this means we need 1.65W * 24 hours = 40Wh battery capacity.  Allow an extra 10Wh or so for charging a smart phone, and we need a battery of somewhere around 50Wh to meet our needs. <br/>
<br/>
So even though there are a few uncertainties around actual averaged RFD900 power consumption and the power consumption that running servald will introduce, we have a ball-park battery size, and one which is much smaller than the 120Wh monsters we have been using to date.  I have ordered a 50Wh battery pack from dealextreme so that I can test the run-time in the next week or two.
<div></div>
</div>