+++
date = "2016-04-03"
title = "Making self-updating APKs"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-153344006344214323" itemprop="description articleBody">
Serval Mesh is designed to operate without infrastructure.  This makes over-the-air updates for it "interesting," because we cannot rely on the internet and Google Play being available, either because the network is broken, or because Naughty People are preventing others from accessing Google Play or installing Serval Mesh specifically.<br/>
<br/>
We have had a solution for this for a while, where we attach the signed manifest to the end of the Serval Mesh APK, so that it can certify to other phones running Serval Mesh, that it is indeed a legitimate update.  That way, the APK can distribute via Rhizome, and each phone receiving it will announce "update available," which then allows the update to be install.<br/>
<br/>
The trouble is, that sometime before Android 5.1.1, Google have stopped allowing APKs to have random stuff attached to the end, presumably for security reasons. After all, we have been bending the ZIP file specification to do this.  Also, we can't just include the manifest inside the APK, because that would change the signature required for the manifest, and so it would never be valid.<br/>
<br/>
Fortunately, ZIP files support the inclusion of comments, which are not included in the Jar signing signature -- so we can put our manifest in as a comment, without it upsetting the signature.  That is, the APK will install on a phone, whether or not the manifest is in there.  Once installed, we can then pull out the manifest, so that the APK can be inserted into Rhizome with the manifest that certifies it is a genuine update of Serval Mesh.<br/>
<br/>
In short, we now have a nicer solution than we had before, and which follows the ZIP file standard completely. Needless to say, we are very happy about this.
<div></div>
</div>