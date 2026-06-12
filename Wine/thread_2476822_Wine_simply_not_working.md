---
title: "Wine simply not working"
date: 2022-07-08
forum: Wine
---

### Post by jonfisher on 2022-07-08
Ubuntu 22.04 lts

I have used Wine with previous Ubuntu versions, but can't get it to work with 22.04 lts...

I've tried installing it from the software center, using Synaptic, using terminal.  I've attempted to run various programs that end with ".exe"
 
Furthermore, when I right click a file, I don't get the option to open with Wine, as it use to be the case.  

Also, I've tried using Wine on both my HP desktop and HP laptop.  I'm baffled.

After uninstalling Wine, I'm currently installing it using this page:  [https://vitux.com/how-to-install-wine-on-ubuntu/](https://vitux.com/how-to-install-wine-on-ubuntu/)

I can report:

```
$ wine --version
wine-6.0.3 (Ubuntu 6.0.3~repack-1)

```

p.s. i know Wine isn't an application, but it doesn't show up by clicking "Show Applications" on the lower left portion of the dock.

---

### Post by Claus7 on 2022-07-08
Hello,

> **jonfisher said:**
> Ubuntu 22.04 lts

The same.

> **jonfisher said:**
> I have used Wine with previous Ubuntu versions, but can't get it to work with 22.04 lts...

Let's see...

> **jonfisher said:**
> I've tried installing it from the software center, using Synaptic, using terminal.  

This a little bit confusing: these are 3 different ways of installing wine. Have you tried all of them? If affirmative, have you removed .wine folder every time you attempted a new installation? Synaptic is fine by the way.

> **jonfisher said:**
> I've attempted to run various programs that end with ".exe"
You should be able to see errors that will guide you.
You can open a terminal where the .exe file exists and type:
wine .exe (the full exe filename)
 
> **jonfisher said:**
> Furthermore, when I right click a file, I don't get the option to open with Wine, as it use to be the case.  

Gone are the days... You could create a custom command though: [https://archived.forum.manjaro.org/t/did-you-know-you-can-add-custom-commands-to-nautilus-right-click-menu/116160](https://archived.forum.manjaro.org/t/did-you-know-you-can-add-custom-commands-to-nautilus-right-click-menu/116160)
this link will give you an idea.

> **jonfisher said:**
> Also, I've tried using Wine on both my HP desktop and HP laptop.  I'm baffled. 

You should be able to see verbally some error messages as stated above, and avoid multiple wine installations.

> **jonfisher said:**
> After uninstalling Wine, I have attempted to install it using this page:  [https://vitux.com/how-to-install-wine-on-ubuntu/](https://vitux.com/how-to-install-wine-on-ubuntu/)

I can report:

```
$ wine --version
wine-6.0.3 (Ubuntu 6.0.3~repack-1)

```

The procedure mentioned there is about bionic and not jammy. Yet, we have the same version installed.

> **jonfisher said:**
> p.s. i know Wine isn't an application, but it doesn't show up by clicking "Show Applications" on the lower left portion of the dock.
It doesn't. The only thing you will be able to see is Windows Applications as a separate category when using Applications extension of gnome-shell, or under Applications using flashback. Also, if you install winetricks, you will come across this icon under gnome-shell.

Regards!

---

### Post by jonfisher on 2022-07-08
> **Claus7 said:**
> Hello,



The same.



Let's see...

  

This a little bit confusing: these are 3 different ways of installing wine. Have you tried all of them? If affirmative, have you removed .wine folder every time you attempted a new installation? Synaptic is fine by the way.


You should be able to see errors that will guide you.
You can open a terminal where the .exe file exists and type:
wine .exe (the full exe filename)
 
  

Gone are the days... You could create a custom command though: [https://archived.forum.manjaro.org/t/did-you-know-you-can-add-custom-commands-to-nautilus-right-click-menu/116160](https://archived.forum.manjaro.org/t/did-you-know-you-can-add-custom-commands-to-nautilus-right-click-menu/116160)
this link will give you an idea.

 

You should be able to see verbally some error messages as stated above, and avoid multiple wine installations.



The procedure mentioned there is about bionic and not jammy. Yet, we have the same version installed.


It doesn't. The only thing you will be able to see is Windows Applications as a separate category when using Applications extension of gnome-shell, or under Applications using flashback. Also, if you install winetricks, you will come across this icon under gnome-shell.

Regards!

I am unable to remove the wine folder inside of the "lib" folder with the GUI...  No option when right clicking or via clicking wine to highlight it and then pressing delete....

---

### Post by Claus7 on 2022-07-08
Hello,

> **jonfisher said:**
> I am unable to remove the wine folder inside of the "lib" folder with the GUI...  No option when right clicking or via clicking wine to highlight it and then pressing delete....

just open Files, then on the right hand side of the titlebar click the button with three horizontal lines and choose show hidden files. There should be a .wine folder there. Just remove it.

Regards!

---

### Post by jonfisher on 2022-07-08
> **Claus7 said:**
> Hello,



just open Files, then on the right hand side of the titlebar click the button with three horizontal lines and choose show hidden files. There should be a .wine folder there. Just remove it.

Regards!

What folder would the hidden wine folder be in please...  I don't see it in the home or lib folder...

I just purged wine64 -  Also used Synaptic to completely remove Wine and even Wine32...  am going to proceed to install in from the software center... Kinda trying everything...

---

### Post by jonfisher on 2022-07-09
[QUOTE=Claus7;14103454]
You should be able to see errors that will guide you.
You can open a terminal where the .exe file exists and type:
wine .exe (the full exe filename)
 
ok, I went to the folder and attempted to run one of the programs.  It appears that it wants the 32 bit version of wine installed also - even though this time I installed it from Ubuntu Software center (and my system is 64 bit)

```

$ wine CCS64.exe
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32"
0024:err:module:process_init L"C:\\windows\\system32\\CCS64.exe" not found

*AND*

$ 0094:err:rpc:I_RpcReceive we got fault packet with status 0x1c010003


```

I can install the 32 bit version using Synaptic or terminal.  I've done this before, so I dunno what difference it will make...

---

### Post by jonfisher on 2022-07-09
upddate.  I installed the 32 bit version.  Opened the correct folder and typed "wine CCS64.exe" into terminal.  

Got this.

```

$ wine CCS64.exe
0024:err:module:process_init L"C:\\windows\\system32\\CCS64.exe" not found

```

update:  The exact folder where CCS64.exe is located is Home/Downloads/Release

---

### Post by jonfisher on 2022-07-09
update.  I did in terminal, "cd Downloads" then "cd Release" then typed wine CCS64.exe

and it worked!

Would be nice in the future if right clicking an .exe file will bring that Wine option up again (to execute a program with Wine), but beggers can't be choosers - smiles...

update:  I learned that I can right click the folder that it's in and select open in terminal, then type wine CCS64.exe    (learn something new every day, smiles!)

---

