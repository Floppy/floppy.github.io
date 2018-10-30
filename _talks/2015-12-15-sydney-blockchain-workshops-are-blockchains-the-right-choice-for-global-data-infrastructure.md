---
title: Are Blockchains The Right Choice For Global Data Infrastructure?
host:
  url: http://sydney.blockchainworkshops.org/
  name: Sydney Blockchain Workshops
youtube: cwnlAS6RcvA
attribution:
  copyrightHolder:
    name: Open Data Institute
    url: https://theodi.org
  license:
    name: CC BY-SA 2.0 UK
    url: https://creativecommons.org/licenses/by-sa/2.0/uk/deed.en_GB
---
In December 2015, [ODI Labs](https://theodi.org/labs) delivered a talk to the [Sydney Blockchain Workshops](http://sydney.blockchainworkshops.org/), asking whether blockchains were always the right choice for global data infrastructure. In the talk, I explain how [blockchains](http://theodi.org/blog/data-infrastructure-technology-blockchains) are a great technology for shared-write, trust-free data collaboration networks, but warn that not everything needs those capabilities, and for many applications the technology may have undesirable aspects.

## Transcript

Hi, I’m James Smith and I’m Head of Labs at the Open Data Institute in London. The ODI is a nonprofit that [connects, equips and inspires people around the world to innovate with data](http://theodi.org/about). We’re not just about open data, though that’s an important part of it; we look at the entire [Data Spectrum](http://theodi.org/data-spectrum), whether closed, shared or open, big or small, government, personal or commercial. We see [data as infrastructure](http://theodi.org/data-infrastructure) for the modern digital economy, which enables new businesses and societies.

We’re very interested in the infrastructure for this data. If the data itself is critical infrastructure, then it has to be always available, resilient, redundant, and accessible from anywhere at any time. Because of this, we’ve got a real interest in distributed data storage technologies and how they can enable a global data infrastructure.

In our work with governments and businesses, we’ve seen a sudden spike of interest in these ideas, and in blockchain technology in particular. Many organisations are saying they need some sort of “blockchain strategy”, maybe without always knowing what they mean by those words. There is a another technology gold rush happening, and we’re trying to help organisations understand what it is they are looking at, particularly around the open public data that’s an essential component of our data infrastructure.

Any technology has a particular set of properties that make it unique, and as any developer will tell you, it’s important to pick technologies based on those properties. In the case of blockchains, the most important properties are shared-write, so anyone can store data in the system, and trust-free, so no central authority is required to verify those writes. It’s also very well suited to widely distributed systems. When asking the question “Would this be better with a blockchain?” we have to keep these properties in mind.

**When can blockchains work best?**

There are a lot of cases out there where a shared-write trust-free database is a very useful thing, particularly in widely-distributed international systems without an existing central authority.

Supply chains are a great example; [Provenance](https://theodi.org/start-ups/provenance), a graduate of the [ODI Startup programme](http://theodi.org/odi-startup-programme), are building a system on top of Ethereum which allows secure, trusted tracing of commodities across our global supply network, so that you can be sure that your Fairtrade organic decaf latte really is all of those things. Using a blockchain approach, it manages this without any central authority, and without exposing commercially sensitive information.

Domain Name System (DNS) is another; the ability of the network to arrive at consensus over domain registrations in a distributed way could remove the centralised aspects of DNS, which can be a security risk.

How about real-world addresses? Addresses are created in a widely-distributed manner, and central authorities often take a very long time to update the canonical lists. Here in the UK we often find people in newly-built areas unable to get basic services because their address doesn’t exist in the database yet, despite the fact they’re physically living there. Also, sometimes that central authority is a privatised company, as it is now in the UK. Addresses are critical infrastructure, created by a widely distributed group; it seems a good fit. Australia has recently announced it will be opening up the geocoded national address file as open data; perhaps there is an opportunity there.

However, we also see blockchains being suggested for things that don’t really require those properties.

Land registries are a commonly-proposed use, and Odessa is the latest authority planning something in this area, with a [property auction powered by a blockchain](http://cointelegraph.com/news/first-blockchain-powered-government-to-launch-in-odessa-ukraine). But what does this really add? One of the core jobs for a country is to look after property rights; all a blockchain approach can do is reduce corruption by exposing that data publicly and detecting fraud from within the system. Perhaps, though, if that’s necessary, there are deeper issues to look at first before imposing a technocratic solution.

There are many other ideas being thrown around in areas where an effective centralised authority already exists and does the job. Applying blockchains in these areas can seem a bit like chasing the technology purely for its own sake, not because it solves a fundamental problem.

**When blockchain technology is not the answer**

There are also more controversial applications, where blockchains paradoxically enable more centralisation, surveillance and control. There is a persistent idea floating around about paying state benefits in a cryptocurrency, which can track how they are spent, and restrict what people can buy with them. No matter what you think of the idea, it’s a political and social question, not a technological one.

Now, don’t get me wrong. Blockchains are an incredible technology for shared write, trust-free data management, and have real potential to revolutionise our global data infrastructure. However, many of the applications for which they are being mooted simply don’t need that level of capability, and in many cases other properties of the system are undesirable.

A really important one is immutability. Once data is added to a blockchain, it’s there forever. It can’t be changed or removed without destroying the integrity of the whole system. On the surface this seems great from a technical point of view. However, immutability can remove the human element of our social systems.

A simple example might be the [EU “right to be forgotten” judgement](http://ec.europa.eu/justice/data-protection/files/factsheets/factsheet_data_protection_en.pdf), where EU citizens can ask to have links removed from Google’s index. What if the thing they want to be forgotten is stored in an immutable blockchain?

And some legislation can require the full rewriting of history. In the UK, if you change your gender, you have a right to have that change reflected in all official documentation back into the past, to rewrite history. Not just to have the change recorded, but to make it so that the old information never existed. What happens if your gender is stored with a land purchase in a blockchain land registry? Has a supposedly neutral technology choice become oppressive?

And what of illegal or private information? Once it’s in a blockchain, it’s extremely hard to remove. Is then everyone with a copy of the blockchain then guilty of possessing something they shouldn’t?

The way we store information using a blockchain is really important. It seems likely that most systems will be hybrids, using a blockchain to store audit data and verify integrity, but storing the data itself in a separate data store, which can change and be rewritten if necessary.

**Asking social questions**

There is a danger that the rush to move things onto the blockchain will encourage a black-and-white view of the world, in which history is immutable and we approach inflexible rule-by-algorithm. As with all web-scale technologies, we need to consider what social impacts there are, and what consequences there may be. This is especially relevant in a global, immutable, public record.

At the ODI we’re interested in all these social questions as well as the technology itself. We are certain that blockchains have a big role to play, as part of a suite of new distributed technologies. We’re also certain that existing institutions need help to understand the choices that they are making, both on a technical and social level. We want to work with our international network of [ODI Nodes, ODI Members and ODI Startups](http://theodi.org/our-network) to explore these questions and help work out how this technology can help people.

We want you to be part of that conversation as well; the challenge for all of us when applying blockchains to our global data infrastructure is to use them where appropriate, but to always remember that such systems should be designed to serve people, and that our choice of technology may have political and social implications. Algorithms are not politically neutral, the human condition is rarely black and white, and we over-simplify at our peril.

**This talk was supported by [Deutsche Bank](https://www.db.com/company/index.htm) and is part of ODI Labs’ work on [data infrastructure](http://theodi.org/data-infrastructure). If you’re interested in supporting our R&D work on data infrastructure and blockchains, email [labs@theodi.org](mailto:labs@theodi.org).**
