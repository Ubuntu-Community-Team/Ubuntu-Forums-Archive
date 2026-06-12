---
title: "[SOLVED] Help On Conquer Online 2.0!"
date: 2008-05-05
forum: Wine
---

### Post by pogztimz on 2008-05-05
i have recently installed Ubuntu 8.04 on my computer and i have a problem playing Conquer Online 2.0 on it. i have already tried the instructions indicated at [http://ubuntuforums.org/showthread.php?t=731293&highlight=Conquer+Online](http://ubuntuforums.org/showthread.php?t=731293&highlight=Conquer+Online) but to no avail.. pls help me on this ty..

---

### Post by pogztimz on 2008-06-10
:popcorn: hahaha! i am so happy finally i can play Conquer Online on Ubuntu!

I found solution on this site.. [http://www.playonlinux.com/en/topic-1552-Conquer_Online_20.html](http://www.playonlinux.com/en/topic-1552-Conquer_Online_20.html)
Tnx to Chain2k <<< PRO


*REQUIREMENTS*

1. Conquer_v5022_10.exe from [http://co.91.com](http://co.91.com)

2. Install Play On Linux (POL).
For Hardy Repository. Copy and Paste this at the Terminal
> sudo wget [http://playonlinux.botux.net/playonlinux_hardy.list](http://playonlinux.botux.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux
 

   For Gutsy Repository. Copy and Paste this at the Terminal
> sudo wget [http://playonlinux.botux.net/playonlinux_gutsy.list](http://playonlinux.botux.net/playonlinux_gutsy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux

3.Copy the script below and save it on your Documents Folder.

> #!/bin/bash
if [ "$PLAYONLINUX" = "" ]
then
exit 0
fi
source "$PLAYONLINUX/lib/sources"

cfg_check

#Game and script presentation
presentation "Conquer Online" "TQ Digital" "http://co.91.com" "chain" "ConquerOnline"

# Preparing translations
en_co()
{
LNG_CO_PRES="Conquer Online is a Massive Multiplayer Online Role Playing Game (MMORPG). In Conquer, thousands of online players adventure together in an enormous, persistent game world, forming friendships, slaying monsters, engaging in quests, and role-playing their characters in the game world."
LNG_CO_PRES_TITLE="Game Announce"
LNG_CO_DOWNED="Choose already downloaded .exe or .zip installer"
LNG_CO_URL="Open link in default browser to download installer manually"
LNG_CO_HOWTO="Please, choose preferable mirror on the page that will be displayed and download the client.
Make sure its VERSION is NOT LOWER than v5022 or installation can FAIL"
LNG_CO_WAIT_END="Click on "Next" after downloading and then indicate where the installer has been stored"
LNG_CO_INSTALLER_QUESTION="Where is the installer?"
LNG_CO_INSTALLER_ERROR="You have to choose the proper file"
LNG_CO_DEFAULT="Please, use default directory 'C:\Program Files\Conquer 2.0' in windows installation dialog."
LNG_CO_WINE_DOWNLOAD="We have to download and prepare wine version 1.0~rc2
with the patch for animated cursor.
Thanx to H.Verbeet for patch"
LNG_WA_EXTRACT_WAIT="Please, wait for preparing wine installation"
LNG_CO_FONT_DOWNLOAD="We have to download Sim Sun font"
LNG_CO_WINE_EXISTS="Patched wine version installed successfully or already present"
LANG_CO_WINEFAILED="Sorry, patched wine installation not found or failed, you need to redownload wine package"
LANG_CO_LAST="Installation finished. Don't forget to register an account on site for playing.
ATTENTION:
You MUST hold ALT button during LOGIN and PASSWORD input or you'll be unable to connect.
To make your life easy you can check 'Remember' on logon screen"
LANG_CO_CANCEL="Script canceled"
LANG_CO_FIN="Finish"
}
fr_co()
{
LNG_CO_PRES="FRENCH! Conquer Online is a Massive Multiplayer Online Role Playing Game (MMORPG). In Conquer, thousands of online players adventure together in an enormous, persistent game world, forming friendships, slaying monsters, engaging in quests, and role-playing their characters in the game world."
LNG_CO_PRES_TITLE="Game Announce"
LNG_CO_DOWNED="Choose already downloaded .exe or .zip installer"
LNG_CO_URL="Open link in default browser to download installer manually"
LNG_CO_HOWTO="Please, choose preferable mirror on the page that will be displayed and download the client.
Make sure its VERSION is NOT LOWER than v5022 or installation can FAIL"
LNG_CO_WAIT_END="Click on "Next" after downloading and then indicate where the installer has been stored"
LNG_CO_INSTALLER_QUESTION="Where is the installer?"
LNG_CO_INSTALLER_ERROR="You have to choose the proper file"
LNG_CO_DEFAULT="Please, use default directory 'C:\Program Files\Conquer 2.0' in windows installation dialog."
LNG_CO_WINE_DOWNLOAD="We have to download and prepare wine version 1.0~rc2
with the patch for animated cursor.
Thanx to H.Verbeet for patch"
LNG_WA_EXTRACT_WAIT="Please, wait for preparing wine installation"
LNG_CO_FONT_DOWNLOAD="We have to download Sim Sun font"
LNG_CO_WINE_EXISTS="Patched wine version installed successfully or already present"
LANG_CO_WINEFAILED="Sorry, patched wine installation not found or failed, you need to redownload wine package"
LANG_CO_LAST="Installation finished. Don't forget to register an account on site for playing.
ATTENTION:
You MUST hold ALT button during LOGIN and PASSWORD input or you'll be unable to connect.
To make your life easy you can check 'Remember' on logon screen"
LANG_CO_CANCEL="Script canceled"
LANG_CO_FIN="Finish"
}

#define variables for wine version to easy change it later
# WINE_PACK_CO="1.0-rc2_ani.tar.gz"
# WINE_VER_CO="1.0-rc2_ani"
WINE_PACK_CO="wine-ani.tar.gz"
WINE_VER_CO="1.0~rc1.ani"
# define function to really cancel the script execution and remove tmp directories
cancel_co ()
{
if [ "$?" = "1" ]
then
attention "$LANG_CO_CANCEL" "$LANG_CO_FIN" 0 0 0 "" "$LANG_CO_FIN"
rm $REPERTOIRE/tmp/ConquerOnline/ -r
rm $REPERTOIRE/wineprefix/ConquerOnline -r
exit 0
fi
}

#define function to check proper installer
check_installer()
{
INSTALLER_PATH=$(select_file "$LNG_CO_INSTALLER_QUESTION" "" 3 11 1 )
cancel_co
#define variable for filename for easy script reading
FILE_NAME=$(basename "$INSTALLER_PATH")
#define variables that check picked filename for beginning string and for extension
GAME_NAME=$(expr "$FILE_NAME" : '\(Conquer\)')$(expr "$FILE_NAME" : '.*\(.exe\)')
ZIP_NAME=$(expr "$FILE_NAME" : '\(Conquer\)')$(expr "$FILE_NAME" : '.*\(.zip\)')
#message "$ZIP_NAME"
#first checking for .exe file, if not - call the function from the beginning,
#if .exe ok - check for zip, if ok - extract and change installer path for wine
if [ "$GAME_NAME" != "Conquer.exe" ]
then
if [ "$ZIP_NAME" != "Conquer.zip" ]
then
error "$LNG_CO_INSTALLER_ERROR" "" 0 0 1 "" ""
check_installer
else
run_and_wait "$LNG_EXTRACT_WAIT" "unzip $INSTALLER_PATH -d $REPERTOIRE/tmp/ConquerOnline/" "" 4 11 1
cancel_co
#so as we don't really know filename we will check temp directory for extracted .exe
INSTALLER_PATH="$(ls | grep .exe)"
fi
fi
}
# define function for checking if /WineVersions/1.0-rc2_ani exists in case of failed downloading
check_wine_co()
{
if [ ! -e "$REPERTOIRE/WineVersions/$WINE_VER_CO/usr/bin/wine" ]
then
message "$LANG_CO_WINEFAILED"
rm $REPERTOIRE/WineVersions/$WINE_VER_CO/ -r
download "$LNG_CO_WINE_DOWNLOAD" "http://switch.dl.sourceforge.net/sourceforge/djlrepository/$WINE_PACK_CO" "" 5 11 1
run_and_wait "$LNG_EXTRACT_WAIT" "tar -xvzf $WINE_PACK_CO" "" 6 11 1
cancel_co
cp -r "$WINE_VER_CO" $REPERTOIRE/WineVersions/
check_wine_co
else
message "$LNG_CO_WINE_EXISTS" "" 5 11
fi
}
#add fonts to registry
add_fonts()
{
echo "\"Arial\"=\"arial.ttf\"" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "\"Courier New\"=\"cour.ttf\"" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "\"Sim Sun\"=\"simsun.ttf\"" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
}

# change language
case "$POL_LANG" in
"fr_FR.UTF-8")
fr_co
;;
"en_US.UTF-8")
en_co
;;
*)
en_co
;;
esac

#prepare clean directory
if [ -d "$REPERTOIRE/tmp/ConquerOnline/" ]
then
rm $REPERTOIRE/tmp/ConquerOnline/ -R
fi
mkdir -p $REPERTOIRE/tmp/ConquerOnline
cd $REPERTOIRE/tmp/ConquerOnline/
#tell user about download options or proceed to downloading
message "$LNG_CO_PRES" "$LNG_CO_PRES_TITLE"
down=$(menu "" "$LNG_CO_DOWNED"~"$LNG_CO_URL" "" 1 11 1 "" "~")
cancel_co
if [ "$down" == "$LNG_CO_URL" ]
then
message "$LNG_CO_HOWTO" "" 2 11
browser [http://co.91.com/downloads/client.shtml](http://co.91.com/downloads/client.shtml)
message "$LNG_CO_WAIT_END"
fi
check_installer

#Downloading and installing wine with patch for animated cursors
#mkdir -p $REPERTOIRE/tmp/ConquerOnline
cd $REPERTOIRE/tmp/ConquerOnline/

#prepare patched wine
check_wine_co

#Prefix's creation
mkdir -p $REPERTOIRE/wineprefix/ConquerOnline/
select_prefix "$REPERTOIRE/wineprefix/ConquerOnline/"
polprefixcreate 7 11

#install game with patched wine
attention "$LNG_CO_DEFAULT" "" 8 11
Set_WineVersion_Session "$WINE_VER_CO"
cd $REPERTOIRE/tmp/ConquerOnline/
wine "$INSTALLER_PATH"

#download simsun font and fix Fonts prefix problem
if [ -d "$REPERTOIRE/wineprefix/ConquerOnline/drive_c/windows/Fonts/" ]
then
rm $REPERTOIRE/wineprefix/ConquerOnline/drive_c/windows/Fonts/ -R
fi
cd $REPERTOIRE/wineprefix/ConquerOnline/drive_c/windows/
ln -s fonts Fonts

cd $REPERTOIRE/tmp/ConquerOnline/
download "$LNG_CO_FONT_DOWNLOAD" "http://www.vietnamtourism.com/c_pages/font/simsun.ttf" "" 9 11 0
cp -f simsun.ttf $REPERTOIRE/wineprefix/ConquerOnline/drive_c/windows/Fonts/

#copy needed dll's from game directory
cp -f $REPERTOIRE/wineprefix/ConquerOnline/drive_c/Program\ Files/Conquer\ 2.0/mfc42.dll $REPERTOIRE/wineprefix/ConquerOnline/drive_c/windows/system32/
cp -f $REPERTOIRE/wineprefix/ConquerOnline/drive_c/Program\ Files/Conquer\ 2.0/msvcp60.dll $REPERTOIRE/wineprefix/ConquerOnline/drive_c/windows/system32/

# Apply Fix with dll's and fonts in menu
echo "[HKEY_CURRENT_USER\Software\Wine\DllOverrides]" > $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "\"mfc42\"=\"native\"" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "\"msvcp60\"=\"native\"" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "[HKEY_CURRENT_CONFIG\Software\Fonts]" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "\"LogPixels\"=dword:00000051" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
echo "[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Fonts]" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
add_fonts
echo "[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Fonts]" >> $REPERTOIRE/tmp/ConquerOnline/fix.reg
add_fonts
regedit $REPERTOIRE/tmp/ConquerOnline/fix.reg

#change wine options, reboot and create launcher
Set_Desktop On 1024 768
simulate_reboot 10 11
cd $DESKTOP && rm -f "Conquer 2.0.lnk" "Conquer 2.0.desktop"
creer_lanceur "ConquerOnline" "Program Files/Conquer 2.0/" "play.exe" "ConquerOnline" "Conquer Online"
Set_WineVersion_Assign "$WINE_VER_CO" "Conquer Online"

#tell user about sign-in specific issues, clear temp and finish.
attention "$LANG_CO_LAST" "$LANG_CO_FIN" 11 11 0 "" "$LANG_CO_FIN"
rm $REPERTOIRE/tmp/ConquerOnline/ -R
exit 0

4. Now you are ready to install Conquer Online.

5. Run POL from Applications --> Games --> Play On Linux
   From the Tools Menu, Click Run A Non-Official Script and Paste the   Script below.

6. Browse the Script that u have just saved from your Documents Folder.

7. After the installation. Go to Tools Menu again and Install Direct X.

Cheers and Have Fun...

****NOTE****
To input password on logon page user have to hold ALT key. That's all

---

### Post by mikerphone on 2008-06-22
when  try to install well 
1st it makes me agree to terms
2nd it ask me if i wanna download the following conquer to folder programs conquer 2.0
3rd installing 
4th configuering new software
5th working installing
6th gone the farthest iv ever seen it go
7th wow its working since i put the document fold in named conquer 2.0 
8th grats its done now finishing
9th logging in
10th auto patching
11th clicked bypass and it shut off
12th retrying to log on
13th standerd def
14th failure to auto patch notice
15th downloading all patchs
16th  HELP ME

---

### Post by pogztimz on 2008-06-23
> **mikerphone said:**
> when  try to install well 
1st it makes me agree to terms
2nd it ask me if i wanna download the following conquer to folder programs conquer 2.0
3rd installing 
4th configuering new software
5th working installing
6th gone the farthest iv ever seen it go
7th wow its working since i put the document fold in named conquer 2.0 
8th grats its done now finishing
9th logging in
10th auto patching
11th clicked bypass and it shut off
12th retrying to log on
13th standerd def
14th failure to auto patch notice
15th downloading all patchs
16th  HELP ME

did u followed the instructions step by step..?? it worked fine on me..

---

### Post by GrantsV on 2008-11-18
I get past the  main login. But when creating a new character and submitting the name, class and size (big, small) I always get:

"Sorry, the name you specified contains invalid characters."

Everything else appears to be working fine.

---

### Post by pogztimz on 2008-11-24
> **GrantsV said:**
> I get past the  main login. But when creating a new character and submitting the name, class and size (big, small) I always get:

"Sorry, the name you specified contains invalid characters."

Everything else appears to be working fine.

hmmm. try creating chars with simple names. or use CHARACTER MAP from Accessories if u wanna put special characters in ur name.. i hope this works for u.. :-)

---

### Post by squall273 on 2008-12-29
When i try and run conquer after i have installed it through POL it freezes the wine prefix as soon as the anti-trojan starts to run. What should i do? I have already tried re-installing conquer but it still crashes in the same spot.

---

### Post by joseacavallo on 2009-08-03
I think you could be missing tho install the directx, open POL, then click on install, and choose directx, follow the steps, and you will be able to play it.

---

### Post by User-X on 2010-01-29
Hello i am new here i install all like in this forum and Co start but is said dirctx 3d i setup dirctx 9c and now all fix only one problem wine do not see my video card [nvidia GeForce 8400M GS] and Co popup msg of dirctx or setup video card again reinstall video card did not help =\ any one can help me thanks in advance
edit: i reinstall Conquer and install wine and now i pass all screens but after i click enter i see black screen and sound of log-in but is stack did not log in any idia ?

---

### Post by RockStarzInc on 2010-12-04
Pogztimz, You are a true genius!!!

---

### Post by 01Dunno on 2012-02-25
hi there !
i too want to instal conquer online in ubuntu
i have ubuntu 11.10 and i follow your steps
but then i had a problem when installing your script

it says:
"Here the source code of the script. Check it carrefully"

No source code appears or the i agree button ...
what should i do ?

---

