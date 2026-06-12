---
title: "pcsx on powerpc"
date: 2009-04-08
forum: x86 64-bit Users
---

### Post by Cloud x blue on 2009-04-08
I've tried looking everywhere for this and I just cant find the solution and this is the last place i can think of really... Ive gotten  the screen to come up, but every time i try to run the cd it i get the error "RGB & YUV not found.    Quitting" right after it just shuts down... I also tried epsxe but i cant even get the window to come up. If anyone knows whats going on or needs more information I can try to provide it thanks.

---

### Post by Cloud x blue on 2009-04-08
sorry for the double post but here are the errors i get, finally had time to do this

WHEN I CLICK RUN CD I GET

cloudxblue@Ps3-Ubuntu:~$ pcsx
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
Loading memory card /home/cloudxblue/.pcsx/memcards/card1.mcd
Loading memory card /home/cloudxblue/.pcsx/memcards/card2.mcd
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
RGB & YUV not found.  Quitting.
cloudxblue@Ps3-Ubuntu:~$ 

_________________________

WHEN I CLICK CONFIG

Scanning /usr/lib/games/psemu/ for plugins
    Plugin file symlink: /usr/lib/games/psemu/cfgDFSound -> /home/cloudxblue/.pcsx/plugins/cfgDFSound
    Config file symlink: /usr/lib/games/psemu/cfgDFSound -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFSound
    Plugin file symlink: /usr/lib/games/psemu/cfgDFXVideo -> /home/cloudxblue/.pcsx/plugins/cfgDFXVideo
    Config file symlink: /usr/lib/games/psemu/cfgDFXVideo -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFXVideo
    Plugin file symlink: /usr/lib/games/psemu/libDFCdrom.so -> /home/cloudxblue/.pcsx/plugins/libDFCdrom.so
    Plugin file symlink: /usr/lib/games/psemu/cfgDFIso -> /home/cloudxblue/.pcsx/plugins/cfgDFIso
    Config file symlink: /usr/lib/games/psemu/cfgDFIso -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFIso
    Plugin file symlink: /usr/lib/games/psemu/libDFSound.so -> /home/cloudxblue/.pcsx/plugins/libDFSound.so
    Plugin file symlink: /usr/lib/games/psemu/libDFIso.so -> /home/cloudxblue/.pcsx/plugins/libDFIso.so
    Plugin file symlink: /usr/lib/games/psemu/libDFXVideo.so -> /home/cloudxblue/.pcsx/plugins/libDFXVideo.so
    Plugin file symlink: /usr/lib/games/psemu/libDFInput.so -> /home/cloudxblue/.pcsx/plugins/libDFInput.so
    Plugin file symlink: /usr/lib/games/psemu/cfgDFCdrom -> /home/cloudxblue/.pcsx/plugins/cfgDFCdrom
    Config file symlink: /usr/lib/games/psemu/cfgDFCdrom -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFCdrom
    Plugin file symlink: /usr/lib/games/psemu/cfgDFInput -> /home/cloudxblue/.pcsx/plugins/cfgDFInput
    Config file symlink: /usr/lib/games/psemu/cfgDFInput -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFInput
Could not open plugins directory: '/usr/local/lib/games/psemu/'
Scanning /home/cloudxblue/.pcsx/plugins for plugins
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFSound -> /home/cloudxblue/.pcsx/plugins/cfgDFSound
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFSound -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFSound
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/dfxvideo.cfg -> /home/cloudxblue/.pcsx/plugins/dfxvideo.cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/dfxvideo.cfg -> /home/cloudxblue/.pcsx/plugins/cfg/dfxvideo.cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFXVideo -> /home/cloudxblue/.pcsx/plugins/cfgDFXVideo
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFXVideo -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFXVideo
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFCdrom.so -> /home/cloudxblue/.pcsx/plugins/libDFCdrom.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/dfcdrom.cfg -> /home/cloudxblue/.pcsx/plugins/dfcdrom.cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/dfcdrom.cfg -> /home/cloudxblue/.pcsx/plugins/cfg/dfcdrom.cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFIso -> /home/cloudxblue/.pcsx/plugins/cfgDFIso
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFIso -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFIso
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFSound.so -> /home/cloudxblue/.pcsx/plugins/libDFSound.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFIso.so -> /home/cloudxblue/.pcsx/plugins/libDFIso.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/dfiso.cfg -> /home/cloudxblue/.pcsx/plugins/dfiso.cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/dfiso.cfg -> /home/cloudxblue/.pcsx/plugins/cfg/dfiso.cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFXVideo.so -> /home/cloudxblue/.pcsx/plugins/libDFXVideo.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFInput.so -> /home/cloudxblue/.pcsx/plugins/libDFInput.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfg -> /home/cloudxblue/.pcsx/plugins/cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfg -> /home/cloudxblue/.pcsx/plugins/cfg/cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFCdrom -> /home/cloudxblue/.pcsx/plugins/cfgDFCdrom
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFCdrom -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFCdrom
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFInput -> /home/cloudxblue/.pcsx/plugins/cfgDFInput
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFInput -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFInput
Scanning bios dir /home/cloudxblue/Desktop/.pcsx/bios
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3000.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3000.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/.
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH5000.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH5000.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3002.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3002.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH5500.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH5500.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph7000.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph7000.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH1001.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH1001.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH7001.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH7001.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph7003.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph7003.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph5502.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph5502.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH101.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH101.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/scph7502.bin
    /home/cloudxblue/Desktop/.pcsx/bios/scph7502.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/..
