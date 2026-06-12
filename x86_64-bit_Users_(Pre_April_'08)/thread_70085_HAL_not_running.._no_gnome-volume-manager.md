---
title: "HAL not running.. no gnome-volume-manager"
date: 2005-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by dmallery on 2005-09-28
hi
i am running an up to date (apt) amd64 machine..  is very stable and useful.
when x starts up, i get a box saying that HAL can't start.  subsequently gnome-volume-manager can't work.. it reports that it can't find hal.
(btw: "which hal" yields no response)
is this a current bug?  how does one start hal?
i really need to get to my camera (/media/usbdisk).
i would be so grateful for a clue...
thanks in advance
dave mallery

---

### Post by mlomker on 2005-09-28
HAL is supposed to start during boot-up.  You might want to look through the output of **dmesg | less** to see if there are any errors regarding it.

I'd search Google and here with the exact error message (either from dmesg or the gnome message) as the next step.

---

### Post by rplantz on 2005-10-01
I would use Synaptic (or apt-get) to install hal.

I accidentally (well, stupidly is more accurate) deleted hal a few days ago. I was trying to get my usb printer to come alive without having to reboot. It seemed like usbmgr might give me more control. (This was based on the name -- 1st stupid thing.) It was late, and I didn't look carefully at the things that would be *removed* when usbmgr was installed -- 2nd stupid thing.

usbmgr didn't help, but I couldn't get to most devices. I managed to get to my Hoary CD and get hal back. Sorry, I don't recall precisely what I did. But once I got hal back, I was able to restore things.

I still have to have the printer on when I boot in order to use it.

Bob

---

### Post by mlomker on 2005-10-02
> Sorry, I don't recall precisely what I did. But once I got hal back, I was able to restore things.

```

sudo apt-get install --reinstall hal

```

Might want to do Dbus as well:

```

sudo apt-get install --reinstall dbus-1

```

---

### Post by Ranime on 2005-10-08
Tnx a lot!!

I had the hal problem for 5 months allready! Your comment worked like a charm. for a week now I haven't gotten the message that HAL wasn't initialized.

Superb!! \\:D/

---

