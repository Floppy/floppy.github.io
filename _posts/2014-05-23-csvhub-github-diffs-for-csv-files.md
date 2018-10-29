---
title: CSVHub - GitHub diffs for CSV files
attribution:
  copyrightHolder:
    name: Open Data Institute
    url: https://theodi.org
  license:
    name: CC BY-SA 2.0 UK
    url: https://creativecommons.org/licenses/by-sa/2.0/uk/deed.en_GB
categories:
  - odi
  - github
  - git
  - data
  - csv
---
![null](http://bd7a65e2cb448908f934-86a50c88e47af9e1fb58ce0672b5a500.r32.cf3.rackcdn.com/uploads/assets/7f/3c/537f3c4b1f986a085f000010/Screen_Shot_2014-05-22_at_21.24.46.png)

Over the last few months, I’ve spent some time working on how we collaborate on data publishing, particularly when using [GitHub](http://github.com), an integral part of our software development process.

I wrote a couple of articles last year about [how git could be used for data](http://theodi.org/blog/adapting-git-simple-data), and came to the conclusion that rendering of CSV diffs was an important feature that was needed. Using Paul Fitzpatrick’s brilliant [daff](https://github.com/paulfitz/daff) library, I put CSV diffs into GitLab (an open source GitHub clone), but then again most people aren’t using that.

Shortly after this, GitHub added CSV viewing support in their web interface, which is fantastic, but still doesn’t handle changes well.

Well, this week was innovation week again, and my colleague Stuart came up with the suggestion of putting the CSV diff capability we did for GitLab into a browser plugin that would work on the main GitHub site. This seemed like an excellent idea.

In the end, it was pretty easy, and version 1.0.0 is now released! If you’re running Chrome, you can install it from the Chrome Web Store by clicking below:

[Install CSVHub now!](https://chrome.google.com/webstore/detail/csvhub/dbemglgpbebafkibfncdpdmdikacingf)

It will let you see additions, deletions and modifications per-cell, in both commit views and pull requests.

Want some examples? Install the extension and take a look at these:

*   [theodi/test-data](https://github.com/theodi/test-data/commit/9f391e6e35963b96aa0eed56c20ccd70f326e1f7)
*   [datasets/s-and-p-500-companies](https://github.com/datasets/s-and-p-500-companies/commit/e64871e745a0d34ec3a0ae1b702886a1925d4cdf#diff-fc13dde00d8f846b940d1524b58652f9R269)
*   [datasets/gold-prices](https://github.com/datasets/gold-prices/commit/92d91c206a3b5ab2b4bb74575409eff1221d31cb)

It’s open source, of course, so if you want to contribute improvements, or find any errors in it, you can visit the [GitHub repository](https://github.com/theodi/csvhub).

And, if you’re from GitHub, I would dearly love to have this built in to the main site. I’ve even written you a [Ruby port of the daff code](https://github.com/theodi/coopy-ruby) so you can do it all server side. Go on, you know you want to!
