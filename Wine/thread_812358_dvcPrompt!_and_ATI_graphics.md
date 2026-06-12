---
title: "dvcPrompt! and ATI graphics"
date: 2008-05-29
forum: Wine
---

### Post by ezramorris on 2008-05-29
Hi,
I'm trying to install dvcPrompt! (a teleprompt program) through wine, the installer runs great, but when I try to run it I get this:
```
ezra@ezra-laptop:~/.wine/drive_c/Program Files/DVcreators/dvcPrompt!$ wine dvc*.exe
fixme:advapi:RegisterEventSourceA ((null),"MDM"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MDM"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0001002,(nil),0x0000,0x00000000,(nil),0x7e0fb9e0): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ntoskrnl:KeInitializeSpinLock 0x4577a4
fixme:spoolsv:serv_main (0 (nil))
ALSA lib pcm_dmix.c:813:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:winspool:OpenPrinterW PRINTER_DEFAULTS ignored => (null),(nil),0x00000008
[COLOR="Red"][B]X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  2863
  Current serial number in output stream:  2864[/B][/COLOR]

```
I've also got the red bit in other programs I ran, so I'm guessing this is a general issue. I have tried both with and without compiz.

Any ideas?

```
ezra@ezra-laptop:~$ apt-cache policy wine
wine:
  Installed: 0.9.59-0ubuntu5
  Candidate: 0.9.59-0ubuntu5
  Version table:
 *** 0.9.59-0ubuntu5 0
        500 http://gb.archive.ubuntu.com hardy-updates/universe Packages
        100 /var/lib/dpkg/status
     0.9.59-0ubuntu4 0
        500 http://gb.archive.ubuntu.com hardy/universe Packages

```

P.S. as a side note - is it possible to install another version of Wine but keep the original? so i could use the repo one for stuff that works, and the latest from the wine site for testing.

---

