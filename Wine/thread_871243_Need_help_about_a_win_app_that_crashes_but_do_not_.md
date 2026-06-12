---
title: "Need help about a win app that crashes but do not output anything in the terminal"
date: 2008-07-26
forum: Wine
---

### Post by graben3 on 2008-07-26
Hello,

I have installed many Windows app in Wine with sometimes difficulties but I managed to make them work using the terminal output from wine and got excellent results...

However the app im trying to install do not output anything in the terminal and wont start after the splash screen. It produces an error.log file and this screnshot I attach here.

This app is special since it does not need any registry key and can be copied to any other windows machine without installation.

My question : 

Is there a way of telling in what language an app was programmed perhaps by looking at the binary code of the main executable of the app ? Is there anything I can do besides wine tricks which did not affect anything (I installed like 80% of wine tricks available to see if it got better....each time I installed a new winetrick I retry running my app...nothing seemed to change)

Im kind of hopeless now... all my debugging tricks (using the terminal and checking in wine source code) were only good if the program outputs something in the terminal of course. Im looking for a better way to understand what is wrong with this app...perhaps somebody knows a better way to debug wine than I do !

Here is the content of the error.log file the program produces on crashing :
Application

===========

   Program: Int&#130;gration 12.0 LAN

   N/S:  /  ()

   Path and name: C:\Program Files\Avantage\MAINMENU.EXE

   Size: 7,771,648 bytes

   Date: 2008/07/26

   Command line: "C:/Program Files/Avantage/MAINMENU.EXE"

   Error ocurred at: 2008/07/26, 17:53:38

   Utilisateur: TL

   Langue: Fran&#135;ais



Error description: Error BASE/1004  Class: 'NIL' has no exported method: HWND

   Args:



Dll's

===========

   C:\Program Files\Avantage\AVANTAGE.DLL  (2008/07/26  01:13:16)

   C:\Program Files\Avantage\AVASTR01.DLL  (2008/07/26  01:13:24)

   C:\Program Files\Avantage\AVASTR02.DLL  (2008/07/26  01:13:33)

   C:\Program Files\Avantage\AVADLG01.DLL  (2008/07/26  01:13:24)

   C:\Program Files\Avantage\AVADLG02.DLL  (2008/07/26  01:13:30)



Stack Calls

===========

   Called from HWND(0)

   Called from TMDIFRAME:RESIZE(222)

   Called from TMDIFRAME:HANDLE2(0)

   Called from TMDIFRAME:HANDLEEVENT(4295)

   Called from _FWH(3808)

   Called from MOVEWINDOW(0)

   Called from TMDIFRAME:MOVE(2758)

   Called from TMDIFRAME:CREATE(854)

   Called from TMDIFRAME:NEW(161)

   Called from MAIN(62)



System

======

   Windows version: Windows 2000 Professional 5.00.2195 Service Pack 4

   XHB version    : xHarbour build 0.99.3 Intl. (SimpLex)



   Windows total applications running: 2

      1 MDI Frame

      2 Wine System Tray



Variables in use

