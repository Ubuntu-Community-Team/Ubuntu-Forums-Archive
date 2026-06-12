---
title: "How Do I install VMware Workstation on Ubuntu 8.10 x64?"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by kodemunke on 2008-11-13
Hey guys what's up? I am a total n00b when it comes to the Ubuntu operating system. I just want to know how to install VMware Workstation 6.5.0.118166. Could someone please give me a step by step walkthrough that has worked for them? All of the guides that I have found have not worked for me. Its starting to be a real pain in the A$$ trying to figure this out. I just need to know how to convert the .rpm to .deb and then successfully install the application. PLEASE HELP ME!! I want to run XP inside of Ubuntu. I have to have XP for school. Thanks a lot. I hope to hear from someone soon.:guitar:

---

### Post by jamillikan on 2008-11-13
Download the bundle instead.  Then, issue the command in a terminal:

sudo sh nameofvmwareworkstation.bundle {ENTER}

That "should" do it.  If not, check back and let me know.  Otherwise, you should download the tar.gz version and unpack it.  If you need help with that, just ask.

Joe

---

### Post by bosp7 on 2008-11-13
I second what Joe said about downloading and installing the bundle.

Unity is very buggy on 8.10 64bit though.  It worked for me at first, but after restarting Workstation it no longer worked.  When you click the Unity button it will max out one of my cores and then just hang.

I was able to un-install workstation then reinstall and get it working again, but the same thing happened after the first time I restarted it.

I hope I can find a fix soon, because I've already gotten addicted to Unity.

---

### Post by kodemunke on 2008-11-14
Thanks Dude that totally worked. I just had to figure out the 'cd Desktop' code in the Terminal to access the file on my Desktop. Thanks a lot man.

---

