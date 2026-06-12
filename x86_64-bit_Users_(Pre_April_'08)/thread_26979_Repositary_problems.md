---
title: "Repositary problems"
date: 2005-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mytos on 2005-04-14
I tried several different respositary lines that i found on this forum, but it still can't find these

 - Preview amd64 Binary-1 (20041020) unstable/main Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Preview%20amd64%20Binary-1%20(20041020)_dists_unstable_main_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)
W: Kunde inte ta status på källkodspaketlistan cdrom://Ubuntu 4.10 _Warty Warthog_ - Preview amd64 Binary-1 (20041020) unstable/restricted Packages (/var/lib/apt/lists/Ubuntu%204.10%20%5fWarty%20Warthog%5f%20-%20Preview%20amd64%20Binary-1%20(20041020)_dists_unstable_restricted_binary-amd64_Packages) - stat (2 Filen eller katalogen finns inte)


I think i need to get this working to download flash for mozilla and get smbfs for samba so i can get network with windows computers working

---

### Post by p!=f on 2005-04-14
Please post your /etc/apt/sources.list here and be sure you run 
```

sudo apt-get update

```
or update repositories using synaptic after the changes made in that file.

---

### Post by Mytos on 2005-04-14
oh i solved my problem..
It contained cd-rom thingy, i just remove that and updated through synaptics instead and now it seems to work =)

---

