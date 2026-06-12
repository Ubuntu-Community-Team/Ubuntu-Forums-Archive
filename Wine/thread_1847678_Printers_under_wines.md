---
title: "Printers under wines"
date: 2011-09-21
forum: Wine
---

### Post by mekhetfi.miled on 2011-09-21
[COLOR=black][FONT=Verdana]Dear Sir,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My plan to run oracle forms, reports 6i application under wine,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1- i succeed run it but when i tried to printout it's gave me no printer available, that i already have Zebra ZM400, so [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1- How i can configure printers under wine?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2- Can i run terminal from cmd.exe (So i can use HOST command from the forms 6i)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]3- How i can change the default printer from wine (CMD command).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks in advanced,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Miled Moukhtafi[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Oracle DBA[/FONT][/COLOR]

---

### Post by ergo-proxy on 2011-09-21
Check here 
[http://wiki.winehq.org/Printing](http://wiki.winehq.org/Printing)
but I doubt it works for you... maybe if you tried to use a network printer... but not sure.

---

### Post by disabledaccount on 2011-09-21
Generally printers are available trough windows (wine) API, so if Your priner works in Linux (CUPS) then it should work in wine too -> configure the printer under Linux.
Windows cmd is not supported very well, but if Your cmd works, then You can just map the printer as a device port of Your choice by creating a link somewhere in wine prefix scope, e.g. $HOME/.wine/dosdevices.
This works well for almost any external device, even such unusal ones like interface for frequncy converters (I'm using Moeller DriveSoft2 in such way :) )

---

### Post by mekhetfi.miled on 2011-09-22
thank you,
the printer it's working now under wine, but how i can change the default printer
 
Regards,

---

