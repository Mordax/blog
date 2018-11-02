---
title: Hacktoberfest Conclusion
layout: post
date: 2018-11-01 16:40:00 -0400
category: ["seneca"]
---

## The Conclusion of Hacktoberfest

This is a more personal blog post. I'm kind of bad at personalizing this sort of thing, which is strange since I have done it before in my [depreciated blog](https://mordax.io/deprecatedblog/). I've even changed the intro to that one to reflect my discomfort with it. 

I feel that I always take a particular tone that at the time seems alright, but later I lament as being fake or an attempt to pander to an audience or just not reflective of myself.  

It's difficult to try to be seen as a professional yet at the same time try to encourage others to read by being friendly. Just thought I'd warn you ahead of time.

Either way, let's get into a reflection on [Hacktoberfest](https://hacktoberfest.digitalocean.com/) and my five PRs. 

#### **Issues**
1. Bettering docs for Windows developers contributing to Solidity
2. [Writing an edge test case for Solidity](https://github.com/ethereum/solidity/issues/5103)
3. [Removing unnecessary submodule uses in Solidity](https://github.com/ethereum/solidity/issues/5142)
4. Cleaning up logic in my and my partner-in-crime's Canvas Fingerprinting data analysis
5. Fixing up that data analysis' readme for better installation instructions + making a wiki

#### **Pull Request links**
1. [Windows Developer Solidity Doc change](https://github.com/ethereum/solidity/pull/5181)
2. [Solidity two's complement edge case testing](https://github.com/ethereum/solidity/pull/5213)
3. [Removing submodule use in Solidity](https://github.com/ethereum/solidity/pull/5215)
4. [Cleaning up Canvas Fingerprinting Jupyter Notebook](https://github.com/biskit1/Overscripted-Data-Analysis-Challenge/pull/1)
5. [Improving personal docs for the Notebook](https://github.com/biskit1/Overscripted-Data-Analysis-Challenge/pull/2)

#### **Specific blogs on each PR**
1. [Solidity Doc blog](https://mordax.io/blog/seneca/2018/10/10/Solidity-Docs.html)
2. [Solidity Edge Case Test](https://mordax.io/blog/seneca/2018/10/15/Solidity-signed-type-test.html)  
3. [Removing Submodules from Solidity](https://mordax.io/blog/seneca/2018/10/15/Removing-submodule-mentions.html)  
4. && 5. [Canvas Fingerprinting PR blogs](https://mordax.io/blog/seneca/2018/10/15/Logic-cleanup.html)  

#### **Reflections**  

I worked in two repos during Hacktoberfest.   

One was [Solidity](https://github.com/ethereum/solidity), which is a contract-oriented programming language that utilizes the Ethereum Virtual Machine - a decentralized virtual machine that allows you to execute scripts on the Ethereum connected nodes. 

The other was me and my [software pal's](https://github.com/biskit1) data analysis that we submitted to [Mozilla's Overscripted challenge](https://github.com/mozilla/Overscripted-Data-Analysis-Challenge). Mozilla wanted to demonstrate that science can be collaborative and open sourced. Data science is relatively new and an intersection between science and software. By injecting open source ideas into scientific methods, we just may be able to find some fascinating discoveries. If you are interested in reading more about our foray into data science and how that led us all the way to England, there will be another blog post detailing that adventure.  

----
<br/>

### Solidity  
My experience with contributing to Solidity is a good one. The maintainers are kind, quick to respond and are reasonable and pleasant with their code reviews. I've started to understand a little bit more on how Solidity is structured, however it is still extremely young. There's a lot that needs to be tested and carefully checked to avoid potential bugs that can cause problems on the EVM, especially since it's supposed to be decentralized and safe.   

I went into Solidity worried that my inexperience and potentially unintelligent questions would brand me as a perpetual outsider but the people were great and patient and their code reviews revealed very little that I had to fix. If I had to give advice to other people, it is this: don't overthink too much. And don't be shy to ask a question. The great thing about this industry is that as long as you're willing to learn and work to improve, you will be appreciated.  

The only thing I'd change about my experience with Solidity is just asking for clarification - although I figured it out on my own in due time, it was still a good chunk of time wasted that could've been put towards something more productive. We tend to say in the field to "Google it" and StackOverflow isn't exactly very welcoming in questions that could be answered after some hunting. But besides the obvious trolling or questions that could immediately spring up in Google if they bothered, take it as a potential documentation improvement. Getting clarification saves you time, lessens the amount of stress and anxiety, and helps other people who run into that problem.  

-----
<br/>
### Canvas Fingerprinting Analysis  
I personally think I slightly cheated on this one. I was finishing up Hacktober as fast as I could due to the fact that I had a last minute trip planned and that it was tied into an assignment. Me and my software pal had to present this analysis and I thought it would be great to fix up some things in our repo. 

I think the maintainers were just immaculate beings of incredible software prowess that even the transistors bow down to them. Also, it was almost instantaneous in how quickly my pull requests were merged. They really work hard to the point that I don't think they sleep. How do they accept my PRs so fast?  

Jokes aside, I think what I would do differently is take the time to ask more questions to the Mozilla folks who reviewed our code, and do some time management so that we can continue improving our analysis. 

-----  
<br>

#### **Conclusion**  
Hacktoberfest was my first foray into an online global challenge. I think it was a great incentive to contribute to projects that perhaps you may be a bit too intimidated to try. I think what Digital Ocean is doing is a great way to encourage more activity in the sphere of open source. The best way to have excellent software is to have passionate programmers dedicating their time to helping improve it.   

And of course - all developers love free T-shirts.