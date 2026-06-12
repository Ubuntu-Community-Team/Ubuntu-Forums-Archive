---
title: "Another brightness thread"
date: 2008-08-10
forum: x86 64-bit Users
---

### Post by kjohansen on 2008-08-10
I have been all over this forum and the world to find a solution to my screen brightness problem.  I have tried every solution I could find and none have worked.

The most promising seemed to be the toshset app.  This worked for my bluetooth controls but for my lcd command, it errors.

Even more perplexing the screen will dim when idle as controlled by the power manager, but I cant control it.  I dont care if the functions keys dont work, an ugly work around is fine with me.

Does anyone have any suggestion on how to get brightness working?

I would be eternally grateful to whomever saves my eyes from the dim screen I am stuck with.

Error from toshset
```

johank@johank-laptop:~$ sudo toshset -lcd 2
SciFeature:action: error setting lcd brightness
	SciSet returned: FAILURE
lcd brightness: bright


```

Info:
```

johank@johank-laptop:~$ sudo lshw | head -n 30
johank-laptop             
    description: Notebook
    product: TECRA A9
    vendor: TOSHIBA
    version: PTS53U-0KR023
    capabilities: smbios-2.4 dmi-2.4
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=2E544080-5795-11DD-8053-B05D78060870
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$C0871N2S
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 2.00 (03/06/2008)
          size: 96KiB
          capacity: 4032KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing vesa cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0


```

---

### Post by ericson578 on 2008-08-11
I installed the Power Manager Brightness Applet 2.22.1 (can't remember if I used the package manager or just downloaded it)

Here's the url for more info: [http://www.gnome.org/projects/gnome-power-manager/](http://www.gnome.org/projects/gnome-power-manager/)

Added this to my top menu bar, works great!

---

### Post by cdtech on 2008-08-11
A quick fix to adjust the brightness would be to go into "gconf-editor" under "apps > gnome-power-manager > backlight" and adjust it that way until you find a fix.

---

### Post by kjohansen on 2008-08-14
i could of sworn that the computer would dim on idle, but apparently I lied.

any ideas on whether this is a graphics card problem or a toshiba problem...

---

