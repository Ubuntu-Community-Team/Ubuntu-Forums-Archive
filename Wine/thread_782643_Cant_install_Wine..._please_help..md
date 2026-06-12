---
title: "Cant install Wine... please help."
date: 2008-05-05
forum: Wine
---

### Post by malaya on 2008-05-05
- please help me. i tried to install wine.. but i received this error message

> Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems


- then when i try to update the same error message appears
- skipping that step, i try to click the link from the winehq.com to install wine.. and then i received this error message

> cannot install 'wine'(E:Unable to correct problems you have held broken packages)

- please help me... thanks in advance!

---

### Post by jacksaff on 2008-05-05
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

---

### Post by malaya on 2008-05-06
> **jacksaff said:**
> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

thanks i have my wine now

---

### Post by marianlibrarian on 2008-05-08
Thank you too. That took care of that error message but I am still unable to update wine due to the following:

  	 	 	 	 	 	 	 	 	 	  [http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg:](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg:) Could not resolve 'wine.lowvoice.nl'
 [http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz:](http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz:) Could not resolve 'wine.lowvoice.nl'

---

