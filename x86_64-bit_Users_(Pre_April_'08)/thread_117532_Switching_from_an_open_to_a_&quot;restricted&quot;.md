---
title: "Switching from an open to a &quot;restricted&quot; wireless network ?"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by mumbly_58 on 2006-01-15
Hi !
I've got an Acer aspire 5024 (64 bits Turion) with Ubuntu breezy amd64-k8
I have to switch from open to restricted (wep key) wireless network ...
But it does not work ... I mean, it freezes my computer whenever i want to switch from open to restricted ! 
I've tried several things : 
1/ i've tried to configure my wlan0 with system/admin/network and create "profiles" ---> Freeze !!!!
2/ i've tried to configure my /etc/network/interfaces : nothing happens ...
...
I must configure it by hand with iwconfig options :
iwconfig wlan0 key xxxxxxxxxxxxxxxxxxxxxx
But if i do : ifconfig down and ifconfig up ---------> freeze !

Is there a way to have my wireless wlan0 interface working fine (from the begining - from the boot) with restricted or open networks ?

I've tried wifi-radar : this soft freezes too !!!

PS : I use 64 bits broadcom drivers from acer with acer_acpi ...

---

