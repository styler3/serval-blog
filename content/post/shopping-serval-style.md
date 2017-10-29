+++
date = "2011-12-19"
title = "Shopping Serval Style"
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-2730130348211082889" itemprop="description articleBody">
We are currently preparing to provide the latest Serval mesh telephony technology for use in a disaster response training exercise with a major relief agency in late February 2012 -- about two months from now.  In that time we need to not only get our prototype Field Communications Unit (FCU) kit together, but also finish some software development that is key for making the technology useful for the relief agency.  You can watch a demo of one of the features we are working on in the video below, where I send a photo from one phone to another, without infrastructure.  This is the same technology we have used to <a href="http://servalpaul.blogspot.com/2011/11/demonstrating-serval-rhizome-store-and.html">send an SMS more than 10,000km without infrastructure</a>.<br/>
<br/>

<iframe allowfullscreen="allowFullScreen" frameborder="0" mozallowfullscreen="mozallowfullscreen" src="https://www.youtube.com/embed/r_LdiGE4uME?feature=player_embedded" webkitallowfullscreen="webkitallowfullscreen"></iframe>
<br/>
<br/>
On the hardware side, we have ordered 50 Huawei IDEOS X1 phones for AUD$71.10 each -- pretty cheap for a fully featured Android smart phone, complete with digital compass, GPS, accelerometers, a capacitive screen and enough CPU and RAM to meet our needs. These phones are network locked, but that doesn't worry us as we won't ever be putting a SIM card in them, because they will be used solely as mesh communications devices. <br/>
<br/>
It turns out that buying 50 phones at a time is an interesting exercise.  People want to know that you are not planning to resell them or export them.  Some shops will even try to limit you to buying five or less at a time.  Those tactics are legal in some places, but not here in sunny South Australia, where we have an excellent <a href="http://www.legislation.sa.gov.au/LZ/C/A/FAIR%20TRADING%20ACT%201987.aspx">Fair Trading Act</a> that correctly classifies such terms of trade as discriminatory, or in some cases as tantamount to <a href="http://en.wikipedia.org/wiki/Bait-and-switch">bait-and-switch</a>.<br/>
<br/>
In fact, until quite recently the South Australian consumer protection and gambling laws were so strong that cereal-packet competitions could not require a South Australian resident to purchase a product to participate in a trade promotion lottery, because it would be considered gambling, i.e., pay for chance to win.  So when I was growing up it was quite common to see terms and conditions looking quite normal, and then have sections specially for South Australians, that would often say something along the lines of:<br/>
<blockquote class="tr_bq">
"10. To enter, cut the bar code from a packet of XYZ and include it in your entry as proof-of-purchase.  Residents of South Australia are permitted to submit a hand drawn facsimile of the proof-of-purchase.</blockquote>
<blockquote class="tr_bq">
...</blockquote>
<blockquote class="tr_bq">
17. Only one entry per household per day.  Residents of South Australia may enter more than once per day."</blockquote>
<br/>
There were certainly occasions in my childhood when we would go to the effort of getting the coloured pencils out to draw a barcode by hand to get the chance to win a prize.  I think we sometimes did it just because we could.  Sadly, with the introduction of poker machines (Australia has fully 21% of the worlds poker or slot machines --- a statistic that is disturbing given that Australia has only about 1% of the developed-world population) and the general liberalisation of gambling in South Australia the situation has changed, and I believe we have lost our little parochialism.<br/>
<br/>
Anyway, I digress.<br/>
<br/>
After the difficulties I encountered initially in sourcing 50 mobile phones, I eventually went to our local post office to see if they would order me 50, since they had the model I wanted in their catalog.  Not only were they willing to order them (I promised to pay up-front, since it was a large purchase), they also kindly sliced 10% off the price.  So I now have a box of 44 phones in my lounge room, with the remaining 6 on back order:<br/>
<br/>

<a href="http://4.bp.blogspot.com/-Wi_N1ODorKc/Tu-lea4NzVI/AAAAAAAAAJI/Xy2J68pH8xA/s1600/19122011341.jpg"><img src="http://4.bp.blogspot.com/-Wi_N1ODorKc/Tu-lea4NzVI/AAAAAAAAAJI/Xy2J68pH8xA/s400/19122011341.jpg"/></a>
<br/>
<br/>
<br/>
At this price, the phones don't come with SD cards, which we do need for the Serval Rhizome software to do anything useful, as store-and-forward requires somewhere to store!  So I hunted around, and after some luke-warm experiences with suppliers either being unwilling to give me a decent price for what is clearly a wholesale quantity, or failing to stock enough, I tried OfficeWorks.  They had enough in stock, but were charging $16 for 4GB cards, which I had quotes from other local stores for $7.  So I loaded my basket with 50 memory cards, and proceeded to try their price-matching policy:<br/>
<br/>

<a href="http://4.bp.blogspot.com/-DE9caYqgZvs/Tu-lb__AjOI/AAAAAAAAAJA/wuYrbz5YbMI/s1600/18122011340.jpg"><img src="http://4.bp.blogspot.com/-DE9caYqgZvs/Tu-lb__AjOI/AAAAAAAAAJA/wuYrbz5YbMI/s400/18122011340.jpg"/></a>
<br/>
However, the large price difference and quantity did trigger concern from their store manager.  He was very friendly and amiable, but did point out that to get the price matched, I had to find a local supplier with the quantity I wanted actually in stock.  But that wasn't easy to arrange, as most of the cheaper suppliers only had a few on hand.  There is of course a silliness in their rule, as I could have bought them in small batches such that each batch was small enough that the cheaper shop held sufficient stock.  But in the end I did manage to find a cheap supplier on eBay who had plenty in stock at $5.80 a piece for SANDisk 4GB class 4 microSD memory cards.  Now we just have to see if they will arrive.<br/>
<br/>
So that covered the phones and memory cards.  The next challenge was to come up with a way to easily charge 50 phones.  Not only did it need to work in my home, but it also had to have the potential to work in a real disaster zone, and one which might not be in Australia.  Having enough power boards to plug 50 little USB charger bricks was not an attractive option, especially since I need to fit all of this into my 23kg luggage limit when I fly, and 50 phones alone are not that light.<br/>
<br/>
What I have decided to do is to chop up a pile of USB leads and wire them up to some automotive 5v accessory power supplies that are commonly used to power portable DVD players and the like.  Apart from being the cheapest 5v high-current power supplies I could find (AUD$40 for 5A), they have the benefit of running on 12v, or in the case of some models, on 12v-24v, so that they can even work in a truck.  This means that in-vehicle mass-charging is possible when the power grid is off.  It also means that they can all be charged using a single cheap 13.8v power supply, which are also quite cheap; you could even use an old computer power-supply.  You can see my prototype here:<br/>
<br/>

<a href="http://2.bp.blogspot.com/-t3SoThn4ODk/Tu-linc429I/AAAAAAAAAJQ/puHdKvbDyJ8/s1600/19122011342.jpg"><img src="http://2.bp.blogspot.com/-t3SoThn4ODk/Tu-linc429I/AAAAAAAAAJQ/puHdKvbDyJ8/s400/19122011342.jpg"/></a>
<br/>
So now I just need to get back to writing the software that needs to go on these phones ...
<div></div>
</div>