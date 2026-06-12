---
title: "Opening downloaded files from firefox32"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by robwg on 2007-05-08
Hi

I've installed firefox32 using the script in Kilz thread ([http://ubuntuforums.org/showthread.php?t=202537&highlight=java]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java")) and the flash and mplayer plugins are now working. (Thanks Kilz!)

A small problem I have is that files in the Download Manager don't launch when I double-click on them any more. eg if I download a .pdf file and double-click on it nothing happens. Does this work for anyone and did you have to tweak anything to get it going?

Thanks

---

### Post by leona on 2007-05-08
Nope and if you right click, on the file in the download box, and choose open folder it also doesn't work either, don't know why, but it just doesn't work. :(

---

### Post by Kilz on 2007-05-08
> **robwg said:**
> Hi

I've installed firefox32 using the script in Kilz thread ([http://ubuntuforums.org/showthread.php?t=202537&highlight=java]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java")) and the flash and mplayer plugins are now working. (Thanks Kilz!)

A small problem I have is that files in the Download Manager don't launch when I double-click on them any more. eg if I download a .pdf file and double-click on it nothing happens. Does this work for anyone and did you have to tweak anything to get it going?

Thanks

If you go to the location of the file and try to open it, does it open?

---

### Post by robwg on 2007-05-08
> If you go to the location of the file and try to open it, does it open?

Hi Kilz

Yes if I double-click on the file in Nautilus it opens as expected. It's not a deal breaker; I just wondered if it could be made to work. As Leona noted the 'Open folder' option doesn't work either. I've replaced the original version of firefox per the notes at the end of the howto so I can't try to see if it works in that.

Thanks again for your script and your posts in this forum. I was going to install the 32-bit version for an easy life, but your posts shamed me into using the 'proper' version! So far I'm glad I did! :)

---

### Post by shad0w_walker on 2007-05-19
Im having the exact same problem with my install, tried swiftfox(32bit) and firefox32 installed from the script, no kind of ability to open files. The 64bit version of firefox still works perfectly for opening files though.

Any suggestions would be greatly appreciated, its not a major problem, just one of those little ones that lingers.

---

### Post by ronocdh on 2007-05-19
> **shad0w_walker said:**
> Im having the exact same problem with my install, tried swiftfox(32bit) and firefox32 installed from the script, no kind of ability to open files. The 64bit version of firefox still works perfectly for opening files though.

Any suggestions would be greatly appreciated, its not a major problem, just one of those little ones that lingers.
How about adding [this extension]("https://addons.mozilla.org/en-US/firefox/addon/256") and giving it a try? Also, in case you aren't using it already, there's [this one]("https://addons.mozilla.org/en-US/firefox/addon/201") which is great for large downloads and operates pretty separately from the regular Firefox download functionality.

Post back with results!

---

### Post by shad0w_walker on 2007-05-19
Iv already got download manager tweak installed, does exactly the same as the normal manager. Thanks for the suggestion though.

Begining to think this is a problem with firefox opening anything external to itself, i tried to open a email link and evolution did not open as it should.

---

### Post by Kilz on 2007-05-19
> **shad0w_walker said:**
> Iv already got download manager tweak installed, does exactly the same as the normal manager. Thanks for the suggestion though.

Begining to think this is a problem with firefox opening anything external to itself, i tried to open a email link and evolution did not open as it should.

Links clicked on a page like the email link need to be setup for other applications to use it. As referenced on the howto page.

[INDENT]"You must setup what program is called for some things. There is [a post on the settings here]("http://ubuntuforums.org/showpost.php?p=2582830&postcount=11"), untill I have time to expand it a little."[/INDENT]

This is not the same thing as the "open" on the download window.

---

### Post by shad0w_walker on 2007-05-19
I understand there is a difference between the two things but i thought i would mention this, seeing as all my settings between 64bit and 32bit firefox are identical and 64bit firefox opens evolution when i click on an email link.

---

### Post by Kilz on 2007-05-19
> **shad0w_walker said:**
> I understand there is a difference between the two things but i thought i would mention this, seeing as all my settings between 64bit and 32bit firefox are identical and 64bit firefox opens evolution when i click on an email link.

No, the settings are not identical. The settings for that are in the application folders. The application folders are different. I have given you the information on how to fix it. Maybe you didnt see it on the howto, but the link is in my last post.

