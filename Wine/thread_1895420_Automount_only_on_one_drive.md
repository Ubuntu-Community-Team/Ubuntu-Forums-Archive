---
title: "Automount only on one drive"
date: 2011-12-14
forum: Wine
---

### Post by Automat2 on 2011-12-14
I have got two dvd drives.

I modified /etc/fstab adding these lines:
```
/dev/cdrom             /media/cdrom   auto    ro,user,noauto,unhide   0      0
/dev/cdrom1             /media/cdrom1   auto    ro,user,noauto,unhide   0      0
```Then, I created the two subfolders "cdrom" and "cdrom1" in "/media"

I mapped Winecfg to d: and e: and changed the default to "CDROM" in both drives d: and e:

Now, ```
ls -la ~/.wine/dosdevices/
``` gives me the following output:
> drwxrwxr-x 2 jordi jordi 4096 2011-12-14 21:54 .
drwxrwxr-x 4 jordi jordi 4096 2011-12-14 23:14 ..
lrwxrwxrwx 1 jordi jordi   10 2011-11-28 19:30 c: -> ../drive_c
lrwxrwxrwx 1 jordi jordi   12 2011-12-14 21:53 d: -> /media/cdrom
lrwxrwxrwx 1 jordi jordi   13 2011-12-14 21:54 e: -> /media/cdrom1
lrwxrwxrwx 1 jordi jordi   10 2011-12-02 16:10 f:: -> /dev/cdrom
lrwxrwxrwx 1 jordi jordi   11 2011-11-28 19:36 h: -> /home/jordi
lrwxrwxrwx 1 jordi jordi    1 2011-11-28 19:30 z: -> /
And DvdFab only works on my secondary drive, that has been renamed as d: in wine but not on my primary.

Do you know any solution to make wine work on both drives and how to reassign the driver letters as Ubuntu does? This is d: to the top drive and e: to the bottom one.

---

### Post by PaJoe on 2011-12-15
DvdFab had worked correctly for me until I upgraded to 11.10. I tried both Crossover Office and wine but the auto mount no longer works correctly. Automount worked with 11.04 and previous versions. Previous versions dvdfab would get the name of the dvd without any intervention, it was automatic.I thought that previously when using the wine configuration tool and you selected autodetect it found the drives.

I did not change fstab  and I did not change fstab with previous versions that worked OK 

This is how I do it:

On my system I must wait until Ubuntu mounts the drive, then use 

winecfg > drives > autodetect  then I find the drive, may be G may be something else, after I click on the drive  in the "path"  box it will show 

/media/  


Then I click on the  "browse" button  and select the actual dvd with the proper name and hit apply, the next time dvdfab starts it will find the dvd and use the correct name. This method works with both my optical drives.
 
I must do this with every dvd because Ubuntu renames the mount point when it mounts a different dvd and this procedure must be done each time before starting  dvdfab. Crossover office is the same way and it uses the same wine configuration  setup as wine.

Once again, with 11.04 and previous versions, everything was automatic and dvdfab found the drive with the correct name , it stopped working  with 11.10.  I check the forums whenever i get a chance hoping to find a fix.

Here is a similar thread on the problem with Crossover office, however Codeweavers Support offers no help because dvdfab is not one of their supported applications.:

[http://www.codeweavers.com/support/tickets/browse/?ticket_id=865091;list=6;ticket_level=0](http://www.codeweavers.com/support/tickets/browse/?ticket_id=865091;list=6;ticket_level=0)

If you find a solution please post it, until then I will continue to use winecfg - drives - browse method  listed above to assign the drive. It's not bad unless you want to do several dvds, then you must close dvdfab, manually assign the drive and restart dvdfab.


BTW : I did try various versions of dvdfab and get the same results, works in 11.04 not 11.10

---

### Post by Automat2 on 2011-12-29
I looked on the web, and found these solutions:

```

ln -s /mnt/cdrom ~/.wine/dosdevices/d:
ln -s /mnt/cdrom1 ~/.wine/dosdevices/e:

```Which seems to have sorted the problem.

And then, I found this other workaround, but I haven't tried it.

```
$ mkdir /home/user/.wine/dosdevices 
$ cd /home/user/.wine/dosdevices 
$ ln -s ../fake_windows c: 
$ ln -s /mnt/cdrom d:
```

---

