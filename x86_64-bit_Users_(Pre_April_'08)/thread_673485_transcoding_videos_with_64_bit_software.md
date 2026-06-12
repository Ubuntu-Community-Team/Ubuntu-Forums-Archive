---
title: "transcoding videos with 64 bit software"
date: 2008-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by boandmichele on 2008-01-20
im converting several videos to *.iso, so i can burn them onto dvds.  im currently using devede, and the process of conversion is taking over an hour for a 500 megabyte file.  

is this normal?  isnt this the thing that 64 bit processors are supposed to do very quickly?  

what am i doing wrong?  

im proudly using ubuntu amd64 on a core2duo 6550 2.33ghz, with 4gigs of ram, so this shouldnt take that long, i didnt think...

---

### Post by Kilz on 2008-01-20
> **boandmichele said:**
> im converting several videos to *.iso, so i can burn them onto dvds.  im currently using devede, and the process of conversion is taking over an hour for a 500 megabyte file.  

is this normal?  isnt this the thing that 64 bit processors are supposed to do very quickly?  

what am i doing wrong?  

im proudly using ubuntu amd64 on a core2duo 6550 2.33ghz, with 4gigs of ram, so this shouldnt take that long, i didnt think...

Yes, it can take awhile, depending on what is being done. The thing is, if you do the same thing on a 32bit computer (I have) it takes quite a bit longer. You can shorten it a little by not having it make the iso, but just create disk structure in a folder. Then burn the audio_ts and video_ts folders to a blank dvd. I use Brasero to burn, and use the create data dvd project, and drag the folders inti Brasero. K3b has a video dvd project, same thing, drag the audio_ts and video_ts folders into the project.

---

### Post by boandmichele on 2008-01-21
excellent, i do think that would save some time.  i will give it a try, and thanks for the suggestion.

---

