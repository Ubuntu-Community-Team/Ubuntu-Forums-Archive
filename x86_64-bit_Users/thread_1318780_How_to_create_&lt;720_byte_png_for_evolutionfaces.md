---
title: "How to create &lt;720 byte png for evolution/faces"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by Oldhacker on 2009-11-07
Having made a switch from Thunderbird to Evolution today and being generally impressed with improved compatibility with Gnome, I am attempting to create a working png photo that will function in the "faces" plugin.

Using Gimp, I selected the photo and saved it as a 48x48 pixel png.
So far, so good. Then, I created a subdirectory in Evolution called Faces, there being none by default. I moved the png image into this subdirectory. However, when I attempt to insert "face" into an email, it tells me that the png must be <720 bytes!

How do I accomplish this?

Thanks

---

### Post by Oldhacker on 2009-11-08
More googling brought the answer. 

openssl base64 -e -A < face.png > ~/.evolution/faces

There were some more complications, like using apt-get install for a couple of peripheral utilities, but it can be done. 

Now that I have solved the challenge, whether it was worth it is an open question.

---

