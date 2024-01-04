---
layout: post
title: LLM-Supported Development
comments: true
categories:
- dxw
- software
- ai
republished:
  attribution:
    copyrightHolder:
      name: dxw
      url: https://www.dxw.com
---

{:.danger}
DISCLAIMER: AI is the latest thing in the hype cycle, specifically LLMs. I don't buy into the hype, but I did work in AI research 20 years ago, and the recent progress is properly incredible compared to where we were back then. I'm not an AGI hype man, but also I definitely think this is a lot more interesting and potentially useful than "fancy autocomplete" as some have said. OK, on with the actual post...

When [ChatGPT](https://chat.openai.com) first launched, almost a year ago, it didn't take long for people to realise that it could write code. My immediate reaction to that was "lol, call me when it can open PRs on my projects to fill in all the tests I didn't get round to writing".

Fast forward a few months (and the last few months in AI/LLMs have been _wild_), and it seems that I wasn't the only person who thought that. Enter [Sweep](https://sweep.dev) (ignore the slightly-offensive tagline that it's an "AI-powered junior developer", let's call it an "LLM-powered PR generator"). I've tried it a couple of times on my own side-project code (more on that later), and I'm definitely intrigued.

It works in a way that's tightly integrated into the GitHub workflow, so you start out by opening an issue asking it to make a particular change. For instance: [Sweep: add unit tests for application_helper.rb](https://github.com/manyfold3d/manyfold/issues/1651). There's a bunch of code in that file that I wrote in a hurry, and because this is a hobby project, I didn't fully TDD it. So, can Sweep backfill the gaps for me?

I tried this first in the summer, and frankly Sweep fell flat on its face. It produced invalid code that didn't even parse, let alone pass any tests. So, I forgot about it for a while. But, the other day, I gave it another shot, and yeah, it's got a _lot_ better.

Sweep goes away and starts adding comments to the ticket about what it's doing. It's very very open about how it's working, which is unusual for AI tools; you really can see how it's breaking down the problem and what it's currently up to. First, it reads the entire codebase and interprets the request with that in mind - then it comes up with a plan of changes to make, before it finally goes to make them.

![Sweep reading my code](/images/posts/2023-11-30-llm-supported-development/searching.png)

![Sweep planning out what it's going to write](/images/posts/2023-11-30-llm-supported-development/coding.png)

Once it's done that, it [opens a pull request](https://github.com/Floppy/van_dam/pull/1653) with its changes, just as a human would. The tests and checks run, and if something fails, Sweep automatically reads the errors, feeding it back into the changes it made. You can then do a human pass over the PR (as you would with any code) and provide feedback just as you would for a human colleague.

![A detailed PR description , written by Sweep](/images/posts/2023-11-30-llm-supported-development/pr.png)

So how does it do? In the case linked above, it wrote a new test file, added a load of happy-path tests, which (a) made sense, and (b) passed! It made one mistake, which brought up a failing test, and honestly it was a pretty reasonable error. I can imagine a junior dev calling over their colleague to say "why doesn't this pass?". It took me a minute or two to realise what was wrong, then I left a comment for Sweep. Sure enough, a few minutes later it fixed it exactly as I intended.

Here's where things go off the rails a bit though. It also had some code style errors, and when I asked it to use double quotes for strings in the whole file to fix a lint problem, it completely misunderstood and went off on a rampage writing more tests (which, to be fair, were useful, just not what I asked for). Then when I asked it to undo that commit and go back to the previous version, it just started spewing out syntactically broken code. So, it's not perfect yet.

BUT, those first two commits and the tests it wrote were great. So, I manually rolled the branch back and merged it in. My app is now partly written by a chatbot; strange days.

Sweep also hits a lot of other buttons that make me prefer it over things like Copilot. It's open source, you can self-host it, and it's open about how it's working. There's no black box here, apart from the actual ChatGPT LLM itself.

So, am I afraid AI is coming for my job? Well, not really. I think we might see it being used more and more though, in certain places. I don't want AI to help me write algorithms or structure my architecture - that's the interesting and fun bit. But, if something can run through my code finding errors, filling in gaps, take away the less-fun work that tends to get pushed aside, but is really important? Yeah, I'm interested, and I'll keep exploring the possibilities.
