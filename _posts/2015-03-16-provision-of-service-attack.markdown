---
layout: post
title: Provision of Service Attack
date: 2015-03-16 06:48
comments: true
categories: election
---

Running for election really does give you a different view on some things. 

Until last year, I was pretty opposed to clicktivism; you know, the [38 Degrees](http://38degrees.org.uk) style of campaigning
where hundreds of people will send an identical email to their candidates or MPs to
tell them where they stand on something.

I'd softened a bit after I chaired a [Cleanweb London event on online activism](https://www.youtube.com/watch?v=nUJGveEH6Po), but generally
I subscribed to the more traditional view that fewer well-crafted letters were a better 
way of doing it. 

## Denial of service

I've heard stories of other candidates who were unable to get anything done other than
just emailing back to bulk messages, replying to each email individually!

Now, that may still be the case for most people in politics, but for
me it's utterly changed over the last few weeks.

I *love* 38 Degrees emails and the like. I love days where
a campaign obviously kicks in and I get over 100 emails about [TTIP](http://www.somethingnew.org.uk/ttip_putting_corporations_first), or something
like that.

Many candidates will see this as spam, but not me. Why not? Because I know how to
handle it. Because I can use it
for what it is.

## Provision of service

We're using [NationBuilder](http://nationbuilder.com) to run the campaign; it handles the website (though I hate CMSes and
would be happier with Jekyll, but whatever), but most importantly it handles our contact
database. All the emails we get to official addresses come into the system and get
flagged for followup.

On a 38 Degrees day (as I've come to call them), this followup list gets pretty big
and the load is unmanageable for a human. 

But all the emails are useful. They give me an idea of who cares about what, and 
more specifically, where they live and their email address. 

To build my database of potential voters, this is *amazing*. Suddenly I have 100 more people
who I know care about certain things, whom I can email about events, updates, blog posts,
etc. People who want to hear back.

## Deploy the robots

So I've created a [script that helps manage this](https://github.com/SomethingNewUK/nb-email-processor).
It's open source, so if you want to do the same, you can.

Here's what it does:

 * Looks at all the open followups in NationBuilder, and for each one:
 * Get the email text that need replying to
 * Work out who the email is to, and reassign it to the right
    person (for campaigns that aren't using the right addresses).
 * Look for certain [consistent text](https://github.com/SomethingNewUK/nb-email-processor/blob/master/tags.yml) in the email to identify the campaign,
    and apply a tag.
 * Find the address, and run it through [Open Addresses](http://openaddressesuk.org)' [Sorting Office](http://sorting-office.openaddressesuk.org)
    app (which I helped write at work) to turn it into structured data. Note we don't
    submit the address into Open Addresses, as even though the existence of an address isn't personal information,  it feels like it is, and I don't want to annoy anyone.
 * Set the address for the sender back into NationBuilder. This also does auto-assignment
    to wards, constituencies, etc.

This runs every hour using the [Heroku](http://heroku.com) scheduler.

There are a couple of gotchas. The [NationBuilder API](http://nationbuilder.com/api_documentation) is great, but one thing it can't
do is get followups and email content. That made it a fair bit harder, and I have to actually
drive the website (using Capybara and PhantomJS) and pretend to be a real human user in order
to read the emails. It works OK, but it's brittle and very slow.

Also, reliably extracting the address is hard and varies across campaigns. I'm hoping to improve
[Sorting Office](http://sorting-office.openaddressesuk.org) itself to do this job, 
so I can just drop the entire email into it and get back the address only.

## Back to humanity

So now, instead of a ton of emails, I have a load of tagged contacts in NationBuilder. It's then
easy to build a list of people who want to hear back on a particular subject.

At this point, I make sure I read the email properly, look at the links, and write a blog post in response.

I can then, every few hours, send a bulk email back to the senders with a quick answer, 
a link to detailed the blog post, details of our party and campaign, and links to things 
like upcoming events. The open and clickthrough rate is surprisingly good.

So, all in all, once this is up and running, handling a high-impact day of emails takes only a few clicks, and each
sender gets a well-thought-out response and ways to engage further.

I have to admit, as well, that I get a certain amount of pleasure from imagining the inbox of my opponents on days like these.

## Wishlist

If you're running these bulk email campaigns, here are a few requests:

 * Update your data regularly. [YourNextMP](http://yournextmp.com) is doing a sterling job of maintaining
   candidate lists, and contact details. Make sure you're up to date, and make sure
   your email gets to the right place.
 * Make sure the address is easily-parsed; well-separated from other text 
   in a predictable way, and not shoved together with phone numbers, names etc. You could
   integrate [Sorting Office](http://sorting-office.openaddressesuk.org) into your 
   own applications to help with this, if you want to be proper amazing.
 * Add some sort of unique campaign identifier that people *can't* change - it'll help
   me tag things. Also, maybe a suggested hashtag?
 * Make sure you include the originating campaign link. I get that you want it to look
   like it's only written by the constituent, but honestly, on that you're not fooling anybody. 
   Often I actually want to share it on as well!
 * If you *really* want to help people like me, then make all the important metadata
   machine-readable. I'm talking about a JSON attachment or something, containing 
   a structured address, name, other contact details and the unique campaign ID.
 
If you're NationBuilder, please let me fetch emails via the API. You don't really want me
scraping your site, after all, the overhead is huge!

And last of all, if you're a candidate, then you'd better accept it's time to tool up.
Your voters have new opportunities to engage, and you'd better be ready to handle them.
The future's not slowing down just because you're not ready.