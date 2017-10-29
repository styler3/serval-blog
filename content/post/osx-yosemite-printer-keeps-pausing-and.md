+++
date = "2015-03-02"
title = "OSX Yosemite Printer keeps pausing, and gets stuck on \"Ready to print\""
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-3131465705559509625" itemprop="description articleBody">
If you are printing to a PaperCut server, apparently printing can have trouble from a mac running Yosemite, due to the improved security in CUPS 2.0, which is part of Yosemite.<br/>
<br/>
The interim solution is to relax the sandboxing policy in CUPS 2.0, so that it behaves like it used to.  Of course, it would be better if PaperCut fixed the underlying problem in their software.<br/>
<br/>
The short version of what to do is:<br/>
<br/>
<code>sudo sh -c 'echo "Sandboxing Relaxed" &gt;&gt; /etc/cups/cups-files.conf'</code><br/><code>sudo launchctl stop org.cups.cupsd</code><br/>
<br/>
The long version can be found at:<br/>
<br/>
<a href="http://www.papercut.com/kb/Main/MacOS1010YosemiteKnownIssues">http://www.papercut.com/kb/Main/MacOS1010YosemiteKnownIssues</a>
<div></div>
</div>
