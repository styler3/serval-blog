+++
date = "2016-06-01"
title = "Mesh Extenders for the Pacific"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-8168311626862827539" itemprop="description articleBody">
Recently we were named a winner in the <a href="http://pacifichumanitarianchallenge.org/">Pacific Humanitarian Challenge</a>, receiving a grant from the Australian Department of Foreign Affairs to undertake a pilot of the Serval Mesh in one or more Pacific nations.<br/>
<br/>
We're now starting to get underway in our planning for this, in particular, how we can make the Mesh Extender easily manufacturable in reasonable quantities (we need about 100 for the pilot), and as robust and reliable as possible, without making it too expensive.  Of course, we know that at these small quantities, the cost will still be much higher than we would like.<br/>
<br/>
We have begun talking with our good friends at RFDesign about making an all-in-one Mesh Extender PCB, including both RFD900X + Atheros 9k based embedded Linux computer.  I think we have some good ideas about how we can go about that within the budget constraints of this project.  In many ways, this is the most important part, because it simply isn't realistic to hand-build 100+ Mesh Extenders the way that we have been prototyping them so far.<br/>
<br/>
<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container"><tbody>
<tr><td><a href="https://upload.wikimedia.org/wikipedia/commons/4/40/Bi_material_molding_machine.jpg"><img src="https://upload.wikimedia.org/wikipedia/commons/4/40/Bi_material_molding_machine.jpg"/></a></td></tr>
<tr><td class="tr-caption">A picture of an injection moulding machine (<a href="https://commons.wikimedia.org/wiki/User:Cjp24">Cjp24</a> CC-BY-SA 3.0), because this post was too boring with just text.</td></tr>
</tbody></table>
<br/>
One of the really interesting ideas we are exploring is including a solar and battery controller in the unit, so that you can just plug in a solar panel, car battery or other supply to run the unit, in addition to the normal 5V USB supply.  You would then also be able to connect two LiFePO4 cells, that the unit would charge from the supply, and use to operate when there is no power supply available.  We have yet to work out what impact this will have on the cost, although at this stage, the RFD900 radio is by far the single most expensive component, so we are hopeful that we can make it fit.<br/>
<br/>
I have also been introduced to the world of injection moulding through a helpful colleague here in the department.  Together with a local injection moulding company, we think we have found a way to get full-custom polycarbonate injection-moulded cases designed and manufactured at a relatively affordable price.  We are currently aiming for IP65 or IP66 rating for the case, so that it can be safely used in dusty outback conditions, as well as in tropical maritime climates.<br/>
<br/>
However, injection moulding is not cheap, so "relatively affordable" is still code for "will stretch our budget to the very limit".  Our current estimate is that it will take at least AUD$30,000 for us to get the tools designed, built, and then squeeze out several hundred complete cases.  Given that it was previously looking like $50,000 to just get the tools made, and then only being able to do large production runs, this is a huge step forward. Also, with the injection moulding company being within easy riding distance, and being able to do very small production runs, and pick them up in beloved <a href="http://bakfiets-adelaide.blogspot.com.au/">my cargo bike</a>, this all spells good news for the Mesh Extender being able to be turned into a real, purchasable product, with some very nice characteristics and capabilities.<br/>
<br/>
There are some other hurdles to jump through before we would be able to offer it as a complete product, including regulatory certification from the FCC and our Australian equivalent, and ideally, also EC approval from Europe.  Given the current shenanigans with the FCC, TP-LINK and locking down router firmware to prevent undesired 3rd-party access, we are thinking very carefully about how we can avoid that whole problem, but still have common hardware between the totally incompatible US/Australia/New Zealand/Canada versus Europe radio bands that we need to use for the UHF radio.<br/>
<br/>
One approach that we are thinking about is having the power/data cable that feeds the Mesh Extender be wired differently for each regulatory domain.  That way, the firmware and everything can be completely common, and the radio firmware can simply probe the cable to work out which bands it should be operating on.  Given that owners of Mesh Extenders are likely in many cases to be internationally mobile, especially when trying to respond to disaster events, we think that this is a sensible approach.<br/>
<br/>
We would also likely have another cable wiring that would tell the unit to accept unsigned firmware, so that people who wish to replace the firmware and experiment can do so, but there would be no risk of someone accidentally flashing the unit with firmware that would make it operate outside of authorised bands.<br/>
<br/>
We understand that this whole area is a rather sensitive one for all of us in the open-source community, so we invite your feedback on whether what we are proposing in this regard, and whether there might be any better ways of doing it, without risking the FCC of EC folks refusing certification.<br/>
<br/>
Also, I'll be picking the brains of some other folks who have created open-source consumer products to try to find out about and avoid any likely hazards along the way.  If you have any wisdom or experience to offer here, it would also be very welcome.<br/>
<br/>
Paul.
<div></div>
</div>