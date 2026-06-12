---
title: "Super Circular Security"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by IconK7 on 2006-02-04
Well, I'm trying to install the outrageously hyped Ubunbtu Linux  operating system (64-bit). After changing video cards (from a pcie-X800XL to a pci-Radeon 7000) I finally got it to install. 
    So, how do you make anything work? After several installs (7 so far), I have been able to click on a few desktop icons, and use Firefox to reach the internet, but that's it. 
    When I try to use anything worth doing, like use the Synaptic Package Manager, I get a Password prompt, I type in the password, then I'm told I don't have 'permission' to use this resource.  Then when I click on it again, I don't even get the Password prompt. I try to log in as root so I will get that permission, but then I'm told I don't have permission to log in as root either.  I read the Help file to enable Root to login to Gnome, but again the Password prompt, which begets no response at all, and again all succeeding clicks get no response at all. I can click on the Login Screen Setup once, but after the inevitable denial the thing won't even come up again. A red icon tells me that there are 46 updates available, but gives me a Password prompt then a No Permission response then no further response at all. 
    It's a VERY secure system. Permission is dangerous, so you can't have it. Root has Permission, but you have to have Permission first before you're allowed to use Root. You can't DO anything, but you CAN brag that you have the most secure Operating System on the planet!
    The first install I tried yesterday corrupted both my hard drives, so I spent several hours of the day re-Formatting & Re-Installing WinXP (32-bit) and Mandriva 2006 (64-bit). The 'problem' then was the X800XL videocard, which Ubuntu said prevented X from installing because of a 'conflict' with an unspecified non-video PCI device. The Radeon 7000 PCI videocard works, but what a huge step down!
    What can I do to fix this? WinXP works normally on this machine, and the 64-bit Mandriva works (though some things aren't available). Is there any point in spending more hours to get Ubuntu working?

---

### Post by tombeharrell on 2006-04-26
The first user (that you created when you installed) automatically gets superuser rights. When you run a program that needs these rights, you'll be asked for your own password (assuming you're logged in as that first user).

You can make other users sudo-able too, i.e. have admin rights, from user management. They'll still be asked to confirm their own password when a program needs admin rights.

To run a command in the terminal as super user, prefix commands with 'sudo'.

The root account is disabled by default in Ubuntu, and 'best practice' is to keep it that way and use sudo from your own account, only when you know you need to.

---

