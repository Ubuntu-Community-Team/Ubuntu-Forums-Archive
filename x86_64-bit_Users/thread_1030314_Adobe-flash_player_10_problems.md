---
title: "Adobe-flash player 10 problems"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by wolfyking2 on 2009-01-04
Ok, so I'm trying to install it, but it's all so confusing, 'running in terminal' and what not.  I don't get any of that.  But I think your supposed to do this.  Ok, I downloaded the tar.gz thing to my desktop.  I open my folder, and theirs 2 things in there.  Flashplayer-installer and flashplayerlib.so.  There's a little lock above the Flashplayer-installer.  So, I double click it, and some options come up, they are 'run in terminal, display, cancel, and run'  So, I click run in terminal (because that's what all the guides say) and nothing.  A little browser comes up for a second, then disappears.  Am I doing something wrong?  Please tell me everything I have to do o get it, I really want to go on youtube and miniclip:(

---

### Post by elwin_windleaf on 2009-01-04
I don't remember running anything when I installed mine: I just had to copy the libflashplayer.so into my Firefox plugins folder.

Try copying the file into the following folder: /home/[your user here]/.mozilla/plugins/

You'll have to remove any previous versions of the flash player first, and Firefox will have to be restarted for it to take effect.

I hope that helps/works, and anybody can feel free to correct me if I got it wrong!

---

### Post by wolfyking2 on 2009-01-04
I did exactly what you said, and nothing happened, but it might be me.  When you mean 'restart' firefox, do you mean just exiting and re-opening it? if-so, it doesn't work, and I need more help.

and, I read a tutorial thing, does the plugin folder have to be in the firefox folder?  Or not?

---

### Post by pragmatine on 2009-01-04
Ubuntu already provides a package for the flash-plugin - called flashplugin-nonfree - install it using synaptic - you dont need to and shouldnt bother using the tar.gz package from adobe

---

### Post by bushda on 2009-01-04
The flashplugin-nonfree uses the nsplugin package and the 32-bit version of Flash. If you're trying to use the 64-bit version of Flash, you need to uninstall the flashplugin-nonfree package and copy the files in the tar.gz to /home/YOURUSERNAME/.mozilla/firefox/plugins.

---

### Post by tuxxy on 2009-01-04
Extract the contents of the .tar.gz, copy the libflashplayer.so file to your **/usr/lib/mozilla/plugins** directory and restart firefox, also the new 64-bit plugin is much better than the flashplugin-nonfree provided in the repos.

---

### Post by wolfyking2 on 2009-01-04
ok...I'm pretty sure I have that nonfree plugin thing, because I'm doing exactly what you guys say, and nothings happening, so I'm gonna check that out (if I knew how, answers would be nice >.<)  sorry, I'm bad with computers

---

### Post by elwin_windleaf on 2009-01-04
To remove the old version, you can go to the Applications menu, and select Add/Remove.

From there, select "All Available Applications" from the dropdown menu labeled "Show".

Type "flashplugin" into the search box (without the quotes), and make sure that is unchecked. When you've done all of that, click the "Apply Changes" button.

---

### Post by wolfyking2 on 2009-01-05
Darn...I looked at that, no 'flashplugin' came up.  But, I saw installations for adobe flash-player 10 and macromedia flash player, but I couldn't download them because it says my hardrive isn't correct.  I keep on getting somewere and stuck.  Does this mean I need a different plugin?  Because I'm serious, I'm doing exactly what you people say, and nothinh's happening.

Oh geez, I just found out I have a powerpc, and that means I can't have flash...Then how am I supposed to view youtube and what-not?

---

### Post by Sef on 2009-01-05
> Oh geez, I just found out I have a powerpc, and that means I can't have flash...Then how am I supposed to view youtube and what-not?

Check out Swfdek or Gnash.  They are in Add/Remove.

---

### Post by stchman on 2009-01-05
I got it to work doing the following:

First remove flashplugin-nonfree completely.

```
sudo apt-get autoremove flashplugin-nonfree
```

After unpack the Flash 10 alpha into the ~/.mozilla/plugins folder.

Are you running Intrepid or Hardy?

---

### Post by wolfyking2 on 2009-01-05
> **Sef said:**
> Check out Swfdek or Gnash.  They are in Add/Remove. I already had Gnash, and I just downloaded Swfdek, but it didn't do anything.  am I doing something wrong (AGAIN?)

---

### Post by PanicIRAQ on 2009-01-05
I'm a noob to linux and I do not know what version I have of ubuntu (i know it's 8.10 but i mean like 64 bit er whatever).  How do I check this, I am trying to get Flash plugin on my laptop as well so that I can get on youtube and stuff.

I've tried the flashplugin-nonfree and it half worked.  I got a gray box where the video (on youtube) should be but no video.  Does anyone know what could be going on?

---

### Post by elwin_windleaf on 2009-01-05
There's a Firefox plugin that you need to install in addition to the Gnash or Swfdek applications. Try these:

```
sudo apt-get install mozilla-plugin-gnash
```

If that one doesn't work out for you, you can try the Swfdek version:

```
sudo apt-get install swfdec-mozilla
```

If you're not comfortable with the command line, you should be able to go to Add/Remove Programs and search for either "swfdec-mozilla" or "mozilla-plugin-gnash" with similar results.

Good luck, and way to stick with it!

---

### Post by wolfyking2 on 2009-01-05
Wait, these codes, do you put them in terminal?  If you do, how do you get it to run.  Because I'm copying the messages in the terminal, and nothing happens.  I'll try everything though.

---

### Post by tuxxy on 2009-01-05
If they dont run correctly in terminal your best opening up synaptic and search for the individual packages manually.

---

### Post by elwin_windleaf on 2009-01-05
> **tuxxy said:**
> If they dont run correctly in terminal your best opening up synaptic and search for the individual packages manually.

Agreed: If you're not having any luck with the terminal, try Add/Remove Programs or Synaptic.

Once you're in one of those programs, try searching for "swfdec-mozilla" or "mozilla-plugin-gnash" and installing one of them from there.

---

### Post by wolfyking2 on 2009-01-05
nothing's coming up...you know what, I shouldn't really worry, I'm getting a PC on thursday (possibly the next)

---

