---
title: "Problems when installing kubuntu"
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ninjaa on 2006-09-25
Hi.

I have som serious problems to get kubuntu and xubuntu work on my computer. I can boot up and choose "Install Kubuntu", but when kubuntu do a system check it always hangs when "starting ACPI services" comes up. I have tried with acpi=off and that doesn´t work either.
Then I tried to install suse and it worked to do a normal install, but the system hangs when i start suse. 
Anyone who know what the problem could be?

/Danny

---

### Post by kuja on 2006-09-25
Could be a BIOS issue, maybe. Take a looksee at the ACPI related BIOS settings.

---

### Post by ninjaa on 2006-09-25
In BIOS there stod "ACPI suspend type [S1].
I can choose S1, S3 or both. Does it work to switch to s3 maybe?

---

### Post by tymek666 on 2006-09-25
Are you running ati chipset?

---

### Post by ninjaa on 2006-09-25
No. My computer specs are A64 3500+, epox nforce3, nvidia geforce3.

---

### Post by tymek666 on 2006-09-26
Maybe try to boot with noapic option.

---

