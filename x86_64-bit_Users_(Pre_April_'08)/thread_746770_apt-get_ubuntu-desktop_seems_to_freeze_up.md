---
title: "apt-get ubuntu-desktop seems to freeze up"
date: 2008-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by eriksays on 2008-04-05
running 7.10 for 64 bit intel architecture.

installed "server version" and followed up with "sudo apt-get install ubuntu-desktop"

install seemed to have run well; however it never really finished as i was left with the system asking for the cd to be inserted (it was inserted)

link to the architecture i'm running: [http://www.circuitcity.com/ccd/productDetail.do?oid=206394&WT.mc_n=8360&WT.mc_t=U&cm_ven=EMAIL&cm_cat=CIRCUITCITY.COM&cm_pla=EMA_ORDER_CONFIRMATION_DI-%3ES2%20-%20PRODUCT%20SPOT&cm_ite=1%20PRODUCT&cm_keycode=8360#prodspecs](http://www.circuitcity.com/ccd/productDetail.do?oid=206394&WT.mc_n=8360&WT.mc_t=U&cm_ven=EMAIL&cm_cat=CIRCUITCITY.COM&cm_pla=EMA_ORDER_CONFIRMATION_DI-%3ES2%20-%20PRODUCT%20SPOT&cm_ite=1%20PRODUCT&cm_keycode=8360#prodspecs)

if anyone has suggestions, thank you:

---

### Post by Kilz on 2008-04-05
> **eriksays said:**
> running 7.10 for 64 bit intel architecture.

installed "server version" and followed up with "sudo apt-get install ubuntu-desktop"

install seemed to have run well; however it never really finished as i was left with the system asking for the cd to be inserted (it was inserted)

link to the architecture i'm running: [http://www.circuitcity.com/ccd/productDetail.do?oid=206394&WT.mc_n=8360&WT.mc_t=U&cm_ven=EMAIL&cm_cat=CIRCUITCITY.COM&cm_pla=EMA_ORDER_CONFIRMATION_DI-%3ES2%20-%20PRODUCT%20SPOT&cm_ite=1%20PRODUCT&cm_keycode=8360#prodspecs](http://www.circuitcity.com/ccd/productDetail.do?oid=206394&WT.mc_n=8360&WT.mc_t=U&cm_ven=EMAIL&cm_cat=CIRCUITCITY.COM&cm_pla=EMA_ORDER_CONFIRMATION_DI-%3ES2%20-%20PRODUCT%20SPOT&cm_ite=1%20PRODUCT&cm_keycode=8360#prodspecs)

if anyone has suggestions, thank you:

Without the desktop, you may not have the cd auto mount. So you will have to mount the cd. The other alternative is to comment out the cd line in your sources.list, this is a better idea as you will get all the latest packages.

---

