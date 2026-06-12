---
title: "AMD laptop heating issues"
date: 2005-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by WebDrake on 2005-11-17
I came across this message on one of the Debian usenet groups...  Seems kind of relevant.  Anyone have this experience with Ubuntu?

If someone knows how to fix it, perhaps someone could go across and help out the poor guy; the original post was on linux.debian.ports.x86-64 .

> I've been working steadily over the past few weeks to get my new HP nx6125
working under Debian (amd64 port) and have made significant progress.
However, there is one considerable problem: thermal events don't seem to be
recognised or processed by the kernel (until I do a
cat /proc/acpi/thermal_zone/TZ?/temperature). As soon as I do anything CPU
intensive I really run the risk of frying my laptop :-(

To be more specific, I am running kernel 2.6.13.4
([www.kernel.org](www.kernel.org) vanilla) with the double timer patch applied (see
[http://bugzilla.kernel.org/attachment.cgi?id=6061&action=view)](http://bugzilla.kernel.org/attachment.cgi?id=6061&action=view)). When I boot
up, my thermal trip points get set nicely. The first is at 58 *C, then 65*C,
then 75 *C, and 80*C (S5 = 95 *C). When I was testing things I was doing
frequent executions of

cat /proc/acpi/thermal_zone/TZ?/temperature

and I would observe the temp rise to 58 C, then the fan would kick in, the
first trip point would then (automatically) re-set to 50 C and the CPU would
cool through 8 C before the fan turned off (nice, I thought, and very clever
this re-setting of trip points--sorry I'm very new to ACPI). When the fan
turned off, the trip point would again re-set to 58 C. So, I thought all was
working well. However, subsequent tests done by running glxgears and not
executing the above cat command allowed the CPU temp to rise above several
trip points without the fans kicking in! Only when I ran the above cat
command did the fans start!?

So, I stopped acpid and did a

cat /proc/acpi/event

while running glxgears. I waited a while and then did a
cat  /proc/acpi/thermal_zone/TZ?/temperature to see that indeed the temp of
TZ1 had exceeded 58C---and immediately /proc/acpi/event received a thermal
event (note: the temp had already exceeded 58 C, my first thermal trip point;
the thermal event only occurred when I did the 'cat'). So, in order for
thermal events to "get through/processed" I need to keep doing
cat  /proc/acpi/thermal_zone/TZ?/temperature!!!!

Can anybody shed some light on this behaviour. I don't know much about ACPI,
but it seems (?) like the linux kernel is not processing the thermal events
properly. Incidentally, I am also seeing spurious syslog errors that read
APIC error on CPU0: 40(40) meaning that some interrupts presumably are not
being correctly identified by the interrupt controller (thermal ones? could
there be some correlation here?).

Other info: the HP nx6125 is a Turion 64 based laptop with ATI chipset (yes,
 I know). I am running acpid and have just installed powernowd (doesn't fix
 it). I have also observed the above behaviour running the standard Debian
 2.6.12-1-amd64 kernel (booting with no_timer_check to avoid double timer
 interrupts).  Any help, suggestions would be greatly appreciated.  If anyone
 has any ideas why catting  /proc/acpi/thermal_zone/TZ?/temperature gets
 things to work, I'd be very happy to hear an explanation, too.


---

### Post by grillip on 2006-01-24
[http://acpi.sourceforge.net/dsdt/view.php?manufacturer=HP&name=nx6125](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=HP&name=nx6125)

---

### Post by hlm_worker on 2006-02-08
Hi,
As a near future new HP nx6125 owner (turion), it isn't clear for me if the heating issues are related to the ubuntu AMD-64 release only, or to the x86 release too ?
Thanks

---

