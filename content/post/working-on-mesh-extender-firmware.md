+++
date = "2015-12-10"
title = "Working on Mesh Extender firmware"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-6372541028817949535" itemprop="description articleBody">
I've been working on various aspects of the Mesh Extender firmware lately.<br/>
<br/>
There are now a bunch of configuration options you can set by putting text files on the FAT partition of the USB memory stick.  This makes it fairly easy to set the configuration in the field, but putting the USB stick into almost any computer.  Gory details for them are <a href="https://github.com/servalproject/mesh-extender-builder/blob/master/README.md">on github</a>, but I'll introduce a couple of fun ones now.<br/>
<br/>
<span><b>otabid.txt</b></span> lets you specify a Rhizome Bundle ID (BID) that will be assumed to contain over-the-air updates.  Together with the <span><b>over-the-air-updates/bootstrap</b></span> program in the <span><b>mesh-extender-builder</b></span> repository linked above, this creates a nice easy way to update the main Serval binaries and configuration files on a Mesh Extender.  While this facility was designed to help with the development process, it will also come in handy for general software updates.  By setting the BID to a BID of your own choice, it is possible to have separate groups of Mesh Extenders that get updated separately, so that you can, for example, maintain separate development and production devices.<br/>
<br/>
The second file is <b><span>monitor.sid</span></b>, and works with the above so that you can get a Mesh Extender to send a MeshMS message to someone whenever they apply an over-the-air update.  The message contains the GIT commit of the mesh-extender-builder repository that built the over-the-air update, thus providing you with a nice easy way to keep track of which Mesh Extenders have which version of what.<br/>
<br/>
Sending the MeshMS was pretty easy, as we have a nice command line interface for doing so. The only real magic is getting the SID of the Mesh Extender, which we do with a nested shell command to get the SID out of Serval's keyring structure.  Here is the complete bit of code that sends the MeshMS, if <span><b>monitor.sid</b></span> exists.<br/>
<br/>
<div class="p1">
<span class="s1"><span># Now send a MeshMS to whoever cares about this mesh extender</span></span></div>
<div class="p1">
<span class="s1"><span>if [ -e /dos/monitor.sid ]; then</span></span></div>
<div class="p1">
<span class="s1"><span>  RECIPIENT=`cat /dos/monitor.sid`</span></span></div>
<div class="p1">
<span class="s1"><span>  COMMIT="GITCOMMITSTUFF"</span></span></div>
<div class="p1">
<span class="s1"><span>  /serval/servald meshms send message `/serval/servald keyring list | tail -1 | cut -f1 -d:` ${RECIPIENT} "Over-the-air-update installed on this mesh extender: git ${COMMIT}"</span></span></div>
<br/>
<div class="p1">
<span class="s1"><span>fi</span></span></div>
<div class="p1">
<span class="s1"><span><br/></span></span></div>
<div class="p1">
What was really nice was that this worked first time.  Once I got the SID out of my phone, and put it on the Mesh Extender, and pushed out an OTA update, I had a MeshMS within a minute or so that looked like this:</div>
<div class="p1">
<br/></div>

<a href="http://2.bp.blogspot.com/-CP1VHwuqx2M/Vmog7h6V0uI/AAAAAAAAFvo/vtIEz3-wIKw/s1600/%253Atmp%253Ame-ota-notification.png"><img src="http://2.bp.blogspot.com/-CP1VHwuqx2M/Vmog7h6V0uI/AAAAAAAAFvo/vtIEz3-wIKw/s1600/%253Atmp%253Ame-ota-notification.png"/></a>
<div class="p1">
<br/></div>
<div class="p1">
Note that the timestamp is the creation time of the OTA update, not the time it was applied.</div>
<div class="p1">
<br/></div>
<div class="p1">
Also, note that these OTA updates are pushed out over the Serval Mesh itself -- the Mesh Extender has no internet access.  In other words, we now have a nice facility that allows us to update Mesh Extenders in the field, without any supporting infrastructure, and with enough feedback so that we know which devices have been updated to what version.</div>
<div></div>
</div>