---
title: Solidity Chronicles | Signed Type testing 
layout: post
date: 2018-10-15 16:15:00 -0400
category: ["seneca"]
---

## Delving into the backbone of Solidity

Making a simple Solidity unit test.

#### **Issue:**

Here's the [issue](https://github.com/ethereum/solidity/issues/5103) that popped up in Solidity. This is a request 
for testing this particular edge case:
```c
int x = -2**255;
assert(-x == x);
```

The maintainer references this [comment](https://github.com/ethereum/solidity/pull/5087#discussion_r220715840) in another issue, where someone contributed a doc change 
to solidity. From the [doc page:](https://solidity.readthedocs.io/en/latest/types.html#addition-subtraction-and-multiplication)

```bash
Addition, subtraction and multiplication have the usual semantics. They wrap in two’s complement representation, meaning that for example uint256(0) - uint256(1) == 2**256 - 1. You have to take these overflows into account when designing safe smart contracts.

The expression -x is equivalent to (T(0) - x) where T is the type of x. This means that -x will not be negative if the type of x is an unsigned integer type. Also, -x can be positive if x is negative. There is another caveat also resulting from two’s complement representation:

int x = -2**255;
assert(-x == x);

This means that even if a number is negative, you cannot assume that its negation will be positive.
```  

What this means is that once you hit the upper limit of what Solidity can handle (uint 256 which is 2^256-1). This means that once you go one over that limitation, you "wrap around"
back to 1. The basic int that you use in Solidity is actually an unsigned integer, not a signed integer like the int moniker suggests. Solidity does not handle signed integers with a "-" before the number but can handle negative binary.

It's still confusing even to me, but basically, due to [two's complement](https://en.wikipedia.org/wiki/Two%27s_complement) which Solidity uses, a negative value of a signed int will be the same as its positive value. 

#### **Solution:**
The tricky thing is is that the Solidity maintainers tend to not write a lot of information on issues. They'll either write it in the title or reference a short comment in another issue. It is a bit tricky of finding useful information. 

The hint in the referrenced comment was that this test was for the `EndToEndSuite`. There's quite a few tests in Solidity and searching for endtoend actually brings up two files with the same name, one being `EndToEndTest.cpp` and `SolidityEndToEndTest.cpp`. Through personal inferral, it seemed `SolidityEndToEndTest` was the most logical place because it was actually testing the language functions. The other one appears to be from my knowledge a low level Ethereum testing. 

Looking at the other tests, you are able to inferr the structure of how tests are presented. At first there was confusion on exactly what was to be tested but it's a bad habit for me to overthink things. So the test ended up just being on the above assert exactly shown. Here's the [Pull request](https://github.com/ethereum/solidity/pull/5213) and the test that was written:

```c++
BOOST_AUTO_TEST_CASE(flipping_sign_tests)
{
	char const* sourceCode = R"(
		contract test {
			function f() public returns (bool){
				int x = -2**255;
				assert(-x == x);
				return true;
			}
		}
	)";
	compileAndRun(sourceCode);
	ABI_CHECK(callContractFunction("f()"), encodeArgs(true));
}
```
Basically it makes sure that if you write a negative signed integer in a contract that it is the same as the positive version of that integer. 

#### **Side Issues and Their Solutions**

After a rebase on my issue branch, there was an error that had popped up. Forcibly pushing it solved the issue but other people's commits in the rebase appeared as part of the commits I did. After reverting changes and rebasing again, the same error popped up - 

```git
! [rejected]          issue-branch -> issue-branch(non-fast-forward)
error: failed to push some refs to 'git@github.com:mordax/solidity.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details
```

A good friend of mine [0xazure](https://github.com/0xazure), helped out in a private message and gave this fix:

 - Revert back before the rebase.
 - Do the rebase.
 - Do `git push --force-with-lease $branchName` ($branchName being the actual name of the branch to be pushed).
 - Be relieved.

Although I'm relatively comfortable with Git, there are some cases that pop up here and there that catch me off guard. If you're finding multiple commits that are not authored by you in your Pull Request after rebasing and pushing, do the above to fix it. 

Had some more requests from the maintainer to squash commits (bringing multiple commits into one clean commit) and found this technique to be the most effective:

- `git rebase -i HEAD~#` where `#` is how many commits starting from the end you want to include in your squash.
- This will force a text file to open that'll list something like: 

```git
pick ceb2ee9 this is a commit message
pick 9zfsd64 this is another commit message 

# Rebase .... (# commands)
# Commands:
# p, pick = use commit
...
# s, squash = use commit, but meld into previous commit
```
- Leave the commit with the message you want for your squash, leave it as `pick`
- Change the other commits' `pick` to `squash` and then save
- Push and rejoice at one clean commit



#### **Benefits**

- Testing is underrated. At least in my educational experience, we maybe touched upon testing code once and that was [JUnit.](https://junit.org/junit4/) Only in my open source program do we legitimately learn various tooling and get into the habit of testing. 
- The more Solidity can test against potential exploits, the better trust is in these decentralized applications. 
- Personally, it becomes easier to understand how contract programming and decentralized programs work, as it remains to be confusing due to its youth.

Happily [merged.](https://github.com/ethereum/solidity/pull/5213)
