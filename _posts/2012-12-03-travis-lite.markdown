---
layout: post
title: "Travis Lite"
---

Lately I've been going through a lot of the issues in [Travis CI][travis-ci]'s issue tracker. After seeing a lot of issues
being closed (and closing several myself), I see some things being requested a lot, but that just aren't something that
would fit with Travis (at least not right now). One of those things is a more light-weight client.

The Travis CI web client is one of the reasons I love Travis as much as I do. There's no need to refresh, you just go
to your repository page and see the build stream in as you (or someone else) pushes commits. However, not all browsers
and computers can handle such a JavaScript-intensive page.

This inspired me to create a more light-weight version of the Travis webpage, and I'm happy to announce that it is now
live: [Travis Lite][travis-lite]. Travis Lite is built on the [Travis CI API][travis-api] that the Travis team has been
awesome enough to provide.

Travis Lite is still a work in progress, but you can see the list of the latest builds, as well as the latest builds
for a repository. The goal is for all of the Travis URL endpoints to be implemented, so you can just replace the
"travis-ci.org" part of the URL with "travis-lite.com".

The app is [open source][travis-lite-github], and contributions are greatly welcomed.

[travis-ci]: http://travis-ci.org/
[travis-lite]: http://travis-lite.com/
[travis-api]: https://api.travis-ci.org/
[travis-lite-github]: https://github.com/henrikhodne/travis-lite
[henrikhodne]: http://twitter.com/henrikhodne
