---
title: "Garena firewall error!!"
date: 2008-06-17
forum: Wine
---

### Post by myromance123 on 2008-06-17
Hello, Im new to ubuntu and have been using it for only 4 days. I have set up Garena and for the first day it worked. But now it has the error "You were unable to host game/join host because your firewall/anti-virus has blocked your access". At first this error only occured when I tried to join a game, but now its at the login screen and wont let me through.

   I have searched painstakingly and still cannot find a solution anywhere, so I am pleading here. If there is any place/link or update or solution to my Garena problems please tell me. Thnx

---

### Post by eragon100 on 2008-06-17
What is that??

Anyway, you might have accidentaly enabled ufw, the ubuntu firewall. Since it's useless resource-bloat anyway, I suggest you remove it from your system:

Applications -> accesiores -> terminal

Now type the following command:

sudo apt-get remove ufw

pres enter, it will ask for your password (no, it's NOT MEANT to show asterisks while you type it.)

restart computer and try again, problem should be solved. Have fun! :)

---

### Post by myromance123 on 2008-06-17
Thnx for replying, I tried what you said but to no avail. The error is persistent as ever. Seems ufw has nothing to do with it. There arent any antivirus programs on my pc either. I have also uninstalled, redownloaded and reinstalled it. Could garena itself have a problem ?? anyone know ??

---

### Post by abrizan on 2008-06-19
the error is due to unimplemented calls in wine's replacement for mswsock.dll

All you need to do is grab the original from windows and place it in 
~/.wine/drive_c/windows/system32
Also copy ws2help.dll from windows to that location.

In the wine configuration tool click the libraries tab and add "mswsock". set it to native only. Wine complains but that fixes it.

I still can't login because the garena window doesn't render correctly, i may need to "Emulate virtual desktop"

---

### Post by myromance123 on 2008-06-19
I did exactly what you said. ALthough I dont have windows anymore, I got the .dll file from dll-files.com  .  I set them up, and now Garena wont load at all. No login screen whatsoever. Could this be the "Emulate virtual desktop" problem you were talking about?

---

### Post by myromance123 on 2008-06-20
Anyone, and I mean anyone!!, who knows how to get garena working at all on ubuntu hardy heron (8.04 LTS) please DO NOT HESITATE to let me in on what you did :)  

       I will use ANY help given because I am only 1 ubuntu week old.
Thnx for the replies so far. :]

---

### Post by muski on 2008-10-02
might be a little too late a reply but anyway 

if you delete skin.ggz in skins folder from garena directory it will work.It will download the missing link but somehow magically garena runs when you do this or maybe did work for me . Its quite buggy though ... fonts are not visible but if you know what you are looking for in GG client it wont make a difference.

hope that helps

---

