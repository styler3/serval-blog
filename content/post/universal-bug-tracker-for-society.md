+++
date = "2012-06-06"
title = "The Universal Bug Tracker For Society"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-662268362159487186" itemprop="description articleBody">
<br/>
I have a problem. I have too many ideas for things that should be
made or fixed to make the world a better place.<br/>
<br/>
 Let me explain a
little. I run the Serval Project, making mobile telecommunications
available in many situations where it is not currently possible.  In
leading that project I have discovered that there are some serious
problems with WiFi for supporting ad-hoc network that it would be
great to have fixed.  
<br/>
<br/>

Then I also discovered that it would be really great to make
mobile phones with a built-in Arduino or similar micro-controller and
accessible hardware port so that people can innovate with mobile
hardware just like they do with mobile software.  This could be used
to make all sorts of things, from powerful yet cheap environmental
monitoring systems, to supporting long-range mobile mesh networks, to
creating really low-cost medical monitoring devices (for example, a
pulse-oximetry machine is really just four LEDs plus some signal
processing that a phone could easily provide).<br/>
<br/>
This is already too much for me to do right now.  But I have other ideas queued up, and that I come up with over time.<br/>
<br/>
For example, since being inspired by Prof. David Powers during my undergraduate
degree, I have been convinced that we need to make laws
machine-readable.  This makes a lot of sense, since the whole idea of
legal language is to be clear and precise. In the past legalese was
the best we had to express the logic part of laws, but now we have
computer languages and compilers that are so precise that it is
almost annoying, but more importantly, can help us to visualise and
transform legal logic into other equivalent forms that allows the
intent and effect of the laws to be checked before being proclaimed.<br/>
<br/>
With some careful construction, we could make a LawCompiler 1.0 that
lets us do this kind of thing.  Much would be possible with just a
combination of definitions and logic blocks.   For example, to work
out if someone could legally work in Australia, we might have a logic
block like:<br/>
<blockquote>
<span>FUNCTION CanLegallyWorkInAustralia BEGIN<br/> IF
IsAustralianCitizen OR IsNewZealandCitizen OR HoldsValidWorkVisa THEN
<br/>  RETURN true<br/> ELSE<br/>  RETURN false<br/> END IF<br/>END FUNCTION</span></blockquote>
Then all that needs to be done is to recurse back through the
referenced terms in the logic block and define them also.  The ideal
would be that terms are defined as logic blocks themselves, but at
some point there is probably a need to define some in legal terms, so
you simply have a definition, e.g., we might cheat in the above and
define IsNewZealandCitizen like:<br/>
<blockquote>
<span>DEFINITION IsNewZealandCitizen IN ENGLISH IS<br/> “A
person shall be considered a citizen of New Zealand if  they are not a
citizen of Australia, and if they currently hold citizenship in the
nation of New Zealand.”<br/>END DEFINITION</span></blockquote>
But eventually we could do things like:<br/>
<blockquote>
<span>IMPORT IsNewZealandCitizen FROM  </span><span>NewZealand.CitizenshipAct.1992;</span></blockquote>
This would allow a flexible, bottom-up approach to harmonising
laws between jurisdictions where it makes sense (some distinction
between dynamic versus static binding of definitions would be
necessary).  For example, states or counties could reference common
dog-ownership regulations, or countries in the European Union could
harmonise laws by referencing definitions created by the EU, and such
harmonisations could be made progressively.<br/>
<br/>
The compilable laws would be no
less readable than ones in legalese by the average person on the street, and would have the
advantage of being subject to precise interpretation, irrespective of
the human languages involved, thus aiding translation and consistency
in jurisdictions where laws have versions in multiple languages.  To
aid interpretation, or to help find bugs in laws, such logical
definitions of laws can be transformed, e.g., into a truth table,
that allows for checking that the law does not create any strange
corner cases, which is a very common problem in laws of any
significant complexity.  For our legality of working test above, the
truth table would resolve to something like:<br/>
<br/>
<table cellpadding="4" cellspacing="0">
<colgroup><col></col>
<col></col>
<col></col>
<col></col>
</colgroup><tbody>
<tr valign="TOP">
<td>
   CanLegallyWorkInAustralia<br/>
</td>
<td>
   IsAustralianCitizen<br/>
</td>
<td>
   IsNewZealandCitizen<br/>
</td>
<td>
   HoldsValidWorkVisa<br/>
</td>
</tr>
<tr valign="TOP">
<td>
   TRUE<br/>
</td>
<td>
   TRUE<br/>
</td>
<td>
   N/A<br/>
</td>
<td>
   N/A<br/>
</td>
</tr>
<tr valign="TOP">
<td>
   TRUE<br/>
