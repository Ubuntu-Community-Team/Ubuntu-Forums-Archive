---
title: "Hibernation issues"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sketchyjustin on 2007-10-25
Hibernate / suspend don't seem to be working.  I've googled like crazy for a fix and keep seeing the same few suggestions that don't work.  So...  How can I disable suspend / hibernate entirely?  I used System / Preferences / Power Management and set both values (set computer to sleep / display to sleep) to NEVER, but it still passes out if I leave it for an hour or two.

---

### Post by sketchyjustin on 2007-10-26
Well, never mind.  Just commented out the following lines in /etc/default/acpi-support:

# Comment the next line to disable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true


Figured I'd throw that up here for future reference.

---

