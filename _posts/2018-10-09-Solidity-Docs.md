---
title: Solidity Chronicles | Documentation for Windows Developers
layout: post
date: 2018-10-09 20:43:00 -0400
category: ["seneca"]
---

## Short chit-chat about Ethereum

Solidity is a programming language based on contracts as opposed to objects and is the backbone for making applications that run
on the Ethereum blockchain. [Ethereum](https://www.ethereum.org/) is (during the time of writing), the second most popular cryptocurrency
after Bitcoin. 

If Bitcoin is a speculative gold currency, Ethereum is the up-and-comer hoping to fulfill the original dream of decentralization.

Writing programs in Solidity and producing decentralized applications is not an easy feat. Ethereum was created in 2015 which is extremely young for a technology.
Bitcoin, by comparison, was made in 2008, however it currently can only handle simple programming scripts.    

What this means for Ethereum is that any tutorials written for it get outdated extremely fast. Already certain important tools like Testrpc that emulate the blockchain for private testing have been renamed to [Ganache](https://truffleframework.com/ganache). 

Thinking in terms of blockchain applications is complicated. Even the traditional Hello World becomes confusing in Solidity. Writing the code is simple, seeing the Hello World in action is not.  

Some terms for my own memory and maybe yours (and potentially to keep updating):

| Term | Definition |
| ---- | ---------- |
| [Solidity](https://solidity.readthedocs.io/en/latest/) | A contract-based programming language similar to C/C++ (has structs and the like.) Most popular contract language at the moment. You can make your own defined coins and immediately compare it to Ether. |  
| [Dapp](https://en.wikipedia.org/wiki/Decentralized_application)  | A decentralized application running on top of the Ethereum blockchain is the common explanation, but it doesn't have to be Blockchain or Ethereum based.|  
|[Ether](https://www.ethereum.org/ether) | The actual crypto money used in Ethereum that you can exchange, mine and watch on the market.| 
| [Gas](https://www.investopedia.com/terms/g/gas-ethereum.asp) |  Here's where the complexity of Ethereum begins to add up. Gas is a seperate, monetary calculation to pay out the blockchain as a thank you for running your Dapp. Helps allocate resources and hamper spam on the Blockchain network.|   
|[Gwei](https://gwei.io/)| The smallest denomination of Ether you can get. Equivalent to the idea of a penny.|   
|[Vyper](https://vyper.readthedocs.io/en/latest/) | A competing contract similar to Python that has some interesting differences.  
|[Ganache](https://truffleframework.com/docs/ganache/overview)| Formerly TestRPC, now part of the Truffle suite of frameworks. A blockchain emulator that spits out premade Ethereum addresses for testing and mimicks mining and other blockchain activities. |
|[Geth](https://github.com/ethereum/go-ethereum/wiki/geth) | Another blockchain/ethereum node emulator but implemented in Golang. Maintained by Ethereum. |  
|[Truffle](https://truffleframework.com/docs/truffle/overview)| A popular framework that generates, compiles and migrates solidity contracts, testing framework and other extras.|  
|[Web3.js](https://web3js.readthedocs.io/en/1.0/)| A javascript API that can interact with an Ethereum node and get all kinds of information from it (version, resets, etc).|  
|[Drizzle](https://truffleframework.com/docs/drizzle/overview)| A collection of front end frameworks for better visualizing contract information and interaction to make a user friendly Dapp. Uses Redux and can integrate with React applications.|  
|[Drizzle box](https://github.com/truffle-box/drizzle-box) | A useful box that unpacks a fully functioning Dapp using Drizzle and Truffle for better clarity of how Dapps work.|   
|[List of Dapps](https://www.stateofthedapps.com/)| A useful website that showcases Dapps for better understanding of current use.|  


Hopefully this list clears up some terms and gives out some useful links.   

---       


#### **Back to the Solidity Documentation.**   

Setting up Solidity for bug fixing on a Windows machine was maybe less frustrating than most projects. There's a very nice [building from source](https://solidity.readthedocs.io/en/latest/installing-solidity.html#building-from-source) explanation for Solidity developers that really cleanly spelled out the setup for all environments. _Personally would recommend doing the building from Command Prompt, except maybe for the git commands._

The issues began mostly during the [contributing part](https://solidity.readthedocs.io/en/latest/contributing.html), where they go into running compiler tests and such. 

Ran into a few Yak shaving issues on this [section](https://solidity.readthedocs.io/en/latest/contributing.html#running-the-compiler-tests) that hopefully either I would open an issue or they will fix themselves:
- Would be nice to split those command into Linux and Windows (and Mac if needed) sections.
- scripts/tests.sh has this error via Git Bash for Windows:  
```bash
$ scripts/tests.sh
Running commandline tests...
/d/solidity
Checking that the bug list is up to date...
/usr/bin/env: ‘python2’: No such file or directory
Commandline tests FAILED
```  
Properly installing Python 2.7 doesn't fix this issue. If I find the answer to this, I will update the post.

---

The command that is supposed to run the tests without any extra application installs is a shell based file:

`./scripts/soltest.sh --no-ipc --no-smt`

Meaning Windows can't run it. Haven't tried it with Cygwin installed but running it on Git Bash fails and gives this error:

```bash
$ ./scripts/soltest.sh --no-ipc --no-smt
./scripts/soltest.sh: line 43: /d/solidity/scripts/../build/test/soltest: No such file or directory
```

I was unable to fully understand why shell scripts don't run on Git Bash because that file certainly does exist, at least in the Solidity folder at that path location.

> **Here's How Windows Developers can run the Solidity tests** 

You have to use the Soltest generated by the Cmake in order to run it. 

**Git Bash for Windows Soltest command:**  
`./build/test/RelWithDebInfo/soltest.exe -- --no-ipc --no-smt`

**Windows Command Prompt Soltest command:**  
`.\build\test\RelWithDebInfo\soltest.exe -- --no-ipc --no-smt`

Hopefully this extra information will shave off a little more of the Yak for Windows Solidity developers. 

The Doc pull request is located [here](https://github.com/ethereum/solidity/pull/5181).
 