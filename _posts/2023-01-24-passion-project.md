---
title: The rise and fall of a passion project
subtitle: On the importance of documenting your work
author: Alex Mazansky
layout: post
excerpt_separator: <!--more-->
---

In mid-2020, life was very different than it is now. The world was a few months into the pandemic, so like many other students interested in computer science with little else to do, I started working on passion projects. This post will describe one of those endeavors, and through the story of the project's rise and fall, I will relay an important lesson I've learned about work and memory over long periods of time.<!--more-->

Having been stuck at home for months already, I had quickly taken to listening to music on Spotify as a way to pass the time. As I became increasingly familiar with the platform's capabilities, I found that there were a few things I really wanted the app to be able to do, that it just couldn't at the time. The two main features I wanted were:

- The ability to see a list of songs I most recently played
- A way to change the cover image of a playlist from a mobile device

By deduction, I figured that Spotify definitely had the technical capability to implement both of these features. After all, if the much-beloved Spotify Wrapped tells users how many times they listened to a song in a given year, the app had to be keeping track of when people listened to what, so it should be pretty trivial to list the last few dozen songs a user played. Same story with the second feature: users could already change playlist cover images on the desktop client, so it should be easy to make a way to do it on mobile.

At around the same time as I wondered why these features hadn't already been implemented, I found out about the [Spotify Web API](https://developer.spotify.com/documentation/web-api/reference/#/). After browsing through the docs, I noticed that the two features I wanted were already available as API endpoints! In other words, while Spotify hadn't made these features part of the app yet (although I suspected they would soon),[^1] they *were* available to anyone who knew how to write code to send specific web requests off to the API. As someone who did indeed know how to send said requests, I set out to make my own front-end user interface for the missing features. I created a new git repository, fired up my code editor, and got to work. And thus, [TuneUtils](https://github.com/amazansky/TuneUtils) was born.

I decided to use PHP for this endeavor. While I am indeed aware of the [many criticisms](https://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/) against the language, this project was just meant to be a quick and dirty fix to some problems that Spotify was already likely in the process of solving natively. (And don't worry, I also took the free time during the pandemic as an opportunity to start learning some alternatives to PHP.) A few days later, I had coded up interfaces and API calls for the two features I wanted. I went on NameCheap and bought the domain tuneutils.com, spun up a free Heroku Dyno to host the website, and set it going. I told some friends about my project, and it seemed they found it useful too, since I checked Spotify's developer dashboard shortly after releasing the website and it had already received a few dozen API calls.

I had plans to code a few more features such as a way to compare two users' music taste based on the songs they frequently listened to, or a way to sort a user's playlist based on Spotify's AI-determined metrics of its songs.[^2] But as always happens sooner or later in the lifecycle of a passion project, I got busy again at the start of the school year, and I had to stop working on TuneUtils. While I left the website up for people to use, I wasn't actively developing it anymore.

By the time 2021 rolled around—just a few months after I launched TuneUtils—both of the features I originally set out to make interfaces for had been addressed natively in Spotify's clients.[^3] So when the tuneutils.com domain came up for renewal in September 2021, I decided that it probably wasn't paying for another year. But I still wanted to keep the site around to showcase my work, so I migrated TuneUtils to a [subdomain of the personal domain](https://tuneutils.amazansky.com) I used at the time. A few config changes and a git commit later, and things were up and running again for another while.

That was until earlier this month (January 2023), when someone contacted me to let me know that one of the links on my projects page was broken. Curious, I checked it out and indeed, the TuneUtils website link landed at a Heroku page that indicated the site hadn't been set up. I tried to log into my account to see what was up, but it said my login credentials (which I knew to be correct since they were stored in a password manager) weren't valid.

A little worried about my account, I searched my email for "Heroku" and quickly figured out what was going on. It turned out that I had been given ample warning about the issue, meaning the blame was squarely on me for this, but Heroku's cries had fallen on deaf ears as my account notifications were set to land in an email inbox I don't actively monitor. Whoops.

The problems I faced were threefold:

1. Heroku was ending support for the version of PHP that TuneUtils used. This was no big deal, since I could just upgrade it, right?
2. They were also ending support for free Dynos, which TuneUtils ran on. This meant I would either have to switch to a different hosting service or start paying to keep using Heroku.
3. Since I hadn't logged into my Heroku account for over a year, it was automatically deleted in accordance with Heroku's data protection policy.

Well, at least that explained why I couldn't log in.

At this point, I contemplated my options. I could either archive the project and take it off the web for good, or I could get things running again for another little while. Since I still wanted something to show for my work, I got to setting everything back up again. I made a new Heroku account, activated the Heroku platform credits from my [GitHub Student Developer Pack](https://education.github.com/pack/), got my PHP version up to date, and re-deployed TuneUtils.

Problem solved for now, but what happens next January when my credits expire? I'm not sure yet—it'll depend on a few factors: whether I've done any additional work on the project, my capacity to get things running again at the time, and whether I still feel the need to have the site online. But what happens if I don't? Will the record of TuneUtils live on at all, or will it fall by wayside as an abandoned and forgotten project?

Unfortunately, I've learned the answer to this question the hard way. One too many times, I haven't been careful enough about storing records or code relating to projects I've worked on, and then when I tried to find my work later, I came up short. For example, a few years ago I worked on a case involving social media location records, for which I coded a data visualization using Mapbox. When I tried to search through my computer files a while later for anything related to the case so I could show someone else my work, I found nothing. Maybe the files are still sitting somewhere on my hard drive and managed to evade my queries; maybe they truly are lost forever, and the only record of my ever having worked on the project is the memories of those who saw the results.

But that's just one example, and I've had several others. In fact, even some aspects of TuneUtils—the subject of the very blog post you're reading right now—have been lost to time since I first developed it. Like the API usage data in the Spotify dashboard I mentioned earlier. That data is only saved for the most recent few months from the time of access, and since I never screenshotted or downloaded it, now I have no record of people ever having used the site.

That brings me to the importance of documenting the work you do. And when I say "documenting" in this case, I don't mean writing comments in your code (although that is certainly an important practice as well, and one worthy of every developer's time and attention). I mean the idea of recording and saving information relating to your projects' *existence, development, and lifecycle*. For many reasons, the material you save can turn out to be very useful down the line. And while documenting takes a little extra effort during the process of making something, it can turn out to pay dividends when you need to find records quickly later.

This is all to say: sometime between now and next January, I need to prepare for the possibility that I won't want to keep TuneUtils online for yet another year. I'll need to take screenshots of the website to put in the readme of its git repository when I archive it, and I'll need to download the site's Spotify API usage data (if, for some reason, anybody decides to use the site in the next year). Equally as importantly, I'll need to store all those records somewhere that I'll remember,[^4] since having information that you can't find is pretty much as good as not having it at all.

So while this process will take some extra time and effort on my part, I've decided that I'm okay with that.

[^1]: I'll get to the details later, but both features were ultimately implemented within a few months of my creating TuneUtils.
[^2]: If you're curious about these metrics, you can read my [other post]({% post_url 2021-03-09-mood %}) describing how I made a mood tracker out of them.
[^3]: From a cursory internet search, it seems that recently played songs went into beta around [October 2020](https://www.businessinsider.com/guides/streaming/how-to-see-spotify-listening-history), and changing playlist cover art from mobile was released around [December](https://newsroom.spotify.com/2020-12-08/how-to-upload-a-custom-playlist-image-using-your-phone/).
[^4]: Stay tuned for a post on this blog (whenever I get around to it) about my new plan for keeping information like this accessible for a long time to come.
