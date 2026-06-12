---
title: "Can't download updates"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by hansmax on 2009-01-04
I'm not sure this falls under the 64-bit category, but I'm new here so bear with me, please.  I've been trying to download updates, and keep getting the following message:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...ntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/...ntu2_amd64.deb)
404 Not Found

I have Ubuntu 8.04.01 (64-bit) installed with Wubi on my C: drive in WinXPMCE. I have the same version (32-bit) installed in my second computer upstairs (this one is on its own partition), and downloads work fine up there. I have Internet working. (Cable) Upstairs is wireless off my cable. When I enter the IP Address in Firefox in WinXP, it also says that it could not be found. (I should mention that when I tried yesterday, the error message gave me an address, today it didn't). Anyone have any ideas?

---

### Post by 2hot6ft2 on 2009-01-04
That's not a full address. And that's why it can't be found.
The ... should have something else there wherever you got it it's wrong.
Try copying the whole line. And if you get a link on a page you right click and copy link location otherwise you end up with what you have there. An incomplete link.

---

### Post by hansmax on 2009-01-04
No, I mean that I entered the IP address that they provided yesterday in Firefox, both in Ubuntu and WinXP.  It could not find the page either way.  I just tried pasting the complete address into the address bar of a new window, and it told me page could not be found.  I got it from the error message that the Update Manager put out.  If that is not a correct address, how do I redirect it to the correct one?  This is what I got and tried:

//us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_0.2.5-0ubuntu2_amd64.deb

---

### Post by hansmax on 2009-01-04
//us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_0.2.5-0ubuntu2_amd64.deb

This is the address that I got from the update manager's error message and just tried again, with no luck.  Yesterday I tried the actual IP address that was provided, and that didn't work either.  Sorry for the double post.  I got confused.

---

### Post by dragos240 on 2009-01-04
try reloading your software sources, i hope that solves this.

---

### Post by hansmax on 2009-01-04
That did the trick, I think.  Before it offered me 6 updates and didn't download any of them.  This time it offered me 226 updates and downloaded them all.  Thanks, dragos240, and thanks to all who replied.

---

### Post by dragos240 on 2009-01-04
> **hansmax said:**
> That did the trick, I think.  Before it offered me 6 updates and didn't download any of them.  This time it offered me 226 updates and downloaded them all.  Thanks, dragos240, and thanks to all who replied.

Thanks! By the way nice signature.

---

