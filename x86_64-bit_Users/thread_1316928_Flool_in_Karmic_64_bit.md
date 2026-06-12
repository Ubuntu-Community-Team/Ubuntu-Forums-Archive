---
title: "Flool in Karmic 64 bit"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by nixed242 on 2009-11-06
I'm trying to get Floola to work in Karmic. I've downloaded the binary from their website, and I've also installed all the necessary libraries, including libstd++5. However, Floola still gives me an error message - 

```
./Floola: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

The libstc__5 library is located in /usr/lib/ and I've also tried putting a symlink in /usr/local/lib with no results. 

Does anyone know where Floola looks to find the libstdc++.so.5 file exactly since it's not finding it? Could I just drop a symlink for libstdc++.so.5 in the correct folder to make Floola work?

---

### Post by vancouverite on 2009-11-06
Hi nixed242,
I checked synamptic and it looks like Karmic uses libstdc++6, not 5.  

You can get the deb file for the libstdc++5 from the ubuntu packages site for Jaunty:

[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

Download the deb and:
sudo dpkg -i [package].deb

I haven't done this myself, so I don't know if it will allow v5 and v6 to co-exist, and I have no idea what uninstalling v6 will do.

If it wants to uninstall v6 you could also try 
sudo dpkg -x [package].deb and it will just extract the contents, not install it.  Then just manually move libstc++.so.5 to /usr/lib.

Van

---

### Post by blueridgedog on 2009-11-08
I fixed mine and made note of the steps:

[http://ubuntuforums.org/showthread.php?p=8275834#post8275834](http://ubuntuforums.org/showthread.php?p=8275834#post8275834)

After you extract the files, change into the directory that was made (usr) then into the next (lib) and copy libstdc++.so.5 (just a link) and libstdc++.so.5.0.7 to /usr/lib32 with a sudo.

If you get stuck, feel free to reply.

---

### Post by nixed242 on 2009-11-12
> **blueridgedog said:**
> I fixed mine and made note of the steps:

[http://ubuntuforums.org/showthread.php?p=8275834#post8275834](http://ubuntuforums.org/showthread.php?p=8275834#post8275834)

After you extract the files, change into the directory that was made (usr) then into the next (lib) and copy libstdc++.so.5 (just a link) and libstdc++.so.5.0.7 to /usr/lib32 with a sudo.

If you get stuck, feel free to reply.

Thank You. Your fix worked! I had put the files in /usr/lib which is why it didn't.

---

