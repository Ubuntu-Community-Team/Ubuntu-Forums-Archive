---
title: "another .bat problem."
date: 2008-07-23
forum: Wine
---

### Post by leveliv on 2008-07-23
Alright here's the problem:

I cd to where my .bat is...run wine cmd.exe
it pops up fine blah blah ..I'm already CD'd to where the .bat is so I say 
setup.bat   then I get this:
```
setup.bat


  Make sure u have ~3Gb free space on disk

  Close ALL background programs
  Don't run any programs when setup working. 

  Rebuilding will take a about ~35min or more..

Press Return key to continue: 


               Rebuilding...
  ----------------------------------
  Progress: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 1%
fixme:cmd:WCMD_for /R needs to handle supplied root
Syntax error
Invalid name

Invalid name



               Rebuilding...
  ----------------------------------
  Progress: &#1778;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; 3%

SlavaSoft Optimizing Checksum Utility - fsum 2.52.00337
Implemented using SlavaSoft QuickHash Library <www.slavasoft.com>
Copyright (C) SlavaSoft Inc. 1999-2007. All rights reserved.



            ==SETUP FAILED==

  Setup was interupted by background program
       or insufficient disk space

       (read \#readme#\error.txt)


Press Return key to continue: 

```


So what I would like to know is how can I make this .bat file....into a .sh file for ease to work with it in windows?  (.bat below)

[PHP]@echo off

cls

echo.

echo.

echo   Make sure u have ~3Gb free space on disk

echo.

echo   Close ALL background programs

echo   Don't run any programs when setup working. 

echo.

echo   Rebuilding will take a about ~35min or more..

echo.

pause

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ²²²²²²²²²²²²²²²²²²²² 1%%

ren dec.dll dec.exe >nul

for /R main %%i in (*.ogg) do dec.exe -Q "%%i" >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: Û²²²²²²²²²²²²²²²²²²² 3%%

move precomp.dll precomp.exe >nul

precomp -omain\iw_00.iwd -r main\iw_00.pcf >nul

move precomp.exe precomp.dll >nul

cd main >nul

fsum -c iw_00.sfv >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

cd .. >nul

del /f /q main\iw_00.pcf >nul

del /F /S /Q main\*.ogg >nul

del /F /Q dec.exe >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: Û²²²²²²²²²²²²²²²²²²² 5%%

cd main >nul

cd iw_01

..\zip a -tzip -r iw_01.iwd -mx1 >nul

move iw_01.iwd .. >nul

cd .. >nul

del /f /q /s iw_01\*.* >nul

rd /q /s iw_01 >nul



cd iw_02 >nul

..\zip a -tzip -r iw_02.iwd -mx1 >nul

move iw_02.iwd .. >nul

cd .. >nul

del /f /q /s iw_02\*.* >nul

rd /q /s iw_02 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛ²²²²²²²²²²²²²²²²²² 10%%

cd iw_03 >nul

..\zip a -tzip -r iw_03.iwd -mx1 >nul

move iw_03.iwd .. >nul

cd .. >nul

del /f /q /s iw_03\*.* >nul

rd /q /s iw_03 >nul



cd iw_04 >nul

..\zip a -tzip -r iw_04.iwd -mx1 >nul

move iw_04.iwd .. >nul

cd .. >nul

del /f /q /s iw_04\*.* >nul

rd /q /s iw_04 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛ²²²²²²²²²²²²²²²²² 15%%

cd iw_05 >nul

..\zip a -tzip -r iw_05.iwd -mx1 >nul

move iw_05.iwd .. >nul

cd .. >nul

del /f /q /s iw_05\*.* >nul

rd /q /s iw_05 >nul



cd iw_06 >nul

..\zip a -tzip -r iw_06.iwd -mx1 >nul

move iw_06.iwd .. >nul

cd .. >nul

del /f /q /s iw_06\*.* >nul

rd /q /s iw_06 >nul



cd iw_07 >nul

..\zip a -tzip -r iw_07.iwd -mx1 >nul

move iw_07.iwd .. >nul

cd .. >nul

del /f /q /s iw_07\*.* >nul

rd /q /s iw_07 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛ²²²²²²²²²²²²²²²² 20%%

cd iw_08 >nul

..\zip a -tzip -r iw_08.iwd -mx1 >nul

move iw_08.iwd .. >nul

cd .. >nul

del /f /q /s iw_08\*.* >nul

rd /q /s iw_08 >nul



cd iw_09 >nul

..\zip a -tzip -r iw_09.iwd -mx1 >nul

move iw_09.iwd .. >nul

cd .. >nul

del /f /q /s iw_09\*.* >nul

rd /q /s iw_09 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛ²²²²²²²²²²²²²²² 25%%

cd iw_10 >nul

..\zip a -tzip -r iw_10.iwd -mx1 >nul

move iw_10.iwd .. >nul

cd .. >nul

del /f /q /s iw_10\*.* >nul

rd /q /s iw_10 >nul



cd iw_11 >nul

..\zip a -tzip -r iw_11.iwd -mx1 >nul

move iw_11.iwd .. >nul

cd .. >nul

del /f /q /s iw_11\*.* >nul

rd /q /s iw_11 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛ²²²²²²²²²²²²²² 30%%

cd localized_english_iw00 >nul

..\zip a -tzip -r localized_english_iw00.iwd -mx1 >nul

move localized_english_iw00.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw00\*.* >nul

