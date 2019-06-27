---
title: Core Dump Madness
layout: post
---

followed this  https://stackoverflow.com/questions/40646694/buffer-overflow-in-64-bit-with-strcpy

took his advice to take out the setuid aspect of the exercise so only working with one user.

but i could not get a core file to get created. 

https://askubuntu.com/questions/966407/where-do-i-find-the-core-dump-in-ubuntu-16-04lts -- this tells you where the core dumps SHOULD go using Ubuntu

https://stackoverflow.com/questions/2065912/core-dumped-but-core-file-is-not-in-the-current-directory/18368068#18368068 -- this is a great post covering core dumps in depth that basically pins it on ulimit

further down in this post, the answer by "ankurrc" shows what the apport.log SHOULD look like. BUT mine didn't have that it had something about unicode error. 

So i googled that and I found:

https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1368911

THERE IS A BUG! Oh fuck.

Fixed that using @dennis schridde's suggestion

NOW i get the same apport.log look as @ankurrc 

Core dump is still not created - this was my dumb mistake - I had a folder called 'core' in my pwd. deleted that an voila I now had core dumps.

