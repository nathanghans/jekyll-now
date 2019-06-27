---
title:BSides Roc
layout:post
---
# Bsides Roc
[Bsides - Rochester](http://bsidesroc.com)

## Introduction

This was my first security conference and I was very excited to attend. I attended SQL Saturday conferences before and this was very similar. Being among peers was very energizing and I got some good information to bring back to my organization.

The talks I attended were

* Jason Scott
* Matt Wright - Using Deep Learning to Undermine Tor
* Jeff Man - More Tales From the Crypt...Analyst
* Frank Fazio - Shock & Awe: Training the Humans
* Zach Bevilacqua - Threat Hunting and Other Arcane Magic
* Mark Manning - Kubernetes: DevOps vs "Security People"
* Chaim Sanders - Plaing the short game: the effects of data breaches on share prices

I also visited the lock picking village and talked to folks from [RockGameDev](http://rocgamedev.com/) and [Interlock - Hackerspace](https://www.interlockroc.org/)

# Talk Recap

## Jason Scott

Very interesting talk about [archive.org](archive.org) and [emularity](https://www.archiveteam.org/index.php?title=Emularity). He is very passionate about what he does and it shows. When I have time I'm going to have to check out emularity and try some of the old video games. If you are interested in helping out Jason and his team of rogue archivists visit [the archive page](https://www.archiveteam.org/index.php?title=Main_Page). 

He did touch on a topic - the territorial nature of people - that really hit a chord. Instead of embracing the energy and enthusiasm of Jason and his team the archiving profession were the loudest critics. This is gatekeeping - no one can archive unless they have been pre-approved by another archivist. Short sighted is what it is. Instead of harnessing the passion that Jason and his team have, the "professionals" decide to try to quash that enthusiasm. As a result the world is a worst place because of these Archivists. I applaud Jason and his team for moving forward in their quest.

## Matt Wright

I'm not sure I'm skilled enough to fully grasp what Matt was talking about. I thought the talk was interesting, but I didn't quite grasp the main thread. It seemed to be a talk about how to undermine privacy by using machine learning to un-anonymize traffic. Maybe?

## Jeff Man

Interesting talk about working in the NSA. Not much actionable advice to take away - but I did walk away from this talk with an interest in finding books to reading on the field of Security/Hackers. I found a few from trawling the internet. [Link](https://www.reddit.com/r/hacking/comments/a6aewa/is_this_book_any_good/), [link](https://www.reddit.com/r/hacking/comments/atbsgj/good_books_for_hackers_to_read/), [link](https://www.reddit.com/r/sysadmin/comments/84vyuj/anybody_sysadmin_fiction_recommendations/)

One small regret - I was listening to Paul's Security Weekly on the way home from the conference and Jeff mentioned an article about scientists had used quantum computing to reverse time. I would have liked to have talked to him about that. Next time.

## Frank Fazio

I have done a few computer talks at local libraries in the past, so Frank's talk really hit home. I thought it was very useful and I could see myself doing something very similar. His main points were:

* Tell a story
* Use pictures
* Use real world examples
* Don't sell fear - sell solutions

## Zach Bevilacqua

My favorite talk. This was the meat and potatoes of this conference for me as a blue teamer. It also gave me a shot of confidence as I had been doing some of this to a smaller scale in my first year in InfoSec. 

Zach defined threat hunting as the proactive search for anomolous activity. He mentioned two strategies:

1. Theory/Intel Based - This is short-term based - 1 or 2 days. Known IOCs/artifacts. 
2. Project/Digital Forensics Based- This is long term, well documented and planned. Unkown IOCs and artifacts. 

All threat hunting answers the questions: who, what, when, where. The threat hunter determines the Why.

He likened building skill in threat hunting to a game. In a game you get an item or ability, become a master of it, then get another ability.

Zach mentioned the importance of not data hoarding - and collecting pertinent security only.

He had a funny security toilet reference. It wasn't flushing your data down but it was a unique take on the concentric circle model. He had Response, Intelligence, and Detection at the 3 stops of the circle. 

* Response covered standards and policies, incident response, tool and tuning, path and configuration management
* Intelligence coveres inventory, user configu, threat monitoring
* SOC, vulnerability management, red team

He mentioned using US-Cert TA18 074A, MITRE, and Cyber Kill Chain for a threat model.

Zach said to look at user behavior analytics. Some items to look for:

* Wildly different network location
* Anamolous Logins
* use of PSEXEC
* DNS
* User creation/deletion
* Registry edits
* Web shell
* VNC

Zach introduced me to the term "configuration drift." This is a term used to monitor changes from default configurations - an important item to monitor for in threat hunting.

He said to monitor web server logs to monitor for entropy in IIS files. For example, if 99% of traffic is going to index.html but 1% is going to  suspiciousfile.js - you can hunt to find out why that one file is in use.

Also - Track user agent string entropy.

One good way to start on threat hunting is to find your own activity in the logs. If you can track yourself and understand what you did, you will learn how to track others.

Great talk.

## Mark Manning - Kubernetes: DevOps vs "Security People"

This talk was also a bit above my head. Mark helped me understand Kubernetes a bit more. I walked away with a better understanding that if I find myself in an environment with kubernetes to listen to the developers architects for insight into how we can work together to secure that environment. 

## Chaim Sanders - Plaing the short game: the effects of data breaches on share prices

Chaim might have been the most charasmatic speaker besides Jason Scott, but I admit at this point in the day I was a bit fried and didn't walk away with much about this talk.

## Misc

Other than the talks, I really enjoyed the lock picking village. I picked the 3 easy locks. At my next conference I hope to spend more time here.

I was really impressed with the community in rochester. They have physical spaces for [RockGameDev](http://rocgamedev.com/) and [Interlock - Hackerspace](https://www.interlockroc.org/). The folks involved with both were really friendly and welcoming.

These types of spaces would be awesome to have in the Albany area. I found out we do have a [game space](https://www.techvalleygamespace.com/) I haven't found a 'hackerspace' yet. I'll keep looking. 

The work these folks have done to build this community is really impressive.

If you want to catch the talks, they can be found here: [Youtube for all the talks](https://www.youtube.com/channel/UCkmXzx6WTF6rqvX07tXfinA/videos?view=0&sort=dd&flow=grid)
