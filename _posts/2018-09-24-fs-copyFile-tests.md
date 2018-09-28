---
title: fs.copyFile Filer tests
layout: post
date: 2018-09-24 13:48:00 -0400
category: ["seneca"]
---

## Basic tests for not yet implemented fs.copyFile in Filer

Filer doesn't currently have support for a newer Node fs implementation called [fs.copyFile](https://nodejs.org/api/fs.html#fs_fs_copyfile_src_dest_flags_callback). 

**fs.copyFile format:**  
{% highlight javascript %}
fs.copyFile(src, dest[, flags], callback)
{% endhighlight %}

Where _src_ => is the source file you want to copy,
_dest_ => the file to be changed to src's contents. Both src and dest can be strings, buffers or urls.

[flags] are optional and can be either one (or more than one) of the following:  
_COPYFILE_EXCL_ => which will make sure the copy fails if destination target already exists  
_COPYFILE_FICLONE_ => The copy operation will attempt to create a copy-on-write reflink. Basically what that means that if the location is equivalent in content to the src, it won't copy it, thus removing unecessary operations. If the platform doesn't support it, _a fallback copy mechanism is used_.  
_COPYFILE_FICLONE_FORCE_ => Same as Ficlone, except if the platform doesn't support it, it will fail as opposed to using a fallback mechanism.  

---

So what I did was open an [issue](https://github.com/filerjs/filer/issues/436) for it. 

Filer has a bunch of implementations for other fs methods but it does not have copyFile. On recommendation from one of the maintainers, I opted for the simpler route of implementing some basic testing of a potential future implementing.  

What the test is supposed to do: 
- Check if function exists
- Check if it fails if src doesn't exist
- Check if it successfully copies the file

What I forgot to implement: 
- Check if it fails if dest doesn't exist

This is still a work in progress. Something that took a while for me to understand is that you can give incomplete code or finish small chunks of problems and push them through. I'm too used to having to make sure the entire thing working before making it. It was strange to write tests before writing any implementation but there's an entire idea behind it called [Test-Driven Development.](https://en.wikipedia.org/wiki/Test-driven_development)

Here is the link to the [Pull Request](https://github.com/filerjs/filer/pull/481) with the tests I outline above.

It was also my first time giving a [code review](https://github.com/filerjs/filer/pull/471). 

The Travis build was failing due to simple linting issues - some spaces were 4 where they should've been 2, missing semicolons, etc. So I offered a simple fix, asking the programmer to `npm run lint:fix` which is a command in Filer's test that does the lint fixes for you. 

They took my advice and happily enough, their tests passed Travis this time. 

---

My PR received a very detailed and thoughtful review. I'm still working on cleaning it up.





