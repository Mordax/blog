---
title: Solidity Chronicles | Removing Submodules
layout: post
date: 2018-10-15 16:15:00 -0400
category: ["seneca"]
---

## Removing Submodule Mentions

This is probably going to be a shorter post. 

#### Issue:
[Remove mention of submodules from Docs and build scripts](https://github.com/ethereum/solidity/issues/5142)

#### Solution:
 - Remove mention from documentation on building from source [here](https://solidity.readthedocs.io/en/latest/installing-solidity.html#clone-the-repository). If you're interested in what it said before, see the previous versions of the docs. 
 - Remove mention from the build lists:
    - From appveyor.yml
    - And this file was seperated to handle an unforseen build break: scripts/create_source_tarball.sh

#### Benefit:
 - Reduces code that needs to be run
 - Reduces chances of bugs
 - Cleans up documentation.

Here's the [Pull Request](https://github.com/ethereum/solidity/pull/5215). And it was merged, happily.