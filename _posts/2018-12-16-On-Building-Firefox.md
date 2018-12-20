---
title: On Building Firefox
layout: post
date: 2018-12-16 19:48:00 -0400
category: ["seneca"]
---

#### **Preamble**

[Firefox](https://www.mozilla.org/en-US/firefox/new/) is one of those classic open source projects, alongside the Linux project, that are massive in scale and have also been around for a long time. 

The more you enter the open source ecosytem, the more its inevitable that most of your time will be used up on relatively newer frameworks and software systems.

Sadly, I've noticed with a lot of newer frameworks, due to their lack of maturity, tend to be buggy, and documentation hard to deal with. As opposed to building projects within it, I'd find myself debugging the environment itself.

Firefox was the most enjoyable environment I've ever set up and worked in. ASP.NET was the only comparable experience I've had. 

The reason for this preamble was to emphasis just how wonderful it is to work in a mature code environment. Even though I'm a Windows user [life of a PC gamer is hard], it was still quite smooth. 

----

#### **Introduction**  

A [list of limited bugs](https://bugzilla.mozilla.org/buglist.cgi?status_whiteboard_type=allwordssubstr&query_format=advanced&status_whiteboard=%5Bseneca-eslint%5D&list_id=14476024) had popped up over at [Bugzilla](https://bugzilla.mozilla.org/), and our particular class was in a lucky position to work on it. In a series of overwhelming myself with opportunities and seeing if I can deliver, I made my interest clear immediately. 

[Mark Banner](https://mozillians.org/en-CA/u/Standard8/) had kindly offered to mentor the bugs. They were all regarding turning on ESLint rules on various folders in the Firefox code, both automatically fixing issues and also manually going in and fixing them. 


#### **Issue**

[Enable ESLint for dom/base/test/chrome and dom/base/test/unit.](https://bugzilla.mozilla.org/show_bug.cgi?id=1508983)

#### **Steps and Side Issues**

A lot of the initial steps were mentioned via email by my prof, [humphd](https://blog.humphd.org/) and expanded on by Mark, and I will do my best to remember and reiterate the steps. Also note that these instructions use Mercurial, __not__ Git. Git has different instructions.

- [Build Firefox for the Desktop](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Build_Instructions/Simple_Firefox_build#Building_Firefox_for_the_Desktop) - These instructions are for building on Windows 10, but can be modified to suit your OS. Just follow Mozilla's documentation closely.
   - Install VS 2017 Update 8
   - If already installed, find and launch the Visual Studio Installer and hit modify
   - When installing or in the installer, check `Desktop development with C++` and `Game development with C++` from the list **BUT**
   - __Potential trip up__ - When you check the above, examine the optional details of the installation and make sure the following is checkmarked (when you click back and forth between the main options, it unchecks it for installation automatically):
      - `Windows 10 SDK for Desktop C++ x86 and x64` - minimum version supported is 10.0.15063.0 and be mindful that it's both x86 and x64.
      - `Visual C++ ATL support`
      - `Windows 10 SDK` - min. 10.0.10240.0
   - Download [MozillaBuild](https://ftp.mozilla.org/pub/mozilla.org/mozilla/libraries/win32/MozillaBuildSetup-Latest.exe) (actual download link). This will make a new installation directory called `mozilla-build`. This a bat shell that looks like the Command Prompt.
   - Make a new directory called `mozilla-source`.
   - Run `hg clone https://hg.mozilla.org/mozilla-central` in the new directory
   > Here's where it got more tricky for me. I come from a Git background. Mozilla uses [Mercurial](https://www.mercurial-scm.org/). It's actually not that different from Git but there's always some growing pains for learning a new tool.  
   - cd into `mozilla-central` (directory where hg cloned into) 
   - Run ./mach bootstrap
   - Select the `Firefox for Desktop Artifact Mode` option
   -  If you want to actually run Firefox, in mozilla-central, add a file called .mozconfig with the following one line content:
      - `ac_add_options --enable-artifact-builds`
   -  Run `./mach build`

- Remove the directory that you want to enable ESLint on from the .eslintignore file
- Run `./mach lint --fix eslint path/to/directory ` where path/to/directory is the path to the directory you're enabling ESLint on.
- If you want to see the errors show up without fixing or to check your work, run `./mach lint -l eslint path/to/directory` . This [Mozilla doc](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/ESLint) is very helpful.
- Commit the automatic fix to Mercurial - `hg commit -m "Bug nnn - Enable ESLint for path/to/directory (automatic changes)"` Where nnn is the bug number in bugzilla for your issue. **BUT BEFORE YOU DO THIS**, do not include .eslintignore in this initial commit for a smoother patch submission. 
   - You can use `hg status` to view modified files that will be incorporated in a commit, like in Git. 
   - If you see .eslintignore, add to the above command after hg commit - `-X '.eslintignore'` this will remove it from the tracked files.
   - Also, be mindful - if you put a # before the bug number (which a lot of us did), the submitter later on won't be able to submit it due to it not handling the #. 
- Re-run `./mach lint -l eslint path/to/directory` to see the remaining problems
- Go in and manually solve them. I may talk about this some other time, out of scope for this post.
- Do another commit `hg commit -m "Bug nnn - Enable ESLint for path/to/directory (manual changes)`
-  Submit to Phabricator via [Moz-phab](https://github.com/mozilla-conduit/review). Mozilla has a [doc](https://moz-conduit.readthedocs.io/en/latest/phabricator-user.html) Some issues I noted with Moz-Phab:
   - You need PHP, Arcanist and Moz-Phab in your path. If you're on Windows 10, running via the Mozilla start shell, everytime you relaunch it, you have to do the following commands  
```bash
export PATH="${PATH}:/pathto/phabricator/review-1.8"   
export PATH="${PATH}:/pathto/phabricator/arcanist/bin"  
export PATH="${PATH}:/pathto/PHP"  
```
where pathto is the folders where it takes to get to the location of the bins. Be mindful to use absolute not relative location. And for some reason, even if the bins are in the Windows path via Environmental variables, the Mozilla shell doesn't sense them. I think this has to do with the fact that the `export` command is a Linux based command, while Windows uses `set` path instead. I think this may be a bug.
   - Something I've noticed is that if you are not meticulously reading the Phabricator user docs, and not clicking away to look at each link that relates to setup (like Arcanist), it's very easy to make mistakes. That's out of scope for this post - I may go in there and maybe submit some patches. 
   - Learning how mercurial does its commit rollbacks and squashing - `hg histedit` was the most popular command I had to keep running. For some reason, it's much slower than squashing in Git and I had to be careful to allow a good while for mercurial to sense that I had closed the adjustment text. I tend to quickly quit if I sense something goes wrong but I had to be mindful in this case. I'll be checking out their Git for Firefox MDN docs. 
   - Moz-phab kept re-uploading commits I hadn't modified, which would relaunch the Mozilla phabricator bots to check the code. Besides the range option and that doesn't allow you to specify combos like only upload commits 2 and 4.
   
All in all, I actually really enjoyed building and fixing things in Firefox - I was less frustrated as a Windows user than I thought I would be. It can be a bit confusing though - there's multiple locations to work in (bugzilla for issues, mercurial for commits, moz-phab for submission, Phabricator for review). It opens a lot of avenues for potential slip ups.

But other than that, I'm really happy and humbled that I now have code in the browser that I've used ever since I was a kid. 

#### **Benefits:**

Hopefully turning on ESLint in all of these folders can help avoid and potentially fix existing bugs.

Also, it was a great experience for me. I'll definitely return to Firefox for sure!

Here's the links to my (landed!) code:

[dom/base/test/chrome (automatic changes)](https://phabricator.services.mozilla.com/rMCU002907f3b577b9ec1f339c85896f1d1d2983ab06)  
[dom/base/test/chrome (manual changes)](https://phabricator.services.mozilla.com/rMCU61192787a882e30a7c17c3e5b1a7768ee14597b6)  
[dom/base/test/unit (automatic changes)](https://phabricator.services.mozilla.com/rMCUdd6e480be25351f9e291575cb1505a297b60f506)  
[dom/base/test/unit (manual changes)](https://phabricator.services.mozilla.com/rMCU6b3257019239c944cbb551938375617ab7793dcf)  
