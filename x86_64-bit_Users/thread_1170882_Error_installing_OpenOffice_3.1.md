---
title: "Error installing OpenOffice 3.1"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by teixidoj on 2009-05-26
Hello Team,

I am getting the following error when I attempt to install OpenOffice 3.1 Has anyone run into this issue and what can I do to fix it? The error is in the attached file.

Thank you,

John...

---

### Post by pixel :-) on 2009-05-26
I bet you tried to install the 32 bit version.

try [http://news.softpedia.com/newsPDF/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.pdf]("http://news.softpedia.com/newsPDF/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.pdf")

---

### Post by khelben1979 on 2009-05-26
[Download OpenOffice]("http://download.openoffice.org/").

---

### Post by Possum Films on 2009-06-03
Here is how I managed to install OpenOffice 3.1:

I downloaded the files from this site: [http://ftp.iinet.net.au/pub/openoffice/stable/3.1.0/OOo_3.1.0_LinuxX86-64_install_en-US_deb.tar.gz]("http://ftp.iinet.net.au/pub/openoffice/stable/3.1.0/OOo_3.1.0_LinuxX86-64_install_en-US_deb.tar.gz") 

I removed OpenOffice 3.0 using Synaptic.

I extracted all of the files from the tar.gz file to my home directory, and then ran this code in the terminal:

```

cd OOO310_m11_native_packed-3_en-US.9399/DEBS
sudo dpkg -i *.deb
sudo dpkg -i desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb

```

---

### Post by ken78724 on 2009-06-04
Mr. P: 
you say quotes: "I removed OpenOffice 3.0 using Synaptic." Tell us what you mean; did you uninstall, or what is involved in removing OO 3.0? Would be very interested in having OO 3.1, especially if it would allow me to open folders that have been locked since I believe 9-29-08. One day I will go where you are now. 

Many thanks for posting this thread!!!! ;);););)
Kenneth

---

### Post by ken78724 on 2009-06-04
Possum Films, am unclear... after download OO3.1 from [http://ftp.iinet.net.au/pub/openoffi...-US_deb.tar.gz](http://ftp.iinet.net.au/pub/openoffi...-US_deb.tar.gz)

You say you "removed OpenOffice 3.0 using Synaptic". What code is used to do a clean removal? 

looking to you for clarification:popcorn:

---

### Post by teixidoj on 2009-06-05
I finally got it to work with the following command "sudo apt-get dist-upgrade". This was acheived after much research on the web. I don't mind a challenge, but this was like passing a stone. I could see Linux on the desktops in corporations, but they will need a sharp IT staff.

John...

---

