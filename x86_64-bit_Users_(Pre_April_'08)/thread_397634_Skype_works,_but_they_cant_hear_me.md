---
title: "Skype works, but they cant hear me"
date: 2007-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by alek66 on 2007-03-30
I installed skype,usign automatix2. it works great, but they cant hear me how can  solved this or even better is there another program that runs with skype protocol

---

### Post by josephus on 2007-03-31
Have you tested if your mic is working when you aren't using skype?

---

### Post by alek66 on 2007-03-31
I have conected it, and I can hear it.

---

### Post by josephus on 2007-03-31
Go into Tools->Options->Sound Devices and change the Audio System to use.

Also go into the volume/control menu for your sound device and play with the settings there,  there is a lot settings to control and turn them up to make sure you haven't accidentally muted your mic.

---

### Post by rash1970 on 2007-04-01
Hello there,

I'm having the same problem. I checked my settings and everything seems to be fine. The microphone is not muted. I'm using ALSA mixer. I also have Skype set to ALSA. 

Best regards.

---

### Post by alek66 on 2007-04-01
Does gnome and kde have the same "sound server" ( i dont the actual name of it)
I remember i didnt have this problems under suse with kde.

---

### Post by rash1970 on 2007-04-01
> **alek66 said:**
> Does gnome and kde have the same "sound server" ( i dont the actual name of it)
I remember i didnt have this problems under suse with kde.

I'm not sure. I'm new at using Skype on Ubuntu (and new to linux in general).  Perhaps someone with more experience can help.

---

### Post by rash1970 on 2007-04-01
I've just tried the method in Ubuntu Linux for Non-Geeks and it didn't work. It consisted of downloading Skype RPM for Mandriva 10.1 and newer, installing Alien, converting Skype to a DEB package and then installing that.

---

### Post by alek66 on 2007-04-01
And wengo phone crashes on amd64... so... i am pretty tied up.

---

### Post by slowcoach on 2007-04-02
You could try also enabling Capture in the volume control preferences, I have had to do this in the past to get the Mic working.

---

### Post by rash1970 on 2007-04-02
Hi Slowcoach,

It was already enabled. Didn't help.

---

### Post by slowcoach on 2007-04-02
Found this....

 David Kaplan  said on 2007-03-30:

I found the solution to my problem somewhere in the bugs (though I cannot locate it now) and am reporting it here for future reference as several others reported similar bugs (though I can't find them now).

Basically, I had to remove .asoundrc and .asoundrc.asoundconf. This made Skype much happier.

 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

---

### Post by alek66 on 2007-04-03
I will try it when I get home.
You can use skype now? people can hear you?

---

### Post by alek66 on 2007-04-03
> **slowcoach said:**
> Found this....

 David Kaplan  said on 2007-03-30:

I found the solution to my problem somewhere in the bugs (though I cannot locate it now) and am reporting it here for future reference as several others reported similar bugs (though I can't find them now).

Basically, I had to remove .asoundrc and .asoundrc.asoundconf. This made Skype much happier.

 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

where did you remove those files...couldnt locate them.

---

### Post by rajeev1204 on 2007-04-04
Hi

This may sound silly but , have u done the skype test call and couldnt hear ur voice?

OOPS cos then iam in trouble too cos i havent done a voice chat with a real person.

The test call goes fine

---

### Post by slowcoach on 2007-04-04
> **alek66 said:**
> where did you remove those files...couldnt locate them.

I don't use skype myself, I would assume that those hidden files are in the Home Folder.

---

### Post by rash1970 on 2007-04-07
I can't find these files to save my life.  Any suggestions?  I searched the home folder to no avail.

---

