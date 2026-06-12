---
title: "Browser uploading pictures on the wrong side"
date: 2009-03-04
forum: x86 64-bit Users
---

### Post by NoaHall on 2009-03-04
I use a website called bilddagboken, a swedish image diary, however my trouble is that no matter which browser I use (Opera, Firefox, Galeon, Konqueror) the images which were taken by the camera on it's side, such as portraits, it uploads every image so it is landscape, no matter what I do to edit that image. I can't think why, but I think it may be the fact that uploading function of Bilddagboken uses something that 64 bit linux can't handle, because it worked just fine when I had 32 bit linux and on Windows. Also, my friends and people I know do not have this problem. Any suggestion will be appreciated. =)

---

### Post by Keith_Beef on 2009-03-04
> **NoaHall said:**
> I use a website called bilddagboken, a swedish image diary, however my trouble is that no matter which browser I use (Opera, Firefox, Galeon, Konqueror) the images which were taken by the camera on it's side, such as portraits, it uploads every image so it is landscape, no matter what I do to edit that image. I can't think why, but I think it may be the fact that uploading function of Bilddagboken uses something that 64 bit linux can't handle, because it worked just fine when I had 32 bit linux and on Windows. Also, my friends and people I know do not have this problem. Any suggestion will be appreciated. =)

I couldn't find my way to Bilddagboken to try this out, but here's what I think...

Set up your camera for small images, to make uploading faster during these tests.

Take three pictures.
[LIST=1]
[*]Landscape
[*]Portrait, right side of camera upwards
[*]Portrait, left side of camera upwards
[/LIST]

Don't use any image editing software, but give each image file name a prefix like "32bit__"

In 32-bit linux, use your favorite navigator to upload the pictures.

Rename the files by changing the prefix to "64bit__".

In 64-bit linux, use the same navigator as before to upload the pictures.

Now compare the uploaded pictures.

I suspect that some Java is being used to read the exif tags during upload, and that 64-bit Java is failing to correctly read the orientation tag.

PS. I couldn't connect to the Swedish or the English versions, but the [Finnish version ]("http://kuvapaivakirja.fi/p/main.html")is available. I'll try to run the experiment I described for myself with 32-bit and 64-bit Ubuntu tonight.

Now, the English version is available...I made an account, uploaded three pictures, but "the site is experiencing technical difficulties" and the Java uploader just crashes Netscape... not very inspiring...


K.

---

### Post by NoaHall on 2009-03-05
Yes, the other language versions aren't very good at all.

Anyway, when I uploaded a portrait picture, it loaded on the wrong side, and this was the same if the camera was on its right or left. Changing the name didn't changed anything, and it still came up on the wrong side. I expect too it is the java, because the site is pretty built on it.
Thanks for your help. 
Noah.

---

