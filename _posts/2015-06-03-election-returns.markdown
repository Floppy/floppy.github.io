---
layout: post
title: Election Returns
date: 2015-06-03 08:30
comments: true
categories: election
---

I've put it off for too long, and so for the last couple of evenings I've been completing the election spending and donation returns for the Horsham campaign. I was warned that this was an awkward process, but it's been basically fine (though we've not had to do any of the complex stuff).

The Electoral Commission, as always, provide a whole load of documentation and help with filling in the data, which you can [download from their website](http://www.electoralcommission.org.uk/i-am-a/candidate-or-agent/uk-parliamentary-general-election-great-britain) (see the resources in Part 3).

The return has to be in within 35 days of the election, so we have around another 10 days to finish it.

## Short and long

There are two returns to fill in; one for the long campaign (19th December to 29th March) and one for the short campaign (30th March to 7th May). You need to account for spending and donations during these periods separately.

## Worksheets

The commission provide two versions of the returns; PDF and Excel. I decided to fill it all out using Excel (well, LibreOffice), which would have been much quicker if they'd actually included formulae in the template sheets. As it was, I spent half the time putting in all the SUMs, cross-references, and so on that meant that it all added up correctly. 

And of course, I had to do it twice, once for long and once for short, because there are two different sheets, even though they are basically identical except for the title.

Suggestions for the EC:

 * Make one sheet and have an option for short and long campaign. Less for you to maintain.
 * Include the formulae so that using the sheet is harder to get wrong.
 * Make a nice simple webapp for the form instead. Probably not high up the list, but it's a really easy problem; you could have one in a couple of weeks of developer work.
 
## The data

We've been [keeping our books openly](https://somethingnewuk.github.io/finances/) all along, so we had everything we needed all ready to go. We have even been assigning things to the return spending categories as we go so as to be ready to fill this in.

It's hosted on github in CSV files, and uses Jekyll to render the HTML views of each file. I started working on a Jekyll view to generate the actual return content as well, though there was so little to fill in that in the end I did it manually.  I'd like to come back to that though, and make it so that our open data finances can automatically create the return numbers, not least so we can publish them ourselves.

I won't publish the filled-in return we send in, as it includes donor addresses, which I would consider personal information. We already publish names, but I don't think I should publish addresses for large donors, not without more thought anyway. Also, the commission will report the summary anyway, and you can see [all the detail for yourself already](https://somethingnewuk.github.io/finances/horsham/donations.html).

## Points of Interest

There are a few little points I learned along the way that are worth nothing down:

### Verifying donors

You have to verify that all donors *over* £50 (not £50 and over) are registered voters. This, for me, involved calling up their local council's election office and just asking. Given the name and address, they will just tell you if that's right.

I suppose that's fine, though it seemed a bit... easy. I didn't have to prove anything about who I was, do anything in writing, or whatever. I guess it would be hard to abuse though; someone would notice if you were attempting to find someone by calling up 50 times with different addresses. Still, seems... leaky.

### Overseas donors

Our largest donor (thanks Phil!) is overseas, though is still a registered voter here, so can legally donate. The form has a space for the donor's address, which I suppose means they can double check the donors with the councils. However, his is abroad, so wouldn't identify the council. In the end, I just wrote in the space after his address "Overseas voter, registered with Brighton council". Hopefully that will work.

### Small donations

The way the form is laid out, you only have to declare details of large donations over £50, but there is a box for "total donations" as well. If you're filling it in with a formula, then you need somewhere to add in the small donation total, which isn't there otherwise. I just added another row in the declared donations tab marked `<=£50`, with the total. Obviously all those are shown in our open finances as well, split out properly. 

Sidenote: I want to see UKIP do that, and prove just how much of their finance comes from small donors, as they love to say, and [how much comes from the owner of the Daily Express](http://www.bbc.co.uk/news/election-2015-32340976).

### Crowdfunding

As we were crowdfunding during both the long and short campaigns, I've split the funds raised across the two returns based on when people pledged, rather than when the money was taken (which would all be in the short campaign). That's based on the fact that you report spending based on when an invoiced spend was *used*, instead of just the date on the invoice. Seems like the right thing to do.

### Fees

I had to call up the commission to ask about crowdfunding fees. Around £95 of the £1620 we raised ended up going to [Crowdfunder.co.uk](http://crowdfunder.co.uk) (quite rightly), but it was unclear how this should be counted, and where.

The Electoral Commission are still getting to grips with crowdfunding, even though a *huge* number of candidates did it this time. They had to go off and check the answer to the question, and still didn't actually completely answer it.

The answer (so far) is that the donations should be listed *as donated*, not with the fee removed. So, if you gave 100 quid to Crowdfunder for the campaign, it's declared as £100, not £95. If you paid with PayPal, you also paid their small fee on top, though it was itemised separately. As it wasn't reported *to you* as being part of your donation, I'm not considering it part of the donation.

The fee will be listed somewhere, though they've yet to get back to me on that. I'm guessing (and will update here when I know) that it will go in as an administration expense under section F.

I'm surprised the Commission are still so unprepared for this; wasn't it obvious that it would be a thing this time? Why isn't it explicitly mentioned in the guidance?

### Deposit

One last note. You don't declare the deposit as spending, and in fact you don't have to declare money raised to cover the deposit as a campaign donation. We didn't split it out that way, so I'm just declaring the lot. That's why it might look like we raised more than we spent; I assure you that wasn't the case!

## Party spending

We also have to declare any spending done by the party as a whole. This will include things like [NationBuilder](http://nationbuilder.com) and  [Soundcloud](http://soundcloud.com) fees, which were non-constituency specific. We have 3 months to fill in that return though, so I'll come back to that another time.

## Summary

All in all, pretty simple, though a little time-consuming. We didn't have to deal with unpaid invoices, rejected donations, or anything complex, so I guess that made it easier.

So, this has been about the form-filling really (always a good topic for a blog post). I'll follow up soon with a post that actually goes into the spending data, and talk about what we spent, why, and whether it was worth it!