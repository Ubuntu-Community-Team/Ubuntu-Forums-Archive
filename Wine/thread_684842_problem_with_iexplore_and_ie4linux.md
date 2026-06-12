---
title: "problem with iexplore and ie4linux"
date: 2008-02-01
forum: Wine
---

### Post by anthonylane13 on 2008-02-01
I've had a good mooch around the forums and I can't see that there's a post out there that deals with this...

When I run iexplore.exe from wine I get a blank screen (see screenshot attached)

So I downloaded ie4linux and installed it, it seemed to go ok, but there's no launcher on my apps menu and I when I try to run from the installation folder I get the following error.
```
bash: ies4linux: command not found
```

Any help would be much appreciated as I need to test my sites in IE before I can safely put them on my server.

Thanks in advance

---

### Post by anthonylane13 on 2008-02-01
sorry - forgot to upload file
D'oh!

---

### Post by ajgreeny on 2008-02-01
The command in the apps menu launcher will need to be the full path to the ie4linux binary (I don't know if it's an exe or a standard linux binary file) but if it is in the ~/.wine folder the command will be something like this
```
wine "/home/username/.wine/drive_c/Program Files/ie4linux/ie4linux.exe"
```Note the quote marks, needed as the folder Program Files has a space in it.

However, have a look in the apps menu under the Wine entry, if it's there.  ie4linux could be in there already.

---

### Post by luctor on 2008-02-01
i installed ies4linux today
to run it I just have to type ie6 in the command line or the command box (ALT-F2)

---

### Post by anthonylane13 on 2008-02-01
Thanks for your replies - sadly I'm no nearer to the truth.

I think I must not have either of these programs installed correctly, (although I followed the instructions on the respective web pages for each product).

If I type ie6 into the terminal or command window I get:
```
 ie6: command not found
```

and there is no launcher for wine in my applications menu...
I tried to launch ie4linux from inside my wine/drice_c/program files but there is no ie4linux folder in that directory.

ie4linux has installed straight into my home/username directory...

Any more advice would be much appreciated.

Thanks again.

---

### Post by drummingpariah on 2008-02-25
I'm encountering the same problem.  I need ie4linux so that I can install certain .net plugins that don't work with Firefox (something to do with the Gecko interface is just incompatible), but installing the plugins drops them into the /home/username/.wine directory.  The default ie4linux install directory is /home/username/ies4linux for some reason, and it doesn't play very nicely with Wine in general.  I'm in fairly desperate need of this plugin (it's for a badly designed CMS that the company I'm working with is pretty in bed with at this point, so I have no way out of that) and I would hate to have to dual-boot for something as silly as this.  I'm going to try ie4linux explorer emulator 7.0 in the current Beta release (here [http://www.tatanka.com.br/ies4linux/page/Beta](http://www.tatanka.com.br/ies4linux/page/Beta)) but my hopes are rather low.  Just getting ie4linux to run from the console was a bit of a  hassle, but the beta site was the reason I worked it out in the end.  Any insight would be greatly appreciated.

---

### Post by brento73 on 2008-04-18
I installed ies4linux and it ran fine the first time, but after that I'm getting the same blank screen as with the wine IE. Has anyone figured out how to fix this?

---

### Post by MadTxn on 2008-04-29
~/bin/ie6

---

