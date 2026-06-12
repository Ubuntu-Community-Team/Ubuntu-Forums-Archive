---
title: "I'm back! modem issues"
date: 2006-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by teripittman on 2006-04-08
I've posted about this before but the issue is truly making me crazy. The modem worked fine in Hoary. Now it won't hang up correctly so I can't connect the next time I dial. On bootup, I get an "illegal UART type" for both ttyS0 and ttyS1. wvdial always dials but never connects. It does seem to hang up correctly. Both Gnome ppp tool and the network tool will dial out sometimes but don't hang up correctly. It seems to help when I delete the postfix processes, but not always. Does anyone have any ideas on what I can do to fix this? It's a G3 with an external modem. (I'm not home so don't have the brand but I think it's a Supra Express)

---

### Post by eriefisher on 2006-04-08
The supra express come in both serial and usb I think. There should be no problem with a serial modem but if it is a usb type you might have a driver issue.
Most usb modems are still software modems(winmodems). I would maybe look into another modem driver if of course it is in fact a usb type.

eriefisher

---

### Post by teripittman on 2006-04-09
Nope, this is not a USB modem. It uses the old style Apple modem port. Worked fine in Hoary. I suspect that something in the Gnome desktop upgrade caused this. I can't figure outt why I get that illegal UART message. And the same modem works fine under OS9, of course. I can get it to work reliably a couple of times after I reboot the machine. Then it's a struggle. I am trying to hold on until the Dapper Dan upgrade, thinking that there might be a fix by then.

---

### Post by eriefisher on 2006-04-09
After a quick Google search the one thing that keeps popping up is to use "setserial" to define the irq. I don't know much about it but it might be worth a try.

eriefisher

---

### Post by teripittman on 2006-04-21
[QUOTE=eriefisher]After a quick Google search the one thing that keeps popping up is to use "setserial" to define the irq. I don't know much about it but it might be worth a try.

eriefisher[/QUOTE]
I think you're on to something. I can at least use this to pull up the info on the two ports but I still can't get the autoconfig command to work. Also can't change the IRQs which are set for 15 and 16 (which seems strange). UART type shows it as undefined. I'm going to have to hack around and see if I can't get it to work a bit better. Thanks for the help!

---

