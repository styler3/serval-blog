+++
date = "2012-10-15"
title = "Secure Communications Is Valuable"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-1051280553755018652" itemprop="description articleBody">
Well, we already knew this, but it is pleasing to see when others create things that are similar to what we are doing.  In this case, it is Phil Zimmermann (of PGP fame).  He has a startup called Secure Circle offering secure telephony and messaging:<br/>
<br/>
<a href="http://www.fastcompany.com/3001938/phil-zimmermanns-silent-circle-builds-secure-seductive-fortress-around-your-smartphone">http://www.fastcompany.com/3001938/phil-zimmermanns-silent-circle-builds-secure-seductive-fortress-around-your-smartphone</a><br/>
<br/>
The actual company website is <a href="https://silentcircle.com/">here</a>.<br/>
<br/>
Similarities between Silent Circle and Serval include the use of ECC for the crypto (we are using Curve25519 (effectively 251 bits) while they are using the NIST 384-bit curve), and some of the telephony services being offered.   There is no reason why we couldn't move to 384-bit or stronger crypto, but we do not see the need at this time.  It would be quite possible for us (or someone else) to switch out the crypto system for a different one should people desire to do so. The most practical reason why we are are not yet on a longer ECC system is that the NaCl library that we use is yet to support one, which reflects, in part, the fact that a (well implemented) 251-bit ECC system offers ample security for the time being.<br/>
<br/>
Differences include that Serval is free (as in beer and as in liberty) and open-source, and rather importantly, that Serval technologies are designed for resilience, and do not require a cellular network or internet access to facilitate communications.<br/>
<br/>
<br/>
<div></div>
</div>