Finished scanning bios dir /home/cloudxblue/Desktop/.pcsx/bios
BIOS directory is now /home/cloudxblue/Desktop/.pcsx/bios
Scanning bios dir /home/cloudxblue/Desktop/.pcsx/bios
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3000.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3000.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/.
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH5000.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH5000.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3002.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3002.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH5500.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH5500.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph7000.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph7000.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH1001.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH1001.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH7001.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH7001.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph7003.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph7003.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph5502.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph5502.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH101.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH101.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/scph7502.bin
    /home/cloudxblue/Desktop/.pcsx/bios/scph7502.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/..
Finished scanning bios dir /home/cloudxblue/Desktop/.pcsx/bios
Scanning /home/cloudxblue/.pcsx/plugins for plugins
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFSound -> /home/cloudxblue/.pcsx/plugins/cfgDFSound
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFSound -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFSound
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/dfxvideo.cfg -> /home/cloudxblue/.pcsx/plugins/dfxvideo.cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/dfxvideo.cfg -> /home/cloudxblue/.pcsx/plugins/cfg/dfxvideo.cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFXVideo -> /home/cloudxblue/.pcsx/plugins/cfgDFXVideo
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFXVideo -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFXVideo
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFCdrom.so -> /home/cloudxblue/.pcsx/plugins/libDFCdrom.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/dfcdrom.cfg -> /home/cloudxblue/.pcsx/plugins/dfcdrom.cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/dfcdrom.cfg -> /home/cloudxblue/.pcsx/plugins/cfg/dfcdrom.cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFIso -> /home/cloudxblue/.pcsx/plugins/cfgDFIso
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFIso -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFIso
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFSound.so -> /home/cloudxblue/.pcsx/plugins/libDFSound.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFIso.so -> /home/cloudxblue/.pcsx/plugins/libDFIso.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/dfiso.cfg -> /home/cloudxblue/.pcsx/plugins/dfiso.cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/dfiso.cfg -> /home/cloudxblue/.pcsx/plugins/cfg/dfiso.cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFXVideo.so -> /home/cloudxblue/.pcsx/plugins/libDFXVideo.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/libDFInput.so -> /home/cloudxblue/.pcsx/plugins/libDFInput.so
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfg -> /home/cloudxblue/.pcsx/plugins/cfg
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfg -> /home/cloudxblue/.pcsx/plugins/cfg/cfg
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFCdrom -> /home/cloudxblue/.pcsx/plugins/cfgDFCdrom
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFCdrom -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFCdrom
    Plugin file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFInput -> /home/cloudxblue/.pcsx/plugins/cfgDFInput
    Config file symlink: /home/cloudxblue/.pcsx/plugins/cfgDFInput -> /home/cloudxblue/.pcsx/plugins/cfg/cfgDFInput
Scanning bios dir /home/cloudxblue/Desktop/.pcsx/bios
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3000.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3000.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/.
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH5000.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH5000.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3002.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Dtlh3002.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH5500.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH5500.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph7000.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph7000.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH1001.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH1001.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH7001.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH7001.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph7003.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph7003.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/Scph5502.bin
    /home/cloudxblue/Desktop/.pcsx/bios/Scph5502.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/SCPH101.BIN
    /home/cloudxblue/Desktop/.pcsx/bios/SCPH101.BIN is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/scph7502.bin
    /home/cloudxblue/Desktop/.pcsx/bios/scph7502.bin is a valid BIOS file
  Checking is_valid_bios_file - /home/cloudxblue/Desktop/.pcsx/bios/..
Finished scanning bios dir /home/cloudxblue/Desktop/.pcsx/bios


________________________________

WHEN I CLICK TO CONFIG XVIDEO DRIVER 1.1.17

Configuring plugin - 2
Configuring plugin /home/cloudxblue/.pcsx/plugins/libDFXVideo.so

(cfgDFXVideo:5286): Gtk-CRITICAL **: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed

(cfgDFXVideo:5286): Gtk-CRITICAL **: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed

(cfgDFXVideo:5286): Gtk-CRITICAL **: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed

(cfgDFXVideo:5286): Gtk-CRITICAL **: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed

(cfgDFXVideo:5286): Gtk-CRITICAL **: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed

(cfgDFXVideo:5286): Gtk-CRITICAL **: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed

________________________


CONFIG ALSA SOUND 1.0.0

Configuring plugin - 4
Configuring plugin /home/cloudxblue/.pcsx/plugins/libDFSound.so
Error - no configuration file

___________________________

GAMEPAD/KEYBOARD INPUT 0.1.0

Configuring plugin - 8
Configuring plugin /home/cloudxblue/.pcsx/plugins/libDFInput.so
DFInput warning: config file not found.

_____________________________________

ISO IMAGE READER 1.1.0 (I CAN ALSO CHOOSE CD-ROM DRIVE READER 1.1.0

Configuring plugin - 1
Configuring plugin /home/cloudxblue/.pcsx/plugins/libDFIso.so

____________________________________

So thats all i get I've been trying this for so long and don't know what else to do hope someone can help me with this information.

---

### Post by Cloud x blue on 2009-04-15
I have a new problem even tho i doubt anyone will help since i  had to do everything on my own so far lol. I now finally get pcsx to come up and I can choose what cd to play, but wen i do for instants my ff7 cd all i get is red blocks with some wired sound. I know it cant be my cd cause i keep good care of my cds no matter how old they are.

---

### Post by smkururu on 2009-05-22
Same problem with me. How do you get pcsx to work? thanks.

---