</td>
<td>
   N/A<br/>
</td>
<td>
   TRUE<br/>
</td>
<td>
   N/A<br/>
</td>
</tr>
<tr valign="TOP">
<td>
   TRUE<br/>
</td>
<td>
   N/A<br/>
</td>
<td>
   N/A<br/>
</td>
<td>
   TRUE<br/>
</td>
</tr>
<tr valign="TOP">
<td>
   FALSE<br/>
</td>
<td>
   FALSE<br/>
</td>
<td>
   FALSE<br/>
</td>
<td>
   FALSE<br/>
</td>
</tr>
</tbody></table>
<br/>
By definition each of the lines in the truth table are mutually
exclusive, and so it becomes fairly easy to work out what will happen
in any given situation.  Of course for realistic laws, there may be
dozens of input factors, and so the truth-table may grow very large,
but that can always be avoided by creating intermediate definitions
for common cases.  This also helps promote the cleaning up of the
logic in laws instead of perpetually tacking bits on the end that
make the entire thing incomprehensible. Income tax laws are a good
example of this.  By being able to compare truth-tables before and
after a patch, it becomes possible to know <i>with complete
certainty</i>, that the patch to the law (or cleanup of the law) has
not changed the meaning of the law in any unexpected way.<br/>
<br/>
Anyway, I digress greatly, but that is perhaps the point.  I need
a place to capture all these ideas, so that they can be vetted,
prioritised and actioned, either by myself or someone else. 
Similarly, it would be great to capture everyone else's ideas, and
basically assemble a <a href="http://ubt4s.org/">Universal Bug Tracker For Society (UBT4S)</a>.  <br/>
<br/>
This
would make it easier for me to sleep at night, knowing that the ideas
are captured. It would also allow me to be much more effective by
being able to more easily focus on exactly one bug at a time, and to
record any progress or thoughts relating to others. But again, I
suspect that the impact will actually be much greater from other
people entering the feature requests and bugs of society that they
think of or notice.<br/>
<br/>
The UBT4S also makes it easy for people who are not plagued by new ideas to join in the
effort, but who want to make a positive impact in the world: They
can simply go to the UBT4S, browse the bugs and feature requests,
maybe vote some up or down, add some notes, or, hopefully, assign one
to themselves and do some work on it.<br/>
<br/>
The underlying philosophy that makes the UBT4S make sense is the
realisation that if you are a social entrepreneur having someone else
cut your lunch by doing something you had planned to gives you a free
lunch in the form of releasing you to pursue other innovations. I'll write a blog post on this competition-is-a-gift aspect of social entrepreneurship soon.<br/>
<br/>
But right now, this is what I am going to do: I am going to register ubt4s.org
and setup a bug tracker there, that will be open to anyone to
register and contribute to. I will pre-load it with some bugs and
feature requests for society that I have in mind (including those
above). 
<br/>
<br/>
I will also lay out some rules for the UBT4S.  These rules will be
subject to the UBT4S itself, and so if you don't like them, then
please submit an issue that describes the problem <i>and</i> how they
can be improved.<br/>
<br/>
This is a very important point, because I don't want
the UBT4S to be a whinge board about all that is wrong with society.
I also don't want it to be a place where people say that country X
needs party Y in power.  The political domain is already quite
saturated, and not a fun place to operate for the most part.  <br/>
<br/>
The
UBT4S, on the other hand, is a place where tools and
personal-action is the approach.  Think of it as a meta-project
around various various existing and yet-to-exist open-software, open-hardware and life-hacking
projects that has “universal peace and happiness” as its' goal (which I have purposely not defined),
and then identifies tools that can be used to edge closer to that.<br/>
<br/>
I
immediately recognise that this approach has limitations, but then so
does Newtonian Physics, but that doesn't stop us using
non-relativistic rulers to measure how tall our kids are, and nor
should the fact that the UBT4S has natural limitations prevent us
from achieving as much universal peace and happiness as we can using
that tool.<br/>
<br/>
So now I throw the challenge out to you:  visit <a href="http://ubt4s.org/">UBT4S.org</a>, add
bugs, issues and feature requests.  Comment on existing issues, and maybe start Wiki pages to begin marshalling resources for them. If you are part of a project that
is providing a solution (or part of a solution) to an issue, then
make a note of that in the tracker.  That way people who want to help
in that particular area can find the right projects to join, donate
to or otherwise help.<br/>
<br/>

I look forward to seeing you at the UBT4S.<br/>
<br/>
(Also if anyone has a better idea than using Google Code, I'm all ears.  Add it as an issue to the UBT4S, and we can work on fixing it.)<br/>
<div></div>
</div>