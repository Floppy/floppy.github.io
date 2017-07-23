---
layout: post
title: "Open Party Finance Data"
date: 2014-11-24 07:18
comments: true
categories:
- election
- opendata
---

One of the things we want to do with Something New is to be as transparent as we possible can on donations and spending. We do have to report a certain amount to the Electoral Commission, but it's also about walking the talk of openness and transparency.

We're not raising money yet, so donations will come later, but we have started to track our spending. Working at the ODI, I'm surrounded by smart people, and there's always someone who knows about whatever you're trying to do. So, when thinking about spending data, I went to have a chat with Ian Makgill of [Spend Network](https://spendnetwork.com/), and asked if there were any formats that parties already use.

Fairly obviously, there weren't, so I then asked "what would you *want* them to do?", and together we came up with a decent schema for political spending data. We're now publishing our finances in that format, so I thought I'd give you a quick run through.

I talked about this in a recent [ODI Friday Lunchtime Lecture](https://theodi.org/lunchtime-lectures/friday-lunchtime-lecture-data-for-democracy-how-to-stand-for-parliament-with-open-data), so you can watch the video if you like. Or, read on below...

<div style="width:500px; height:281px; margin: 0px auto">
  <iframe src="//player.vimeo.com/video/111864914" frameborder="0" width="100%" height="281px" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>

## Schema

You can see the full schema on our [finances microsite](https://somethingnewuk.github.io/finances/).

It divides into a few sections. First there are names for suppliers and buyers, but also URIs, so we can uniquely identify them and correlate across other spending. Then we have the amount and date, including foreign currency where appropriate. Next comes a description of the item, and some categorisation of the product or service, and finally the supplier's transaction ID. I want to add links to (PDF?) copies of receipts as well, though I've not got to that yet.

There are a few interesting parts to this, which I'll go into next...

## URIs

It's easy enough to write the name of a company or buyer, but if we want to uniquely identify them, we need a URI. For companies, we use the [OpenCorporates](http://opencorporates.com) URL; they cover millions of companies across the world, which is great. Unfortunately they don’t seem to include [NationBuilder](http://nationbuilder.com), who I suspect are based somewhere OpenCorporates don’t cover yet. Won’t be long, I’m sure.

Charities are another matter; there isn't a stable-looking URL for a charity on the [Charity Commission](https://www.gov.uk/government/organisations/charity-commission) website, only a search box. Fortunately there is a project called [OpenCharities](http://opencharities.org/) which does the same thing for charities as OpenCorporates does for companies, so I can use their URLs. Hurrah for Open Data.

One room I booked was from... I have no idea. I guess it's an unincorporated association. How we define URIs for things that barely exist legally, I don't know. If you do, let me know.

The last bit here is URIs for councils. Again, when booking rooms, councils are often the supplier, particularly Parish Councils. The LGA defines a set of URIs for councils down to the local authority level, but it doesn't go down to the parish level. In fact, it looks like there may not even be a proper list of parish councils, let alone a URI for each. The closest we have appears to be [this unofficial list](http://politicsresources.net/area/uk/parish.htm). We could do with an OpenCouncils project, perhaps, to bring these all together and let people reference them reliably.

The last bit on URIs was to talk about buyer URIs. For the party, that should be easy enough, but for individuals? What's *my* URI? I don't feel quite right with it just being my website, but that's basically the right thing to do. So, I've made one up. If you need to refer to me officially, you can use [http://id.floppy.org.uk](http://id.floppy.org.uk). It also acts as an OpenID delegator (see the source for how), so it's now also my OpenID. If you visit it, you won't get much though, except a GIF of a [rotating owl](https://www.youtube.com/watch?v=9hBpF_Zj4OA). Because... reasons.

## Codes

Moving on, let's talk about codes. We use two different coding schemes for the data. The first is from the electoral commission, which is only really useful for official reporting. The other is the [UN Standard Products and Services Code (UNSPSC)](http://unspsc.org). The UNSPSC has a decent search function, so it's easy enough to classify your spending, and the categories are *very* fine-grained. At least, they are in the area of traditional products; it's a bit vague on the whole "Internet" thing. Probably needs an update. Still, it's a standard, and will suffice for us. We can always use new codes as they create them.

## Publishing

The last bit to talk about is how we publish the data. As I mentioned, the schema and data are wrapped up in a Datapackage, which is a JSON file which lists the fields, license, data file locations, etc. All this is in a [GitHub repository](https://github.com/SomethingNewUK/finances), and it's the live version, which means that we're not really publishing our data; instead you're seeing the real thing all the time.

Having the data in GitHub lets us do something cool - publish it on the web using github pages. If it's in a gh-pages branch, GitHub will publish it for us, and run it through [Jekyll](http://jekyllrb.com), which means you can also generate HTML pages alongside.

Jekyll has support for data files, both in JSON and YAML, and in CSV (which I [specifically added](https://github.com/jekyll/jekyll/pull/2761) over the summer so I could use it for this - yay Open Source!). If we tell Jekyll that our entire repository is a source of data files, we can access all the files, both the CSVs and datapackage, from the HTML-generating files. That means we can have a single source of data, and use Jekyll to automatically publish both a human-readable version and the original machine-readable files. We've basically rolled our own data publishing system, which is pretty cool. You can see how it all works in the [repository](https://github.com/SomethingNewUK/finances), but if you need more explanation, leave a comment and I'll elaborate.

## Validation & Certification

The last thing is that it's all validated and certified using tools I've helped build at the ODI. We use [CSVlint](http://csvlint.io) to check that the CSV files are valid when they're committed, and we've also obtained an [Open Data Certificate](https://certificates.theodi.org/datasets/2254/certificates/14550) for the data, showing that it's good, reliable, open data.

I'd love to see more parties doing this. The data schema is totally reusable, as is the rest, and this took me no more than a few hours to put together from scratch. There is no technological reason why all the parties couldn't open up all their data tomorrow. All that they lack is the vision and the courage.
