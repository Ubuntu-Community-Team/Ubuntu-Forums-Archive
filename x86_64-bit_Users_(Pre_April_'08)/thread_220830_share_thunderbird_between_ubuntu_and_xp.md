---
title: "share thunderbird between ubuntu and xp"
date: 2006-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Donnieboii on 2006-07-22
Hello,

i've been trying to share my mail and settings between ubuntu and xp with thunderbird using [this]("http://ubuntuforums.org/showthread.php?t=203524&highlight=howto+thunderbird") howto.
I create profile in windows and make sure it works then in ubuntu I create new profile and direct it to that folder when i try to run thunderbird it says > cant run this profile its being in use already please close other instance or try different profile.
but this morning i tried again new p[rofile and evrything and it work so to test it i closed thunderbird and restarted it but came up with this error again... does anyone know how to solve this??

Thankss...

Donnieboii

---

### Post by Donnieboii on 2006-07-22
bump.. does anyone know?

---

### Post by juicemansam on 2006-07-22
I haven't read the how-to, but here's what I did while working with a 64-bit and 32-bit linux installation (seperate hard drives). It's the concept, not the implementation that I'm focusing on.

I have two hard drives, where one has a 64-bit system, and the other a 32-bit system. My permanent system is the 64-bit system, but due to bad motherboard, I had to use my 32-bit system, but didn't want to have two copies of emails, or more importantly, lose them by setting up a POP account (of course I could easily not remove them from the server).

Basically what I did was mount the hard drive with the thunderbird profile I will permanently use (the 64-bit OS), and make a symlink to the profile directory in question. Then I edited the profiles.ini (in .mozilla-thunderbird) file and changed the name of default directory to be that of the symlinked one.

In your case you'll need a fat-based partition. I'd setup thunderbird in Windows first, and have it use that partition for storing it's data. Then just mount/symlink and edit the profile.ini in Linux. I'm not sure about the procedure on setting up thunderbird in Windows, but I suspect it has something to do with "Local directory" in the account settings. I don't know if you can just change the directory without it already existing first, so I'd copy it to the new location before changing anything in thunderbird.

I'll try sharing my thunderbird settings on my brother's XP computer across the network with my ubuntu system (should be very similar but with network shares instead of partitions), and post back with what worked.

---

### Post by Donnieboii on 2006-07-23
thanks... i will try that.. but have you seen my other thread... about the wine-tools.. do you know anything for that???

thanks..

Donnieboii

---

