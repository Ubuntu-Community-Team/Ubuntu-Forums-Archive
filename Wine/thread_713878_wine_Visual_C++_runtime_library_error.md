---
title: "wine Visual C++ runtime library error"
date: 2008-03-03
forum: Wine
---

### Post by doug.d2 on 2008-03-03
Hi there friends, I'm from Brazil - Rio! 
On Ubuntu 7.10 amd64,  I install a software on wine without a problem, but when run it, splash a message "Microsoft Visual C++ runtime library" error. 

  I don't find a help about this clearly in "wine forum"

  Any help me?

  Regards,

  Douglas

---

### Post by Joeb454 on 2008-03-03
The program you are trying to run requires the Microsoft Visual C++ Runtime Library in order to run properly.

I'm not sure whether this can run on Linux under WINE...you'll have to check the WINE website :)

---

### Post by happyhamster on 2008-03-04
- You can try installing those libraries using winetricks. You can download the winetricks script from this page:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Next, open a terminal and navigate to the folder where you downloaded the script:

cd /where/you/downloaded/the/script

- Make the script executable:

chmod +x winetricks

- Run winetricks (to see all available options):

./winetricks

- In your case you'll probably have to choose vcrun2005 (else try: vcrun2005sp1 or  vcrun2008):

./winetricks vcrun2005

- When that's done, try to run (or install) your application again. Good luck, and keep us informed.

---