================

   Procedure     Type   Value

   ==========================

   HWND

   TMDIFRAME:RESIZE

     Param   1:    N    0

     Param   2:    N    104

     Param   3:    N    0

     Local   1:    O    Class: TMDIFRAME

     Local   2:    U    

     Local   3:    U    

     Local   4:    U    

     Local   5:    U    

     Local   6:    U    

     Local   7:    U    

   TMDIFRAME:HANDLE2

     Param   1:    N    5

     Param   2:    N    0

     Param   3:    N    104

   TMDIFRAME:HANDLEEVENT

     Param   1:    N    5

     Param   2:    N    0

     Param   3:    N    104

     Local   1:    O    Class: TMDIFRAME

     Local   2:    U    

     Local   3:    U    

     Local   4:    N    0

   _FWH

     Param   1:    N    104

     Param   2:    N    5

     Param   3:    N    0

     Param   4:    N    104

     Param   5:    N    4

     Local   1:    O    Class: TMDIFRAME

   MOVEWINDOW

     Param   1:    N    65580

     Param   2:    N    0

     Param   3:    N    0

     Param   4:    N    1

     Param   5:    N    1

     Param   6:    L    .T.

   TMDIFRAME:MOVE

     Param   1:    N    0

     Param   2:    N    0

     Param   3:    N    1

     Param   4:    N    1

     Local   1:    L    .T.

     Local   2:    L    .T.

     Local   3:    L    .F.

     Local   4:    O    Class: TMDIFRAME

     Local   5:    L    .F.

     Local   6:    L    .F.

     Local   7:    L    .F.

   TMDIFRAME:CREATE

     Local   1:    C    "TMDIFRAME"

     Local   2:    O    Class: TMDIFRAME

     Local   3:    A    Len:    4

     Local   4:    L    .T.

   TMDIFRAME:NEW

     Param   1:    U    

     Param   2:    U    

     Param   3:    U    

     Param   4:    U    

     Param   5:    C    "MDI Frame"

     Param   6:    N    47120384

     Param   7:    O    Class: TMENU

     Param   8:    U    

     Param   9:    U    

     Param  10:    N    0

     Param  11:    N    16777215

     Param  12:    L    .F.

     Param  13:    L    .F.

     Param  14:    N    9

     Param  15:    U    

     Param  16:    U    

     Param  17:    L    .F.

     Local   1:    O    Class: TMDIFRAME

   MAIN

     Local   1:    U    

     Local   2:    U    

     Local   3:    U    

     Local   4:    U    

     Local   5:    U    

     Local   6:    U    

     Local   7:    U    

     Local   8:    U    

     Local   9:    N    5

     Local  10:    U    

     Local  11:    C    ""

     Local  12:    N    1680

     Local  13:    L    .T.

     Local  14:    U    

     Local  15:    U    

     Local  16:    U    

     Local  17:    U    

     Local  18:    L    .T.

     Local  19:    L    .F.

     Local  20:    L    .F.

     Local  21:    O    Class: TDIALOG

     Local  22:    O    Class: TICON

     Local  23:    U    

     Local  24:    U    

     Local  25:    O    Class: APP



Linked RDDs

===========

   DBF

   DBFFPT

   DBFCDX



Path   : Z:\home\graben\

Default: 

CurDir : home\graben



DataBases in use

================



Classes in use:

===============

     1 C Structure C Array of [2] CType: -4

     2 C Structure ULONGLONG

     3 C Structure C Array of [2] CType: 4

     4 C Structure LONGLONG

     5 C Structure RECT

     6 C Structure POINT

     7 C Structure HH_POPUP

     8 HBCLASS

     9 HBOBJECT

    10 APP

    11 S_INTRO

    12 TFONT

    13 TCURSOR

    14 TINI

    15 TWINDOW

    16 TDIALOG

    17 TBRUSH

    18 TCONTROL

    19 TBITMAP

    20 TIMAGE

    21 GET

    22 TGET

    23 TTIMER

    24 TICON

    25 TMDIFRAME

    26 TMENU

    27 TMENUITEM

    28 ERROR

    29 S_LICENCE



Memory Analysis

===============

   Dynamic memory consume:

      Actual  Value:          0 bytes

      Highest Value:          0 bytes



---

### Post by LinuxRocks713 on 2008-07-28
> **graben3 said:**
> Hello,

I have installed many Windows app in Wine with sometimes difficulties but I managed to make them work using the terminal output from wine and got excellent results...

However the app im trying to install do not output anything in the terminal and wont start after the splash screen. It produces an error.log file and this screnshot I attach here.

This app is special since it does not need any registry key and can be copied to any other windows machine without installation.

My question : 

Is there a way of telling in what language an app was programmed perhaps by looking at the binary code of the main executable of the app ? Is there anything I can do besides wine tricks which did not affect anything (I installed like 80% of wine tricks available to see if it got better....each time I installed a new winetrick I retry running my app...nothing seemed to change)

Im kind of hopeless now... all my debugging tricks (using the terminal and checking in wine source code) were only good if the program outputs something in the terminal of course. Im looking for a better way to understand what is wrong with this app...perhaps somebody knows a better way to debug wine than I do !

Here is the content of the error.log file the program produces on crashing :
<huge snip>


What do you mean by "with terminal output"? If the app runs without output, it means that it's perfect. So somethings wrong with the program itself.

---

### Post by graben3 on 2008-07-28
> **LinuxRocks713 said:**
> What do you mean by "with terminal output"? If the app runs without output, it means that it's perfect. So somethings wrong with the program itself.

The app runs without that error in windows XP. Its not perfect, it displays an error dialog box...but do not display any output to the terminal window. Seems to me like this app has a way too much perfect error handling mechanism so no errors shows in Wine and the errors the app shows in the error dialog are of no use to me.

My question is : 

Can someone suggest me a way to debug the problem so I can make it run... im searching for new tools to make this app work since my usual procedure to make wine app work are no longer usable

---

