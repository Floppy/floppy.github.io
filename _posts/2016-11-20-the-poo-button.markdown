---
layout: post
title: The Poo Button
date: 2016-11-20 00:00
comments: true
categories:
- coding
- internet of things
---

{:.alert}
If you're visiting from the [Wired article](http://www.wired.co.uk/article/amazon-dash-hack-poo-button-internet-of-things) and want to show your appreciation somehow, you can [make a donation](https://www.justgiving.com/4w350m3/donation/direct/charity/99993#MessageAndAmount) to the [Cri du Chat Syndrome Support Group](http://criduchat.org.uk) to help families affected the syndrome that meant I did this thing in the first place. Thanks!

<img src='/images/poobutton.jpg' alt='The Poo Button' style='max-width: 50%; float: right; margin-left: 10px'/>

A little while ago, my colleague Stuart hacked a couple of [Amazon Dash buttons](https://www.amazon.co.uk/b?ie=UTF8&node=10833773031) to [create a behaviour scoreboard for his son](https://hackernoon.com/quantified-boy-726e9558594f#.dj7xkh8ra) - an experiment in Internet of Parenting, if you will.

I thought that was pretty cool, so I popped a Dash button onto my Amazon wishlist, but without a clear idea of what to do with it; just for fun. Then though, my wife asked what it was, and a couple of days later came up with an idea. And this time, my hacking around might actually be useful.

## The Challenge

My daughter has [Cri du Chat Syndrome](http://criduchat.org.uk), a genetic condition that causes global learning delay and a bunch of other things. One side effect of it is that she has always suffered from chronic constipation; she's been on medication for it for years, and it's a constant mission getting her to poop regularly - her bowel muscles just aren't strong enough, or something.

Anyway, we've changed her medication and it's had some effect, but to be sure we need to track when all her bowel movements happen - this stuff doesn't have an instant effect.

So, writing it all on paper is a bit useless, when we can do better. And what better than to make a "poo button". Let's get a Dash button, stick it on the wall, and use it to log (no pun intended) her logs (OK, pun was intended). I'm not the first to do this of course - one of the first hacks for the Dash was to [track nappy changes](https://medium.com/@edwardbenson/how-i-hacked-amazon-s-5-wifi-button-to-track-baby-data-794214b0bdd8#.n2rjvlxmm).

## The Button

First thing - set up the Dash button in the normal way using the Amazon app on a phone. When it comes to selecting a product, **don't choose anything**, just exit. Then you have a dash button connected to the local network, but that won't order anything from Amazon.

## Intercepting The Presses

Then, we install the [node-dash-button](https://github.com/hortinstein/node-dash-button) library. I'm using a Mac Mini as a home server so it was a matter of installing `npm` with [Homebrew](http://brew.sh/), making sure I had XCode installed, and away we go following the setup in the [README](https://github.com/hortinstein/node-dash-button/blob/master/README.md). The installation worked better as a global thing rather than just for one user:

```
npm install -g node-dash-button
``` 

We then run `sudo /usr/local/lib/node_modules/node-dash-button/bin/findbutton` and get something like this:

<pre>
Watching for arp & udp requests on your local network, please try to press your dash now
Dash buttons should appear as manufactured by 'Amazon Technologies Inc.'
Possible dash hardware address detected: xx:xx:xx:xx:xx:xx Manufacturer: Microchip Technology Inc. Protocol: arp
Possible dash hardware address detected: xx:xx:xx:xx:xx:xx Manufacturer: Amazon Technologies Inc. Protocol: udp
Possible dash hardware address detected: xx:xx:xx:xx:xx:xx Manufacturer: Apple Protocol: arp
Possible dash hardware address detected: xx:xx:xx:xx:xx:xx Manufacturer: Amazon Technologies Inc. Protocol: arp
Possible dash hardware address detected: xx:xx:xx:xx:xx:xx Manufacturer: Microchip Technology Inc. Protocol: arp
</pre>

The Amazon ARP one is the one we want, so we'll keep the address (just shown as x's above) for later.

Now we need a bit of code to detect the button press. I've shamelessly ripped of the code Stuart created in his post - I won't repost it here, [take a look back at his post]((https://hackernoon.com/quantified-boy-726e9558594f#.dj7xkh8ra)) for the breakdown.

## Storing The Data

To store the data, I could do what Stuart did and use [Bothan](https://bothan.io), but my wife will be happier with a spreadsheet. So, let's set up one of my favourite tools of the moment, [Zapier](https://zapier.com), to store the data somewhere useful.

I've created a Zap with a webhook trigger and a Google spreadsheet output. I really wish Zapier would let me publish zaps publicly so you could see it, but they don't, so you'll have to take my word for it that it's easy.

To test it, we can send a message to the webhook with `curl` (this project is so pun-rich it's amazing):

```
curl -X POST -d '{"when": "2016-01-01T09:00Z"}' https://hooks.zapier.com/hooks/catch/.../.../
```

Zapier detects the POST, and then sends the `when` value into my spreadsheet. Easy as pie. Now all we need to do is get the code to send that POST when it detects a button press. 

## The Code

In the end, the entire code is as simple as:

<pre>
var dash_button = require('/usr/local/lib/node_modules/node-dash-button');
var request = require('/usr/local/lib/node_modules/request');
var poo_button = 'xx:xx:xx:xx:xx:xx' // The MAC address for the button goes here
var webhook = 'https://hooks.zapier.com/hooks/catch/xxxxxx/xxxxxx/';

var dash = dash_button([poo_button], null, null, 'all');

dash.on("detected", function (dash_id){
  if (dash_id === poo_button){
    console.log("Parp!");
    requestData = {
      "when": new Date().toISOString()
    };
    request({
      url: webhook,
      method: "POST",
      json: true,
      headers: {
        "content-type": "application/json",
      },
      body: JSON.stringify(requestData)
    });
  }
});
</pre>

There's a lot of cleanup to do with that code, like sorting the include paths, package.json file, extracting the secure variables, and so on, and I'll carry on doing that and post the source on GitHub when it's OK for public consumption. I know it's shonky as hell right now, but **it works**!

I press a button, and the current time is logged in a spreadsheet. Bingo!

## Next

So there are a few things that would be good to do next.

* Somehow enable use of the Bristol Stool Scale to store the type. This is kind of helpful, though not essential. We could have more than one button, or we could somehow detect multiple presses. But I don't know if it's necessary.
* A way of packaging this up so it can be used by non-experts. The Internet of Things is all very well, but too often it's about [$700 juicers](https://www.juicero.com/), and not about making people's lives easier. I'd love to know who's really applying this stuff to making life easier for people with extra needs.
* The Dash button is really cool, but it's hard to set up to take control of. An open version that could hook up to an arbitrary URL would be amazing. Maybe that's something IFTTT should look into - they have a [DO button app](https://ifttt.com/products/do/button) already; a hardware version would be great.