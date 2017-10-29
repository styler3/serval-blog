+++
date = "2016-01-19"
title = "autoconf AC_PROG_JAVAC possibly undefined macro"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-813548580786263646" itemprop="description articleBody">
Some folks are occassionally hitting a problem where they receive an error similar to the following when they try to run autoconf on the serval-dna repository (or indeed other software):<br/>
<br/>
<span>autoconf AC_PROG_JAVAC possibly undefined macro</span><br/>
<br/>
This is extremely annoying, and doesn't really give any clues as to the cause.  A bit of googling reveals that this can be fixed in most cases by running:<br/>
<br/>
<span><b>autoreconf -i</b></span><br/>
<br/>
Then autoconf should be able to be run without further problems.
<div></div>
</div>