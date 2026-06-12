---
title: "Can I please get some guidance on learning more about .wine?"
date: 2012-05-10
forum: Wine
---

### Post by SerFaren on 2012-05-10
So, I recently downloaded a save-editor for Mass Effect 2, and I can't figure out how to get it to run properly. I extracted to files to a folder I created named "ME2 Save Editor" and I know I have to run it on .wine. I marked it as executable, however .Wine refuses to run it. Like, I'll

1.) Right Click
2.) Open with...
3.) Wine Program Loader

And it won't do a single thing. It will look like it's loading, but it won't be o_o.
Does anyone know what I'm doing incorrectly? Or a link that could point me to the direction of doing it properly?

(This is what I downloaded, by the way) Mass Effect 2 Gibbed Save Editor [Modified] (From [http://********************/project/4373/#files](http://********************/project/4373/#files))

(I also WANT to download modio, however I don't know if it will simply run off of Ubuntu.)
(Sorry if I didn't stay on topic, per se...)

---

### Post by klashelle on 2012-05-10
I've had this problem and can usually make it work by launching from terminal. wine /path/to/exe

---

### Post by oldos2er on 2012-05-10
Moved to Wine.

---

### Post by SerFaren on 2012-05-10
> **klashelle said:**
> I've had this problem and can usually make it work by launching from terminal. wine /path/to/exe

I just finished trying this, and it says...
```
*******@*******-MT6730:~$ wine /home/*******/.wine/dosdevices/c:/users/*******/me2save/Gibbed.MassEffect2.SaveEdit.exe

wine: cannot find L"C:\\windows\\system32\\plugplay.exe"

wine: Install the Windows version of Mono to run .NET executables
```

---

### Post by flemur13013 on 2012-05-10
I make little scripts like this:

```
cd /home/usename/.wine/drive_c/Programs/IrfanView
wine i_view32.exe &
```

---

### Post by cogadh on 2012-05-11
> **SerFaren said:**
> I just finished trying this, and it says...
```
*******@*******-MT6730:~$ wine /home/*******/.wine/dosdevices/c:/users/*******/me2save/Gibbed.MassEffect2.SaveEdit.exe

wine: cannot find L"C:\\windows\\system32\\plugplay.exe"

wine: Install the Windows version of Mono to run .NET executables
```
Did you do what it says and install Mono? You can use winetricks to do that for you, it should already be installed with the default Wine package.

---

