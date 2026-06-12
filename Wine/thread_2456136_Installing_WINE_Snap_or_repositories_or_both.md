---
title: "Installing WINE: Snap or repositories or both?"
date: 2021-01-05
forum: Wine
---

### Post by Paddy Landau on 2021-01-05
I'm a bit confused about installing WINE. I don't need the latest and greatest, so I'm not going to [install the official PPA]("https://wiki.winehq.org/Ubuntu").

However, I was wondering what the two snap packages wine-platform-5-stable and wine-platform-runtime are. Are they full replacements for installing wine? Do they add to an existing WINE installation?

I currently have the following installed; I don't remember why I chose these; and I'm wondering if I've installed too much:

[LIST]
[*]wine
[*]wine32:i386
[*]Snap package wine-platform-5-stable
[*]Snap package wine-platform-runtime
[/LIST]
I don't have wine64 installed. Should I install it?

I'm running Ubuntu 20.04.

Thanks, from a rather confused person!

---

### Post by deadflowr on 2021-01-05
Use the repository version.
The snap packages are confusing to say the least:
per wine-platform-5-stable:
> description: |
  This snap creates a WINE stable 5 via content sharing to be used by other
  snaps that are using WINE.


And the runtime snaps are more or less the same

Basically, as I read it the snap wine packages aren't wine, both layers to add for using wine programs pre-built as snaps.

---

### Post by Dennis N on 2021-01-05
>  I was wondering what the two snap packages wine-platform-5-stable and wine-platform-runtime are. Are they full replacements for installing wine? Do they add to an existing WINE installation?

Some Windows programs are packaged as Snaps. These are the only ones that can use the packages you displayed.
Such as:
Notepad:
[https://snapcraft.io/install/notepad3/ubuntu](https://snapcraft.io/install/notepad3/ubuntu)
When you install it, it installs the needed support libraries which are what you are displaying:
```
dmn@Sydney-vm:~$ sudo snap install notepad3
```
installs (showing new packages only here):
```
dmn@Sydney-vm:~$ snap list
Name                    Version                     Rev    Tracking         Publisher   Notes
notepad3                5.20.915.1                  137    latest/stable    mmtrt       -
wine-platform-5-stable  5.0.3                       13     latest/stable    mmtrt       -
wine-platform-runtime   v1.0                        200    latest/stable    mmtrt       -

```
And it works!
Non-snap Windows programs work with the repository Wine installation.
There are more such Windows snap packages, but not many. A more interesting package would be the snap for Adobe Acrobat Reader.

---

### Post by Paddy Landau on 2021-01-06
> **deadflowr said:**
> Use the repository version.
The snap packages are confusing to say the least
Yes, I also found the description confusing! But the reply by @Dennis N seems to clarify things.
> **Dennis N said:**
> Some Windows programs are packaged as Snaps. These are the only ones that can use the packages you displayed.
…
A more interesting package would be the snap for Adobe Acrobat Reader.
Thank you. That clarifies things. I installed the snap for Adobe Acrobat Reader (acrordrdc) recently.

So, as a test, I uninstalled the snaps for acrordrdc and both of the WINE packages, and then I reinstalled acrordrdc.

As you predicted, acrordrdc automatically installed the two WINE packages, which explains why I couldn't remember why I installed the two WINE packages — because I didn't!

Thank you

---

