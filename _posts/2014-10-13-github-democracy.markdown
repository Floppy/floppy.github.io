---
layout: post
title: "GitHub Democracy"
date: 2014-10-13 06:45
comments: true
categories:
- politics
- github
- election
---
A year and a quarter ago, in a fit of political anger,
I proposed that a bunch of us should start collaborating
on the public policies we'd *like* to see, rather than just complaining on Twitter.

As I'm a software developer, I suggested that we could use GitHub as a platform,
and a few of us started doing exactly that. 15 months later, the [OpenPolitics Manifesto](http://openpolitics.org.uk)
contains nearly 8000 words of agreed policy ideas, has inspired me to [stand for
election](http://www.wscountytimes.co.uk/news/local/father-of-two-launches-bid-to-be-horsham-s-next-mp-1-6168976), and has spawned a [political party](http://somethingnew.org.uk) which has adopted the manifesto (though
it remains an independent project). I'm quite proud of all of that.

Last night, someone new to the project asked me how it worked, and to clarify who
can take part, and I realised I've never really written it up in a blog form. We have
the [contributing guide](http://openpolitics.org.uk/contributing.html), but that's probably fairly well buried. So, in this post I'm
going to explain the democratic process we've arrived at over the last 15 months.

## Who can make changes?

The simple answer here is "anyone", though the reality is slightly more complex.

Anyone with a GitHub account can hit the edit button and change the text to match what
they want. Thanks to GitHub's great workflow tools, this automatically creates a fork
of the project (a copy, basically) and submits a pull request (PR), which you can 
think of as a "request to adopt the proposed change". The user interface here can 
be confusing to new users though, and that's something we want to improve.

Anyway, once your change is made, it gets added to the [pull request queue](https://github.com/openpolitics/manifesto/pulls), ready
for inspection.

## Who decides what gets accepted?

We're modeled on an open-source type workflow, not a straight-majority universal-suffrage
democratic model. That means that while anyone can submit a change, *not* everyone gets
to vote straight away.

We're a little different from other open policymaking tools, in that we're not actually
trying to express a solution that satisfies the majority. We're trying, with help from
everybody, to build a cohesive platform that will hopefully appeal to some voters. This
is a party-style manifesto, not a universally-accepted list of things we should do.

So, because of that, you can only vote on a change if you've already made a contribution.
That means that the project should be able to maintain the direction and general outlook
that it started with, without being twisted around.

However, as soon as your change is in, you get to vote, so nobody maintains a list of
"approved" contributors. If you add something good enough to get in, you get control.

This is really similar to the process in a bit of open source software, where existing maintainers decide what gets added in order to keep the project moving the right way.

![Service Guarantees Citizenship](https://memecrunch.com/meme/L5EI/service-guarantees-citizenship/image.png)

## What about takeovers?

People often ask what we do about hostile takeovers. Say a number of people make helpful
and acceptable additions (thanks!), but then gang together and vote to bring back
capital punishment.

Again, the open source model helps us here. We can't stop that happening, not at all.
However, it would gain the attacker pretty much nothing, as anyone in the world is
entitled to take the project and fork it into a parallel effort at any time.

If something happened that a caused a large split in the group, I have no doubt the project
would fork into two. That's not a bad thing - the two forks can still share the ideas they
agree on, while maintaining their own differences.

I'm not sure how this will work in practice. I guess we'll cross that bridge when we come to it, but I think we have an escape route prepared if we need it.

## How do changes get voted on?

I initially expected that we'd go with a straight majority vote of contributors, but that's
not what we're doing right now. The long tail of participation is as true in this project
as in any online space, so we have a few very active contributors, some less-regular ones, 
and a long tail of people who've only contributed once.

Because of this, it would be easy for the regular contributors to overrule the long 
tail, but that would lead to complete disengagement and a "why should I contribute"
reaction. After all, if the cabal control all the votes, there's no power.

So, we use a sort of [blackballing](https://en.wikipedia.org/wiki/Blackballing) system instead. A change must get "yes" votes from 10%
of the contributors in order to be passed. However, anyone can block a change,
which means we can't merge it until that block is removed. That means that anyone in the
long tail can make their objections known over the view of the regular contributors, and 
force improvements and further discussion.

So far, this has worked OK. We have a few changes that have been blocked for a long time,
and how to work through those blocks is something we're still learning, but in general it's
working OK.

We try to make sure that blocks are substantive; that is, a simple "NO" isn't allowed. 
For a block to be considered, it must come with reasons, requests for more evidence, or some
other form of constructive feedback. Generally this does seem to happen.

We also keep each vote open for 14 days to give the long tail time to respond.

## Who counts the votes?

Robots! 

Votes are currently expressed in GitHub comments with +1 / -1 statements (using emoticons), and we have a [script that watches those changes](http://votebot.openpolitics.org.uk) and counts them up. There are a number of rules enforced by the robot; for instance, yes votes are cleared by a change to the PR (so you can't amend at the last minute).

Using the GitHub API, we check all this stuff, and then we set the build status appropriately for the change. This means that the GitHub merge button will have a warning on it until the time period has expired, and until it has enough votes and no blocks.

Nothing fundamentally stops earlier merging, and that does happen sometimes for spelling corrections, etc. Only a [couple of admins](https://github.com/orgs/openpolitics/teams/owners) have merge powers, so there is a potential corruption point there; perhaps the robot should do the merging as well, but it's nice to have a human in the final check.

The robot also helps with making the information more accessible. It sends tweets from
[@OpenPoliticsUK](https://twitter.com/openpoliticsuk) for new changes, and notifies our  [#openpolitics IRC channel](irc://irc.freenode.net#openpolitics). It also
has a few web pages that list vote status in a simple way, so we can see who's taking
part, who's voted which way. There is also a [user page](http://votebot.openpolitics.org.uk/users/Floppy) for every contributor that shows
what they have and haven't voted on.

Of course, the robot is [open source](https://github.com/openpolitics/votebot), so you can check that the rules match what's agreed.

## What next?

Usability is a big concern. Currently we use the GitHub editor; I'd rather use [prose.io](http://prose.io),
but it has a massive [bug](https://github.com/prose/prose/issues/643) in it that means that new users don't get invited to sign in to
GitHub first, and changes get lost. If you can fix that, I'll pay you a [$25 bounty](https://www.bountysource.com/issues/1839687-unauthenticated-users-can-t-submit-pull-requests).

However, I'm starting to think we need a completely custom editor that explains every step 
along the way, and hides the GitHubness right down away from the user. Ideally the 
contributor shouldn't know they're using GitHub (unless they want to). The version control 
base layer is important for change visibility, accountability, forking, and so on, but
expecting non-developers to be OK with it from the outset is asking a bit much.

There are other options for the voting as well; I'd like to get something like [Loomio](http://loomio.org/) or 
[DemocracyOS](http://democracyos.org/) integrated into the voting system, so that people don't need to use the pull
request UI to discuss and vote. Again, maybe this should be a custom thing that presents 
the information exactly the way we want.

I'd also like to experiment with wider (but less official) feedback using something like [IAgree](http://iagr.ee). It would be great to have a user agreement level on every point in the manifesto.

If you're working on any of those tools, I'm more than happy to offer input into your API design process!

## Will this scale?

The simple answer here is "I don't know". I really don't. This is an evolved process 
that works for us right now. It will certainly change in future to cope with changing
demand, and I can't anticipate exactly how that will happen.

For now, we're building political policy in a way that anyone can get involved with, and
for me that's revolutionary. How that revolution copes when it hits the mainstream is
a scary adventure I'm looking forward to, but as often stated in software, scaling problems
are "good problems to have".

If you want to get involved, visit the [OpenPolitics Manifesto](http://openpolitics.org.uk) and make a change. If you
want to vote for someone who is using it, or want to stand on the principles yourself,
I humbly suggest you check out our party, [Something New](http://somethingnew.org.uk).