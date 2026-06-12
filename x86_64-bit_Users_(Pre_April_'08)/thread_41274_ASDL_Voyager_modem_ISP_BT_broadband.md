---
title: "ASDL Voyager modem ISP BT broadband"
date: 2005-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fruitbat™ on 2005-06-12
sorry for this newbie questions :???: 

1) not sure if this should be in networking but running 64 bit version of Ubuntu.

i have a asdl voyager modem that my ISP BT broadband sent to me . Have hunted around on net to try and get it to install and setup but it is over my head.

i did try this method from this site

[http://www.thecaretaker.org.uk/drivers/btvoyager/btvoyagerlinux.htm](http://www.thecaretaker.org.uk/drivers/btvoyager/btvoyagerlinux.htm)

but driver/flash are for i386 not 64 bit so dont know if that is reason not working.
Could someone plz plz have a look or if they have already installed this modem to use with BT broadband i would be most grateful for any tips or hints.

i could be doing it all wrong but after spending hrs at it i have hit a brick wall  ](*,) 

Regards
FB

---

### Post by skylark on 2005-06-14
I'm a newbie too and dont have this modem, but I did have a quick glance at that howto. Specifically I read this section:

```
Download the source, either by getting hold of the latest release, or by checking it out of CVS:

mkdir stuff
cd stuff
cvs -d:pserver:anonymous@cvs.eciadsl.sourceforge.net:/cvsroot/eciadsl login
password is guest
cvs -z3 -d:pserver:anonymous@cvs.eciadsl.sourceforge.net:/cvsroot/eciadsl co usermode

Then compile...

cd stuff
make

You could try a make install, use the eciadsl documentation to get the thing working or use the stuff in the rest of this page.

If you want to follow what I did, after compiling, set up a /usr/local/adsl directory.

mkdir /usr/local/adsl
cp eci-load1 eci-load2 pppoeci /usr/local/adsl
cp eci_firm_kit_wanadoo.bin eci_wan3.dmt.bin /usr/local/adsl
```

...which I gather implies you are meant to build the eci_firm_kit_wanadoo.bin binary from source?? which is then flashed to the modem firmware? If this is the case then possibly you should rebuild eci_firm_kit_wanadoo.bin from source but this time specify a 32-bit i386 output target? I think this is possible with some option to gcc but I've never tried it. Ignore this if eci_firm_kit_wanadoo.bin comes precompiled/bundled from somewhere else, in which case I'm not sure where the problem could lie.

---

### Post by mistermax on 2005-12-13
Don't mean to be stupid, but if you can't get connected with the modem- how do you get a connection to cvs.sourceforge to check the eci adsl components out?

---

