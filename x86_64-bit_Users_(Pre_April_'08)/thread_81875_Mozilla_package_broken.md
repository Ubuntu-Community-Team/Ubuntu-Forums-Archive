---
title: "Mozilla package broken"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Simpele on 2005-10-25
When I try to install the Mozilla meta-package through Adept, I get 'BREAK (install)' under Action and when I commit changes, there's no mail-client installed. Is there a solution to the problem?

---

### Post by pepster on 2005-10-25
I had a similar problem. In my case it was a mis-configure repository list due to the hoary -> breezy update.

Make sure your breezy and breezy-updates sections contain 'main' and 'universe'


-Joseph

---

### Post by Simpele on 2005-10-26
Thank you, that worked!

---

