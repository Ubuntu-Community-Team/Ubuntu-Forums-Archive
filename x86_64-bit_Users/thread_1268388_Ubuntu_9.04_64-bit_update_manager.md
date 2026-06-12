---
title: "Ubuntu 9.04 64-bit update manager"
date: 2009-09-16
forum: x86 64-bit Users
---

### Post by Richard Carlson on 2009-09-16
Every thing works well except I can't seem to get update Manager to work. If I run another package such as Synaptic it says another 'synaptic' process is running. I can't seem to figure out how to get this all back on track. I've rebooted the computer  with the same issues.  I also set all default repositories back to default and took out 3rd party repositories. Any help would be appreciated. I want to get this fixed. . . 

Thanks

Rich

---

### Post by coldfusion1313 on 2009-09-16
I just had the same problem.
Try running the update from the terminal
```
sudo aptitude update
```
But first try to run the update and see if it spits a code back at you and if you do copy that code into the terminal. Hope this helps

---

### Post by TheBuzzSaw on 2009-09-16
I'm not sure if my problem is the same as yours. My new Opera loads/runs just fine, but web sites take *forever* to start loading. The program itself doesn't hang or anything; it just does nothing for a while and then starts gathering site elements slowly.

---

### Post by 9170 on 2009-09-17
Do you like to see you update manager? If not can you write in the terminal ```
sudo apt-get update
```

---

### Post by Richard Carlson on 2009-09-17
I ran aptitude and was able to download the latest kernel and nvidia driver this morning. It seems to be working with aptitude. Apt-get with terminal is extremely slow  and I haven't tried update manager yet but will in a couple days to see if anything new and improved has popped up. Thanks for the suggestiions. 


Rich

---

