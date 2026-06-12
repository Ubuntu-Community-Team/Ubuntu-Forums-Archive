---
title: "Please help with getting Realtek ALC888 sound to work on Mythbuntu 9.04, using amd64"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by X00M on 2009-05-11
Hi,

Got a GA-EP31-DS3L mobbo + Intel Q8200, ICH7 chipset that uses an ALC888 Realtek chip.
I have installed the Mythbuntu amd 64-bit release. I didn't see any release for Intel X86-64-bit processors, so I figured this should work for all 64-bit X86 processors? That being said the OS installed fine.

**Update: I managed to get the sound working using this method:**

**Step 1:** Applications->Accessories->Terminal.  At the prompt paste in:
cat /proc/asound/card0/codec#* | grep Codec
it'll return something like, Codec: Realtek ALC888

**Step 2**: Go to [http://www.mjmwired.net/kernel/Docum...figuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt")
Find your Codec. There is a list of model name and descriptions for each Codec starting on line number785. Copy the model name you've got. For me it was 6stack-dig.

**Step 3:** Again at the terminal type sudo gedit /etc/modprobe.d/alsa-base
Provide pw when prompted.  Add at the end of file: options snd-hda-intel model=6stack-dig
Of course with your model in place of 6stack-dig.  Save the file.  That's it!

[B]However it just works, there's no realtek sound manager or any registration of the driver in
the hardware drivers utility. Anyway I can launch some kinf of realtek HD manager or add the
driver properly ?[/B]



I have now re-installed Mythnuntu again and trying to figure out how I can install the sound driver. Is it ok that I am using an AMD 64 release on intel platform ? Are there ALC888 drivers available for the 64-bit release? Also in general is the 64-bit version backwards compatible with 32-bit stull ?


Thanks for your advice..

---

### Post by Yellow Pasque on 2009-05-11
> **X00M said:**
> However it just works, there's no realtek sound manager or any registration of the driver in the hardware drivers utility. Anyway I can launch some kind of realtek HD manager or add the driver properly ?
The hardware drivers utility is only for proprietary/binary blobs. The driver is already added "properly." You're not in Kans, errr, Windowz world anymore.

---

