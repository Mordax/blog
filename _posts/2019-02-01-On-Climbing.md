---
title: On Climbing a Mountain
layout: post
date: 2019-02-01 11:15:00 -0400
category: [seneca]
tags: [mozilla, open_source, hubs, apache, httpd, http, server, chat, box]
---

I underestimated my task. 

I had made a post on the [open source projects I wanted to work on](https://mordax.io/blog/seneca/2019/01/18/On-Hubs-And-Apache.html), and I vastly underestimated the learning curve meant for the projects.

Regarding Apache HTTPD - I had assumed after the longevity of the project that it would be as straightforward to build as [Firefox was](https://mordax.io/blog/seneca/2018/12/16/On-Building-Firefox.html). However, the nature of my x64 Windows machine and my VS studio 2017 tools meant that most of the instructions that were geared to older VS tools were greatly outdated. 

The yak shavving involved in getting it set up was overwhelming. I'd have to generate several makefiles for several utilities outside of httpd, and my makes would constantly complain about Windows issues. 

I spent more time figuring out why it wasn't building than actually doing my bug. And even so, I thought that I would be able to produce a nice, simple Windows 10 build walkthrough if I stuck with it.

I was unable to. I would get extra information found in different documentation, different community comments and each time, would run into problems unique to my environment. I even had a markdown sheet open, ready to document the steps, yet the amount of new information that would pop up would have me step backwards, rewriting that sheet multiple times.

However, my next steps may be to try a user made tool found on [Bitbucket](https://bitbucket.org/wagnersolutions/apache-2.4-build-windows); actually reaching out and asking someone in Apache to walk me through the build,either to call it quits and try to build it on a Linux VM, or scale back and try a less complicated Apache project. 

---
<br>

Regarding Hubs, although the code was well structured and easy to discern what code related to what portion of Hubs, my bugs had turned out to be fully fledged features that make a lot of visual changes to the software. I'm used to not needing to completely understand a lot of the code in a project, even with Ethereum, however in this instance, the bugs really relate to core functions (like creating new rooms, redirecting to other pages, storage etc.)

I managed to do a PR [(found here)](https://github.com/mozilla/hubs/pull/862), but that is just the tip of the iceberg for that particular issue. It's a bug that requires layers of work, back and forth, and discussion on core directions. And the other hard part, I'm unsure of where I can get more real time discussion going. The slack has been left for Discord and the one invite I found had been expired. 

How I fixed this bug - had to heavily rely on the inspector tool - because this was a visual change (making the chat more visible when you enter it), which is done using [Sass](https://sass-lang.com/) (which I've never had to work with before). It was a bit of hunting for the particular object, making it more opaque but still having a nice transition, and observing that they had a shared sheet with predefined colours used throughout Hubs (which made my job easier) and changed it to be clearer than the transparent chat box they currently have.

The next steps would be to sit down and just read as much relevant code as I can, read up on Aframe and various other components that Hubs uses so I can truly understand how Hubs rooms really get built.



