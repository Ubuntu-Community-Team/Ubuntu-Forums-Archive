---
title: "What are some virtual machine programs I can use to run Windows XP inside Ubuntu?"
date: 2008-09-02
forum: x86 64-bit Users
---

### Post by zachhill91 on 2008-09-02
I have Ubuntu 8.04 and I want to run Windows XP inside Ubuntu. Is there any virtual machine programs other than Virtualbox?

I couldn't get Virtual box to work right.

I have almost completely switched to Linux but I still need Windows for those programs that just don't work right under Wine, and I hate to restart my computer to use them.

---

### Post by Kilz on 2008-09-02
> **zachhill91 said:**
> I have Ubuntu 8.04 and I want to run Windows XP inside Ubuntu. Is there any virtual machine programs other than Virtualbox?

I couldn't get Virtual box to work right.

I have almost completely switched to Linux but I still need Windows for those programs that just don't work right under Wine, and I hate to restart my computer to use them.

You can also use vmware. There is[ a free player]("https://help.ubuntu.com/community/VMware/Player"), make sure to download the 64bit linux tar.gz. That link will help you get xp installed.

---

### Post by zachhill91 on 2008-09-02
Ok, I will give that a shot, I will post again when I know if it works or not.

---

### Post by tuxxy on 2008-09-02
[virtualbox guide]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by damis648 on 2008-09-02
Vitualbox is the best, IMO. Tell us what problem you are/were having. Maybe we can help you.

---

### Post by Thelasko on 2008-09-03
> **zachhill91 said:**
> I couldn't get Virtual box to work right.


You likely didn't do [step 2]("https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy)").
```
sudo adduser $USER vboxusers
```

Maybe you did, but in my experience, that's the most common problem people have with VirtualBox OSE.

---

### Post by damis648 on 2008-09-03
> **Thelasko said:**
> You likely didn't do [step 2]("https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy)").
```
sudo adduser $USER vboxusers
```

Maybe you did, but in my experience, that's the most common problem people have with VirtualBox OSE.

Or CSE.

---

### Post by ububuL on 2008-09-03
I use vmware server 1.0.6 and it works pretty well for me except no sound and usb support. I think vmware server 2.0 will support both.

---

### Post by kaligus on 2008-09-04
I have a couple of medical devices which are so tied to windows as to make one wonder if microsoft had something to do with the design an implementation...

virtualbox ose would not install correctly or work with these devices when I did manage to get it working otherwise.

downloading from virtualbox.org the non ose version deb has been nothing but good for me.  There are still some kinks in the networking such that my data-backup has become cumbersome but still better than under windows alone for other reasons.

I have not spent much time looking at the other options mentioned in this thread mostly because I found my solution.

---

### Post by jespdj on 2008-09-04
> **damis648 said:**
> Vitualbox is the best, IMO. Tell us what problem you are/were having. Maybe we can help you.
But VirtualBox does have some limitations. For example, it doesn't support multiple cores in a VM (the VM will use only one core, even if you have a multicore processor), and VirtualBox does not support 64-bit guest operating systems (only 32-bit).

VMWare doesn't have those limitations.

There is a special [virtualization forum](http://ubuntuforums.org/forumdisplay.php?f=308) here. Start with the [Virtualization: Tips and Tutorials](http://ubuntuforums.org/showthread.php?t=781575) sticky there.

---

