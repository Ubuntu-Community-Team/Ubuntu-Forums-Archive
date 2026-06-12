---
title: "Hplip"
date: 2006-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by holzschuh on 2006-09-03
Hello,
    I recently purchased a HP Deskjet 5940 and was hoping to use it as soon as I got home. My computer is a eMachines W3107 with 64- bit Xubuntu installed. I went to the hplip website and I went to installation instructions, following instructions I check that I have hplip installed (which I do) skip steps 2/3 and enter "sudo hp-setup -a" into my command prompt, I enter my password and it says "bash: hp-setup: command not found"
     -Ty

P.S. Thank you in advace for your help or even just reading this.

---

### Post by dbasis on 2006-09-03
tried it with "System->Administration->Printers" ?

---

### Post by hajk on 2006-09-03
> **holzschuh said:**
> Hello,
    I recently purchased a HP Deskjet 5940 and was hoping to use it as soon as I got home. My computer is a eMachines W3107 with 64- bit Xubuntu installed. I went to the hplip website and I went to installation instructions, following instructions I check that I have hplip installed (which I do) skip steps 2/3 and enter "sudo hp-setup -a" into my command prompt, I enter my password and it says "bash: hp-setup: command not found"
     -Ty

P.S. Thank you in advace for your help or even just reading this.

Why did you think you had to download/install HPLIP outside of the apt-get/Synaptic way yourself? It is already up and running in Ubuntu...

Now, after you have gotten rid of the stuff you installed (or tried to install) yourself, just open the System - Administration -Printing menu, click on the new printer icon and take it from there.

Good luck!

---

### Post by kleeman on 2006-09-03
Yes check that you have all three hplip packages installed using a search for hplip in Synaptic. If you want the hplip gui frontend, open a terminal and type 

hp-toolbox

---

### Post by rhomp2002 on 2006-09-03
Entered hp-toolbox and got the message to add a printer using the CUPS admin printers website.  I went there and it asked me to enter the user name and password when I went to set the printer options.  I am the only user and I am also listed with the root password.  I entered them and it just kept asking me to enter the user and root password.  I finally clicked off and it said I could not make the entries without entering the user and root password.  Makes no sense.  What user are they looking for and what root password?  I even went to the admin screen and tried to enter myself as the user and got the message that I was already logged in as being the user.  ](*,) ](*,) ](*,)

---

### Post by kleeman on 2006-09-03
The cups admin is disabled for security reasons and I have never figured out which password it needs. Your best bet in to open the gnome printing tool:
System----> Administration----> Printing

Double click on the Add a Printer icon and look for a detected printer starting with "hp" either under "use a detected printer" or else under "Use another printer by specifying a port".

Be warned Dapper has had issues with cups so this might not work. Personally I didn't find hplip of much use and simply used the gnome tool above which usually finds the printers on your system fairly easily. Another option is the kde tool "kprinter" which tends to be more comprehensive than the gnome tool. I use this for network printers as it has a nice LAN scan utility.

Edit: Here is a link to enable cups admin in Ubuntu

[http://www.kdedevelopers.org/node/2117/](http://www.kdedevelopers.org/node/2117/)

---

