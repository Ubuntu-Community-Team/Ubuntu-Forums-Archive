---
title: "Dialing numbers and letters for PPP"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by michieru on 2005-12-11
I am currently trying to dial a sequence of letters and numbers through PPP.

I already was able to get ubuntu to talk with my usb modem but in order to access the net through it I must dial "S=2" this is basically nextel's packetstream service. But ubuntu only accepts digits. Is there any way to allow characters, and symbols to as well be dialed?

---

### Post by ssam on 2005-12-11
the telephone system only uses 12 tones for dialing, representing 0-9, * and #. sometimes letters are used to represent numbers:
ABC => 2    DEF => 3    GHI => 4    JKL => 5
MNO => 6   PQRS => 7    TUV => 8   WXYZ => 9
so that the phone number "800-hello" would be "0800 43556".

can you use this to translate you're dial up thing into just numbers?

---

### Post by michieru on 2005-12-11
That I understand but it has nothing related to that. s=2 is for packetstream data service. I been trying to use pppconfig instead which allows me to dial that command. But so far without any luck because I am having trouble communicating with the modem.

---

### Post by ssam on 2005-12-11
i am sorry i miss understood your problem.

i usually use wvdial for dialup. it lets you specify initiation commands in its config file. man wvdial has the example
> 
              [Dialer Defaults]
              Modem = /dev/ttyS2
              Baud = 57600
              Init = ATZ
              Init2 = AT S11=50
              Phone = 555-4242
              Username = apenwarr
              Password = my-password

              [Dialer phone2]
              Phone = 555-4243

              [Dialer shh]
              Init3 = ATM0

              [Dialer pulse]
              Dial Command = ATDP

are the things on the init lines what you mean?

---

### Post by michieru on 2005-12-11
No just need the phone number to dial S=2 it's a command for the phone for it can open the packetstream service. But thank you I got it to work with wvdial.

---

