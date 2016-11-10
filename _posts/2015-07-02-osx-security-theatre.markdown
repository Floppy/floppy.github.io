---
layout: post
title: OSX Security Theatre
date: 2015-07-02 00:00
comments: true
categories:
- security
---

I've always been vaguely dissatisfied with my personal security setup. I've been happy it's pretty secure and safe, but the software hasn't been great. However, that's changed recently with a few new releases, so I thought it might be worth sharing my setup with the world. I'm on OSX, so this is specific to that platform, but most things are open source and cross-platform, so there might be something to learn anyway. Also, some of you might tell me how I can improve it even further.

## Passwords

Basic security hygiene means having strong unique passwords on every different site, but obviously that's very difficult. Enter the password manager app, which can generate secure unique passwords and store them in a single place, behind a strong master password.

Obviously make sure the master password is strong; however, it still can be memorable and easy to type. Use [Correct Horse Battery Staple](http://correcthorsebatterystaple.net/) to generate a good one. I'd recommend going over the top on this; make it at least 6 words long.

### KeePass database

I've used the [KeePass](http://keepass.info/) format for many many years, because the format is an open standard, there are many cross-platform apps, and it can be verified as secure by looking at the design. Also, as it's a single file that stores all passwords, there's no cloud storage, and I know that my passwords are not being shared with anyone else. I just don't trust things like LastPass or 1Password, because giving away your passwords is inherently defeating the point. So, KeePass avoids that by giving me complete control over access to the file.

But, because cloud synchronisation (and backup) is useful, I store the file in [Dropbox](https://db.tt/8ZsPh7g). It's encrypted securely on my machine before uploading, so I don't really care whether Dropbox is secure or not (as far as that file's concerned anyway). We do the same with a shared password file for work stored in Google Drive.

### KeePass clients

For a long time I was using [KeePassX](https://www.keepassx.org/), which worked, but didn't have some of the nice features like browser plugins to auto-fill password forms, so there was lots of copying and pasting, and I tended to let the browser store the passwords as well (again defeating the point of a secure store, especially in Chrome).

However, last week I found [MacPass](https://mstarke.github.io/MacPass/). This is a native OSX client, which works nicely and is under active development. Even better, there is a [proposed patch that adds KeePassHTTP support](https://github.com/mstarke/MacPass/pull/247), and someone's [prebuilt the app with that built in](https://github.com/mstarke/MacPass/pull/247#issuecomment-113848747); that's the version I'm using.

KeePassHTTP is a little server in your KeePass app that lets other apps access the database locally, and that means *browser integration* finally.

{:.alert}
**UPDATE**: KeePassHTTP is now supported directly in MacPass using a plugin, so no patch required. Download the standard install of [MacPass](https://mstarke.github.io/MacPass/), then follow the "Using precompiled version" instructions for [MacPassHTTP](https://github.com/MacPass/MacPassHTTP). Works a treat.

### Browser integration

Browser plugins were the thing that made me jealous of LastPass and 1Password users; yeah, they were potentially giving their passwords away, but it was *so easy*. Now I have MacPass+KeePassHTTP, that's changed.

I'm using Firefox (because Chrome [just gets more evil over time](http://www.independent.co.uk/life-style/gadgets-and-tech/news/google-was-downloading-audio-listeners-onto-computers-without-consent-say-chromium-users-10335111.html) and has been purged from my machine), and I'm using a plugin called [PassIFox](https://addons.mozilla.org/en-US/firefox/addon/passifox/). That's really simple to link up to MacPass, and then you can just right-click in forms and tell it to fill in password fields.

I've since turned off all the built-in browser password storage and syncing, and am much more pleased with the system than I've ever been. I'm not sure if it can generate passwords from within Firefox yet, I've not tried it, but I don't mind generating in MacPass; it's not exactly hard.

### iOS app

What about on my phone? Well, that's why the database is stored in Dropbox. I use an app called [iKeePass](https://itunes.apple.com/us/app/ikeepass/id299697688?mt=8) which can read the file directly from Dropbox and open it. Then it's a simple click to copy passwords into the iOS browser app. It's not massively trivial, but it's not too hard for the rare times when I need to use it.

{:.alert}
**UPDATE**: I've changed to using [Keepass Touch](https://itunes.apple.com/us/app/keepass-touch/id966759076?mt=8) instead, which streamlines the process a bit. It still syncs from dropbox, but allows you to unlock the database with Touch ID, which makes everything quicker. It also supports editing the database and creating passwords on iOS, which is great.

## Encryption

I've also used PGP since around 1998, and I'm really please to see that it's basically the only encryption system that's not known or suspected to be compromised by our security agencies. If it's still good enough for Edward Snowden, it's good enough for me.

### GPG Suite

On OSX, if you want to use PGP, you install [GPG Suite](https://gpgtools.org/). It's a nice set of tools and integrations which make using PGP reasonably simple (though it's still not a trivial process to get set up).

Again, pick a good long and memorable passphrase for your PGP key. You'll be typing this one a lot, so make sure it's easy to get right. Also make sure it's different from the KeePass one above! You've still only got two to remember :)

Once you've generated a key pair (one private, one public) using GPG Suite then you will want to back up the private key somewhere nice and secure. I currently have mine in a [Truecrypt](http://truecrypt.sourceforge.net/) volume, which is again backed up in my Dropbox account, though Truecrypt seems to be dead, and not GCHQ-proof any more, so that will change soon.

### Mail integration

For a long while I was using Apple's built-in Mail app as GPGTools integrated nicely with it. However, recently, I've found that [Airmail 2](http://airmailapp.com/) has a [PGP plugin](http://support.airmailapp.com/post/95764147348/gpg-pgp-plugin), and it works almost perfectly. That means I have a decent mail client *with encryption support* finally.

### Keybase

Of course, if you want to encrypt email, you need other people's keys. You can share in a number of ways through GPGTools, but one of the easiest is to use [Keybase](http://keybase.io/Floppy). It's invite-only (shout on Twitter if you want one, plenty of people have spares, including me), and it's basically a way of linking your PGP key to your social network accounts, and letting people get hold of your key easily.

The one big thing I'd change about Keybase is that they should just get rid of the ability to generate and store a private key on their site. I know they're trying to make it easy, but it's a massive security antipattern and even people who I know have decent technical knowledge have used it; it's just too temptingly simple.

Instead, generate your key with GPGTools locally, and upload just the public key to Keybase. That has the advantage that you can pop the right email addresses on it as well.

### iOS mail encryption

Forget it :)

Seriously, this isn't a thing. If you're dealing with encrypted mail, or want to make sure yours is signed, don't bother trying to do it on a phone.

## Miscellanea

I've enabled full-disk encryption ([FileVault](https://support.apple.com/en-us/HT204837)) on my Mac. There's just no reason not to. 

Obviously all remote logins and file transfers are done via SSH as well. My SSH key has a similar master password to the ones above on it to unlock it, and all remote servers I use are set up to only accept login with the right keyfile.

Every website I use that supports it has two-factor authentication turned on. If it supports the Authenticator app then I use that for the second factor, otherwise I fall back to SMS verification, though I consider that insufficient for decent security [after my phone was hijacked](/blog/2015/04/16/anatomy-of-a-hijack/) a few months ago. So, I'm looking at you Twitter; authenticator app support please. 

## What next?

I'm interested in these [FIDO U2F keys](https://www.yubico.com/applications/fido/); it would be good to have the OSX encryption linked to a hardware token like that, so my machine can only be used with it plugged in. Also that can be used with some two-factor auth systems. This needs to be looked into.

However for something physical that can be lost, I'd want to be sure there was a way of having at least two keys that can unlock things, and obviously it would be hard to use with anything that needs unlocking on iOS.

I also need to work on my network security and privacy. I want to get a VPN routed via my home connection for use while out and about, and some way of easily swapping onto the [Tor](http://torproject.org) network that's got decent usability for when I want to be anonymous (or look like I'm in a different country). I'll follow up with a further post if I get any of that sorted.

## Summary

Security is complex, but the software tools are finally getting good now that it's not hard. 

Everything I use that's involved in dealing with secure information above is open source, which means I can be more confident that there aren't hidden backdoors (though of course [you can never be 100% sure](http://siliconangle.com/blog/2013/09/06/bullrun-the-nsa-backdoor-anti-encryption-bug-program-that-breaks-most-encryption-on-the-internet/)). There are equivalent apps for every platform, so I hope this sort of setup is something that anyone could use and be reasonably safe.

I've mentioned the security services above, but I want to finish by saying that *I'm not trying to avoid the law*. I'm not doing anything illegal, but we're now in a world where strong security hygiene is a necessary skill online. Not just because your emails are routinely tracked by our own (and therefore many other) security services, but because the weaknesses they've introduced into online security make it easier for *everyone* to access your communications. By irresponsibly weakening our security standards and introducing backdoors into common security-related code, you have to assume that everything is visible to everyone. 

That means compartmentalising your security with unique passwords, and using strong non-compromised encryption wherever possible.

Remember, it's not paranoia if they're really watching you.

