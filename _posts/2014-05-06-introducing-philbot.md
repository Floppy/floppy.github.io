---
title: Introducing Philbot - a DIY storage appliance
attribution:
  copyrightHolder:
    name: Open Data Institute
    url: https://theodi.org
  license:
    name: CC BY-SA 2.0 UK
    url: https://creativecommons.org/licenses/by-sa/2.0/uk/deed.en_GB
categories:
  - odi
---
Here at the ODI, we love creating content. [Phil](http://theodi.org/team/phil-lang), our Digital Production Editor, handles loads of video, audio, photography, and so on, and because a lot of it is rather large, his laptop threatens to bust its seams on a regular basis. So, he walked over and asked if there was anything the [tech team](https://twitter.com/ukoditech) knew of that would give him more space to work with.

Of course, it wasn’t quite as simple as just having a load of disk space. This is important stuff, so backup is important, and ideally we should be able to access it from the outside. We also have no system administrator (or air conditioning in the server room), so it couldn’t be anything that needed much maintenance.

We’d heard of things like the [Amazon Storage Gateway](https://aws.amazon.com/storagegateway/), and the idea of local storage backed by infinite cloud storage was very appealing. However, we don’t use AWS; instead, we love [Rackspace](https://www.rackspace.co.uk). Not only are they one of our [sponsors](http://directory.theodi.org/members/AR6346HB), but they’re [big on open source](http://www.rackspace.com/cloud/openstack/), and their London data centre runs on [100% renewable energy](https://www.rackspace.co.uk/green-hosting), all of which make us happy.

Unfortunately, there wasn’t anything around that we could use as a storage appliance backed by Rackspace Cloudfiles, which was a problem. Then, we realised - using a little bit of code and some cheap hardware, we could make our own!

![Philbot](https://theodi.github.io/presentations/philbot/philbot.jpg)

So, this is Philbot. It’s pretty simple, hardware wise. It’s a [Raspberry Pi](http://www.raspberrypi.org/) with a 2TB Seagate USB hard disk attached, which it shares over the network using the usual network drive protocols. All in all, under a £100\. Not bad.

The magic is in the software. We’re a Ruby shop mostly, and there are some amazing open source gems out there that let us do most of this really easily.

Firstly, our code uses the [Listen](https://github.com/guard/listen) gem to watch the filesystem and detect when things change. The idea is that when _real_ Phil saves a file onto Philbot’s disk, the script will notice. If a file is added, modified, or deleted, then it’s placed onto a queue (using [Resque](https://github.com/resque/resque)). That queue is processed in the background, and the file is uploaded or removed from Cloudfiles as appropriate using the [fog](https://github.com/fog/fog) gem. All in all, it’s really very little code, mostly just glue to connect together the parts. It’s all test driven with [Cucumber](https://github.com/cucumber/cucumber) as well, another of our favourite tools.

At this point, it works. Human Phil can save files on a large network drive, and they will be instantly backed up to Cloudfiles. If he deletes them, they will be removed from Cloudfiles as well. In future, we want to add a function to “freeze” directories, which removes them from the local storage but leaves them in the cloud for long-term cold storage.

There are some other future plans; we want to make the configuration of the device itself operate using a network drive with a configuration file on it, and then create a Raspberry Pi OS image with it all preconfigured, so that you can just plug it in and get going. That’s in the future though; for now it’s handling our day to day needs nicely.

So, if you would like to have your own cloud storage appliance for less than a hundred quid, why not take a look at the detailed setup instructions in the [Philbot repository on GitHub](https://github.com/theodi/philbot/). Let us know how you get on!
