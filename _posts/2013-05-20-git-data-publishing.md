---
title: Git for Data Publishing
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
  - git
  - data
  - csv
---
Over the last few years, open source software development has been revolutionised by the adoption of distributed version control systems. Using tools like [git](http://git-scm.com) and particularly sites like [GitHub](http://github.com), it’s now incredibly easy to contribute to a project. This has lowered the bar for participation, and has had an incredible impact on the quality and range of open source output, and enabled fantastic service ecosystems and business models to build up.

In contrast, open data is still its infancy as far as tooling and process go. In a world where open data is published sporadically, where it’s hard to get things fixed, and where publishers aren’t recognised or able to easily engage with their user community, can the tools of open source revolutionise open data publishing in the same way?

Personally, I believe this is possible. Data is different from code in many ways, but the open source development model has a lot we can learn from. When I can fork your open dataset, fix errors, and easily get my changes integrated back in, we all win. We could sit down and discuss this for a while; there are certainly lots of issues to think about. However, I’m a hacker at heart, and I think best when my mind can express itself through working code. So, in my 20% time at work, I’ve been experimenting.

Firstly: we can put simple data into GitHub repositories, but it’s not very friendly, so I’ve built a [Git Data Viewer](http://git-viewer.labs.theodi.org/), which wraps around a git repository (not necessarily GitHub), and exposes some information about the contents in a more data-user-friendly way than the standard GitHub view. Currently, if you create a repository, add some data in CSV, and add a [DataPackage](http://data.okfn.org/standards) file to describe it, the app can load that up and show you the details, contents, history, and so on of that dataset. For example, here is a view of the [UK house price dataset](http://git-viewer.labs.theodi.org/repositories/git%3A%2F%2Fgithub.com%2Fdatasets%2Fhouse-prices-uk.git), which was put onto GitHub by [Rufus Pollock](http://rufuspollock.org/). As you can see, it’s substantially friendlier than the [bare repository](https://github.com/datasets/house-prices-uk/) (though data.okfn.org does also provide [a more useful view](http://data.okfn.org/data/house-prices-uk) of this particular dataset).

Secondly, I’ve started experimenting with the process of maintaining and improving this data. I’ve uploaded an [MOD dataset](https://github.com/theodi/dataset-mod-disposals) to play around with; here you can see an [open pull request](https://github.com/theodi/dataset-mod-disposals/pull/1) for an improvement to the file format of the data. I’m already learning that while many operations on datasets match well with Git, some do not. Adding columns, for instance, affects every line, so will be very difficult to merge in if other things have changed as well. I’m unsure at the moment if this is a fundamental limitation in Git itself, or whether we can improve the tooling to make this easier.

I make no claim that this will work, it’s an experiment to see which bits do and which bits don’t, and to see how far we can push our current toolset before it breaks. If you’re interested joining in, please do come and talk to us on our [IRC channel](irc://irc.freenode.net/theodi) (#theodi on irc.freenode.net), check out the [viewer source code](https://github.com/theodi/git-data-viewer), or fork our [test dataset](https://github.com/theodi/dataset-mod-disposals) and send pull requests!
