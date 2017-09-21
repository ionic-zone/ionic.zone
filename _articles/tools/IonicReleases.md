---
title: IonicReleases
date: 2017-09-21 14:00:00 +0000
published: true
last_updated: ''
parent: ['Tools', '../tools']
---
# @IonicReleases - An Ionic Github Releases Twitter bot

Ionic development is distributed to lots of [libraries](/TODO) and [repositories](../understand/ionic-github-repositories). It also tends to move very fast at times, with simultaneous releases of different parts. This can make it quite challenging to know what is going on and to find about about new releases or bugfixes in a reasonable time.

That's why I created the [Twitter account @IonicReleases](https://twitter.com/IonicReleases) that tweets each time a new release for any of the important repositories on Github gets tagged and released:

<a class="twitter-timeline" data-height="800" href="https://twitter.com/IonicReleases">Tweets by IonicReleases</a> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## How it works

The bot is a combination of features from Github, Zapier and Integromat:

1. At [Zapier](https://zapier.com) a "Zap" combines a list of Github releases RSS feeds (e.g. [ionic-team/ionic/releases.atom](https://github.com/ionic-team/ionic/releases.atom), [ionic-team/ionic-native/releases.atom](https://github.com/ionic-team/ionic-native/releases.atom)) into [one big RSS feed and publishes it](https://zapier.com/engine/rss/2208489/ionic-github-releases).
2. Then at [Integromat](https://www.integromat.com/) a "Scenario" retrieves this feed. If there are new items it composes a string out of the available data (repository name, which is not directly available in the RSS feed) and combines it with other available data from the RSS feed to a tweet text, mentioning the repository that got the release and linking to the release notes. It then sends that text as a tweet (and and email directly to me) at the [@IonicReleases](https://twitter.com/IonicReleases) account: 

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">New &quot;Ionic&quot; Release: 3.5.3 <a href="https://t.co/nY7bbz32Ru">https://t.co/nY7bbz32Ru</a></p>&mdash; Ionic Releases (@IonicReleases) <a href="https://twitter.com/IonicReleases/status/885928172755267585">July 14, 2017</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I had to combine Zapier and Integromat to get this functionality working as both only have part of the required features. Nice side effect is that both services can handle that with their free accounts.