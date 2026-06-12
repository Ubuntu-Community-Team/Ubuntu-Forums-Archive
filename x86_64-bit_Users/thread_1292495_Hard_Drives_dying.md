---
title: "Hard Drives dying"
date: 2009-10-15
forum: x86 64-bit Users
---

### Post by GeekPapa on 2009-10-15
I am now working on my third hard drive with Mythbuntu 64.  I bought a 1TB Maxtor and shortly after adding a second one the first one died.  The second one died a few months later.  I replaced them with a Hitachi 640GB drive and it died today.  Between the first and second Maxtor, I changed mother boards from an ECS GF7050VT-M to a Biostar GF7100P-M7S, both hosted my intel Q9400.  The common thread, on the hardware side is that they use similar VIA SATA drivers.  Seagate, who owns Maxtor, has, to their credit agreed to replace the two 1TB drives and replacements are en-route.  I hope to solve my issue here before I get them.  I have replaced my SATA cables too. 

The symptoms are increasing incidents of SATA-resets (really remind me of scsi resets), and eventual death.  "Death" being that the drive will power up, but is no longer recognized by Linux (or any other O/S I have access to).

So, maybe...

Power Supply?
Another Motherboard?
Go back to stone tablet and chizel?

Appreciate the help in advance.

---

### Post by falconindy on 2009-10-16
IMO: Really hard to blame anything but the power supply.

---

### Post by lindsay7 on 2009-10-16
Heat kills hard drives.  Make sure you have some air flowing over the hard drive.  I kept having the hard drive die in a computer which is in a tight compartment under a desk. I kept adding fans until the hard drive failures stopped. I also added a fan that attaches to the hard drive too (Tiger Direct).

---

### Post by Arup on 2009-10-16
In your case its the PSU, the PSU fails to deliver the necessary amps to the HDD thereby killing it. Heat is also another factor that lowers HDD life but won't be directly responsible for killing it though.

---

### Post by GeekPapa on 2009-10-16
> **lindsay7 said:**
> Heat kills hard drives.  Make sure you have some air flowing over the hard drive.  I kept having the hard drive die in a computer which is in a tight compartment under a desk. I kept adding fans until the hard drive failures stopped. I also added a fan that attaches to the hard drive too (Tiger Direct).

I am randomly replying to Lindsay7 because that's my daughter's name and I am grooming her to be a geek like her papa.  :-)  I totally agree.  Heat and power.  I am going to Fry's to get a new case with lots of (quiet) fans and a new super-duper power supply.

Thanks for the input.  I will report back on whether I can rescue the Hitachi.

---

### Post by GeekPapa on 2009-10-18
Ok, well, thanks gang! I put my motherboard and peripherals in a new case with a 600W power supply from Fry's.  Total expense $110.  The new case has NEON! Woo. But actually, it has a top mount USB and front side audio with a place to put my T-Mobile G1 while I am transferring movies, data, or recharging.  Kind of useful... almost.  The case itself has a ton of bays and is generally well-engineered. 

Best of all.  I plugged everything on and it came up first shot with a chkdsk.  Whew... so far everything seems to be intact and running fine.

I think this one can be closed.

---

