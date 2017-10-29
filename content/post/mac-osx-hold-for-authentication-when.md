+++
date = "2015-01-22"
title = "Mac OSX \"Hold for authentication\" when trying to print"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-5043913923495538679" itemprop="description articleBody">
Today I tried to get printing to work from my mac (running Yosemite) to the printers here at work.  The printers are accessed using SMB. <br/>
<br/>
I could easily add the printers, but when I tried to print, it would accept my username and password for the printer, but then revert straight back to saying "Hold for authentication". <br/>
<br/>
Deleting the printers and recreating them didn't fix it. <br/>
Nor did deleting the associated entries from the OSX keyring help.<br/>
<br/>
Thus the usually recommended steps failed to fix the problem.<br/>
<br/>
It took a couple of hours of research and experimentation to discover that <a href="http://people.bu.edu/rbs/ThingsApple/Macintosh/Macintosh-printing.html">this page</a> had most of the information needed to solve the problem.<br/>
<br/>
The problem in my case was caused by the print system on the mac from failing to properly negotiate authentication in some way. But here is how I fixed it:<br/>
<br/>
<i>Step 1</i>: Try to print something to this printer.  Then open the print queue for the printer, and click on the refresh (curly-arrow) icon to the right of the job name.  It should prompt you for your username and password for the print server, and then revert to "Hold for authentication".<br/>
<br/>
This is really important. If you don't try to send a print job and have it stuck in "Hold for authentication" first, strange things can still happen after following the procedure below.  For me, I found that the print job would try to print, but the print queue would then immediately become paused, with the print job marked "Ready to print".  Very frustrating.<br/>
<i><br/></i>
<i>Step 2</i>: Open a terminal window.  Everything we do from here will be done from in the terminal window.<br/>
<br/>
<i>Step 3</i>: Find out the name of the printer on the command line by typing the following and pressing return:<br/>
<br/>
<span><b>lpstat -s</b></span><br/>
<span><b><br/></b></span>
<span><i>Step 4</i>: Find the printer in question in the output. You will see that the names of the print queues have any fancy characters replaced with an underscore.  So your print queue name might have lots of underscores in it.  For example, my printer called "Tonsley : mono" appears in the output of </span><span>lpstat -s</span><span> below as "</span><span>Tonsley___mono</span><span>" (highlighted below):</span><br/>
<span><br/></span>
<div class="p1">
<span class="s1"><span>$ lpstat -s</span></span></div>
<div class="p1">
<span class="s1"><span>system default destination: Tonsley___colour__A3_in_tray_2_</span></span></div>
<div class="p1">
<span class="s1"><span>device for GenericScanner: usb://00000000-0000-0000-FA13-000000000000</span></span></div>
<div class="p1">
<span class="s1"><span>device for LaserJet_6MP__Jet_Direct_: socket://192.168.1.200/</span></span></div>
<div class="p1">
<span class="s1"><span>device for Lexmark_6200_Series: usb://Lexmark/6200%20Series?serial=21B1280030008E5</span></span></div>
<div class="p1">
<span class="s1"><span>device for Loopback: socket://127.0.0.1/</span></span></div>
<div class="p1">
<span class="s1"><span>device for Samsung_CLP_310_Series: usb://Samsung/CLP-310%20Series?serial=149RBAFZ400869Z</span></span></div>
<div class="p1">
<span class="s1"><span>device for Samsung_CLP_315_Series___alfred: dnssd://Samsung%20CLP-315%20Series%20%40%20alfred._ipp._tcp.local.</span></span></div>
<div class="p1">
<span class="s1"><span>device for Samsung_ML_1640_Series: usb://Samsung/ML-1640%20Series?serial=3511BAFS501610N.</span></span></div>
<div class="p1">
<span class="s1"><span>device for Tonsley___colour__A3_in_tray_2_: smb://tonsprint.isd.ad.flinders.edu.au/mdf-colour</span></span></div>
<br/>
<div class="p1">
<span class="s1"><span>device for <b>Tonsley___mono</b>: smb://tonsprint.isd.ad.flinders.edu.au/mfd-bw</span></span></div>
<div class="p1">
<span class="s1"><span>$</span></span></div>
<div class="p1">
<br/></div>
<div class="p1">
<span class="s1"><span><i>Step 5</i>: Force the mac to use username,password authentication for this printer by typing the following command (but don't forget to change the printer name from </span><span>Tonsley___mono</span><span> to the name of your print queue that you obtained in the previous step).  </span></span></div>
<div class="p1">
<span class="s1"><span><br/></span></span></div>
<div class="p1">
<span><span class="s1">sudo lpadmin -p Tonlsey___mono </span>-o auth-info-required=username,password</span></div>
<div class="p1">
<span><br/></span></div>
<div class="p1">
<span>When you hit return after typing this command you will be asked for your mac password.  Type it in.</span></div>
<div class="p1">
<span><br/></span></div>
<div class="p1">
<span><i>Step 6</i>: Attempt to print using the printer.  It should now work.  If it doesn't try deleting the printer and following the sequence again.  If the print queue keeps pausing itself and saying the print job is "ready to print", read the important note on step 1.</span></div>
<div class="p1">
<span><br/></span></div>
<div class="p1">
<span>If this information helps you, please consider donating to <a href="http://servalproject.org/">http://servalproject.org</a>.</span></div>
<div></div>
</div>
