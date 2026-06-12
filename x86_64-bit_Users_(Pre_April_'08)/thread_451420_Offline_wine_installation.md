---
title: "Offline wine installation"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jilbert on 2007-05-22
Hi there, I just installed my feisty ubuntu on my laptop but i have a problem in updating my packages because my laptop is running behind a firewall.. how can i do an offline installation?

---

### Post by Ledah on 2007-05-22
[Here]("http://wine.budgetdedicated.com/archive/index.html") you can download the wine packages. Then type ```
sudo dpkg -i wine_0.9.37~winehq0~ubuntu~7.04-1_amd64.deb
``` (for example) or use gdebi/Kubuntu package menu.

---

### Post by Jilbert on 2007-05-22
okay. thanks but I don't know where to download the package file? do you have the link? please? thanks.. :)

---

### Post by Ledah on 2007-05-22
Hum? :D
Just click at "Wine 0.9.37 amd64" on the site I've posted ;)

---

### Post by Jilbert on 2007-05-22
hi. I was able to download the dev file which is around 9.4 mb but I wasn't able to install it still i keep on getting this error: Dependency is not satisfiable : lib32asound2.

what could be the problem? how can i satisfy the dependency?

thanks..

---

### Post by Ledah on 2007-05-22
[http://packages.ubuntu.com/feisty/libs/lib32asound2](http://packages.ubuntu.com/feisty/libs/lib32asound2)

For other required packages you can also  look at [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by Jilbert on 2007-05-22
I guess i know how to search for the dependencies now.. :) I guess my problem was my laptop is running behind a firewall that's why it would'tn update the dependencies automatically.

I'm doing it manually. whoa! this is a good start for me as a beginner. hee hee hee..

anyway, I still can't make my ATI video card to work. but that's already posted to another portion of this forum. thanks ledah!

---

### Post by Jilbert on 2007-05-22
*sniff *sniff I can't get it to work.. what im doing was im downloadind all the depencies that is beings asked then it asked me to download libc6 which i did but when I installed it it said there is more updated version installed..


sheeze.. now I dont know what to do next...

---

### Post by Ledah on 2007-05-22
Maybe it's better to solve the problem of installing/updating packages via apt/Synaptic/Adept. Updating the packages seperately isn't very comfortable. 

Is there no internet connection on your laptop or what's the problem with your firewall? I guess it's the hardware firewall of a router?!

---

### Post by Jilbert on 2007-05-23
its a a company firewall. we are using ISA  via windows 2003 server for the proxy server. I don't know how to bypass the server.

---

### Post by Jilbert on 2007-05-23
its not always easy to connect to an unrestricted connection specially if you are living in saudi arabia. There's lots of restricted websites here. including ports I guess. I hope I'm wrong. I found a way to bypass our proxy server by using a static IP which is within the subnet of My ISP. In windows, its working properly and there there is no restriction. I tried to use the same IP address here in Ubuntu but for some reason, it is not working. I'm not sure if i did it on the right place.

I went to network and selected the wired connected then changed the DHCP to static IP and I used the same IP. now, the only problem that I have is I don't know where to put the DNS server IP address. because the window is only providing me to put the IP address, the subnet mask and the default gateway, there is no DNS server entry field. 

I know this is not related to this thread but I hope you can help me on this one.  I just need to update my dependency files. 

thanks again..

---

### Post by Jilbert on 2007-05-23
I got it. :) Im updating my packages now :) thanks alot..

more power ledah

---

### Post by Ledah on 2007-05-23
Congratulations ;)

And wine ist working now?

---

