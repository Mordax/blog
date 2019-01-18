---
title: On Hubs and Apache
layout: post
date: 2019-01-18 13:57:00 -0400
category: [seneca]
tags: [mozilla, open_source, hubs, apache, httpd, http, server]
---

After a time of hunting, I've narrowed down some bugs I aim to tackle. 

#### **Side Observations:**

What's interesting is that I didn't expect [Hubs](https://github.com/mozilla/hubs) to be so easy to build (again,  abused windows dev here). And I realized later that because Hubs is so new, the impact of fixing the bugs goes further. Most of the bugs really affect the core use of the project as opposed to small changes/enhancements that I'm used to doing that get somewhat buried deep inside. Although I've seen this with my [supernova](https://github.com/0xazure/supernova) work, it still a slight surprise seeing that this is the case even with a project maintained by Mozilla.

On the other side, I didn't realize how difficult it would be to hunt down a good, introductory bug in [Apache httpd](https://httpd.apache.org/). Although, potentially with the upcoming [HTTP/3 release](https://en.wikipedia.org/wiki/HTTP/3) there will most likely be lots of new bugs due to probable compatibility issues. But so far, the project is like a finely aged wine, where the bugs are so advanced it's like reading [Linear A script](https://en.wikipedia.org/wiki/Linear_A) (be prepared for more historical references in my future blog posts, cringey as they may be). 

### **The Issues:**

Two of the issues are meant for easing into the project community.

* [Hubs doesn't load if you import a custome scene](https://github.com/mozilla/hubs/issues/811)  
    This bug will require some back and forth on whether to remove the ability to import scenes or modify it so that it loads. Currently Hubs uses prerendered rooms. Unless the Sketchfab model is built in [Spoke](https://github.com/MozillaReality/Spoke), there's no other way to have custom rooms. This could also be a potential upstream/downstream/sidestream discussion as well. 
 
* [Add a debug line in httpd if instruction provides invalid path](https://bz.apache.org/bugzilla/show_bug.cgi?id=63079)  
    This will require doing some code reading, asking questions and looking at how other debug lines inside httpd are coded. I'm looking forward to immersing a little bit deeper into a community and learning from some battle hardened programmers.

The last issue is a more complex enhancement that works with a fundamental use case in Hubs.  

* [Enhance Hubs chat so that its more intuitive - potential to be split into new bugs](https://github.com/mozilla/hubs/issues/810)  
    This will also require some back and forth. The simpler thing to tackle is just making the chat area more visible - the harder thing is to implement chat history, understanding what use cases meeting organizers need to have to encourage using Hubs versus something traditional like Skype and also consider limitations of using VR peripherals.

#### **Conclusion:**

The next steps for hubs is to start working on the bugs. And for the httpd project, to actually manage to build it and have a running server spun up. And this time around I'll need figure out a good way to conscientiously document the process while I'm going through with it for potential document contributions in the future.

