+++
date = "2013-05-16"
title = "DiskWarrior Error (-36 2747) \"hardware failure\" unless you wait for hours: solution"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-7997381374002334388" itemprop="description articleBody">
I have a DROBO which I am trying to recover with DiskWarrior.<br/>
<div>
<br/></div>
<div>
When I connect the DROBO and try to run DiskWarrior, I get an error -36 "hardware failure".  </div>
<div>
I can hear the DROBO doing "stuff".</div>
<div>
If I wait several hours until the DROBO is quiet, then DiskWarrior doesn't get the error, and I can try to recover it.</div>
<div>
<br/></div>
<div>
Scratched my head over this for a while, so figured I would post the solution in case anyone has the same problem.</div>
<div>
<br/></div>
<div>
All the forum posts are about dead disks.  </div>
<div>
<br/></div>
<div>
My disk isn't dead, it just has a sick filesystem, as proven by the fact that if I wait long enough, DiskWarrior can try to do something with it.</div>
<div>
<br/></div>
<div>
The disk activity was a clue.  </div>
<div>
<br/></div>
<div>
I suspected that TimeMachine or something else on the mac is trying to fsck the file system in preparation for mounting.  Unfortunately that takes HOURS on this large volume full of time machine backups.</div>
<div>
<br/></div>
<div>
So opened Terminal and typed: ps -ef | grep fsck_hfs and there was the culprit:</div>
<div>
<br/></div>
<div>
<span>    0 67332    18   0  6:26am ??         1:02.06 /System/Library/Filesystems/hfs.fs/Contents/Resources/../../../../../../sbin/fsck_hfs -y /dev/disk5s2</span></div>
<div>
<br/></div>
<div>
To kill it, type kill followed by the second number from the left, in this case: kill 67332</div>
<div>
<br/></div>
<div>
The disk activity stops, and you can then run DiskWarrior.<br/>
<br/>
(If you find this post helpful, please consider making a donation to <a href="http://servalproject.org/">servalproject.org</a> so that we can help people communicate during disasters). </div>
<div></div>
</div>
