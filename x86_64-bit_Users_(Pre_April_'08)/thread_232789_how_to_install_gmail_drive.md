---
title: "how to install gmail drive"
date: 2006-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by kodalisrikanth on 2006-08-09
Hi guys!
      I want to install gmail drive in ubuntu.I have downloaded the software & i have install it....;But my prob is How to mount the gmail drive in this.I know how to mount.But i dont know about how to mount the gmail drive in ubuntu........;
             Thank u

---

### Post by socratux on 2006-08-09
here it is explained:

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html)

maybe interesting as well:

[http://idea.zanestate.edu/archives/2005/07/using-gmail-as-a-hard-drive/](http://idea.zanestate.edu/archives/2005/07/using-gmail-as-a-hard-drive/)

i like the Xmailharddrive

---

### Post by sinaen on 2006-10-23
> **socratux said:**
> here it is explained:

[http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html)

maybe interesting as well:

[http://idea.zanestate.edu/archives/2005/07/using-gmail-as-a-hard-drive/](http://idea.zanestate.edu/archives/2005/07/using-gmail-as-a-hard-drive/)

i like the Xmailharddrive

Right on dude!!! it rocks with xmailharddrive:)

---

### Post by lukosanthropos on 2007-10-24
followed the instructions on the website and all i get is 

```
Ignored option :rw
HTTP Error 400: Bad Request
fuse: bad mount point `/media/gmail': No space left on device
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 166, in <module>
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 92, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/lib/python2.5/site-packages/gmailfs.py", line 1180, in main
    server.main()
  File "/usr/lib/python2.5/site-packages/fuse.py", line 713, in main
    main(**d)
fuse.FuseError: filesystem initialization failed

```
can anyone help?

---

### Post by sinaen on 2007-10-24
maybe you cannot write to the mountpoint.? do a ls -al /media or where your mountpoint lies.

---

### Post by Mevsthevoices on 2007-11-26
You need to install the FUSE perl bidings, that fixed mine

---

### Post by clarknova on 2008-01-03
```
sudo apt-get install libfuse-perl
```

Edit: Sorry, I posted only a partial solution here. The reason you want to install libfuse-perl is so you can update your libgmail to a newer version than what's packaged in gutsy, thus ```
sudo easy_install --upgrade libgmail
```

I learned this here: [http://ubuntuforums.org/showthread.php?t=596352](http://ubuntuforums.org/showthread.php?t=596352) and it worked for me. Also make sure your mount point has the necessary permissions (mine is drwxrwxrwx).

db

---

### Post by ~LoKe on 2008-01-03
I completely forgot about gmail drive ever since I gave up Windows.  This reminded me to give it another shot (wasn't terribly great way back when).

Thanks (sorry this post doesn't help ya).

---

