---
title: "Adept database rebuuild"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by gadfium on 2005-11-21
A process appeared to crash while installing some packages through Adept, and now whenever I launch Adept I'm told it has only read access to the database unless I launch it as root. The error message is misleading; Adept is being run as root, but looking at error messages produced to the Konsole session which spawned it, it is trying to rebuild the database but is failing with a number of error messages. Some of the more alarming of these messages are:

adept: connecting processClick har har
(that's alarming to me because it seems rather unprofessional)

adept: Lister::scheduleRebuild
adept: #error#
(there's no further indication of what the error might be)

QObject::connect: No such signal ept::View::actionsChanged(ept::Lister*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'adept-mainwindow#1')
konsole: konsolePart::startProgram for /bin/echo
adept: Codec Default not found!
Uh oh.. can't write data..

(and later)
adept: 0 in cache
QThread object destroyed while thread is still running.
adept: 0 entities synced, time = 0

I've googled several of these error messages without finding any hits.

Is there a way to run a database rebuild manually instead of doing so through Adept? Any help would be appreciated.

-gadfium

---

### Post by gadfium on 2005-11-22
Seems to be sorted now.

The main error message from adept wasn't at all helpful. It only told me that it couldn't access the database unless it was run as root, yet it was being run as root. I presume this was a generic error message for anything going wrong with database access; it should at the very least suggest what I could do to get a more specific message.

The messages I saw on the command line by running adept from Konsole were more specific but also not helpful. Although adept is now running apparently correctly, almost all of these error messages still appear. It would appear that the programmer has left debug messages in the code, which I consider unprofessional, and which certainly confuse matters when an end user is trying to work out what's wrong.

The solution involved poking things with dselect a few times. I can't explain exactly what I did, but it seems the problem was an incomplete configuration of postfix (which was installed just prior to the problem arising because I tried to install something which required it - I suspect mysql). I used dselect to configure postfix, and while that didn't go smoothly (I had to manually create /etc/postfix/master.cf so the configuration would proceed, and the configuration seemed to hang at least once more), adept now seems to work.

Thanks to anyone who investigated the problem. Although no one posted any suggestions, I know from my own attempts to help on such forums that often people spend time looking at a problem before realising they can't make any useful suggestions.

gadfium

---

