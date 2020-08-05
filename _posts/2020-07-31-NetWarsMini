fbJ1`cXXQS2/;GiclkFm


man items were easy

cat crone.json | jq .[0] | .player
    5  cat crone.json | jq '.[0] | .player'
    6  cat crone.json | jq '.[0] | {player="MonkeyMurphy"}'
    7  cat crone.json | jq '.[0] | [{player="MonkeyMurphy"}]'
    8  cat crone.json | jq '.[0] | {player: "MonkeyMurphy"}'
    9  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC"}'
   10  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game}'
   11  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified}'
   12  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified.verified="yes"}'
   13  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified.verified:"yes"}'
   14  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified[verified: "yes"]}'
   15  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified{verified: "yes"}}'
   16  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified:{verified: "yes"}}'
   17  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified:{verified: "no"}}'
   18  cat crone.json | jq '.[0] | {player: "MonkeyMurphy", console:"PC",game,verified:{verified: "fuck"}}'
   19  cat crone.json | jq '.[0] | {player: "MonkeyMurphy"}

;
   20  cat crone.json | jq '.[] | {player: "MonkeyMurphy", console:"PC",game,verified.verified:"yes"}'
   21  cat crone.json | jq '.[] | {player: "MonkeyMurphy", console:"PC"}'
   22  cat crone.json | jq '[.[] | {player: "MonkeyMurphy", console:"PC"}]'
   23  cat crone.json | jq '.[0]'
   24  cat crone.json | jq '.[0] | .player'
   25  cat crone.json | jq '.[] | .player' | grep Foetualog
   26  cat crone.json | jq '.[] | .player' | grep A5 B5 Foetualog
   27  cat crone.json | jq '.[] | .player' | grep -A 5 -B 5 Foetualog
   28  cat crone.json | jq '.[0]
   29  cat crone.json | jq '.[] | .player,.console,.game' 
   30  history
   31  cat crone.json | jq '.[] | .player,.console,.game'  | Foetualog
   32  cat crone.json | jq '.[] | .player,.console,.game'  | grep Foetualog
   33  cat crone.json | jq '.[] | .player,.console,.game'  | grep -A 5 Foetualog
   34  cat crone.json | jq -j '.[] | .player,.console,.game'
   35  cat crone.json | jq -j '.[] | .player,.console,.game,.runtime'
   36  cat crone.json | jq -j '.[] | .player,", ",.console,", ",.game,", ",.runtime'
   37  cat crone.json | jq -j '.[] | .player,", ",.console,", ",.game,", ",.runtime"\n"'
   38  cat crone.json | jq -j '.[] | .player,", ",.console,", ",.game,", ",.runtime,"\n"'
   39  cat crone.json | jq -j '.[] | .player,", ",.console,", ",.game,", ",.runtime,"\n"' | grep Foetualog
   
   i didn't like doing it in csv format, but that is what the hints led to.
   
     cat crone.json | jq '.[] | .verified.examiner'
    2  cat crone.json | jq '.[] | .player, "," .verified.examiners'
    3  cat crone.json | jq '.[] | .player, ", ", .verified.examiners'
    4  cat crone.json | jq '.[] | .player, "," .verified.examiners'
    5  history
    6  cat crone.json | jq '.[] | .verified.examiner'
    7  cat crone.json | jq '.[] | .verified.examiner, ", ", .player'
    8  cat crone.json | jq '.[] | .verified.examiner, .player'
    9  cat crone.json | jq '.[] | .verified.examiner, .player' | uniq -d
   10  cat crone.json | jq '.[] | select(.verified.verified == 'yes')'
   11  cat crone.json | jq '.[0]'
   12  cat crone.json | jq '.[] | select(.verified.verified == .player)'
   13  cat crone.json | jq '.[] | select(.verified.examiner == .player)'
   14  cat crone.json | jq '.[] | select(.verified.examiner == .player)' | head -20
   15  cat crone.json | jq '.[] | select(.verified.examiner == .player)' | more
   16  history
   
   tried to do a uniq but that didn't work. had to use another hint. Interesting that you can compare a value against another  to another value
   
   
The boss fight. 

#1 - cat the file look for the wroding -- doesn't find it gives error. cat the whole thing and at the bottom is th word it expects. "friendship. 

Why did grep return "Binary file (standard input) matches" --- because the file's first characters were in binary. to overcome this, per the hints - use strings.

#2 


==============

Tried Mini1 - a text adventure - figured I'd already done the text stuff so going to look for some new things

===============

tried MIN Stolen Nuts - didn't work at the time. 

Mini 2 A thin Veneer

Task 1 - figure out what ci/cd it used.

It was right on the homepage

Task 2 - get size of largest directory

Tried to use git clone to pull down the git repo but that didn't work. I took the hint and used wget to pull it down instead and do a du on the file

Task 3 - find flag in index.php

So there was no index.php - i thought theey may have meant index.html - that didn't work. 

I took a hint - git status

So with git status I could see what was removed. based on that I used git restore to restore the file index.php and looked at it in a text editor. 

Task 4 - Secret parameter

Used the same git restore to resotre the png message in the totes-illegit.php folder the flag was in that image. Not the easiest image to read.



MINI2 - Gleeful SQL People

Task 1 - get sha1

just execute the task given. 


Task2 - Get Locations

SELECT count(*) FROM `locations` WHERE 1 

Task 3 

I did not use hints and got my hint from https://www.mysqltutorial.org/mysql-json/ on how to get json. 

here is my answer
SELECT count(*) FROM `locations` WHERE data->'$.security.cameras' = 'nope'

they mention json_extract


this part of this page  https://dev.mysql.com/doc/refman/8.0/en/json.html#json-paths:

 Then:

    $[0] evaluates to 3.

    $[1] evaluates to {"a": [5, 6], "b": 10}.

    $[2] evaluates to [99, 100].

    $[3] evaluates to NULL (it refers to the fourth array element, which does not exist). 

Because $[1] and $[2] evaluate to nonscalar values, they can be used as the basis for more-specific path expressions that select nested values. Examples:

    $[1].a evaluates to [5, 6].

    $[1].a[1] evaluates to 6.

    $[1].b evaluates to 10.

    $[2][0] evaluates to 99. 

SELECT data->'$.inventory', data->'$.security' FROM `locations` WHERE json_extract(data, '$[0].inventory[1]') = 'plastic bags' and data->'$.security.cameras' = 'nope'

this only checks the 2nd field. 

SELECT json_search(data->'$.inventory', 'one', 'paper bags'), data->'$.inventory' FROM `locations` WHERE  json_search(data->'$.inventory', 'one', 'paper bags') is not null and data->'$.security.cameras' = 'nope'

this still doesn't work. Read the question -- yup looking for the wrong kind of bag.

SELECT count(*) FROM `locations` WHERE json_search(data->'$.inventory', 'one', 'plastic bags') is not null and data->'$.security.cameras' = 'nope' 

Ok so this one was tough. i was trying to use the hint but couldn't get json search to work. 1st thing to note - when testing things out use them in the select not the where. where doesn't tell you what's going wrong. 

got it working in select, then put into where, that helped but got wrong number. re-read the question and that helped.




Nut powered Doom

Hidden note -- needed t look at the source code

Trippy

injection. needed hints. I need to get better at sql injection. 

needed the following. I had it close was working with ' or 1' #!-- and the like.

solution: ' or 1 or 1 --
============
Bypass

needed tos earch the source code, then navigate to the yaml file

answer

profpdoomsdaydevwebint.py


================
Crush 'Em

Ok this one new to me. 

apparently you can modify settings using the console. so - search the source code for the "var doomsday_device = new DoomDayDev();" to figure out what the app is calling. 

then use "doomsday_device.fuel_empty_number=0" in the console to force the meter to go down. 

Answer FUEL DEPLETED DEVICE DISABLED!

kind of glad I got past that one. this one was new and exciting to crack.

====================
unusual message

cross site scripting. use send message to insert 

"<SCRIPT>alert("XSS")</SCRIPT>"

send and you get:

ANSWER --- Irregular Message Detected!

=====================

ADMINS ONLY

this is finding the API for the YAML file. we found this before. Tried

/api/file/read/authed%2fconfig.yaml -- but that is the read version. need the write version

/api/file/write/authed%2fconfig.yaml


=====================
you're not allowed to read that

if we look in the inspector we see they are blocking the admin login using CSS. unhide that. 

<li id="adminlink" style="display: none"><a href="/admin">View Messages</a></li>

Get access denied

lets load up burp -- nope don't need it.

try directory traversal, doesn't seem to work with slashes, just modifies the url up to api.

had to take all the hints. %2f indicates that it doesn't parse slashes that way. so if we use %2f instead of / we get:

https://profpdoomsdaydevice.securitytreasurehunt.com//api/file/read/authed%2f..%2f..%2f..%2f..%2fetc%2fpasswd



Answer - 1500

=======================

The source

use the same path traversal as above, but with the py file in the yaml file(used a hint to figure to look in YAML)

https://profpdoomsdaydevice.securitytreasurehunt.com//api/file/read/authed%2f..%2fprofpdoomsdaydevwebint.py

then search that file for destruct and get

/usr/bin/selfdestruct

shut it down

====================

skipping #5




===============================

phpinfo()

use curl to get the data. then search the file for <-- comment -->
comment - TODO: REMOVE THIS

============================
Funny Bunny

had to figure out which word list to use 

wfuzz -w wordlist/general/common.txt --hc 404 localhost/FUZZ.php

--hc will hide those results that give a 404. we get info and marketing. 

used the hints on those.

============================

GET IT TOGETHER

So this took a small amount of time . 

tried to do a lot of curls to get the un-rendered php, then gaveup on that and thought about the challenge -- they gave us a fuzzer what if I could do that. 

wfuzz -w wordlist/general/common.txt --hc 404 localhost/marketing.php?FUZZ=1

ran the above and manually looked for antyhing out of the ordinary

instead of doing manually i use --hh to remove the common word count

located cmd that worked


wfuzz -w wordlist/general/common.txt --hc 404 localhost/marketing.php?cmd=1



=======================

taking the reins

PHEW that was tricky. 

first figure out how to base 64 encode a command

echo uanem | base64

then figure out how to plug that into the curl command

echo id | base64 | curl 127.0.0.1/marketing.php?cmd=$(</dev/stdin)

then lookup the hints because none of the command work. 

they hint to use help and strip the  \n

echo help | tr -d '\n' |  base64 | curl 127.0.0.1/marketing.php?cmd=$(</dev/stdin)

that works. Now try to figure out how to get redis to tell you the version. 
dig around.

then look at the help screen. -- wait a second it says: 

redis-cli 5.0.3

are they looking for 5.0.3

yes they are. NICE>

================================

finished with 100 points. top 50% maybe? that was probaly my best 


