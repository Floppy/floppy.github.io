---
title: Open Workflows for Open Teams (and closed ones too)
republished:
  attribution:
    copyrightHolder:
      name: Open Data Institute
      url: https://theodi.org
    license:
      name: CC BY-SA 2.0 UK
      url: https://creativecommons.org/licenses/by-sa/2.0/uk/deed.en_GB
categories:
  - odi
  - open
  - agile
---
It’s been six weeks since I joined the ODI, and so far, the most interesting thing about working here has been the approach we take to software development. [As others have mentioned](http://theodi.org/blog/better-living-through-openness), we are trying to be radically open in how we work, but I thought I’d go into a little more detail on our actual workflow. We’re only two sprints in, so we’re still iterating this but it’s working nicely so far.

When we started, we spent a while thinking about how we wanted to work, with a few aims in mind:

* we are a collective
* we are transparent
* processes must be low-impact
* use the simplest tools we can

We are, of course, working in an agile fashion, following some elements of [scrum](https://en.wikipedia.org/wiki/Scrum_(development)), but as is proper for an agile process, we are also adapting it to our needs. Scrum too often turns into agile-for-people-who-like-waterfall, which defeats the whole object.

## Collective ownership

Tasks are not assigned up front, they are chosen by the team members. We also collectively agree on what we can achieve during a 2-week sprint. The code itself is also collectively owned; *“Oh, X wrote that, but I don’t really know how it works”* is a **big** danger sign. Instituting a rule of *“you wrote that bit last sprint, so you don’t touch it this time around”* is a Very Good Thing, even if it slows you down sometimes; the long-term benefits will outweigh the temporary cost. We’ve already seen technical debt accumulate in this short time, and while making sure we deal with it quickly by spreading knowledge around the team takes time (and cost us a sprint goal or two), we’re much better off dealing with it immediately.

## Branch/Review/Merge

We love [Git](http://git-scm.com/), and we love the tools that [Github](https://github.com/) have built around it.

We all sat down and watched Zach Holman’s talk [“How Github use Github to build Github”](http://zachholman.com/talk/how-github-uses-github-to-build-github/), and have taken a lot of inspiration from the way they do things. Once you get into your head that branching has zero cost, workflows become so smooth it’s ridiculous. - Branch from master to “feature-{issue_number}-{description}” - Work for a short while (not necessarily until you’re finished) - Open a pull request back to master for discussion - Invite ongoing review on the PR - Get someone else to merge back to master when complete (or earlier if safe)

We’ve already had really positive engagement (both internally and externally) directly in [pull request](https://github.com/theodi/open-orgn-services/pulls) comments, which is just fantastic. Not having to leave your flow to communicate with clients makes a much more productive programmer.

## Issue tracking

We’re also using Github for [issue tracking](https://github.com/theodi/open-orgn-services/issues) and other documentation. While the issue tracking is basic, it does 90% of what you think you need (and you don’t actually need the other 10%). Once you have two separate fields for different types of priorities, or add time-tracking on individual issues, you’re just introducing cruft that clutters the place up and adds admin overhead (nobody ever looks at that stuff anyway).

It took me a while to work out how to model dependencies, but simply adding a link to the master ticket from the sub-ticket (“this is needed for #42”) gives a nice open/closed view in the master ticket, which works well enough. This even works across repositories, meaning that you can use a single issue tracker for a project even if it’s split into multiple places.

![Github issue tracker](https://bd7a65e2cb448908f934-86a50c88e47af9e1fb58ce0672b5a500.r32.cf3.rackcdn.com/uploads/assets/legacy/issues_0.png)

## Learning as we go

Obviously, none of this is fixed in stone and for me, that’s the single most important thing about agile development. We’re not always living up to what we want to do, and besides, what we said we’d do isn’t necessarily the best way. I find myself analysing our workflow and my own performance a **lot**, and end up really looking forward to the retrospectives we have as part of planning for the next sprint. The joy of being at the ODI is that we have a team who really understand and buy into this way of doing things. We work openly *internally* as well as externally, trying to communicate continuously with each other and with our clients. It gives us an instant shared culture, and shared victories (along with shared failures), and those are the things that will bind an excellent team together…

(even if they do take a little more time to do things *right* sometimes)
