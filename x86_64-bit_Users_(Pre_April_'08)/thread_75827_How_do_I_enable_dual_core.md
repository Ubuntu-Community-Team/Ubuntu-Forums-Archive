---
title: "How do I enable dual core?"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubernoob on 2005-10-14
I have AMD Athlon X2 3800+ (64-bit), but only one of the cores are enabled in ubuntu. Does anyone know how i can enable both of them?

---

### Post by Pablo_Escobar on 2005-10-14
You need to install SMP kernel and run Your system with it.
What type of Ubuntu You're using - 32bit or 64bit ??

---

### Post by ubernoob on 2005-10-14
I have installed the 64-bit ubuntu.

I found among alot of other stuff:
linux-image-2.6.12-9-amd64-k8-smp (2.6.12-9-23)
linux-headers-2.6.12-9-amd64-k8-smp

It seems to me that this is the newest kernel. Should i install this one, or is it better with an older more stable kernel? Or is this stable?

And can i just install the kernel from Synaptic, then everything works?

---

### Post by Pablo_Escobar on 2005-10-14
Good news, just install the newest SMP kernel through synaptic.
**DO NOT TOUCH THE STANDARD ONE !!**
When it's installed -> reboot -> at boot choose the SMP kernel -> try if it's all good. If not, at boot choose the old kernel.

---

### Post by ubernoob on 2005-10-14
Thank you very much! That worked surprisingly well! :)

---

### Post by blroth on 2005-10-30
Please  tell me which SMP kernel listed in Synaptic is the newest one to install as opposed to "the standard one" which you said not to install?  Thanks!

---

### Post by ubernoob on 2005-10-30
No, he meant that you shouldn't touch it, like in not uninstall it. You might need the standard one in case you fail to install the smp kernel.

But you are free to install the standard smp-kernel. :)

---

### Post by wishyjr on 2005-10-30
hiya! can you tell me if you installed the complete kernel? or one of the images.

thanks

Nvm, i just did it anyway and it works fine! cheers1

also, further to this is there a way i can assign certain applications to a certain processor? i.e. VMware to my secondary cpu?

---

### Post by ubernoob on 2005-10-30
i installed the image and the headers. I don't know what you mean by complete kernel. But as far as i know, the image is the complete kernel. I need the headers to install other stuff. E.g. vmware and nvidia drivers.

---

### Post by wishyjr on 2005-10-30
its ok i got it sorted, there was an option in synapticwhich was called 'whole kernel' so i was a bit confused for about 5mins then after marking it for installation it used both the image and the headers as dependenciesd anyway :)

so.. do you know how/if you can assign certain apps to a certain cpu?

---

### Post by bks on 2008-05-22
Okay, I have been searching synaptic for an smp kernel, but I can't find one. What key words do I use or what am I looking for, exactly?

---

### Post by enchantedsky on 2008-05-22
You are funny. You know you're replying to a message that's 3 years old right? This is no longer a problem in Ubuntu.....dual-core processors are fully supported now. You can tell by going into System ----> Administration -----> System Monitor and seeing a graph of your dual-core processor work

---

### Post by jspiers on 2008-07-14
Thanks for that.  I too was wondering whether I needed to do anything to activate dual core support.  It seems like many processes only use one core, so I guess what I need to find is multithreaded apps.  Is there anything else to do to maximize usage of my dual core cpu?

---

