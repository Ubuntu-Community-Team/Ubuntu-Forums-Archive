---
title: "Fallout installation problem"
date: 2008-03-04
forum: Wine
---

### Post by kabanowster on 2008-03-04
I'm trying to install Fallout 2 via Wine

when running SETUP.EXE through the terminal it gives this back:

```

err:advapi:service_control_dispatcher pipe connect failed
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  237
  Current serial number in output stream:  238

```

I'm running Kubuntu Gutsy with CompizFusion, 64bits

changing wine OS to win98 does nothing.
I guess it must be something with graphic drivers? I have the latest sourced ati drivers, RadeonX1950.
fglrxinfo gives proper output.


Or maybe Xserver...

any ideas?
:popcorn:

---

### Post by kabanowster on 2008-03-05
any solution? can anyone tell what 'GLXUnsupportedPrivateRequest' means in general?

---

### Post by FrozenFox on 2008-03-05
Hrmmm. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=319](http://appdb.winehq.org/objectManager.php?sClass=version&iId=319)

The wineHQ page suggests everything should work correctly no matter the version between 0.9.46 and 0.9.54. Which version are you using?  wine --version in the terminal. I'll assume you're on the newest one, and guess perhaps something got borked regarding to fallout2. shrug. I've never played the game, but from looking it up it appears not to need a 3d card, so I wouldn't think it's a video driver problem..

My only suggestion is to try installing playonlinux [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)  and install an older version of wine inside it, install fallout2 in there, set playonlinux to run fallout2 in said older wine version, and report back if you have any luck..

---

### Post by kabanowster on 2008-03-06
it's a matter of drivers.. looks like they're little messy. I've got simmilar problems with Xfire for example.

I've installed latest ati drivers several times and from that time CCC tells I have no ATI driver installed, so it doesn't run at all. Also PlayLinux says I have no 3d accel installed... sounds ********.

I've reconfigured xorg and Fallout runs good on default vesa driver. The reinstall of ati then, makes no difference. I think all is just really messed up.. I'll finish playing Fall, then go back to ati drivers... simple. :)

---

