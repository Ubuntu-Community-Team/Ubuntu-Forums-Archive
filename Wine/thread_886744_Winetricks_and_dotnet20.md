---
title: "Winetricks and dotnet20"
date: 2008-08-11
forum: Wine
---

### Post by Cuppy on 2008-08-11
Hi, I seem to be having some trouble with installing dotnet20 with winetricks. I did a search but it doesn't seem like i've gotten any results :(

It's something about sha1sum mismatch. Here's the error message:

gregory@Cuppy:~$ sh winetricks dotnet20
Setting Windows version to win2k
Executing wine regedit /home/gregory/.wine/drive_c/winetrickstmp/set-winver.reg
Executing cp -f /home/gregory/.winetrickscache/dotnet20/l_intl.nls /home/gregory/.wine/drive_c/windows/system32/
sha1sum mismatch!  Rename /home/gregory/.winetrickscache/dotnet20/dotnetfx.exe and try again.


I'd appreciate any help, thanks!

EDIT: Reading through the forum, I've manage to fine the hidden .winetrickscache folder. But I'm still lost as to what I should be renaming dotnetfx.exe to...

---

### Post by FlyingIsFun1217 on 2008-08-11
Check the WineHQ AppDB listing to see if there's anything (or if there's even a listing).

FlyingIsFun1217

---

### Post by Cuppy on 2008-08-11
Well, I got desperate and decided to delete the folder instead of trying to rename it. Then I ran sh winetricks dotnet20 again and it worked!

Hope this'll help someone else :)

---

### Post by Jarzyna on 2009-03-03
Welcome, I have problem with winetricks for Wine; I want download corefonts and flash, then I type:
```

sh winetricks corefonts flash

```
Something that I see after this command:
```

ja@ubuntu:~$ sh winetricks corefonts flash
Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://easynews.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
--2009-03-02 15:13:04--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Translacja easynews.dl.sourceforge.net... 69.16.168.245
&#321;&#261;czenie si&#281; z easynews.dl.sourceforge.net|69.16.168.245|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: nieznana [application/octet-stream]
Zapis do: `arial32.exe'

    [    <=>                                         ] 514.314     25,8K/s   w 27s

2009-03-02 15:13:34 (18,7 KB/s) - zapisano `arial32.exe' [514314]

sha1sum mismatch! Rename /home/ja/.winetrickscache/./arial32.exe and try again.

```


Could somebody tell me how I install this? Maybe is a newer version of winetricks's script?


**EDIT.**
> **Cuppy said:**
> Then I ran sh winetricks dotnet20 again and it worked!
I trying that for a lot of times, but everytimes I have sha1sum mismatch. (And with all winetricks for example dotnet, flash or corefonts).

---

### Post by Jarzyna on 2009-03-08
I'm refreshing my post with problem. ;/

---

### Post by cogadh on 2009-03-08
Did you actually delete the .winetrickscache directory from your home directory? That should force it to re-download everything and correct the error. Also, instead of trying to run them all at once, run them separately, i.e. "sh winetricks corefonts" then "sh winetrick flash".

---

### Post by Jarzyna on 2009-03-08
Wow, and now it's run.. thanks. ;)

I delete "~/.wine" and "~/.winetrickscache" and typed "winecfg" (from another your post from topic about this problem"). Now, I downloaded with winetrick few times and at 3-4 time sha1sum match. 

Thanks one more time. ;)

---

### Post by yug23 on 2009-10-09
I can confirm that deleting the folder .winetrickscache fixed the problem (at least for me!) :)

---

### Post by trike994 on 2010-11-27
the same problem, but i didn't have a ".winetrickcache" folder..
sorry for pushing..
EDIT: ubuntu lucid 10.10

---

### Post by kernst on 2011-01-26
> **trike994 said:**
> the same problem, but i didn't have a ".winetrickcache" folder..
sorry for pushing..
EDIT: ubuntu lucid 10.10

Nowadays it's [FONT=Courier New]~/.cache/winetricks[/FONT]. If anyone reading this post doesn't know what that means, it means you have to go to your home folder in Nautilus (File Manager), then choose *View* -> *Show Hidden Files* from the menu in order to see the ".cache" folder, then delete the "winetricks" folder inside it.

Even winetricks-alpha ([http://winetricks.org/winetricks-alpha](http://winetricks.org/winetricks-alpha), referred to in the WineHQ wiki article, [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)) has this problem from time to time.

Winetricks may also make some assumptions about running inside a folder it has write access to (based on the error messages I saw). I installed 'winetricks-alpha' in /usr/local/bin (which ordinary users can't write to on my system), and the graphical Winetricks UI bombed with error messages about sha1sums. What had really happened was it wasn't able to create a cache folder and it actually didn't download anything at all, but all the error messages were being displayed in the terminal. Deleting [FONT="Courier New"]~/.cache/winetricks[/FONT] and running winetricks from my home directory in a terminal was successful:

```
cd                         # switch to home directory
winetricks-alpha dotnet20  # /usr/local/bin is already in my $PATH
```

---

### Post by HeroKing on 2011-01-26
i actually think deleting the .wine folder is a bad idea. every time i look at it, i see my drive_c folder, and there's no indication that it's a shortcut. so as far as i can tell, you're also deleting your entire "C drive" with all your installed programs. if anyone can tell me they still work w/o problems, i may consider doing that in the future if i have any problems w/winetricks

---

### Post by Heinz on 2011-01-27
If you don't use WINEPREFIX for every installed application you would ruin everything installed in WINE when delting the .wine folder. So, DON'T!

I can only advise to use WINEPREFIX for a single application like WINEPREFIX=~/.wine/game. You can then delete only the game folder without affecting other applications.

This also helps with different settings (orm, ddr, multisampling, glsl, etc.) so that every application can be configured without disturbing others.

---

### Post by allen303allen on 2012-02-08
> **kernst said:**
> Nowadays it's [FONT=Courier New]~/.cache/winetricks[/FONT]. 

and the graphical Winetricks UI bombed with error messages about sha1sums. What had really happened was it wasn't able to create a cache folder and it actually didn't download anything at all, but all the error messages were being displayed in the terminal. Deleting [FONT="Courier New"]~/.cache/winetricks[/FONT] and running winetricks from my home directory in a terminal was successful:


yes, I met the same issue with ubuntu 10.10 and wine 1.3.36 when I use the graphical Winetricks way, but the terminal way seems fine.

---

### Post by pille on 2012-09-18
I have the same problem with Ubuntu 12.04. Every approach solving the problem didn't work.
I deleted the folder, i deleted just the file, severel retries haven't been successful.

```

------------------------------------------------------
Checksum for /home/user/.cache/winetricks/msxml4/msxml.msi did not match, retrying download
------------------------------------------------------
....

------------------------------------------------------
sha1sum mismatch!  Rename /home/user/.cache/winetricks/msxml4/msxml.msi and try again.
------------------------------------------------------


```

any idea why this still doesn't work? i'm using wine 1.4. i think that it the file is being downloaded 2 times.

i'm missing the winelibs for q4wine too.

---

