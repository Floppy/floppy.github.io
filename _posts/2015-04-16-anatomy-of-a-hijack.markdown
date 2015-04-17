---
layout: post
title: Anatomy of a Hijack
date: 2015-04-16 17:00
comments: true
categories: 
---

This post is a brief diversion from election updates to recount the story of 
an attempted account hijacking and theft that happened to me on Monday, and what can be 
learned from it. This might be quite long, but you never know; might be 
interesting to someone.

## Unusual activity

So, the first thing I know is when I get a call from my bank, about possible unusual
account activity. These happen every now and again - you call back, confirm some 
transactions, and everything's fine.

So, I call up, and get put on hold for the fraud dept. Unfortunately I have a meeting
and have to hang up. An hour and a half later, I call back, and after some strangeness
with my account access PIN not seeming to work, we find one unidentified transaction. So,
my card is cancelled, and another will be in the post. This happens sometimes, I guess. End of story.

## Where's my SIM?

An hour after that, I get a text on my phone, thanking me for transferring to my
new SIM card, and that the old one will be disconnected. I immediately call my mobile
operator to see what's going on, but my phone dies a couple of minutes later, kicked
off the network.

Uh oh.

At this point I'm getting worried about Twitter hijacking, or somesuch. After all, we all
have two-factor authentication set up to send SMS codes to our phones these days, right?

So, I borrow a phone from a colleague, and call the operator. Once I get through, they confirm that
my number has been transferred to another SIM on my request. I tell them to kill it *immediately*, 
because that was NOT ME.

Once that's done, and we've added some new security questions, we look at how this happened. 
The log shows that the previous caller didn't know the account PIN, but confirmed 
ownership of the number by verifying the last direct debit amount taken from my bank account.

Oh, shit. They're in the bank account.

## Calling the bank back

Check the online banking - I can't get in.

So I call the bank and get immediately routed through to the fraud department and
go through an unusually large amount of security. They inform me that yes, something 
strange is happening, and did I by any chance recently make a large transfer out 
of my retirement savings?

Er, NO.

That's OK, they say, we didn't think so, and we didn't let it through. The accounts 
are safe, and everything has been locked down. The attacker isn't getting any further.

We set a special password that I make up on the spot so that nobody except me can access
the account until everything is reset with new information.

Finally, after a fraught hour on the phone, I can relax a bit. We're safe it seems.

## So, what happened?

It seems the fraudster and I were interleaving calls all day.

After my first call, coincidentally, they called the bank and pretended to be me. The
number was withheld, but they identified and passed security by giving my name, address, 
email, mobile number, card number and expiry.

As you might notice, all of that would be available to a store with whom I ordered something online.
And that got them all the way into my account, or at least far enough for the next part. So much
for security; we know that the security questions that protect the account online *weren't asked*.

Anyway, once they where in there, I guess they looked up the most recent direct debits; found my mobile operator, 
and got the last amount I paid them. They then reset the security PIN (hence my failure to get in on the 
second call) and called my mobile operator to swap the SIM cards for my number.

They got control of my mobile number pretty much straight away; how do criminals get this level of 
service? Normally moving a number is a total pain in the arse. 

Anyway, once they had that, they called the bank back (I was probably already on the phone to the operator at this
point), and with the extra identification of calling on my number, initiated the transfer. The 
bank were suspicious though;
they called my number back, and got them again, but weren't happy about the response. They locked everything 
down, and their ride was over.

## What went right?

So, the bank spotted the probe, and the hijack in time, so I didn't lose anything. That's good.

My mobile operator sent me a text with a reference number before they disconnected the phone. That's also good.

But...

## What went wrong?

This all comes down to companies being willing to work around their own security on the phone.
If you act the idiot and claim you don't have the security information, it doesn't seem to take a lot
to get in at least to the point where you can start to escalate.

The message I left the bank with after our various calls, was that this was *all their fault*. By
allowing callers to work around security, they are exposing my accounts to hijacking. None of this
was on me, as far as I can tell. Saying "don't use online shopping" these days is not an option, because
even if you shop offline, all that data is linked to, say, your Tesco clubcard. It's basically available
to anyone.

We all need to get more security conscious, and that doesn't just mean having passwords; it also means 
companies asking for them, and denying callers access even if it pisses off a customer or two.

## What did we learn?

### The weakest security link is always the humans

My digital security is good; unique strong passwords, held in a secure password store 
behind another strong password. It would be hard to compromise. However, this attacker
had only a bunch of data that you could hoover up from any online store order. Nothing
specifically about me - they didn't know who I was, where I went to school, my mothers' maiden
name, nothing. But it was enough to convince the bank that they were me. Social engineering is,
as always, the best way to break security.

I guess that the banks and mobile companies have to deal with a lot of people who forget their
security details all the time, so they have to subvert their own security in this way. 
That's... terrifying.

### Don't use real information in security questions

My security questions weren't asked, so weren't compromised, but now I've changed them, I've 
decided not to use real information in these ever again. It's far too easy to find my mother's 
maiden name, or where I was born. From now on, this stuff gets made up.

### Attacks are more complex than you think

This was a five-stage attack. First the obtaining of the merchant data with my details in.
Second, the probe, to see if the card was still active. Then the simple human exploit to get 
into the bank account in a read-only capacity, followed by the phone hijack and the 
final transfer attack.

While the later stages can seem more secure, a simple breach earlier on can leak more information
that allows the attacker to escalate their privileges.

Also, attackers *know* which attacks to use for particular services. It seems likely that the first
call to the bank was intentionally looking for more information to escalate privileges with. Once
they found my mobile operator, they knew that they would take the direct debit details as proof, so off they went.

### SMS two-factor security is not good enough

I'm going to switch to authenticator app security codes, I think, where I can. My mobile is too 
easy to hijack to be a sufficiently good part of the security chain. I was immediately worried that
the mobile hijack was a two-factor auth crack attempt. In the meantime, my authenticator app codes
remained secure on the physical device, not linked to the number.

### Be careful with incoming calls etc

A few times I had calls from the bank during this process, and I always asked them to prove to me who
they were first. They didn't know what to do. In the end I just had to make up my own security, and ask
names of people who had dealt with my case previously, as that's the only information I could think 
they could confirm. I think I might get a password put on my account for them to tell me in future. Not hard!

They also send special fraud centre phone numbers in emails and texts. I never called them, but instead 
always called the general customer service number and asked to be put through to the right area. How do
I know where the email is really from? Publish a PGP key on your site so I can verify the email, and I'll 
call the thing you want me to. Otherwise, no way.

The companies themselves are teaching people security antipatterns by doing this sort of shit.

## Will it get fixed?

I suspect that as long as this sort of fraud costs the banks less than the cost of better security, then they
won't fix it. Therefore, I really don't expect anything to change, unfortunately.

At least all I got was an afternoon of stress, and a few days without a mobile phone and debit card. Nothing was lost in the end, and a few valuable lessons were learned. That's a win, I guess?
