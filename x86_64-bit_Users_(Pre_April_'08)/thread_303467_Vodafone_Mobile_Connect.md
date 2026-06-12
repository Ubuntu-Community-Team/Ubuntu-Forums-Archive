---
title: "Vodafone Mobile Connect"
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by gekkos on 2006-11-20
Hi,
Try to setup my Vodafone Mobile Connect Card but no succes
I was reading a lot of Howto but nothing.
When I check the status with

```
# cardctl status 
  Socket 0: 
    3.3V CardBus card 
    function 0: [ready]
```

and

```
# cardctl config 
  Socket 0: 
    Vcc 3.3V Vpp1 3.3V Vpp2 3.3V 
    interface type is "cardbus" 
    irq 185 [exclusive] [level] 
    function 0:
```

So I think that my card is recognised but when I look in /var/log/syslog I only get this
Code:

```
# tail -f /var/log/syslog localhost kernel: [ 1608.287412] pccard: CardBus card inserted into slot 0
```

My kernel is : 2.6.15-27-amd64-generic

Anyone an idee to help me further??
Thanks

---

### Post by FloSynergy on 2007-03-02
similar issues...have you checked out

[http://www.pharscape.org/index.php?option=content&task=view&id=28](http://www.pharscape.org/index.php?option=content&task=view&id=28) ?

---

