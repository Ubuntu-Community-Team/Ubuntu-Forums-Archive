---
title: "Associativities does not work anymore."
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by mag00 on 2009-03-28
Hello guys.

I will try to explain what is happening here, but since my English is "so so", if you do not understand something, please let me know to try to explain it again.

Here it is.

I have in my Intrepid, a program called GTKOrphan, that is supposed to remove the orphan files from the system. Normally the trash stay on the system when you remove some program.

Recently I have used this program to clean the system and after it was completed I noticed that all "associativities" was broken.

What I mean with "broken"? Before, when I want to open any document I just double-click on it and the system automatically open the software that is configured to open that document. This is used to work in various types of files. Images, OO docs, compressed files, text files, etc..

Now, after the "cleaning", the double-click just do nothing. For example, if I double-click a .PDF file now, the system just seems to process something but nothing happens. And there is no error message or additional information.

Now, I need to identify which file was removed that is killing this functionality.

I have already do all the updates with the Synaptic and used the "Fix broken packages" too. For the Intrepid everything is ok, but for me not.

:(

And now I make a question. What I can do to fix this? I don't want to reinstall the distro.

Thanks

[]'s

---

### Post by mag00 on 2009-03-31
Can you tell me another place to search information about my problem?

And I need a tip. If one of you that reads my first post and understand what is my problem think that the word "associativity" does not mean exactly what I described, please tell me the correct expression I can use to search for this problem on the web.

thanks

[]'s

---

### Post by hellblade on 2009-03-31
I understand your problem but I don't know how to fix it.

Anyways the correct term is file (or application, or mime) associations depending on your desktop terminology used.

You can make a quick test to see if it is a system-wide problem or just your user settings. You can do that either by creating and testing a new user or by testing your current user with clean settings.

To do the latter:
[LIST=1]
[*]Log out of Gnome or whatever desktop you are using.
[*]Switch to a console using Alt-Ctrl-F1
[*]Login
[*]You should now be inside your home directory. Change directory inside home
```
cd /home
```
[*]Move your user settings to a temporary location
```
mv $HOME $HOME.old
```
[*]Switch back to X with Alt-Ctrl-F7
[*]Login as usual and test if double clicking a file works as expected
[/LIST]

Note that by doing the above, when you login your settings will be the defaults (wallpaper, program settings... everything). Don't worry since that's what is supposed to happen.

**To restore your home:**
[LIST=1]
[*]Logout again
[*]Switch back to the console you were in previously (Alt-Ctrl-F1)
[*]Remove your newly created home
```
rm -rf $HOME
```
[*]Restore your "normal" home
```
mv $HOME.old $HOME
```
[/LIST]

It looks to me that GTKOrphan removed some mime related file from your system which might require the reinstallation of some package(s). I do not know which file is responsible for that stuff, thus I cannot find which package might be broken. Maybe someone else knows more.

Good luck.

---

### Post by mag00 on 2009-04-02
Thanks for your reply, hellblade. I understood every thing that you wrote and be sure that this post will be marked in my favorites for future consults.

Anyway, the problem was not in the system. :oops:

I have installed a file manager called PCManager, and with it the problem occurs. With the native Gnome file manager I don't get the problem. For now, the solution was to remove the PCManager and use only the native file manager.

I will find other file manager later.

Again, thanks for your reply. ;)

[]'s

---

