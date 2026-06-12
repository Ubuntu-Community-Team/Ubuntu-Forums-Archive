---
title: "AT&amp;T Sierra 881 wireless card in Hardy Heron"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by ronrafajko on 2008-10-08
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076) has information on how to use an AT&T air card with Linux.

Update: I believe the URL has changed to: [https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/kw/Sierra%20881/r_id/166#driver_download](https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/kw/Sierra%20881/r_id/166#driver_download)


The only thing I needed to change was the PAP/CHAP authentication, which  requires a username and password.  AT&T does not use one so I switched the authentication to scripted and it connected.

I set the modem up on /dev/ttyUSB0 for my HP Pavilion dv6000 laptop computer.

In windows I get between 1388 and 1989 kbps d/l speeds and 356 to 894 kbps U/L speeds with the card.  In Ubuntu I am much slower, around 600 D/L and 78 U/L. :(

update:  after a reinstall of 9.04 after a HDD crash I am now getting a max d/l speed of 361 kb/sec!  :-)

---

