---
title: "SIS 190 problem"
date: 2006-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ashish Meena on 2006-06-22
Hi , 
 As initially linux kernels did not support sis 190 driver I had to get a realtek8139
 lan card . But now in dapper I find that my both lan cards get detected . 
       But the problem is whenever I use SIS 190 lan card  I am able to do "ssh" to other computers and "ping" also works fine  .  But when I try to open anything in browser . It just does not open . Can anybody tell me what can be the problem ??

---

### Post by jvictor on 2006-06-27
Disable IPV6 in ur browser

type about:config

and set

network.dns.disableIpv6 to true

HTH

---

### Post by Ashish Meena on 2006-06-27
I removed my realtek lan card and started using only my onboard lan card and then I typed " iptables -f " and then it started working for me . 
      Actually my kernel some times used to assign eth1 to my sis lan card and eth2 to realtek .And some times eth1 to realtek and eth2 to sis 190 . I dont know why was it happening . So this was also causing problems . Anyway when I did "iptables -f " it started working .
         Can u please tell What is  network.dns.disableIpv6 and what does it do ?? 

Thanks for reply

---

### Post by jvictor on 2006-06-27
The property says it all , IMO, simply put we are just telling firefox that "talk using IPV4 than IPV6"

---

