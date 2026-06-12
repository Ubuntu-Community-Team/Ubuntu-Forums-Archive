---
title: "Error installing directx9 but still working :is that normal?"
date: 2008-08-24
forum: Wine
---

### Post by sonnet on 2008-08-24
Hi I installed the directx9 with wintricks.
The installation process returns me errors like these:
om@tuxonfire ~ $ cd /home/tom/dx
tom@tuxonfire ~/dx $ wine DXSETUP.EXE
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
(snip about 100 lines)
err:setupapi:do_file_copyW Unsupported style(s) 0x144
tom@tuxonfire ~/dx $ err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"
err:rundll32:main Unable to load L"streamci"


I downloaded and copied stremci.dll in system32 folder in wine and checked it was registered a native in wine config.
Then I started dxiag with command "wine dxiag".
I checked about problem and dxiag said that ddrawex was missing, so I downloaded that as well and put in system32 folder. It was soon recognised, I launched dxiag screen again and no problem were found.
So I launched the 3d test on dxiag and they worked.
Is that means that directx9 are installed and working fine in wine?
A strange thing is that I have a directx folder in .wine/system32 but there's nothing in there.All the directx dll are under system32.Is that ok?

---

