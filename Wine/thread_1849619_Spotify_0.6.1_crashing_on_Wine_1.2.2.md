---
title: "Spotify 0.6.1 crashing on Wine 1.2.2"
date: 2011-09-24
forum: Wine
---

### Post by tiptronicus on 2011-09-24
Everytime I start spotify, it crashes with the message spotify.exe has encountered a serious problem and needs to close. I checked appdb.winehq.org, but could not find much help. I found one suggestion to remove the facebook link and did that by removing the app from FB. Still no luck.

---

### Post by noahdiehl on 2011-09-24
I had the same problem... removing the app from FaceBook was the fix here... I would double check the FaceBook app and make sure it is uninstalled.

---

### Post by AndersAA on 2011-09-25
There is a native app available, even with a ppa. Why are you running it through wine?

---

### Post by henson.next on 2011-09-25
I'm pretty sure that the Linux version of spotify doesn't allow you to login with the free account.

I was able to get spotify to launch when I went to the Facebook page and removed the app -- but that was the whole point. Wanted to share some playlists.

Would love to hear of a workaround.

---

### Post by nikidaki on 2011-09-26
Hi to All!
I have exactly the same problem,i try everything,i was ran the spotify under wine,and then 
 a week or so,the problem began,when spotify updated to version 0.6.1
then tried to install the native spotify client,but nothing,says that the packages are missing or broken,searching the web,doesn't find any specific answer.
Please,any help will be appreciated!
Thanks!

---

### Post by nikidaki on 2011-09-26
the answer is here!
[http://www.informationweek.com/byte/howto/personal-tech/desktop-apps/231002893](http://www.informationweek.com/byte/howto/personal-tech/desktop-apps/231002893)
works like a charm !

---

### Post by CJ_Hudson on 2011-09-29
Which is the subscriber version only.

---

### Post by meh_phistopheles on 2011-10-02
i had a problem with spotify free through wine when i first installed it. the problem for me was connecting to facebook. to fix it, i remember spotify would load for like a second, so i had to hurry up and click "File>Connect to facebook" and deactivate connecting to facebook. then, spotify worked on the next start. if spotify doesn't load at all for you and you are connected to facebook, i would try deleting and reinstalling it without connecting to facebook on the first login. 

it sucks that you can't use facebook with spotify free on linux, but it's still not bad having millions of songs for free.

also, i am on wine 1.3.15 with spotify 0.6.1. you might want to try upgrading wine too.

---

### Post by lunalui on 2011-11-18
Hi everyone,
I've been having the same problem for quite some time now, and it's driving me mad. Initially I thought that the facebook connection was the culprit, but I am now positive the problem is more complex.
I have two accounts on spotify. Initially these were a free one and an open one (so only accessible through wine). Some time ago I believe all open accounts were transformed into free accounts, and from then spotify crashed whenever I tried to log into my "open" account. After some tests, and several reisntallations, I gave up on it, and only used my free account.
Today, however, I upgraded to premium and, since then, spotify crashes on both accounts when logging in (or just a few seconds after).
At this point, my premium account seems to work fine under the spotify linux version, but still I would really like to fix the problem under wine. (Of course I've tried reinstalling, upgrading, etc)

the version of wine I'm using on my ubuntu lucid is wine-1.3.31, I do not know which version of spotify I have (but I did reinstall it today! as well as upgrade wine...) 

If you need more pieces of info, do not hesitate to ask. I do hope someone here will understand where the problem comes from: hoping for some help from the support forum for spotify is just wishful thinking

---

### Post by lunalui on 2011-11-23
just wanted to let you know that for some mysterious reason I was able to open both my spotify accounts under wine, without them crashing, for a couple of times today. The sound, though was extremely jumpy... very strange

---

### Post by cgolson84 on 2011-11-24
I just wanted to check in and say that my mother in law and myself are both using the native spotify app in Linux Mint 11 (her) and Xubuntu 11.10 (me) and we are both on free accounts.  We are going to both be subscribing but currently are both using free accounts with zero problems or crashes.  In fact, I am absolutely in love with Spotify, it's fantastic!

---

### Post by lunalui on 2011-11-24
> **cgolson84 said:**
> I just wanted to check in and say that my mother in law and myself are both using the native spotify app in Linux Mint 11 (her) and Xubuntu 11.10 (me) and we are both on free accounts.  We are going to both be subscribing but currently are both using free accounts with zero problems or crashes.  In fact, I am absolutely in love with Spotify, it's fantastic!

thanks for that, you are right! I can indeed access my free spotify account using the linux application. This is very strange, though, for this is what you still can read on the spotify web page:

[I] This is a preview build of Spotify for Linux.  As a preview release this  version is still unsupported, but we're running it ourselves and will  try to make sure it keeps pace with its Mac and Windows siblings, there  are issues regarding decoding of local music on the Linux platform so we  haven't included support for local files in this version.  As we  haven’t found a reliable way to display ads yet, this version is only  available to Spotify Premium and Unlimited subscribers.

[/I]Having said that, now local files seem to be supported, too! I'm really happy about this.
I guess this way you do not get much advertising either? or maybe they solved that problem? Anyway this is absolutely great...
cheers!

---

