---
title: A Series of Fortunate Data Analyses | Logic cleanup
layout: post
date: 2018-10-15 16:15:00 -0400
category: ["seneca"]
---

## Mozilla's Overscripted Challenge Aftermath

The prequel to this series on me and my programming partner's first major [data analysis](https://github.com/biskit1/Overscripted-Data-Analysis-Challenge/blob/master/analyses/canvas_fingerprinting.ipynb), `Canvas_fingerprinting`, will be written after these few posts and will be linked later on. This post contains two PRs done for this Analysis during the Hacktober challenge. 

#### **Issue:**

Restructure our Analysis on Mozilla's Overscripted Challenge slightly to make it flow more logically. Adds some extra TODOs as well. Not posted in issues.

#### **Solution:**

Forked my partner in crime [biskit1's](https://github.com/biskit1) repo to add, PR and merge my changes into our analysis. 

#### **Side Issues and their Solutions:**

We ran into a unique problem in which we couldn't particularly work with Git style branch your fix -> then merge on master due to using a [Jupyter Notebook](https://jupyter.org/). It's an interactive note book that contains a mixture of text, code (running on a simulated environment of your choice, such as Python, C++, etc) and visualizations to better explain an idea or share investigations or other information.  

Jupyter is somewhat monolithic, difficult to split and work on with multiple people in Git due to its cells, which are input lines that can be either code input, code output or markdown text. The idea is that you use one notebook to convey your ideas and everything is run inside of it. So the typical branching, fixing and merging doesn't work well due to the sheer amount of diff and merge conflict management that can arrive just doing minor things like changing the order of cells or adding information which can bump into other information in the notebook. 

The actual code of Jupyter that is not human readable is found in a Jupyter specific structured format that is difficult to program in, difficult to view its output and still presents a large merge conflict management issue. 

Our solution was an inelegant one - I was added as an author to that notebook of my partner (before this solution, I was adding my changes to my own version of analysis in a different branch and we were using a different selection of datasets and running into yak shaving issues in general), which gave me merge permissions. I then forked the repo, did my changes and did a PR and merged into it myself. 

It's not great but it gets things done. 

#### **Benefits:**

- Logic flow is important in showcasing work

----

#### **Issue:**

Nobody knows how to install our analysis. Also, a checklist of things to fix up would be great. 

#### **Solution:**

Reinstall our Data Analysis, find some yak shaving and then rewrite the README to include steps for installation. And also opening up wiki to discuss what needs to be finished.

#### **Benefit:**

- Hopefully people can actually run our analysis ~~and be amazed by it~~.


