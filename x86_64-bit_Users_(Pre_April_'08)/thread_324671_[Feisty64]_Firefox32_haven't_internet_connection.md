---
title: "[Feisty64] Firefox32 haven't internet connection"
date: 2006-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by pynux on 2006-12-24
hi , sorry for my poor English , I'm French
I had install Ubuntu 7.04 64bit edition
it's work fine 

but i downloaded Firefox i686 to have real player and flash9

Firefox 64 bit work fine but not firefox32 (i have install all ia32 in synaptic)
firefox32 run , but don't have internet connection , 
under edgy (6.10) it's work fine ...
I forgot something?

---

### Post by kuja on 2006-12-24
I know what you forgot. You forgot that feisty is still in alpha and won't be released for another 4 months. 2007, april. Where did you get the 32-bit firefox build from though? Perhaps that's related to the problem.

---

### Post by accensi on 2006-12-25
Although your question is more appopriate to the Feisty Development Forum, the solution for your Firefox32 problem is Disable the ipv6 handling in FF32

Open "about:config" page in a window or tab; type ipv6 in the Search field.

Click in the "network.dns.disableIPv6" to set it to true, forcing ipv6 to be disabled.

---

