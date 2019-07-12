Morning Recap

I set out to backup my pfsense router. 

Then I meandered into I should use my old desktop as a NAS. 

No. Too clunky and old school.

AWS - ok what can we do there. 

S3 - Simple Storage Solution. They also have Glacier for archiving and DEEP Glacier for MORE archiving. 

Found this: https://pawelgrzybek.com/my-amazon-s3-photo-backup-solution/


ok. Couple thoughts on this:

1 I could do it manually but that is no fun - AND it wouldn't upload folders of info. 

[]Problem 1 - get any file uploaded to AWS to be in the folder it is in on the LAN.

[x]Problem 2 - all my files are name IMG#### - no good. Create a script to rename all the files in the folders to be DATE-FolderName-Count.extension. Got that done [here]

For some reason I want to run that one by my wife? as if she cares. WTF am I thinking. Oh well.

Anyway. 

I started to work with this: 
http://todhilton.com/technicalwriting/upload-backup-your-files-to-amazon-s3-with-powershell/

but it didn't work out the gate - my guess it is not powershell. 

Setup AWS Powershell on my photo storage machine - 

I used these last night and need to remember them when setting up the powershell cli:

get-awscredentials -listprofile #tells what the profile is

set-awscredential -accesskey -secretkey -storeas #to set the creds into a profile. 

Now to see what I can use the CLI for and if I can get S3 buckets from it.  That is next. 

In between all that I was coordinating a new playground for a local non-profit preschool. 

OHH

The most stressful part

Having to find a new Cell Phone. I hate shopping. 



Afternoon Recap

get-s3bucket -profilename 

WORKS!!!

I think this will be how we create nested folders: https://tommymaynard.com/tag/write-s3object/



that was a god send it works 95% of the way - now I only need to figure out how to verify a file is already there and if so don't -reupload it. 

if my reading of reddit and stack overflow is accurate - then AWS does no check and the files will be uploaded everytime, so I need to account for that on my side. 



Afternoon Recap 2

Sonos like multiroom speaker system. 

So it doesn't appear Amazon Music has a streaming service for multi room speakers. UGH. 

https://www.instructables.com/id/Raspberry-Pi-Multi-Room-Music-Player/

This ^ has a way to set up the raspberry pi with a few receivers - requires spotify musci - we could always activate Spotify for the montsh when we really want. IDK we'll see. 

I think I should set up the R-pi and one receiver to see how it works then go from there. 



Stressed Chapter 1

I had stress today. this isn't nearly the first time, but this is the first time i'm writing it down. 

It went away while my family and I were out mulching some bushes, checking things off the todo list, but other than that it has been around most of the day. 

2 days ago I was stressed AND upset. I didn't like the day I felt out of control. I fixed that with a good mind map exercise and the following day(yesterday) I didn't go on reddit, and tried to maintain perspective by scanning my todo and thoughts list. 

Today tho that didn't help as much. Perhaps why I'm stressed is the fact that I have 3 projects all without resolutions hanging out there, combined with the plan in my head to make Friday-Sunday easy going and not touch the projects - maybe there is a sense that I am not... that I have loose ends. 

3 projects - AWS, SONOS, pfsense


I think I need to find a way to separate the un-ending list of things that could be done at some point - with the tings I am working on now(which there can be a lot of them)
I'm going to try RTM and Trello? Maybe...
