---
layout: post
title: MythRename
tags:
- mythtv
- perl
---
Here in the UK, T4 (a weekend morning kids show thing) put a "T4:" prefix on the front of every program they show, so rather than "Futurama", you get "T4:Futurama". If you want to record these shows, you need to have two rules, you end up with two different titles in the program list, and you get duplicated episodes.

Well, no more. I've written a script called mythrename which strips prefixes from programs in the MythTV database. Configuration is simple - just edit the perl script and add the prefixes you want to remove to the @prefixes array, edit the database options, and away you go. It's best run after every mythfilldatabase run, as the listings grabber does away with all our hard work and puts back the original titles.

There's no readme file - all the explanation you need should be in the Perl script. If there's anything I've left out, please let me know! 