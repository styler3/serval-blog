+++
date = "2011-10-18"
title = "Oh the fun of the Android linker"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1248808150872414981" itemprop="description articleBody">
So this week I decided that I would finally do the initial integration of the excellent <a href="http://nacl.cr.yp.to/">NaCl crypto library</a> into DNA, but with the view of making it available from Android so that it can be used as part of our forthcoming Rhizome browser (this is for browsing Rhizome offerings, not the web -- more on this thing in a future post).<br/>
<br/>
My main objective was to have only one copy of the NaCl library in our Android application so that the APK stays as small as possible, and so that we don't waste any more memory than we need to.<br/>
<br/>
The first challenge is that we want to access NaCl from Java, as well as the command-line dna utility.<br/>
<br/>
The second challenge is that the crypto code should be inseperable from the dna code, so that it is impossible, for example, to use linker tricks to switch the NaCl library for something insecure. <br/>
<br/>
We can't do this perfectly because it needs to be accessible from Java, which can only load native shared libraries, but it seems that we should do what we can.<br/>
<br/>
So I put all of dna and NaCl into a single shared library, libdnalib.so, using the Android NDK to build it, so that we can load it into Java and use the NaCl (and possibly dna) functions directly from in Java. <br/>
This even means that dna's main() function is in there, and so we can run dna queries and actions from in Java as though we were using the command line tool.<br/>
<br/>
Great.<br/>
<br/>
Then I tried a bit of good old fashion linker skullduggery, by making an empty C file, and compiling it linked against libdnalib.so, so that it gets dna's main() from that library, by doing (in effect):<br/>
<br/>
<span class="Apple-style-span">echo &gt;null.c</span><br/>
<span class="Apple-style-span">gcc -o dna null.c -ldnalib</span><br/>
<br/>
However, the linker on Android doesn't look in the host applications lib directory when linking an executable.  The Android linker also doesn't support the <span class="Apple-style-span">-Wl,-rpath=</span> option for specifying where to find a library.<br/>
<br/>
This is a real pain, and probably qualifies as a bug.  I should probably file the bug, but I wanted an immediate solution, since my past attempts at getting the Android folks to fix things have not met with much success.  Besides, I needed a solution that works with <i>existing</i> handsets, not future ones. So in the words of Marvin the Martian, it was back to the old drawing board.<br/>
<br/>
So my solution was to create a wrapper that just dlopen()'s libdnalib.so, and then finds and runs the main() function from in there:<br/>
<br/>
<br/>
<span class="Apple-style-span">#include &lt;dlfcn.h&gt;</span><br/>
<span class="Apple-style-span">#include &lt;stdio.h&gt;</span><br/>
<span class="Apple-style-span"><br/>
</span><br/>
<span class="Apple-style-span">int main(int argc,char **argv)</span><br/>
<span class="Apple-style-span">{</span><br/>
<span class="Apple-style-span"> void *h = dlopen("/data/data/org.servalproject/lib/libdnalib.so",RTLD_LAZY);</span><br/>
<span class="Apple-style-span"> int (*dnamain)(int,char **) = dlsym(h,"main");</span><br/>
<span class="Apple-style-span"> if (!dnamain) return fprintf(stderr,"Could not load libdnalib.so\n");</span><br/>
<span class="Apple-style-span"> return (*dnamain)(argc,argv);</span><br/>
<span class="Apple-style-span"><br/>
</span><br/>
<span class="Apple-style-span">}</span><br/>
<div><br/>
</div><br/>
The downside is that it assumes that /data/data/org.servalproject is where the application will get installed, which the Android people tell us we should not assume. <br/>
<br/>
Thus I will probably be about as popular with them as I am when I tell people to root their phones to get ad-hoc mode WiFi instead of waiting for an API to turn up in some future release of Android.<br/>
<br/>
But, when necessity beckons, one must do what one must do.<br/>
<br/>
And so I now have a solution that works and I can move onto more pressing problems.
<div></div>
</div>