rd /q /s localized_english_iw00 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛ²²²²²²²²²²²²² 35%%

cd localized_english_iw01 >nul

..\zip a -tzip -r localized_english_iw01.iwd -mx1 >nul

move localized_english_iw01.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw01\*.* >nul

rd /q /s localized_english_iw01 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛ²²²²²²²²²²²² 40%%

cd localized_english_iw02 >nul

..\zip a -tzip -r localized_english_iw02.iwd -mx1 >nul

move localized_english_iw02.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw02\*.* >nul

rd /q /s localized_english_iw02 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛ²²²²²²²²²²² 45%%

cd localized_english_iw03 >nul

..\zip a -tzip -r localized_english_iw03.iwd -mx1 >nul

move localized_english_iw03.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw03\*.* >nul

rd /q /s localized_english_iw03 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛ²²²²²²²²²² 50%%

cd localized_english_iw04 >nul

..\zip a -tzip -r localized_english_iw04.iwd -mx1 >nul

move localized_english_iw04.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw04\*.* >nul

rd /q /s localized_english_iw04 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛ²²²²²²²²² 55%%

cd localized_english_iw05 >nul

..\zip a -tzip -r localized_english_iw05.iwd -mx1 >nul

move localized_english_iw05.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw05\*.* >nul

rd /q /s localized_english_iw05 >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛ²²²²²²²² 60%%

cd localized_english_iw06 >nul

..\zip a -tzip -r localized_english_iw06.iwd -mx1 >nul

move localized_english_iw06.iwd .. >nul

cd .. >nul

del /f /q /s localized_english_iw06\*.* >nul

rd /q /s localized_english_iw06 >nul

del /f /q zip.exe >nul

del /f /q iw_00.sfv >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛ²²²²²²² 65%%

move fsum.exe .. >nul

cd .. >nul

move precomp.dll precomp.exe >nul

precomp -ozone1.exe -r zone1.pcf >nul

move precomp.exe precomp.dll >nul

fsum -c zone1.sfv >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /f /q zone1.pcf >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛÛ²²²²²² 70%%

zone1.exe -y >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /f /q zone1.exe >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛ²²²² 80%%



move precomp.dll precomp.exe >nul

precomp -ozone2.exe -r zone2.pcf >nul

move precomp.exe precomp.dll >nul

fsum -c zone2.sfv >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /f /q zone2.pcf >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------


echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛ²²² 85%%

zone2.exe -y >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /f /q zone2.exe >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛ²² 90%%





move precomp.dll precomp.exe >nul

precomp -ozone3.exe -r zone3.pcf >nul

move precomp.exe precomp.dll >nul

fsum -c zone3.sfv >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /f /q zone3.pcf >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛ² 95%%

zone3.exe -y >nul

IF ERRORLEVEL 3 GOTO THREE

IF ERRORLEVEL 2 GOTO TWO

IF ERRORLEVEL 1 GOTO ONE

del /f /q zone3.exe >nul

cls

echo.

echo.

echo                Rebuilding...

echo   ----------------------------------

echo   Progress: ÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛÛ 100%%

del /f /q msvcr80.dll >nul

del /f /q packJPG.dll >nul

del /f /q precomp.dll >nul

del /f /q zlib1.dll >nul

del /f /q fsum.exe >nul

del /f /q *.sfv >nul

cd #readme# >nul

regedit /s CoD4.reg >nul

"%windir%\regedit.exe" /s CoD4.reg >nul

cd .. >nul

move iwdd.dll iwdd.exe >nul

iwdd.exe >nul

del /f /q iwdd.exe >nul





GOTO END



:THREE

ECHO.

ECHO.

ECHO             ==SETUP FAILED==

ECHO.

ECHO   Setup was interupted by background program

ECHO        or insufficient disk space

ECHO.

ECHO        (read \#readme#\error.txt)

ECHO.

ECHO.

pause

exit



:TWO

ECHO.

ECHO.

ECHO             ==SETUP FAILED==

ECHO.

ECHO   Setup was interupted by background program

ECHO        or insufficient disk space

ECHO.

ECHO        (read \#readme#\error.txt)

ECHO.

ECHO.

pause

exit



:ONE

ECHO.

ECHO.

ECHO             ==SETUP FAILED==

ECHO.

ECHO   Setup was interupted by background program

ECHO        or insufficient disk space

ECHO.

ECHO        (read \#readme#\error.txt)

ECHO.

ECHO.

pause

exit



:END

cls

echo.

echo.

echo   Rebuilding complete!

echo.

echo   Now you can run the game from your Desktop!

echo.

echo.

pause

del setup.bat >nul[/PHP]

---

### Post by Oldsoldier2003 on 2008-07-23
moved to Wine in the hopes of getting a response :)

---

### Post by leveliv on 2008-07-24
oh that would explain why I couldn't find it :D

---

### Post by aliayaz on 2008-09-10
shame on you downloading illegal games :P ((not that i dont do it ;) )) your only chance is extracting it ((rebuilding)) in windows and moving the full game to your Ubuntu computer and run it with COD4.exe :) that's what i did but now im back to windows due to no video card drivers ((new video card))

---

### Post by hikaricore on 2008-09-10
Yea... it's quite obvious what this is.

Thread closed.  I've seen these types of batch files before.
We do NOT support piracy.

If you have any objections to this thread closing please contact me.
I'm leaving it here as a warning to others.

---

