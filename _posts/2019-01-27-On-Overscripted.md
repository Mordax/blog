---
title: On the Mozilla Overscripted Challenge
layout: post
date: 2019-01-27 8:52:00 -0400
category: [open_source]
tags: [mozilla, open_source, mozfest, jupyter, pandas, dask, overscripted, challenge, apache, spark, competition, javascript, data, science, analysis, big_data, dataset, open_science]
---

This post is a long time coming. This post will probably be in a part of a series.

Back in August 2018, I was approached by my real life friend [biskit1](https://github.com/biskit1) about a competition Mozilla was hosting called the [Overscripted challenge](https://challenges.mozilla.community/overscripted/). 

> Side note: She wrote a fantastic blog post on it, [found here.](https://medium.com/@chayadanz/mozilla-overscripted-shared-resources-and-collaborative-innovation-d1a5d454747b)

Using a trove of crawled data, 70GB in total, we had to make a [Jupyter Notebook](https://jupyter.org/) outlining observations found in the dataset. This crawl had gathered information of the types of Javascript calls being made by thousands of websites and Mozilla was (and still is) interested in what unseen things were happening behind the scenes of the Web. Repo can be found [here.](https://github.com/mozilla/overscripted)

We were lucky- a previous group had already made some good analyses that we could follow along with, such as eval calls, cryptojacking, and so forth. They've got a [repo as well](https://github.com/mozilla/UCOSP-winter-2018_TrackingTechnologies). Discussing our methodology is beyond the scope of this particular post - I will most likely discuss it at a later time.

This competition had been ongoing for roughly a month and we had joined when there was 2 weeks to spare (and later it was extended last minute which gave us an extra week). Neither of us were data scientists nor of any scientific background (except my partner who briefly dabbled in biology). We were merely programmers, of a +15 to our C++ ability score.

We had to learn a multitude of things in a short time, including Python, its libraries such as [Pandas](https://github.com/pandas-dev/pandas) and [Dask](https://github.com/dask/dask), [Apache Spark](https://spark.apache.org/) and wrap it up neatly inside Jupyter. We never touched any of the tools before the challenge.

When we did a hackathon back in January 2018, we did a bunch of research and programming for a project. But in the end we were too disappointed with what we made to submit it. And for students anxious about having side projects, it was a heavy blow. So for this challenge I told my partner-in-crime that we had to put something up. No matter how ugly, how much we hated it, how juvenile we felt it was, how broken. It was going up no matter what.

---  
<br>
[<img src="{{ site.baseurl }}/assets/img/canvas.png">](https://github.com/mozilla/overscripted/blob/master/analyses/2018_09_biskit1_mordax__canvas_fingerprinting.ipynb)
> <p style="text-align: center;"> Our precious analysis</p>

<br>

My older brother (blessed he is) taught me a very important lesson when I was younger - if you don't answer the right question properly, it doesnt matter if you have the best answer in the world. If you dont follow the instructions, it is worth nothing. That lesson made sense to me now. So I meticulously made sure we covered every minutiae mentioned in the challenge rules, including the fact that we must do a pull request, have our emails included, mention which topic to submit to, and so on.

In the end we were the only people who properly submitted their analysis. There were more than a dozen people who had forked the challenge repo - one even finished their analysis. The rules even said, one winner from 3 topics posted would win. That person could've won, but they didn't follow the instructions all the way to the end. There was another group that mentioned that they were working on it and requested an extension. They also never submitted in the end sadly. 

And the prize was an all expense paid trip to Mozfest 2018 in London, England.

I was certain that they would call off the contest due to the lack of participants. At least we had a unique personal project. The contest ended in September and I put it out of my mind. That is until October.

And we then got the email that we were being invited to Mozfest.

**The utter elation I felt cannot be replicated in writing.** 

The only catch was that Mozfest was happening on October 26 to 28 and the amount of last minute planning I had to do for the two of us was crazy. We also extended the trip since neither of us had gone to London and 3 days wouldn't leave enough time to go sight seeing. 

I may write about my observations and enjoyment in London in a different post. We got to meet the people who were kind enough to review our analysis on Github - it was a surreal experience. 

Mozfest was a very personal experience and an important professional experience. I had yet to be recognized for any software work I had done and it came at a time where I was struggling a lot.

> The lesson I'd want others to take from this post is that both showing up and putting something up is vital.

* You can say that you're working on the project, you need more time or you can watch from the shadows. You can have a completely done project saved on your hard drive. **None of it means anything if you don't show up when it counts.**

* You can do hours of prep, research and other initial investigations. You can write lines and lines and lines of code. You can have sleepless nights, hours of debugging time. **None of it means anything if you don't show what you've made.**

* You can hate what you've made with every fiber of your being, excuse it as school homework that no person in their right mind would like, say that it's the ugliest code known to humankind. **Put it up anyways.**

* You may have put it up, and done the work and showed it off to your friend. Maybe everyone on the internet saw it, loved it and thinks you deserve first place. **None of it means anything if you didn't follow the instructions.**

`The great thing about code is you can always go back and improve it if you really need to. The important thing is having something that you can even improve in the first place.`



ᕕ( ᐛ )ᕗ

---
<br>

Special thanks to the following folks for making this trip so very special to the both of us - 

* Martin Lopatka
* Rosana Ardila
* Konstantina Papadea
* Sarah Bird
* David Zeber
* Vivian Jin
* Ben Miroglio  

And everyone else we managed to encounter on this awesome trip!