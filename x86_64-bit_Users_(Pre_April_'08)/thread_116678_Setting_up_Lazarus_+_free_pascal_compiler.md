---
title: "Setting up Lazarus + free pascal compiler"
date: 2006-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruudiculus on 2006-01-13
I wondered if someone had already managed to get Lazarus running under amd64. (The lazarus website doesn't provide much help for amd64 users - they also don't say that it CAN be used on amd64 machines anyway: so maybe I should give up now anyway because the compiler is only a 32 bit version?)

I've tried to build from source and to turn rpm packges to deb packages and instal them, but all this results in error messages.

The Free Pascal Compiler installed successfully.

Have you got any idea?

---

### Post by Lambert on 2006-01-13
Can't help you directly but saw this recently. Hope it helps.

[http://www.howtoforge.com/lazarus_ubuntu]("http://www.howtoforge.com/lazarus_ubuntu")

---

### Post by ruudiculus on 2006-01-14
Thanks a lot! I'll give it a try tomorrow and get back with the results!

---

### Post by ruudiculus on 2006-01-20
I promised to get back with the results.

Lazarus doesn't work yet. The make command got some errors as you can see:

```
ruud@HP:~/programs/lazarus$ make
make: -iVSPTPSOTO: Command not found
make: -iSP: Command not found
make: -iTP: Command not found
make: -iSO: Command not found
make: -iTO: Command not found
make -C ide ide
make[1]: -iSP: Command not found
make[1]: Entering directory `/home/ruud/programs/lazarus/ide'
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
/bin/mkdir -p units/-
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make --assume-new=../lazarus.exe lazarus.exe
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: Entering directory `/home/ruud/programs/lazarus/ide'
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
FE. -FUunits/-  lazarus.pp
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: FE.: Command not found
make[2]: [lazarus.exe] Error 127 (ignored)
make[2]: Leaving directory `/home/ruud/programs/lazarus/ide'
make[1]: Leaving directory `/home/ruud/programs/lazarus/ide'
make -C ide starter
make[1]: -iSP: Command not found
make[1]: Entering directory `/home/ruud/programs/lazarus/ide'
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make --assume-new=../startlazarus.exe startlazarus.exe
make[1]: -iSP: Command not found
make[1]: -iTP: Command not found
make[1]: -iSO: Command not found
make[1]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: Entering directory `/home/ruud/programs/lazarus/ide'
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
FE. -FUunits/-  startlazarus.lpr
make[2]: -iSP: Command not found
make[2]: -iTP: Command not found
make[2]: -iSO: Command not found
make[2]: -iTO: Command not found
make[2]: FE.: Command not found
make[2]: [startlazarus.exe] Error 127 (ignored)
make[2]: Leaving directory `/home/ruud/programs/lazarus/ide'
make[1]: Leaving directory `/home/ruud/programs/lazarus/ide'

```

Are these things in bold compiler arguments?:
```
make: -iVSPTPSOTO: Command not found
make: **-iSP**: Command not found
make: **-iTP**: Command not found
make:** -iSO**: Command not found
make: **-iTO**: Command not found
```

Does lazarus need the Pascal compiler or the FPC compiler for the *make* command? My guess would be the FPC since all I can see in the lazarus subdirs are **.pas* files and since I have added the FPC path to my *.bash_profile* file.

Well if anyone has an idea to get Lazarus running on an amd64 machine, all are welcome! Meanwhile I'll try to figure it out too. By the way I've got the Free Pascal Compiler version 2.0.2 from the original FPC website.

---

### Post by FPK on 2006-01-25
You need a working fpc, at least
which fpc
which ppcx64
should display executables, so I guess something is wrong with your fpc installation.

---

### Post by ruudiculus on 2006-01-25
> Does lazarus need the Pascal compiler or the FPC compiler for the *make* command? My guess would be the FPC since all I can see in the lazarus subdirs are **.pas* files and since I have added the FPC path to my *.bash_profile* file.

I meant *C compiler* instead of *Pascal compiler* here...sorry for my own confusion.

Which fpc returns nothing, yet so I've put the fpc path into the /etc/bash.bashrc file instead of my user .bash_profile file. Let's reboot!

---

### Post by ruudiculus on 2006-01-25
This helps, but still compiling lazarus with the *make clean all* command still gives errors. Using a normal *make* works! So I finally got Lazarus running!

Yeah! Thanks all!

---

### Post by tasca on 2006-01-25
I had error the same that ruudiculus

 I remade the process leaving the folder /usr/local, lazarus ok.

 executing  make build on fpc, see:

make[4]: Saindo do diretório `/home/tasca/fpc/ide'
make fpc_all
make[4]: Entrando no diretório `/home/tasca/fpc/ide'
/home/tasca/fpc/compiler/ppcx64 -Ur -Xs  -n -Sg -Fu/home/tasca/fpc/rtl/units/x86_64-linux -Fu/home/tasca/fpc/fv/units/x86_64-linux -Fu/home/tasca/fpc/packages/base/gdbint/units/x86_64-linux -Fu/home/tasca/fpc/packages/base/regexpr/units/x86_64-linux -FE. -FUunits/x86_64-linux -Fl/usr/lib/gcc/x86_64-linux-gnu/4.0.3 -Fl/lib32 -Fl/usr/lib32 -Fl/usr/X11R6/lib32 -dx86_64 -dRELEASE -dNODEBUG fp.pas
/usr/bin/ld: cannot find -lncurses
fp.pas(263,5) Error: Error while linking
make[4]: ** [fp] Erro 1
make[4]: Saindo do diretório `/home/tasca/fpc/ide'
make[3]: ** [buildfp] Erro 2
make[3]: Saindo do diretório `/home/tasca/fpc/ide'
make[2]: ** [gdb] Erro 2
make[2]: Saindo do diretório `/home/tasca/fpc/ide'
make[1]: ** [ide_all] Erro 2
make[1]: Saindo do diretório `/home/tasca/fpc'
make: ** [build-stamp.x86_64-linux] Erro 2

somebody has idea?

---

### Post by FPK on 2006-01-25
No, it doesn't need a C compiler.

Usually you should get a soft link in /usr/local/bin/ to ppcx64 which is located in /usr/local/lib/fpc/2.0.2

If this doesn't work for unknown reason, pass the location of the ppcx64 to make by
make FPC=/path/to/ppcx64

---

### Post by FPK on 2006-01-25
[QUOTE=tasca]
-FUunits/x86_64-linux -Fl/usr/lib/gcc/x86_64-linux-gnu/4.0.3 -Fl/lib32 -Fl/usr/lib32 -Fl/usr/X11R6/lib32 -dx86_64 -dRELEASE -dNODEBUG fp.pas
/usr/bin/ld: cannot find -lncurses
fp.pas(263,5) Error: Error while linking
make[4]: ** [fp] Erro 1
make[4]: Saindo do diretório `/home/tasca/fpc/ide'
make[3]: ** [buildfp] Erro 2
make[3]: Saindo do diretório `/home/tasca/fpc/ide'
make[2]: ** [gdb] Erro 2
make[2]: Saindo do diretório `/home/tasca/fpc/ide'
make[1]: ** [ide_all] Erro 2
make[1]: Saindo do diretório `/home/tasca/fpc'
make: ** [build-stamp.x86_64-linux] Erro 2

somebody has idea?[/QUOTE]

Install the libncurses development package, I think it's called something like libncurses5-dev

However, to use lazarus, you don't need to recompile FPC, FPC 2.0.2 should be enough.

---

### Post by ruudiculus on 2006-01-25
Strange thing: I managed to get it working using [this]("http://www.howtoforge.com/lazarus_ubuntu") howto. I had some errors in the final step of replacing the version 2.0.0 fpc with the newer 2.0.2 (from source) so I wanted to try to use the 2.0.2 tar right away (just as the howto described it with the 2.0.0 version). Doing the procedure all over again but this time with fpc version 2.0.2 (which installed fine) resulted in the error messages below when doing *make*

```
ruud@HP:~/programs/lazarus$ make
Makefile:3425: warning: overriding commands for target `examples'
Makefile:3392: warning: ignoring old commands for target `examples'
make -C lcl all
make[1]: Entering directory `/home/ruud/programs/lazarus/lcl'
/bin/rm -f units/x86_64-linux/alllclunits.ppu
/bin/mkdir -p units/x86_64-linux
/home/ruud/programs/fpc/bin/ppcx64 -gl -Fu. -Funonwin32 -Fuwidgetset -Fiinclude -FE. -FUunits/x86_64-linux -Fl/usr/lib/gcc/x86_64-linux-gnu/4.0.2 -Fl/lib32 -Fl/usr/lib32 -Fl/usr/X11R6/lib32 -dx86_64 alllclunits.pp
Free Pascal Compiler version 2.0.0 [2005/05/15] for x86_64
Copyright (c) 1993-2005 by Florian Klaempfl
Target OS: Linux for x86-64
Compiling alllclunits.pp
Fatal: Can't find unit System
Error: Compilation aborted
make[1]: *** [alllclunits.ppu] Error 1
make[1]: Leaving directory `/home/ruud/programs/lazarus/lcl'
make: *** [lcl] Error 2

```

The howto prescribes adding some lines to the user's **.bash_profiles** file in  order to use the fpc from command line. This didn't work for me so I put the lines in the **/etc/bash.bashrc** file. As you can see above, the *make* command finds the fpc, knows for which platform to make and then it says it can't find the unit System. This probably some Pascal unit it needs to compile, but I've used the same lazarus tarball during the previous (successful) make...

Have I overlooked something? Probably...

(Starting all over again with the 2.0.0 version fpc resulted in the same error code. Same with the *make clean all* command from the lazarus README file)

---

### Post by tasca on 2006-01-26
exactly error here.
with fpc 2.0.0, lazarus shows this on console:

tasca@softsul:~/lazarus$ ./lazarus
[WARNING] *******************************************************
[WARNING] **                                                   **
[WARNING] ** Multibyte character encodings (like UTF8) are not **
[WARNING] ** supported at the moment.                          **
[WARNING] ** For full keyboard event support, make sure that   **
[WARNING] ** the LANG environment var has no UTF8              **
[WARNING] **                                                   **
[WARNING] *******************************************************
TApplication.IconChanged - TODO: convert this message...no implementation in gtk  or win32
NOTE: editor options config file not found - using defaults
NOTE: codetools config file not found - using defaults

NOTE: FPC Source Directory not set! (see Environment Options)

NOTE: Could not create Define Template for Free Pascal Sources
NOTE: help options config file not found - using defaults
TMainIDE.DoNewProject A
TMainIDE.DoNewEditorFile A NewFilename=
TPascalParserTool.BuildTree B OnlyIntf=False  project1.lpr
[TCustomFormEditor.CreateComponent] Class='TForm'
TPascalParserTool.BuildTree B OnlyIntf=False  project1.lpr
TMainIDE.DoNewEditorFile end unit1.pas
TMainIDE.DoNewProject end
TApplication.HandleException Error reading EnvironmentOptionsDialog.HorzScrollBar.Page: Access violation
  Stack trace:
  $00000000004A2502
  $00000000004A18AD
  $00000000004965F5
  $00000000004A3362
  $000000000055540A  INITCOMPONENT,  line 2001 of lresources.pp
  $0000000000555207  INITLAZRESOURCECOMPONENT,  line 2020 of lresources.pp
  $0000000000429B5D  INITRESOURCECOMPONENT,  line 1374 of forms.pp
  $000000000042FBCF  TCUSTOMFORM__CREATE,  line 1254 of ./include/customform.inc
  $0000000000731413  TENVIRONMENTOPTIONSDIALOG__CREATE,  line 1555 of environmentopts.pp
  $000000000044F792  TMAINIDE__DOSHOWENVGENERALOPTIONS,  line 3256 of main.pp
  $000000000044F36E  TMAINIDE__MNUENVGENERALOPTIONSCLICKED,  line 3149 of main.pp
  $0000000000658DD3  TIDEMENUITEM__MENUITEMCLICK,  line 490 of menuintf.pas
  $0000000000545713  TMENUITEM__CLICK,  line 74 of ./include/menuitem.inc
  $0000000000545F33  TMENUITEM__DOCLICKED,  line 248 of ./include/menuitem.inc
  $000000000041A3A3
  $00000000005BEFA2  DELIVERMESSAGE,  line 3397 of gtkproc.inc
  $00000000005C8212  GTKACTIVATECB,  line 298 of gtkcallback.inc
TMainIDE.DoCloseEditorFile A PageIndex=0
TCustomFormEditor.DeleteControl TForm1 TRUE
TPascalParserTool.BuildTree B OnlyIntf=False  project1.lpr
TPascalParserTool.BuildTree B OnlyIntf=False  project1.lpr
TMainIDE.DoCloseEditorFile end
LAZARUS END - cleaning up ...
[TMainIDE.Destroy] A
[TMainIDE.Destroy] B  -> inherited Destroy... TMainIDE
[TMainIDE.Destroy] END
tasca@softsul:~/lazarus$

ubuntu64 dapper drake fligth3 with dist-upgrade

---

### Post by ruudiculus on 2006-01-26
Have you also tried the manual above?

It worked for me, finally. At first I had these strange error messages, but then I did:
1. remove fpc 2.0.0 and 2.0.2
2. remove lazarus
3. then reboot
4. install fpc 2.0.0 again
5. adding three lines to /etc/bash.bashrc file (not to **/home/user/.bash_profile** this didn't work!!)
6. rebooting again (this looks like windows :rolleyes: but I don't really know if it matters to do this, but I turned off my computer yesterday after installing FPC and continued today: that's why)
7. make lazarus
8. run ./lazarus

Good luck!

P.S.
I've already made my own manual for Lazarus, which is available following the *howto's* link below.

---

### Post by FPK on 2006-01-26
[QUOTE=ruudiculus]Strange thing: I managed to get it working using [this]("http://www.howtoforge.com/lazarus_ubuntu") howto. I had some errors in the final step of replacing the version 2.0.0 fpc with the newer 2.0.2 (from source) so I wanted to try to use the 2.0.2 tar right away (just as the howto described it with the 2.0.0 version). Doing the procedure all over again but this time with fpc version 2.0.2 (which installed fine) resulted in the error messages below when doing *make*

```
ruud@HP:~/programs/lazarus$ make
Makefile:3425: warning: overriding commands for target `examples'
Makefile:3392: warning: ignoring old commands for target `examples'
make -C lcl all
make[1]: Entering directory `/home/ruud/programs/lazarus/lcl'
/bin/rm -f units/x86_64-linux/alllclunits.ppu
/bin/mkdir -p units/x86_64-linux
/home/ruud/programs/fpc/bin/ppcx64 -gl -Fu. -Funonwin32 -Fuwidgetset -Fiinclude -FE. -FUunits/x86_64-linux -Fl/usr/lib/gcc/x86_64-linux-gnu/4.0.2 -Fl/lib32 -Fl/usr/lib32 -Fl/usr/X11R6/lib32 -dx86_64 alllclunits.pp
Free Pascal Compiler version 2.0.0 [2005/05/15] for x86_64
Copyright (c) 1993-2005 by Florian Klaempfl
Target OS: Linux for x86-64
Compiling alllclunits.pp
Fatal: Can't find unit System
Error: Compilation aborted
make[1]: *** [alllclunits.ppu] Error 1
make[1]: Leaving directory `/home/ruud/programs/lazarus/lcl'
make: *** [lcl] Error 2

```

The howto prescribes adding some lines to the user's **.bash_profiles** file in  order to use the fpc from command line. This didn't work for me so I put the lines in the **/etc/bash.bashrc** file. As you can see above, the *make* command finds the fpc, knows for which platform to make and then it says it can't find the unit System. This probably some Pascal unit it needs to compile, but I've used the same lazarus tarball during the previous (successful) make...

Have I overlooked something? Probably...

(Starting all over again with the 2.0.0 version fpc resulted in the same error code. Same with the *make clean all* command from the lazarus README file)[/QUOTE]

Check if you've an /etc/fpc.cfg and if the -Fu entries point to the correct location. Further, I strongly recommend fpc 2.0.2 for lazarus on x86-64.

About the sources location remark: simply enter the path to the fpc sources in the mentioned dialog. To get the full RAD functionality, all sources are necessary.

---

### Post by tasca on 2006-01-27
Hi

remove lazarus and fpc
reboot
install fpc 2.0.2 (not found pakage 2.11, I found fpc.zip but I not know install), 
reboot
install lazarus 0.9.11 (see some warnings)
install sources fpc 2.11 
startlazarus ok, path to source fpc ok, but environment-editor option:
error float point, out of console:

tasca@softsul:~/lazarus$ ./startlazarus
[WARNING] *******************************************************
[WARNING] **                                                   **
[WARNING] ** Multibyte character encodings (like UTF8) are not **
[WARNING] ** supported at the moment.                          **
[WARNING] ** For full keyboard event support, make sure that   **
[WARNING] ** the LANG environment var has no UTF8              **
[WARNING] **                                                   **
[WARNING] *******************************************************
[WARNING] *******************************************************
[WARNING] **                                                   **
[WARNING] ** Multibyte character encodings (like UTF8) are not **
[WARNING] ** supported at the moment.                          **
[WARNING] ** For full keyboard event support, make sure that   **
[WARNING] ** the LANG environment var has no UTF8              **
[WARNING] **                                                   **
[WARNING] *******************************************************
TApplication.IconChanged - TODO: convert this message...no implementation in gtk  or win32
NOTE: editor options config file not found - using defaults
NOTE: codetools config file not found - using defaults
NOTE: help options config file not found - using defaults
TPascalParserTool.BuildTree B OnlyIntf=True  /home/tasca/unit1.pas
TMainIDE.DoLoadLFM A /home/tasca/unit1.pas IsPartOfProject=True
SUCCESS: streaming lfm="/home/tasca/unit1.lfm"
TApplication.HandleException Invalid floating point operation
  Stack trace:
  $000000000052D743  GETCHILDMINRESIZE,  line 610 of ./include/wincontrol.inc
  $000000000052D0C4  TAUTOSIZEBOX__RESIZECHILDS,  line 774 of ./include/wincontr ol.inc
  $000000000052E1BB  TAUTOSIZEBOX__RESIZETABLE,  line 800 of ./include/wincontro l.inc
  $000000000052E4C0  TAUTOSIZEBOX__ALIGNCONTROLSINTABLE,  line 884 of ./include/ wincontrol.inc
  $0000000000535CAB  TWINCONTROL__ALIGNNONALIGNEDCONTROLS,  line 4120 of ./inclu de/wincontrol.inc
  $000000000052F51E  DOALIGNNOTALIGNED,  line 1574 of ./include/wincontrol.inc
  $000000000052F32C  TWINCONTROL__ALIGNCONTROLS,  line 1627 of ./include/wincont rol.inc
  $0000000000536178  TWINCONTROL__ALIGNCONTROL,  line 4242 of ./include/wincontr ol.inc
  $0000000000535B60  TWINCONTROL__REALIGN,  line 4065 of ./include/wincontrol.in c
  $00000000005315BC  TWINCONTROL__ENABLEALIGN,  line 2080 of ./include/wincontro l.inc
  $0000000000537B65  TWINCONTROL__CREATEWND,  line 5089 of ./include/wincontrol. inc
  $000000000053743F  TWINCONTROL__CREATEHANDLE,  line 4980 of ./include/wincontr ol.inc
  $00000000005383B5  TWINCONTROL__HANDLENEEDED,  line 5289 of ./include/wincontr ol.inc
  $0000000000537A0E  TWINCONTROL__CREATEWND,  line 5070 of ./include/wincontrol. inc
  $000000000053743F  TWINCONTROL__CREATEHANDLE,  line 4980 of ./include/wincontr ol.inc
  $00000000005383B5  TWINCONTROL__HANDLENEEDED,  line 5289 of ./include/wincontr ol.inc
  $0000000000537A0E  TWINCONTROL__CREATEWND,  line 5070 of ./include/wincontrol. inc
TMainIDE.DoCloseEditorFile A PageIndex=0
TCustomFormEditor.DeleteControl TForm1 TRUE
TCustomFormEditor.DeleteControl TButton FALSE
TMainIDE.DoCloseEditorFile end
LAZARUS END - cleaning up ...
[TMainIDE.Destroy] A
[TMainIDE.Destroy] B  -> inherited Destroy... TMainIDE
[TMainIDE.Destroy] END
tasca@softsul:~/lazarus$ ./startlazarus
[WARNING] *******************************************************
[WARNING] **                                                   **
[WARNING] ** Multibyte character encodings (like UTF8) are not **
[WARNING] ** supported at the moment.                          **
[WARNING] ** For full keyboard event support, make sure that   **
[WARNING] ** the LANG environment var has no UTF8              **
[WARNING] **                                                   **
[WARNING] *******************************************************
[WARNING] *******************************************************
[WARNING] **                                                   **
[WARNING] ** Multibyte character encodings (like UTF8) are not **
[WARNING] ** supported at the moment.                          **
[WARNING] ** For full keyboard event support, make sure that   **
[WARNING] ** the LANG environment var has no UTF8              **
[WARNING] **                                                   **
[WARNING] *******************************************************
TApplication.IconChanged - TODO: convert this message...no implementation in gtk or win32
NOTE: editor options config file not found - using defaults
NOTE: codetools config file not found - using defaults
NOTE: help options config file not found - using defaults
TPascalParserTool.BuildTree B OnlyIntf=True  /home/tasca/unit1.pas
TMainIDE.DoLoadLFM A /home/tasca/unit1.pas IsPartOfProject=True
SUCCESS: streaming lfm="/home/tasca/unit1.lfm"
TMainIDE.DoCloseEditorFile A PageIndex=0
TCustomFormEditor.DeleteControl TForm1 TRUE
TCustomFormEditor.DeleteControl TButton FALSE
TMainIDE.DoCloseEditorFile end
LAZARUS END - cleaning up ...
[TMainIDE.Destroy] A
[TMainIDE.Destroy] B  -> inherited Destroy... TMainIDE
[TMainIDE.Destroy] END

I need config editor, because the font size is small.

thanks for help and any sugestions?

---

