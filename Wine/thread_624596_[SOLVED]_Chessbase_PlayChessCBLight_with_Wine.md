---
title: "[SOLVED] Chessbase PlayChess/CBLight with Wine"
date: 2007-11-27
forum: Wine
---

### Post by Sudheesh on 2007-11-27
I  couldn't make the Chessbase PlayChess working  with wine.  Please let me know if any one had made it working with Wine.

I tried the following options:

1) Downloaded the PlayChess installable exe from Chessbase.  Installed using Wine.  While running got  some dll error related MSVR80.dll.

2)Copied the already installed PlayChess folder ( C:\Program Files\PlayChess ) from my Windows folder ( I had dual boot ).  While executing it with wine got an error saying the gdipls.dll is missing. Copied it again from the Windowd folder.  After that I got some run time error.   

Following thread didn't help me much on this.
[http://ubuntuforums.org/showthread.php?t=31659](http://ubuntuforums.org/showthread.php?t=31659)

If any one was able to make it run using Wine please let me know.  Playchess makes me to boot into windows very often!.

---

### Post by UbuWu on 2007-11-27
You could also try out[ pychess]("http://pychess.googlepages.com/"), which has online playing capabilities in the latest beta versions.

---

### Post by Sudheesh on 2007-11-27
Thanks.  But I need to connect to Chessbase server. I guess only PlaChess can do that.

By the way I am using Ubuntu 7.04 feisty.
Wine version 0.9.33

Please help...

---

### Post by hikaricore on 2007-11-27
Have you by any chance tried updating WINE?..

---

### Post by cogadh on 2007-11-27
The actual error output from the terminal would also be helpful.

---

### Post by Sudheesh on 2007-11-28
> Have you by any chance tried updating WINE?

I installed wine using apt-get install wine  probably a week back.  So I guess this should be the latest version.

> The actual error output from the terminal would also be helpful.

I executed  "wine PlayChess.exe"

Infact for both of the approach that mentioned in the first post I got the same kind of error message.

On the GUI the message is some like this.

RunTime Error!
R6034.
An Application has made an attempt to load the C-RunTime library incorrectly.Please contact xxxx

O the Terminal window I got the following error message.

err:module:LdrInitializeThunk "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\ChessBase_org\\PlayChess\\PlayChess.exe" failed, status c0000142

Can any one help?

---

### Post by hikaricore on 2007-11-28
> **Sudheesh said:**
> I installed wine using apt-get install wine  probably a week back.  So I guess this should be the latest version.

No.  The current version of WINE is 0.9.49 see the top of the WINE forum for info on updating wine.

> **Sudheesh said:**
> 
I executed  "wine PlayChess.exe"

Infact for both of the approach that mentioned in the first post I got the same kind of error message.

On the GUI the message is some like this.

RunTime Error!
R6034.
An Application has made an attempt to load the C-RunTime library incorrectly.Please contact xxxx

O the Terminal window I got the following error message.

err:module:LdrInitializeThunk "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\ChessBase_org\\PlayChess\\PlayChess.exe" failed, status c0000142

Can any one help?

I could be wrong, but you may be needing the MSVCR80.dll file in *~/.wine/drive_c/windows/system32*

---

### Post by Sudheesh on 2007-11-28
> No. The current version of WINE is 0.9.49 see the top of the WINE forum for info on updating wine.

Just got the latest version of wine 0.9.49.  Looks like PlayChess is working now. Atleast the GUI is coming up now.   Yet to do a detailed test.

Thanks hikaricore!

By the way MSVCR80.dll file was already present in ~/.wine/drive_c/windows/system32.

Will post the results of a detailed test later..

---

### Post by Sudheesh on 2007-11-28
I have done some more testing. I could connect to the PlayChess server and play some games!.   Though I have n't tested all the features my requirements have been met.

But observed that for some of the windows the borders are missing. As a result I cannot move those windows.

The GUI looks almost  similar to that in Windows.  I didn't know the Linux can have GUI equally or better than in Windows!. Personally I dot like most of the native  Linux applications  GUI and the GUI created wine looks  better than native Linux applications GUI...

If it is possible I am just wondering why people are not writing better GUI's in Linux.

---

### Post by hikaricore on 2007-11-29
Your personal opinions adise, there are several dozen variations of different widget/window designs availible under Linux depending on your window manager and configuration.  So you can't just say that Linux's GUI is crappy, because you're only using Gnome and have never tried another WM that may do a better job or better fit your needs.

I suggest you start a new topic elsewhere if you really want to persue this any further.

---

