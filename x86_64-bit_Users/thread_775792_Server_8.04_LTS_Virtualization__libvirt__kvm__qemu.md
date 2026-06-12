---
title: "Server 8.04 LTS: Virtualization / libvirt / kvm / qemu"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by chrisHHde on 2008-04-30
Hi there,

I have Ubuntu Hardy Server installed on a 64 bit system. Next I tried to get kvm / libvirt going, creating virtual machines with a bridged network.

I did manage to get my bridged network going, i.e. getting access to my local network and the internet, through interface br0.

But when trying to create a new virtual machine with ubuntu-vm-builder, I always get this message at the end of the creation (during which everything seemed to run fine):

```
libvir: QEMU error : No <source> 'network' attribute specified with <interface type='network'/>
```

Before I post all kinds of information regarding the configuration I used (which I will deliberately do, but right at the moment I have libvirt/kvm purged), I would like to know if anyone else had this error, too!?

I think I did everything right according to [Chapter 17. Virtualization]("https://help.ubuntu.com/8.04/serverguide/C/virtualization.html") in the Ubuntu help pages, except that (of course) I had to chose my own networking configuration (i.e. network addresses). In the help chapter, it doesn't say anywhere that any configuration files need to be changed (which in contrary seemed to actually be necessary, as I encountered some error messages, that I could resolve by myself - like f.ex. "sudo modprobe dm-mod")...

Anyways, at least for my 64 bit system the help page seems at least incomplete, and the out-of-the-box configuration seems to be a little buggy still.....

Has anyone got any experience with 64 bit virtualization, using qemu/libvirt/kvm as described in [Chapter 17. Virtualization]("https://help.ubuntu.com/8.04/serverguide/C/virtualization.html")!?

Google didn't help much so far...

---

### Post by GreatBunzinni on 2008-05-11
Could anyone please shed some light on this subject?

---

### Post by chrisHHde on 2008-05-19
Actually, meanwhile I managed to get bridged networking going.

I probably made some configuration error, but I couldn't find it.

I finally got everything right by first creating a virtual machine in the default network an later on switching it to the bridged network.

So actually, there shouldn't be any real problems, just some confusing configuration options, maybe.

---

### Post by pixel :-) on 2008-05-21
repost your problem here [http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

---

### Post by el_baby on 2008-10-31
Hi Chris,

I just had the same problem... did you solve it?

Did you post it at [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308) ? (I couldn't find it).

---

### Post by chrisHHde on 2008-11-02
Yes, I did solve it..... I had made a configuration error.

The configuration-XML of a virtual machine says

```

    <interface type='**network**'>
      <mac address='52:54:00:23:de:77'/>
      <source **network**='default'/>
    </interface>
```

(or the like), and when you choose "interface type='network'", two lines below there must be a tag "source network='...'".

In case you choose to have an "interface type='bridge'" you need to disclaim the source as "bridge" (followed by the bridged network's name).

Like this:
```

    <interface type='**bridge**'>
      <mac address='52:54:00:23:de:77'/>
      <source **bridge**='br0'/>
    </interface>
```

That's what I overlooked in the wiki.

So I guess you should check your config at the regarding places.

---

### Post by el_baby on 2008-11-03
Then I F***d up the wiki... it seemed to me that [[[https://help.ubuntu.com/community/KVM|the](https://help.ubuntu.com/community/KVM|the) wiki]] had different data from [[[http://doc.ubuntu.com/ubuntu/serverguide/C/virtualization.html|the](http://doc.ubuntu.com/ubuntu/serverguide/C/virtualization.html|the) official docs]] and, since it wasn't working for me, the wiki was wrong... now it seems that my mistake was someplace else...

I'm gonna do some more testing and repaire what [[[https://help.ubuntu.com/community/KVM?action=diff&rev2=151&rev1=150|I've](https://help.ubuntu.com/community/KVM?action=diff&rev2=151&rev1=150|I've) modified in the wiki]]...

Thanx for answering.

---

### Post by el_baby on 2008-11-03
Then I F***d up the wiki... it seemed to me that [[[https://help.ubuntu.com/community/KVM|the](https://help.ubuntu.com/community/KVM|the) wiki]] had different data from [[[http://doc.ubuntu.com/ubuntu/serverguide/C/virtualization.html|the](http://doc.ubuntu.com/ubuntu/serverguide/C/virtualization.html|the) official docs]] and, since it wasn't working for me, the wiki was wrong... now it seems that my mistake was someplace else...

I'm gonna do some more testing and repaire what [[[https://help.ubuntu.com/community/KVM?action=diff&rev2=151&rev1=150|I've](https://help.ubuntu.com/community/KVM?action=diff&rev2=151&rev1=150|I've) modified in the wiki]]...

Thanx for answering.

---

### Post by el_baby on 2008-11-03
sorry 'bout the double posting... apparently, the forum went down right after accepting my first post (but I couldn't see it).

---

