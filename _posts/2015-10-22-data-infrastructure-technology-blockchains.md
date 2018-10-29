---
title: 'Data infrastructure technology: are blockchains the answer?'
attribution:
  copyrightHolder:
    name: Open Data Institute
    url: https://theodi.org
  license:
    name: CC BY-SA 2.0 UK
    url: https://creativecommons.org/licenses/by-sa/2.0/uk/deed.en_GB
categories:
  - odi
  - data
  - blockchain
---
How do we make sure data infrastructure is always available, and always trustworthy? Are blockchains the answer?

We believe that [data infrastructure](http://theodi.org/who-owns-our-data-infrastructure) is fundamental to our future. What we normally mean by this is “data as infrastructure” – data is becoming part of the infrastructure of society. In [ODI Labs](http://theodi.org/labs), we have a slightly different take on the issue: if data is to be infrastructure for society, what does that mean about the technology underlying the “infrastructure for data”?

![null](http://bd7a65e2cb448908f934-86a50c88e47af9e1fb58ce0672b5a500.r32.cf3.rackcdn.com/uploads/assets/28/f9/5628f98e1f986a081e000021/data_infra_1.jpg)

_<small>Photo source: [Flickr - r2hox (CC BY-SA 2.0)](https://www.flickr.com/photos/rh2ox/9990016123/ " r2hox ")</small>_

If data is becoming essential to society, then it must be:

*   resilient – always available when needed, with access able to route around damage. It can’t drop offline because of a datacentre outage, or a forgotten domain renewal.
*   robust – data must be verifiable and reliable, resistant to tampering. The concepts of [maldata](https://thehackernews.com/2014/05/microsoft-security-essential-found.html) and data spam aren’t in wide circulation yet, but at some point they will be.
*   scalable – having vital data hosted on a single server will not scale up when that dataset is suddenly in high demand.

A new class of technologies is appearing that cope with many of these problems. In particular, distributed data storage – where the data doesn’t reside in one place but across the network itself – is on the rise. And a lot of people are talking about one specific implementation of that idea: blockchains.

By the way, if you don’t know what I’m talking about, blockchains are basically a way of storing information (transactions, in the case of Bitcoin) in a distributed fashion across the Internet without needing a trusted central server. This [quick primer from the BBC](http://www.bbc.co.uk/news/technology-33090285) is a good introduction to the idea.

There is a lot of hype about “putting things into the blockchain” at the moment. While the technology is fascinating and has huge potential, there are a few things we need to be aware of.

## A blockchain, or THE blockchain?

![null](http://bd7a65e2cb448908f934-86a50c88e47af9e1fb58ce0672b5a500.r32.cf3.rackcdn.com/uploads/assets/28/fd/5628fd8b1f986a081e000025/data_infra_4.jpg)

_<small>Photo source: [Flickr - r2hox (CC BY-SA 2.0)](https://www.flickr.com/photos/rh2ox/9990024683/in/photostream/ " r2hox ")</small>_

There’s a confusing tendency for people to talk about THE blockchain, as opposed to A blockchain, and that implies Bitcoin. Storing data in the Bitcoin blockchain is possible, and has been done [since day one](http://www.righto.com/2014/02/ascii-bernanke-wikileaks-photographs.html), but it isn’t really advisable.

So, instead of using the Bitcoin blockchain, most blockchain data storage systems are using their own chains – for instance, [Namecoin](https://namecoin.info/), [Ethereum](https://ethereum.org/), and [Factom](http://factom.org/) (who are putting [Honduras’ Land Registry](http://siliconangle.com/blog/2015/05/17/honduras-to-use-bitcoin-blockchain-tech-to-run-its-land-registry/) into a blockchain).

However, all of these still have a cryptocurrency involved. The work to verify the blockchain is done by many people, and they need to be paid for the compute time they contribute. Therefore, these systems all have their own currencies internally, like “Ether” or “Factoids”.

Is it realistic to run a distributed data store based on a pseudocurrency model? Does the very concept of financial return introduce the [wrong incentives](https://hbr.org/2009/03/when-economic-incentives-backfire) into the system? At the end of the day, **who pays** to maintain an effective yet radically distributed system?

## Immutability

![null](http://bd7a65e2cb448908f934-86a50c88e47af9e1fb58ce0672b5a500.r32.cf3.rackcdn.com/uploads/assets/28/fb/5628fb551f986a081e000023/data_infra_2.jpg)

_<small>Photo source: [Flickr - r2hox (CC BY-SA 2.0)](https://www.flickr.com/photos/rh2ox/9989876925/ " r2hox ")</small>_

Blockchains are designed to be immutable, to have data written into them and be available forevermore. Technically, that seems a desirable quality as it means you can’t go back and rewrite history: nobody can deny that a transaction took place, even if it was revoked later on.

> A digital register may supersede or expire your permission to do something, but it shouldn’t be able to later refute that permission was ever issued to you. [Paul Downey](https://gds.blog.gov.uk/2015/09/01/registers-authoritative-lists-you-can-trust/)

However, technology, meet society. In the sphere of human life, immutability can be a major problem.

What about the recent [EU right to be forgotten](https://en.wikipedia.org/wiki/Right_to_be_forgotten) ruling? What’s your legal recourse when the data you want removed from public view is stored in an immutable data store? Is there any truly immutable data?

Here’s an example: in the UK, if you change your gender, you of course have the right to have your new gender reflected in all official records. That, though, includes rewriting history and backdating your new gender, so that the gender you were assigned at birth doesn’t appear even in old records. If, say, your driving licence is stored in a blockchain, the old version can’t be modified. It can be revoked and replaced with an updated one, but the original record is still there.

Sure, you could solve those problems by storing only pointers to data in a blockchain, and having the data somewhere else, somewhere mutable, but then you’ve lost the resilience aspect of the technology; the data is still centralised, even though the index is distributed.

How then, do we design data storage in blockchains so that immutability is limited to the things that need to be immutable?

## Beyond blockchains

![null](http://bd7a65e2cb448908f934-86a50c88e47af9e1fb58ce0672b5a500.r32.cf3.rackcdn.com/uploads/assets/29/00/56290077d0d46207c8000031/data_infra_5.jpg)

_<small>Photo source: [Flickr - r2hox (CC BY-SA 2.0)](https://www.flickr.com/photos/rh2ox/9989872634/in/photostream/ " r2hox ")</small>_

Nowadays, when most people say “blockchain”, and even when I say it myself, I treat it as a shorthand for “undefined radically distributed storage technology”. There are many other options out there, from the non-bitcoin blockchains like [Ethereum](https://ethereum.org/) and [MaidSafe](http://maidsafe.net/), to other systems like [Tahoe-LAFS](https://en.wikipedia.org/wiki/Tahoe-LAFS), and even older technologies like BitTorrent. (For great in-depth discussion of these and many others, watch the [Redecentralize interviews](http://redecentralize.org/interviews/)).

Make no mistake, there is huge (and radical) potential in this technology area for data, and for society as a whole, but we need to understand how these technologies are best applied.

### Standards

And whether it’s blockchains or something else, there are plenty of questions. How do we standardise storage in such a system so that we get a single network of data, as opposed to having to use a different storage system every time we want a new type of information? What are the data protocols for distributed storage? How do we talk about, and perhaps enforce, ownership and licensing?

## What are we doing?

We are exploring the potential applications of these technologies in the context of data infrastructure. This applies at different scales: global, national and city data infrastructure. It also applies across sectors: finance, agriculture, nutrition and global development.

ODI Labs are exploring these issues and, as with everything we do at the ODI, we will be collaborating with our network of [Partners](http://theodi.org/membership), [Supporters](http://theodi.org/membership), [Nodes](http://theodi.org/nodes), and [Startups](http://theodi.org/startups). If you would like to get involved in collaboration, and sponsorship, please [get in touch](mailto:labs@theodi.org).

We want to experiment with the technologies, work out some of the tricky social questions, and help guide the future of distributed data storage in the right direction.