---

### Post by shad0w_walker on 2007-05-19
Thanks for the link. It didnt directly tell me how to fix my problem (Opening downloads) but i have now found the problem and the solution


For everyone having issues getting firefox to open external programs such as nautilus, a downloaded file, etc

Open about:config

Search for:

```
network.protocol-handler.external.data
```

And set it to true. Everything should work perfectly now.

---

### Post by Kilz on 2007-05-19
> **shad0w_walker said:**
> Thanks for the link. It didnt directly tell me how to fix my problem (Opening downloads) but i have now found the problem and the solution


For everyone having issues getting firefox to open external programs such as nautilus, a downloaded file, etc

Open about:config

Search for:

```
network.protocol-handler.external.data
```

And set it to true. Everything should work perfectly now.

Thanks for the info. I have placed a link to your post on the howto.

---

### Post by shad0w_walker on 2007-05-20
A slight update. I dont know why in tuxs name its stopped working for me but it has (Certain circumstances forced me to reinstall from a backup) and now the same problem has reappeared, the last fix i posted doesnt seem to work sadly.

---

### Post by shad0w_walker on 2007-05-20
Update!

I have at long last after some painfully boring diving through about:config figured out a solution to this new and improved problem with firefox not opening downloads

If my original suggestion does not solve your problem, please try the following. 

1. Open about:config
2. Create a new string (Right click, New > String)
3. Set the string name to:

```
network.protocol-handler.app.file
```

4. Set the string value to:

```
/usr/bin/gnome-open
```

5. Enjoy!

Hopefully either my first trick or this one will work for you.

---

### Post by ernstblaauw on 2007-05-31
> **shad0w_walker said:**
> Update!

I have at long last after some painfully boring diving through about:config figured out a solution to this new and improved problem with firefox not opening downloads

If my original suggestion does not solve your problem, please try the following. 

1. Open about:config
2. Create a new string (Right click, New > String)
3. Set the string name to:

```
network.protocol-handler.app.file
```

4. Set the string value to:

```
/usr/bin/gnome-open
```

5. Enjoy!

Hopefully either my first trick or this one will work for you.

It works for me! However, I'm using Kubuntu, and gnome-open uses the gonome defaults. Do you know which program is KDE's equivalent to gnome-open?

---

### Post by shad0w_walker on 2007-05-31
Unfortunatly im not a big KDE person so i unfortunatly dont know what to suggest with what to use. Asking for an equivilent to gnome-open on the kubuntu forums might get you some answers.

Also, nice to hear that this works for more than just my system.

P.S. Seems as i have a terrible case of boredom and a couple of mates with the same problem im having a look around for something suitable.

---

### Post by ernstblaauw on 2007-05-31
I think 'gnome-open' is also more like a workaround. Which command issues Konqueror when it want to open something? It looks like some 64-bit <-> 32bit flaw...

---

### Post by shad0w_walker on 2007-05-31
Gnome-open is definatly a work around, but in a gnome environment i havent been able to tell the diffrence from it and normal firefox operation so its a very effective work around.

Im not sure if it will work (No KDE environment to test it in and no kubuntu iso around) but have you tried swapping out 'gnome-open' for 'konqueror'?

---

### Post by ernstblaauw on 2007-05-31
> **shad0w_walker said:**
> Gnome-open is definatly a work around, but in a gnome environment i havent been able to tell the diffrence from it and normal firefox operation so its a very effective work around.

Im not sure if it will work (No KDE environment to test it in and no kubuntu iso around) but have you tried swapping out 'gnome-open' for 'konqueror'?

Well, it works not exactly as hoped: it opens a PDF inside Konqueror, but Konqueror is not default application for that. However, I think it is more suitable than gnome-open, but I'm still interested in a better solution.
Thanks for your help!

---

### Post by synace on 2008-06-06
setting "kfmclient exec" in about:config didn't take, it would not open my file. probably due to the parameter added..

solution for me: 

create my own "kde-open"
/usr/local/bin/kde-open

sudo nano /usr/local/bin/kde-open
```
#!/bin/sh
kfmclient exec "$@"
```

sudo chmod a+x /usr/local/bin/kde-open

firefox:

about:config
network.protocol-handler.app.file      kde-open

---

