---
layout: post
title: OSX Security Theatre Part 2
date: 2016-11-10 00:00
comments: true
categories:
- security
---

{:.alert}
This is part 2 of my security setup. See [part 1](/blog/2015/07/02/osx-security-theatre) for information on password security and encryption topics.

After the 2016 US election, we have an extensive surveillance apparatus in the hands of a man who I definitely don't trust with it. Given that, it's time for another security upgrade.

This part focuses on network security hygiene, and the ability to avoid surveillance. As I said in part 1, this isn't because I'm doing anything illegal, but as I'm politically active, and in declared opposition to many of our current illiberal leaders, it seems only sensible to create a bit of safe space *now* in case someone decides to make my activities illegal in the future.

## Uplink

First up - time to get a decent Internet Service Provider. The UK is passing law after law allowing logging of connections, mandated filtering of Internet content, and so on. The government is on a path to deciding what you can do online, and being able to check up on you. They will rely on the ISPs to enforce this for them.

However, there is one out there that resists this at every opportunity. [Andrews & Arnold](https://aa.net.uk) is a small ISP designed for technical users, and is explicitly [opposed to monitoring and filtering](http://aa.net.uk/kb-broadband-unfiltered.html). That page includes a [warrant canary](https://en.wikipedia.org/wiki/Warrant_canary) for secret monitoring equipment as well, so that's good.

As a bonus, they PGP sign all their emails, run a [support channel on IRC](http://aa.net.uk/kb-irc.html), support the [Open Rights Group](https://www.openrightsgroup.org/), and regularly give evidence to MPs about communications policy. Basically, I know they have my back, and they're now the only people I trust with my uplink.

## Browser & web security

HTTP is the normal way to connect to websites; HTTPS is the secure version, and these days there is no reason not to use it. Many sites still don't send you to an HTTPS version by default, but still allow unencrypted connections. This means your communications can be easily read in transit.

Avoid this by installing [HTTPS Everywhere](https://www.eff.org/https-everywhere) in your browser. It automatically rewrites everything it can to HTTPS, helping you to stay secure.

I'd also recommend [Privacy Badger](https://www.eff.org/privacybadger), which is a browser extension that blocks various evil web tracking methods, helping maintain your online privacy. That means it also blocks all the ads that are doing nasty things, leaving only the ones that behave themselves. I like that over blocking all ads, though to be honest web advertising is so sleazy that I basically don't ever see any - Privacy Badger kills them all.

Which browser though? I use [Firefox](https://www.mozilla.org/en-GB/firefox/new/), personally. It's open source, free, and well-supported. Chrome (and even the open source version Chromium) sends a bunch of information about you back to Google without telling you, and I'd rather that didn't happen, so Firefox it is. I also now use [Firefox on iOS](https://www.mozilla.org/en-GB/firefox/ios/) as well; if you want things like bookmark sharing, you can have them.

One last thing on this - drop Google and change your search provider to [DuckDuckGo](https://duckduckgo.com/), a search engine that doesn't track you. I've found the results to be perfectly fine and have been using it well over a year now.

## VPN

Next, low-level network security. If I'm sat in a coffee shop, I'm probably on some unencrypted wifi network surrounded by a load of other people. It's quite simple to read network traffic in that situation, or even provide a honeypot wifi connection that will man-in-the-middle all your network traffic. So, even though we're as secure as we can be in our browser, let's be 100% sure and set up a VPN (Virtual Private Network).

A VPN is basically a fully-encrypted "tunnel" from your computer to another one somewhere else. That tunnel can go over unencrypted connections, but nobody will be able to see anything inside it.

I've set up a VPN server on a machine in my house, because I want my tunnel to basically allow my communications to be *as secure as they are in my home*. I'm not worried about anonymity at this point. The VPN will basically route all my network activity through my home, and through my trusted ISP.

So, I've got a Mac Mini running OSX El Capitan, with [OSX Server](https://itunes.apple.com/us/app/os-x-server/id883878097) (£15), which comes with the ability to run a VPN. Setup is dead simple for this use case. You can pretty much just enable the VPN in the server app, and the defaults will work. I'm using L2TP, which is the best on offer there. OpenVPN is supposed to be a bit better, but the software setup and maintenance looks like a headache I'd rather not have.

You then set up your VPN on your devices. On OSX that's in the Network preferences window - add a new interface and enter your VPN details. Same on iOS, under General settings.

The main problem is that you need to know where to connect to. Many ISPs don't provide a static IP, so you end up using Dynamic DNS. Your router may have support for this built in, but mine doesn't, so I'm using [ddclient](https://sourceforge.net/p/ddclient/wiki/Home/) running on the Mac Mini to automatically update my [Cloudflare](https://www.cloudflare.com/) DNS records. Works like a charm. I'll probably do a separate post just on that config, because it's a little involved, but this isn't the place.

{:.alert}
I've since found a little OSX menubar app called [VPN monitor](https://itunes.apple.com/cn/app/vpn-monitor/id887410814?l=en&mt=12) that for a couple of quid automatically connects to your VPN whenever you connect to a network. You can add safe networks, like home and work, where it won't bother, but the rest of the time it'll route your traffic via the VPN automatically. Security by default is always a good thing.

## Anonymity

Of course, that only gives me security, not anonymity. All the traffic still flows over my home ISP uplink as if I was in the house. For proper anonymity, we need something more, and that thing is [Tor](https://www.torproject.org).

Tor works by encrypting your traffic, sending it all over the network through multiple hosts, then having it emerge somewhere else on the network completely unrelated to you. It slows things down a lot, so you wouldn't use it all the time, but it's a great option to have available.

I've got two Tor options set up. The first is simple - just install [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en). That gives you an anonymised browser session without any further setup. For most people that's probably fine.

The second is more involved. If I need to cover my tracks with anything that's *not* browser based, or I want to hide my machine completely, I can route all my network traffic through a tor proxy running in the background.

Setup isn't hard. You can install Tor with [homebrew](https://brew.sh) (also useful for installing ddclient), and the default installation pretty much sets up the proxy for you.

I then created a new network location in the Network preferences on my laptop, and in the advanced settings for the wifi connection, enabled the SOCKS proxy to `localhost` port `9050`. That means that anything on that network connection should be sent through the proxy first, which will route it through Tor. Then you've got two network locations to choose from, which you can switch between in the Apple menu. One-click switch to anonymise all my traffic? Nice.

Now, there are [good reasons not to do this](https://www.torproject.org/docs/faq.html.en#AttacksOnOnionRouting) if you're *really* paranoid. Because your entire network traffic is being routed together, it might be possible to tell who you are from things like background processes checking in with Apple, or similar correlations. It's not something I would do unless it was really necessary, but it's nice to have it there ready. 

It also still [leaks metadata via DNS](https://www.dnsleaktest.com/), because your DNS lookups don't go via the proxy, but it's a step in the right direction and should be OK for casual use. If I manage to improve it I'll update here.

## What next?

So I think that's everything I've got set up, security-wise. What should I do next? Suggestions appreciated!