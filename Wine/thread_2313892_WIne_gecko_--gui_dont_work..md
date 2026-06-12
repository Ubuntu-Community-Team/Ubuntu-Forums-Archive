---
title: "WIne gecko --gui dont work."
date: 2016-02-16
forum: Wine
---

### Post by Portaro on 2016-02-16
There is my problem wine gecko --gui dont work, anyone have an idea why this occur, I also search the gecko.exe and dont find it.

> $ wine gecko --guifixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:wer:WerRegisterMemoryBlock (0x530aa498 6144) stub
fixme:wer:WerRegisterMemoryBlock (0x530a4000 4) stub
err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder
err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder
err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder
err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder
wine: cannot find L"C:\\windows\\system32\\gecko.exe"
[1153]$ err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder
err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder
err:menubuilder:convert_to_native_icon error 0x88982F81 initializing encoder




---

### Post by gordintoronto on 2016-02-17
try this command: sudo locate gecko.exe

It might be in Wine's C:\\windows\\system32

What does gecko -gui do?

---

### Post by Portaro on 2016-04-22
Excuse me for this later reply, the command with sudo dont work.
The gecko --gui command I see on a configuration of an  aplication to install on wine I think ,  but now  I dont remember why I need to launch gecko in gui mode to install and what is the aplication .

---

