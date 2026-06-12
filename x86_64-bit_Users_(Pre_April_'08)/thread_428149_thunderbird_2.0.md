---
title: "thunderbird 2.0"
date: 2007-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by fain on 2007-04-30
ok ive installed the Thunderbird 2.0 from their site. i used my profile from my windows install. i changed anything that pointed towards a windows dir. now every thing works fine except external http and mailto protocols. 
i made ```
Network.protocol-handler.expose.http true
``` which does nothing it seems
```
network.protocol-handler.expose-all true
``` wants to save each file in a tmp dir
```
network.protocol-handler.external.http true
``` this works fine except that each http link to a image opens in a new Firefox tab. so if i have five [http://images](http://images) in a message it opens each image in five separate tabs

i have also added ```
network.protocol-handler.app.http /path/to/firefox
```
what am i missing?
i changed url-handlers http to "firefox -remote "openurl(%s,new-tab)" well i think that was there already.
also my mailto protocol opens a new message but does not put the email message in the to line :confused: i have done the same to that protocol

i found this thread with a similar problem with mozilla-mail but they didn't solve it.
[http://osdir.com/ml/mozilla.devel.windows/2004-12/msg00002.html]("http://osdir.com/ml/mozilla.devel.windows/2004-12/msg00002.html")

---

### Post by RawMustard on 2007-05-01
I just [[COLOR="Blue"]This >>[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2544688#post2544688") and it works fine. However I'm having other problems with TB 2.0, namely installing dictionaries.

---

### Post by Kilz on 2007-05-01
I have gotten a little experience building mozilla code over the last few days. I will take a look to see if I can build a 64bit 2.0 version of Thunderbird. I would like to run it on my Dapper install. Of course I wouldnt be able to use the name or official branding.

---

### Post by fain on 2007-05-01
> **Kilz said:**
> I have gotten a little experience building mozilla code over the last few days. I will take a look to see if I can build a 64bit 2.0 version of Thunderbird. I would like to run it on my Dapper install. Of course I wouldnt be able to use the name or official branding.



sounds good. :)

---

### Post by Kilz on 2007-05-01
> **fain said:**
> sounds good. :)

[Here is a link to the 64bit build]("http://www.filecrunch.com/file/~5yupwo") I made of the 2.0 thunderbird code. It doesnt have any official branding, so I can distribute it. Its only a tarball, I want to see if it works for a few people before packaging it in a deb. You should be able to unpack it and run it from the folder it makes. I am also trying a new file hosting site for sharing the files.

---

### Post by Tickle Me Elmo on 2007-05-02
Do you have any idea when it'll be available to feisty, and if I run 1.5 - will it automatically update to 2.0 when it's out?

Cheers!
(from a ubuntu first time - I used to run Centos previously on my desktop)

---

### Post by flapane on 2007-05-02
what about feisty amd64?

---

### Post by fain on 2007-05-02
> **Kilz said:**
> [Here is a link to the 64bit build]("http://www.filecrunch.com/file/~5yupwo") I made of the 2.0 thunderbird code. It doesnt have any official branding, so I can distribute it. Its only a tarball, I want to see if it works for a few people before packaging it in a deb. You should be able to unpack it and run it from the folder it makes. I am also trying a new file hosting site for sharing the files.


well the program works great :) but i still have the same problem as b4 :(

---

### Post by kleeman on 2007-05-02
Works for me kilz. Seems snappier than the 32bit version I tried a week or so back.
deb would be nice....:) :)

---

### Post by Kilz on 2007-05-02
> **kleeman said:**
> Works for me kilz. Seems snappier than the 32bit version I tried a week or so back.
deb would be nice....:) :)

To do that, I would want to use an icon for the menu. Since I cant use official branding, Im going to have to find a graphic that has a free license.

---

### Post by fain on 2007-05-02
WOOT!!!!!!!!! u rock kilz :guitar: i didnt have much time to mess with it earlier. 
i just had to add these three strings in about:config

```

network.protocol-handler.app.ftp , /path/to/firefox
network.protocol-handler.app.http , /path/to/firefox
network.protocol-handler.app.https , /path/to/firefox
```

and

```
network.protocol-handler.app.mailto , /path/to/thunderbird
```
in my firefox about:config and everything works perfect now
thanks :)

---

### Post by firecat53 on 2007-05-03
Kilz, your build works great here!  Thanks!   (Feisty AMD-64)

Scott

---

### Post by Ledah on 2007-05-24
The package from Kilz doesn't exist anymore. Is there another place, where I can get a 64Bit Version of Thunderbird 2?

---

### Post by Kilz on 2007-05-24
I dont even have a copy of it any more due to a stupid move on my part. I will never , never, never ,never, never, never, never again mess around with a shell script that deletes things unless its on a virtual machine. I lost not only my home partition, but nsf networked folders on my file server that were mounted on my home partition.
Perhaps someone would happen to have it. If not I will try at some point in the future to build it again....... But right now I am doing the backup disk, file replacement, drudge work.

---

### Post by fain on 2007-05-24
i still have it. i am putting this temporary link up so kilz can get it and repost it. i will leave it up for awhile tho. 

hope it works

```
http://fain.kicks-***.net:666/build-of-thunderbird-2.0.0.0.code-en-US.linux-x86_64.tar.gz
```

hmm ok maybe not cause the boards censors its posts and my domain has a curse word lol

just replace the *** with the other word for donkey

---

### Post by Ledah on 2007-05-26
Thanks for your help. Well, I found in the backport discussion the [link]("http://ubuntuforums.org/showpost.php?p=2717660&postcount=99") to the [preview archives]("https://wiki.ubuntu.com/MozillaTeam/PreviewArchives") of the mozilla team. The Thunderbird 2.0 in their repository works for me :)

---

### Post by fain on 2007-05-26
nice thx :)

---

