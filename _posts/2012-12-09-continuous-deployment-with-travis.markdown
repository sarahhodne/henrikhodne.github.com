---
layout: post
title: "Continuous Deployment with Travis"
---

After I launched Travis Lite last week, it didn't take long before I got the [first pull request][first-pr]. The day
after I got [another one][second-pr]. And [another one][third-pr]. Anyways, I'm often out and about and reading GitHub
messages on my phone, and while I could merge in the changes, I couldn't immediately deploy them (well, I could, but
SSH is not exactly ideal to work with on a phone). I wanted a way for the site to be deployed immediately if the Travis
build passed.

[first-pr]: https://github.com/henrikhodne/travis-lite/pull/2
[second-pr]: https://github.com/henrikhodne/travis-lite/pull/6
[third-pr]: https://github.com/henrikhodne/travis-lite/pull/7

I remembered someone writing about this in a Travis issue earlier, and sure enough, after a quick search I found [this
article][metabates-deploying] by Mark Bates on deploying to Heroku from Travis. It was just what I needed. There were
a few things I wanted to change, though:

[metabates-deploying]: http://metabates.com/2012/10/23/deploying-to-heroku-from-travisci/

- Everything was placed in the .travis.yml file. I like to keep my .travis.yml file as clean as possible.
- It put the Heroku API key in clear text.
- It clears all of the SSH keys when it's done.
- *Every* passing build gets deployed. Even pull requests.

After making a few updates, I came up with [this][continuous-deployment-commit]. It makes sure that we're not testing a
pull request, that we tested on 1.9.3 and that we're testing on master. If all of these things are true, and the test
passed, we deploy. I encrypted the Heroku API key using [secure environment variables][], and extracted the entire
script to `script/deploy`.

[continuous-deployment-commit]: https://github.com/henrikhodne/travis-lite/commit/006e246c86efcd9eb70aea7bfe1100be8c7a1ebb
[secure environment variables]: http://about.travis-ci.org/docs/user/build-configuration/#Secure-environment-variables

I guess time will show if continuous deployment is a good idea. At the moment, Travis Lite is a very small project, and
deployment is a very easy process. If you need to do more advanced things, like running migrations, this may not be a
good idea.
