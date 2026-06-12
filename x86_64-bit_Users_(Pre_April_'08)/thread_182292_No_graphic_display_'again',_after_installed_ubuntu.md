---
title: "No graphic display 'again', after installed ubuntu."
date: 2006-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-05-25
On my PC (64AMD) I have one hd40 (slave, where I run ubuntu 6.06) and another hd80 (the master, where I've just installed ubuntu). In other words I have 120GB on my PC.
Now, because my hd40 is full, I w'd like to transfer datos to the 80hd.
I dont know how.

WHAT HAD I TRYED?
Installed ubuntu 5.10 64bit on the 80hd, but didnt display graphic (again, "it had happened when I installed ubuntu on 40hd as well). So then, I tryed to do what I'd done before, 'ctrl+alt+F1', and logged in:

Typed 'lspci' to get the graphic card details (nVidia Corporation NV34 [GeForce FX5200LP] (rev a1), then:

'sudo dpkg-reconfigure xserver-xorg'

then I choose:

'nv' 

enter:

'nv nVidia FX5200LP' 

And the problem was suppost to be sorted, but it didn't.

So I rebboted and logged in to ubuntu on 40hd.
I've tryed to save datos on hda2, but no allowed.(not saving datos in, or evan deleting the hda1 or 2 or 3 to mount again). (I had mounted them before (hda1 hda2 hda3)).
So on the terminal, I tryed:

'sudo mount /dev/hda2 /mnt/hda2'  (by the way I've tryed without 'sudo')

then enter, came up 

'mount: you must specify the file system file'

then I typed 

'cd hda2' 

enter 

'ls'

Didn't show any thing, because there is nothing there, then nautilus. ... I can only open, but not alowed to copy or even delete to mount again.

So basically, I would like to use both hdds.
WHAT CAN I DO TO USE BOTH HDDS AT THE SAME TIME?
Or](*,) 
HOW CAN I DISPLAY GRAPHIC? (what have I missed?)

---

### Post by Mustard on 2006-05-25
Have you tried using the 'vesa' drivers instead of the 'nv' drivers?

> sudo mount /dev/hda2 /mnt/hda2 
mount: you must specify the file system file

Well the error message has basically told you what the problem is.  If you need to know more about a command you can use the 'man' command to read the manual.

```
man mount
#this will open the manual for the mount command
#press 'q' key to exit the manual
```

```
sudo mount -t ext3 /dev/hda2 /mnt/hda2 -o defaults,rw
#this command include the -t option
#which specifies the filesystem type 'ext3'
#its also using the -o option to specify extra options
#ie defaults, and rw (read/write)
```

---

### Post by sidy on 2006-05-26
```
sudo mount -t ext3 /dev/hda2 /mnt/hda2 -o defaults,rw

#this command include the -t option
#which specifies the filesystem type 'ext3'
#its also using the -o option to specify extra options
#ie defaults, and rw (read/write)
```

I've tryed the above code, but when I go to hda2 on nautilus I still can't copy anything into hda2. 
I also clicked with the right botton of the mouse on hda2 went to permisstion to be able to read, write, excecute, but says at the bottom 'You are not the onwer, so you can't change these permissions'.
What should I done?

And when I put on terminal 'sudo mount /dev/hda2 /mnt/hda2'  , still says 'you must specify the filesystem type'. 

What is the procedure?

rgds.

---

### Post by sidy on 2006-05-26
'vesa' didn't work either. (but when I switch the pc on it says NVIDIA)

What is the procedure?

rgds.

---

### Post by Mustard on 2006-05-26
Reading over your post, I'm getting a bit lost.

---

### Post by sidy on 2006-05-28
[QUOTE=Mustard]Reading over your post, I'm getting a bit lost.[/QUOTE]

Sorry! (I've massed/mixed up information) Basically...

When I typed:

'sudo mount -t ext3 /dev/hda2 /mnt/hda2 -o defaults,rw'    #came up:

'already mounted or busy'

EXTRA INFORMATION:
This morning I installed again the ubuntu 5.10 64bit on my AMD64 PC, for others reasons (installed on 65gb of my 80hd, the other 15 is for windows already installed).
As soon as the installation finished I have a black screen with a dash on the ledft-top-corner and that sound biiiiii, biiiiii, bii, bii!, but few seconds after I heard the song of ubuntu-gnome... as I was having the nomal graphic screen displaying. 

Then I 'Ctrl+Alt+F1'

And again I typed 

'sudo dpkg-reconfigure xserver-xorg'

then I choose:

'nv'

enter:

'nv nVidia FX5200LP'

then:

'sudo /etc/init.d/gdm stop'

then:

'sudo /etc/init.d/gdm restart'

And I was suppost to have graphic screen displaying, but it didn't.

So right now I would need to know how the have graphic screen displaying.

Otherwise I can boot the PC through the hd40 and from there I will be ok to use both hds. (I have learned, on the terminal 'sudo nautilus' and on root I can change the permissions). But the thing is 
I WOULD LIKE TO BOOT ON DIRECT ON hda AND HAVE GRAPHIC DISPLAYING AS I NORMALLY SHOULD! Not through the other hd.

If you could sitll help would be great.

Thank you again.

---

