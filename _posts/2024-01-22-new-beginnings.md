---
layout: post
title: New Beginnings
comments: true
categories:
- manyfold
- projects
---
Last Thursday was my last day at [dxw](https://dxw.com). I loved it there, it's full of Good People and Good Work, and being a trustee of the Employee Ownership Trust for the last couple of years has been a true honour. But, something came along I couldn't say no to.

Over the last couple of years, I've been building a self-hosted web app called [Manyfold](https://github.com/manyfold3d/manyfold) (previously named VanDAM, because a weak pun is fine to start with). I built it to scratch an itch I had with managing a large library of 3d model files for 3d printing, but over the years, a few other people have started using it and finding it useful.

In the summer, I put in a wild application for grant funding to [NLNet Foundation's](https://nlnet.nl/) [NGI Zero Entrust](https://nlnet.nl/NGI0/) fund, which supports work on open standards, open data, and open source software for the good of the Internet as a whole. To my very great surprise, [they agreed](https://nlnet.nl/project/Personal-3D-archive/), so starting today I get to spend a few months working on Manyfold and the software it's built on, to make something useful for even more people.

The work is in 6 main [milestones](https://github.com/manyfold3d/manyfold/milestones):

1. Core feature enhancements; adding a bunch of things like model format conversion, licence information, internationalisation and translation, and more.
1. Improved deployment; making the app easier to set up and run in different environments, from personal NASes (NASii?) to full-on cloud deployments.
1. Security & compliance; making sure the app is secure, accessible, and [sustainable](https://w3c.github.io/sustyweb/).
1. Documentation; user guides, admin manuals, contributor guides, all that good stuff.
1. 3D model compression; 3d models can be large and lots of formats are inefficient. I'm intending to create a new format based on the [progressive meshes](https://hhoppe.com/proj/pm/) algorithm that will enable models to be streamed efficiently. This is particularly cool, as this was part of the background I learned about doing my PhD; about time that was useful.
1. ActivityPub federation; make the site multiuser, build feeds and social features, and then make it federate using [ActivityPub](https://activitypub.rocks) (like [Mastodon](https://joinmastodon.org) and others). If I get this right, then we can create a "decentralised Thingiverse", where it will no longer matter which site your content is on.

Those last two are the coolest, and I'm particularly excited about getting started on those. I've got about 6 months of funding to do this, which is frankly incredible, though I've got no idea what happens after that. I'll also be available for small contracts to build up a diversity of income, so let me know if you have anything I can help with!

If you're interested in the project, you can follow progress in the Fediverse at [manyfold@3dp.chat](https://3dp.chat/@manyfold), and of course if you want to get involved or run your own, check out [the GitHub repository](https://github.com/manyfold3d/manyfold) (better documentation coming soon).
