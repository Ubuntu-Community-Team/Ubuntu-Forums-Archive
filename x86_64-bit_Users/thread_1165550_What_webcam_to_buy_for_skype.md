---
title: "What webcam to buy for skype"
date: 2009-05-20
forum: x86 64-bit Users
---

### Post by rold50 on 2009-05-20
What webcam works right out of the box with skype on Jaunty 64-bit?

---

### Post by Arup on 2009-05-20
Almost all do like cheap unknown brands using Zcam chipset to all varieties of Logitechas well, just stay off MS webcams, they are a pain to setup.

---

### Post by rold50 on 2009-05-21
I currently have logitech quickcam messenger and I can't get it to work with skype. In 32-bit ubuntu, I was able to use gstfakevideo and it worked. But that doesn't work in 64-bit.

---

### Post by Jimtheplanner on 2009-05-21
I've been there done that with webcams. I went through hoops to get Logitech to work....  

Then I came across a post somewhere from someone who spotted a picture of a Skype developer using a "Philips Webcam". He went out & bought one which worked first time. I did the same never looked back.

Mine is an SPC530NC.

Hope this helps...

Jim

---

### Post by Dougie187 on 2009-05-21
I currently have a logitech and it was plug-n-play. Worked without doing anything.

---

### Post by TURBO_TURBINA on 2009-05-21
I am using the Microsoft LifeCam V5000. Excellent in all aspects. Compatibility, size and quality. Recommended for linux.

---

### Post by rold50 on 2009-05-21
> **Jimtheplanner said:**
> I've been there done that with webcams. I went through hoops to get Logitech to work....  

Then I came across a post somewhere from someone who spotted a picture of a Skype developer using a "Philips Webcam". He went out & bought one which worked first time. I did the same never looked back.

Mine is an SPC530NC.

Hope this helps...

Jim

Thanks. but it seems SPC530NC is not available here in the US.


Dougie187 - what model of logitech webcam do you have?

TURBO_TURBINA - Is that the same as Microsoft LifeCam VX-5000?

---

### Post by Dougie187 on 2009-05-22
I think it's a vista something or other. Actually, sorry It is a Creative Labs. Not Logitech. It works great though. I couldn't tell you the version, just if I saw it I would know it.

EDIT:

Actually, here it is.

[webcam]("http://images.google.com/imgres?imgurl=http://picnicb.us.ciao.com/us/10258495.jpg&imgrefurl=http://www.ciao.com/Creative_Live_Cam_Vista_IM_VF0420__Review_10373081&usg=__6o6D92nuRLwbefM8kEn_qKOKzyw=&h=300&w=400&sz=23&hl=en&start=57&sig2=pszm-J0S2ii0VeC4pHPfbg&um=1&tbnid=kCZP3qPJZoobuM:&tbnh=93&tbnw=124&prev=/images%3Fq%3Dcreative%2Blabs%2Bwebcam%2Bvista%26ndsp%3D18%26hl%3Den%26rlz%3D1B5_____enUS324US324%26sa%3DN%26start%3D54%26um%3D1&ei=7TwXSsiLNZq6tAPO-bjhCA")

I have the black one.

---

### Post by the_nz_monkey on 2009-05-22
I'd have a look here:
[http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/")

This lists the current state of the UVC camera drivers for linux.

Basically speaking, if it's on this list, it should just work in Jaunty.

And here's the Ubuntu community page on the subject:
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

I ended up buying a Logitech S5500 - and it appears to work fine in Skype.

---

### Post by komealy on 2009-05-22
If you make sure to install the lib32v4l-0 package any v4l compatible webcam will work in skype.  I have an hp and a logitech quickcam express (both very, very old) that work fine now that I have lib32v4l-0 installed.  I figured this out by hitting up medibuntu.org and installing skype from their repositories.  NOTE: do not send problems with packages there to ubuntu, medibuntu has a forum on their site that you can use.   They set up all the dependancies that are necessary for the 64 bit systems to work with skypes inherently 32 bit setup, other libs include the ia32-libs (among others) that you probably already have if skypes voice calls work properly.

---

