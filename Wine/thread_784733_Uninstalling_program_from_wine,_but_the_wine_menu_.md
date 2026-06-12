---
title: "Uninstalling program from wine, but the wine menu program still exist"
date: 2008-05-06
forum: Wine
---

### Post by Afif K fiska on 2008-05-06
I'am using wine ver 0.9.61.
I want to install wireshark which have executable files. In the middle of the instalation, wireshark must installing other program too, it's winpcap. But when installing winpcap, popup window come from wine tell that gecko isn't install and the installation cannot continue. Then i install it. But after i install gecko, the installation still can't continue. Finaly, i decide not to install wireshark and this winpcap. The problem begin, the wireshark is showed in the wine menu tree. I've uninstall it from wine, but, why does it's always still there. I try to manually delete that wireshark from the wine menu program. I look for the wine start up folder and manually erase it. But it's still there. How to uninstall this completely from wine ? cause the program menu for wireshark in wine is still showed. 
Really apreciate for your help

---

### Post by cogadh on 2008-05-06
The application itself is actually uninstalled, the shortcuts were just left behind. You should just be able to right-click on the menu entry and delete it manually. 

BTW - The reason you couldn't get Wireshark to work is because WinPcap needs to install a driver in order for it to work. Windows drivers don't work in Linux or in Wine.

EDIT - Crap, I forgot that menu editing is different in Ubuntu as compared to Kubuntu (which is what I use). In order to manually remove the menu entries, you need to go to System > Preferences > Main Menu.

---

### Post by Afif K fiska on 2008-05-07
> **cogadh said:**
> The application itself is actually uninstalled, the shortcuts were just left behind. You should just be able to right-click on the menu entry and delete it manually. 

BTW - The reason you couldn't get Wireshark to work is because WinPcap needs to install a driver in order for it to work. Windows drivers don't work in Linux or in Wine.

EDIT - Crap, I forgot that menu editing is different in Ubuntu as compared to Kubuntu (which is what I use). In order to manually remove the menu entries, you need to go to System > Preferences > Main Menu.

Thank's for your answer. It works!!!!!

---

### Post by MaindotC on 2008-05-07
You know instead of wine'ing it you could just do
```

sudo apt-get install wireshark

```

Does that help?

---

### Post by Afif K fiska on 2008-05-07
> **strAlan said:**
> You know instead of wine'ing it you could just do
```

sudo apt-get install wireshark

```

Does that help?

it's really help, thank you so much...:)

---

### Post by MaindotC on 2008-05-07
No problem :) Welcome to Ubuntu!

---

### Post by Scooter7 on 2008-05-07
I know your problem is technically solved, but you can also look at this:

[http://www.ethereal.com/](http://www.ethereal.com/)

It's a program similar to Wireshark, I think.

---

