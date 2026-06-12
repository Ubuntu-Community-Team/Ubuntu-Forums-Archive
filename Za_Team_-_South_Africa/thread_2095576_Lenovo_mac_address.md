---
title: "Lenovo mac address"
date: 2012-12-17
forum: Za Team - South Africa
---

### Post by roanantelope on 2012-12-17
Hi Ubuntu,

I have a think pad by Lenovo. The mac address is underneath the lap top, but this does not seem to be correct. what other way can I check for the mac address please.

roanantelope.

---

### Post by haqking on 2012-12-17
> **roanantelope said:**
> Hi Ubuntu,

I have a think pad by Lenovo. The mac address is underneath the lap top, but this does not seem to be correct. what other way can I check for the mac address please.

roanantelope.

```
ifconfig
```

and look for the HW address

---

### Post by roanantelope on 2012-12-21
Thank you Shadow valley beans,
I found the mac address and the one I had was also correct. The problem is that when I activate the access control on my net-gear wi-fi. it will not allow my laptop access. If I disable the access control I have access. There are very close computers and I do not want to leave the access control off.

Regards,

roanantelope.

---

### Post by haqking on 2012-12-21
> **roanantelope said:**
> Thank you Shadow valley beans,
I found the mac address and the one I had was also correct. The problem is that when I activate the access control on my net-gear wi-fi. it will not allow my laptop access. If I disable the access control I have access. There are very close computers and I do not want to leave the access control off.

Regards,

roanantelope.

Well so in yoru access control list you have put the correct mac adress i presume ?

Remember that 0 will be a zero and not a letter, common mistake.

MAC addresses are hexadecimal so will only ever be a-f 0-9

also with it off, when connected most routers shoud list connected devices and you can choose them from the list.

Also you will have a mac address for your ethernet eth0 and your wireless (probably wlan0)

---

### Post by roanantelope on 2012-12-26
> **haqking said:**
> Well so in yoru access control list you have put the correct mac adress i presume ?

Remember that 0 will be a zero and not a letter, common mistake.

MAC addresses are hexadecimal so will only ever be a-f 0-9

also with it off, when connected most routers shoud list connected devices and you can choose them from the list.

Also you will have a mac address for your ethernet eth0 and your wireless (probably wlan0)
Thankyou haqking,

I went into attachments connected, and found that a different mac address was given. I used these mac numbers, and lo and behold it allows only the two laptops through that I authorized. I appreciate your help. Seasons greetings to you and family.

Regards,
roanantelope.

---

### Post by haqking on 2012-12-26
> **roanantelope said:**
> Thankyou haqking,

I went into attachments connected, and found that a different mac address was given. I used these mac numbers, and lo and behold it allows only the two laptops through that I authorized. I appreciate your help. Seasons greetings to you and family.

Regards,
roanantelope.

You're welcome.

remember too use thread tools to mark as solved.

Cheers

---

