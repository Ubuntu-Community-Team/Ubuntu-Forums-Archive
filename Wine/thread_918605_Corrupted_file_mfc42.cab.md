---
title: "Corrupted file: mfc42.cab"
date: 2008-09-13
forum: Wine
---

### Post by SwissPT88 on 2008-09-13
I was having trouble installing ies4linux IE6 on my Ubunty Hardy..

I kept getting the error:

"Corrupted file: mfc42.cab"

After some searching I saw how to get to where the .cab file _should_ be. Type:

```

cd .wine/drive_c/windows/system32

```
Once I was in that folder I saw that the mfc42.cab file I needed was NOT there.  I needed to download mfc42.dll apparently and then copy that or rename it to mfc42.cab.  I googled mfc42.dll and downloaded it quite easily.. 

After downloading it, I had this:

mfc42.zip

So I did:

```

unzip mfc42.zip 

```
..which gave me the mfc42.dll file. Then i did:

```

cp mfc42.dll mfc42.cab

```
and I had the file I needed. Then I just needed to stick that file in the folder where it should have been all along, the one I mentioned earlier.. So I did..

```

cp mfc42.cab .wine/drive_c/windows/system32

```
That's it. Go back to the ies4linux-2-whatever folder and type:

```

./ies4linux 

```
..and should install correctly.  Hopefully this will help some poor soul :)

---

### Post by v_krishna on 2008-10-23
as per [http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html](http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html) I think the problem has to do with wget timing out. you solved the issue by downloading the specific file manually, but you should also be able to change the wget settings (run ./ies4linux, click the advanced tab, and change the wget settings to "-c -t 10 -T 10")

---

### Post by voldemorte on 2009-05-11
I get this error message when I manually downloaded the .dll file n replaced it. > /home/voldemorte/.ies4linux/downloads/mfc42.cab: no valid cabinets found  An error occured when trying to cabextract some files.

 help needed

---

### Post by voldemorte on 2009-05-11
And when I don't replace the file it say the file not found

---

### Post by benjamindlevin on 2009-09-26
i too am having this problem.  at first it would tell me corrupt mfc42.cab, but then i found the fix here.  however, now it begins as if to install and just freezes.  

has anyone been able to remedy this?

thanks in advance

---

### Post by oldmankit on 2010-01-15
I'm having a similar error, however I'm totally unable to find mfc42.cab.  All links on the net seem to point here:

[http://activex.microsoft.com/controls/vc/mfc42.cab](http://activex.microsoft.com/controls/vc/mfc42.cab)

However, that link isn't doing anything.  I can get mfc42.dll easily from my windows xp partition, but not the cab file which seems to be needed for installation.

Is anybody able to send me this file, or show me a working link to find it?

Thanks.

---

