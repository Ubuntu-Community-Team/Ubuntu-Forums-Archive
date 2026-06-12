---
title: "Failed to open URL &quot;~/.wine/dosdevices/c:&quot;."
date: 2008-05-07
forum: Wine
---

### Post by xXChaoticNoiseXx on 2008-05-07
Specs:
Xubuntu Hardy Heron
Compiz Fusion + Emerald
Wine is the latest version

ok i have 2 problems regarding wine.

I cannot browse my c:/ Drive using the menu shortcut. I recieve the error:

[B]Failed to open URL "~/.wine/dosdevices/c:".
The URL "~/.wine/dosdevices/c:" is not supported.[/B]

or

[B]Failed to open URL "~/.wine/drive_c:".
The URL "~/.wine/drive_c:" is not supported.[/B]

if i input either one of these URLS into the terminal they execute and bring up the drive

my next problem is when ever i run the command:

**$ wine guild wars -opengl**

i get the error

[B]wine: could not load L"C:\\windows\\system32\\guild.exe": Module not found
[/B]

Would the module be openGl or is the problem in wine?

Im not a master but im fairly well versed in linux so i can do complex task if the solution calls for it. Please help me. I dont know what to do

---

### Post by stupidforum on 2008-05-08
Usually you would want to run:
wine c:\\Program\ Files\\Guild\ Wars\\Gw.exe
not sure if the -opengl flag works for gw either.

---

### Post by Specto on 2008-05-24
> **xXChaoticNoiseXx said:**
> Specs:

I cannot browse my c:/ Drive using the menu shortcut. I recieve the error:

[B]Failed to open URL "~/.wine/dosdevices/c:".
The URL "~/.wine/dosdevices/c:" is not supported.[/B]

or

[B]Failed to open URL "~/.wine/drive_c:".
The URL "~/.wine/drive_c:" is not supported.[/B]


A simple but inperfect solution:

```
sudo mousepad /usr/share/applications/wine-browsedrive.desktop
```

change line:

```
Exec=xdg-open ~/.wine/drive_c
```

to

```
Exec=xdg-open /home/your_user_name/.wine/drive_c
```


Wait about one minute for changes to take effect.

Don't forget to change **your_user_name** to your user name ;)

---

### Post by gsmanners on 2008-05-25
Since I have both Nautilus and Thunar (as well as a number of other file managers), what happens here is that when I invoke "xdg-open ~/.wine/drive_c" through xfrun4 or through the menu, it loads in Nautilus. However, if I invoke "bash -c 'xdg-open ~/.wine/drive_c'" through xfrun4, then I get Thunar (because Bash takes care of the ~ I guess).

I think what happens is that xdg-open attempts to load Thunar and fails because Thunar doesn't do Bash-type completion.

---

### Post by Hypocritus on 2008-12-02
> **Specto said:**
> A simple but inperfect solution:

```
sudo mousepad /usr/share/applications/wine-browsedrive.desktop
```

change line:

```
Exec=xdg-open ~/.wine/drive_c
```

to

```
Exec=xdg-open /home/your_user_name/.wine/drive_c
```


Wait about one minute for changes to take effect.

Don't forget to change **your_user_name** to your user name ;)

This actually is a great solution, even if it's a workaround for something that might ought to work already. Thanks **Specto**! You helped me!

---

### Post by Redline21 on 2009-04-06
Yes, it is a nice solution, but it only works for one user. Any other user is going to have problems, as it will not be pointing to the wine directory in their profile. We really need something that will make this work for all users.

---

### Post by mattvision on 2009-08-16
> **gsmanners said:**
> Since I have both Nautilus and Thunar (as well as a number of other file managers), what happens here is that when I invoke "xdg-open ~/.wine/drive_c" through xfrun4 or through the menu, it loads in Nautilus. However, if I invoke "bash -c 'xdg-open ~/.wine/drive_c'" through xfrun4, then I get Thunar (because Bash takes care of the ~ I guess).

I think what happens is that xdg-open attempts to load Thunar and fails because Thunar doesn't do Bash-type completion.

Thank you!
I replaced Exec=xdg-open ~/.wine/drive_c with Exec=bash -c 'xdg-open ~/.wine/drive_c'
Works great for all users!

---

