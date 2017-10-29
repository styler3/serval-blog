+++
date = "2014-08-15"
title = "Pure C firmware loader for RFD900 Radios"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3037202682203179557" itemprop="description articleBody">
We are using the RFD900 radios in the Mesh Extenders, as described in previous posts.<br/>
<br/>
The normal route for programming these is to use a python script or mono based GUI that comes with <a href="https://github.com/tridge/SiK">the SiK firmware</a>.  However, for auto-updates on the Mesh Extender we need to run the update process from on the Mesh Extender itself.<br/>
<br/>
It is possible to install python on the little OpenWRT boxes we use for the Mesh Extenders, however it isn't ideal on several fronts. <br/>
<br/>
First, it is way bigger than the entire rest of the mesh extender distribution, and seriously bloats the upgrade bundles if we want them to be all-inclusive.<br/>
<br/>
Second, for reasons I don't entirely understand, it isn't possible to run the python script headless in an /etc/rc.d script, which is basically a show stopper.<br/>
<br/>
Third, the python firmware loader doesn't check if the firmware is already the same as what is on the radio.  This means that the flash would get worn out a little with each Mesh Extender software update, even if it doesn't change the radio firmware.<br/>
<br/>
Fourth, you have to specify the baudrate of the radio.  It would be much nicer and safer to have it auto-detect.<br/>
<br/>
Our solution is to write our own compact RFD900 firmware loader in pure C that addresses all these problems. <br/>
<br/>
I have just finished the first working version, which can be downloaded from <a href="https://github.com/servalproject/flash-rfd900">https://github.com/servalproject/flash-rfd900</a>.<br/>
<br/>
It probably has some bugs, and might brick your RFD900 (although it might also help un brick it, too ;)<br/>
<br/>
It is very easy to build and use:<br/>
<br/>
To compile, just type make.  It is bland enough that it should work on most UNIX-like systems.  That said, I have only tested it on my Mac.<br/>
<br/>
To run, you need to tell it the firmware file (in intelhex format) and serial port, e.g.:<br/>
<br/>
<pre>flash900 radio~rfd900a.ihx /dev/cu.usbserial-A901G64G</pre>
<br/>
When running, it will display something like:<br/>
<br/>
<pre>Read 1760 IHEX records from firmware file
Trying to get command mode...
Checking if stuck in bootloader
Trying to switch to AT command mode
Switching to boot loader...
Got OK at 115200
Board id = $43, freq = $91
Erased parameters.
Checking if the radio already has this version of firmware...

Firmware differs: erasing and flashing...
Erasing flash.
Flash erased, now writing new firmware.
Range $f7fe - $f7ff
</pre>
<div>
<br/></div>
The Range line shows the memory range currently being verified/written, so you know how far along it is.  The flash gets verified as it is written, and the program will exit with an error if verification fails after writing.<br/>
<br/>
If you want to force it to flash the radio even if the firmware is the same, add "force" to the end of the command line:<br/>
<br/>
<pre>flash900 radio~rfd900a.ihx /dev/cu.usbserial-A901G64G force</pre>
<br/>
While this little program is far from perfect, hopefully it will be of use to some people out there.
<div></div>
</div>