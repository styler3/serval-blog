+++
date = "2011-12-19"
title = "Misleading \"Out of Memory\" Error in SQLite3"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-4890757535798254655" itemprop="description articleBody">
(Please take a look at our crowd-funding campaign at <a href="http://igg.me/at/speakfreely">igg.me/at/speakfreely</a>.)<br/>
<br/>
The following is recorded in the hope that it may save someone else the hassle of tracking down this kind of error.<br/>
<br/>
While working on Serval 0.08 I have been working with SQLite3 for the first time.<br/>
<br/>
I had the following fairly innocent query causing SQLite to report an "out of memory" error:<br/>
<br/>
<span class="Apple-style-span">int count=sqlite_exec_int64("SELECT COUNT(*) FROM FILES WHERE id='%s' AND datavalid&lt;&gt;0;",hash); </span><br/>
<br/>
<div>
<br/></div>
<div>
After spending a bit of time hunting everywhere to find where I could possibly have leaked enough RAM for SQLite3 to get upset, I finally realised that the column <span class="Apple-style-span">datavalid</span> did not exist in the <span class="Apple-style-span">FILES</span> table.  I had <i>meant</i> to update the <span class="Apple-style-span">CREATE TABLE</span> statement, but obviously hadn't gotten around to it.</div>
<div>
<br/></div>
<div>
I updated the <span class="Apple-style-span">CREATE TABLE</span> statement to include a definition for the <span class="Apple-style-span">datavalid</span> column, and the "out of memory" errors are now a thing of the past.</div>
<div>
<br/></div>
<div>
I can only guess that somewhere in SQLite3 when it tries to find the column, it gets a NULL pointer returned, which some other part of itself then interprets as a failure to allocate memory to retrieve the column, rather than the failure of the column itself to exist.</div>
<div></div>
</div>
