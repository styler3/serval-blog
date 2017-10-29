+++
date = "2011-11-21"
title = "Building The Serval BatPhone Software"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8674018287085734752" itemprop="description articleBody">
We have been putting some significant effort into making the Serval BatPhone software easier to build from scratch, especially first time around.<br/>
<br/>
<a href="http://3.bp.blogspot.com/-JXog0HFRX-o/TsrrbJo7wJI/AAAAAAAAAIQ/ERD-UzjtYEo/s1600/TerminalScreenSnapz003.png"><img src="http://3.bp.blogspot.com/-JXog0HFRX-o/TsrrbJo7wJI/AAAAAAAAAIQ/ERD-UzjtYEo/s640/TerminalScreenSnapz003.png"/></a><br/>
<br/>
The procedure for Mac/Linux has now been reduced to (assuming you want the wifi-autodetect branch, which for now you probably do):<br/>
<br/>
<br/>
1. <span class="Apple-style-span"><b>git clone git://github.com/servalproject/batphone.git -b wifi-autodetect</b></span><br/>
2. <span class="Apple-style-span"><b>cd batphone</b></span><br/>
3. <span class="Apple-style-span"><b>./BUILD.txt</b></span><br/>
<br/>
After that, you should be able to compile the software from in Eclipse without difficulty, as all the messy stuff has been taken care of (git sub-modules, JNI/NDK compilation, NaCl preparation, among others).<br/>
<br/>
This easy build process will be pushed up to the master branch fairly soon, but for now, it is only available with the wifi-autodetect branch.<br/>
<br/>
Note that building on Windows remains unsupported, as end of line markers in files get messed up if great care is not taken.  If you want to build on Windows, we recommend you install a Linux virtual machine, e.g., using the free VirtualBox software, and run the build process from in there.
<div></div>
</div>