---
title: "Can't get crack running"
date: 2011-08-27
forum: Wine
---

### Post by frederikfaye on 2011-08-27
Hello people, I've recently successfully downloaded and installed Call of Duty 5: World at War, but I'm having problems getting the campaign-mode to launch.

The readme that followed the downloaded iso-file is as follows:
  1. Unrar.
  2. Burn or mount the image.
  3. Install the game using the following serial number:
     MPC8-MD8P-78P1-75DU-890F
  4. Copy the cracked content over from the Crack directory on the disc to
     your installation directory.
  5. Play the game.

I mounted the iso, installed the game, but how am I to interpret number 4, when I'm using Ubuntu 10.04? As far as I know, there isn't really any installation directory to be found.

Well, anyways, a desktop icon called "Call of Duty(R) - World at War(TM) - Solo - Co op" was created, but when I click it, the following message occurs: 

[I]"Cannot locate the DVD-ROM
Please insert the correct DVD-ROM, select OK and restart application"[/I]

The command for this icon is: 'env WINEPREFIX="/home/freden/.wine" wine C:\\Program\ Files\\Activision\\Call\ of\ Duty\ -\ World\ at\ War\\CoDWaW.exe'

In the terminal, I then changed this to go straight for one .CoDWaW.exe-file, as it was located in the unrar'ed and mounted folder: 
'env WINEPREFIX="/home/freden/.wine" wine /media/rld-cod5/Setup/rsrc/CoDWaW.exe' 
whereafter an error message occurs, saying that CoDWaW.exe has run into a serious problem, and because of this, it will be shut down. It suggests that this could be caused by an error in the problem, or a problem with Wine. I have Wine1.2, so that shouldn't be the problem. After closing this error message, an "application error" message with some numbers occur. In the terminal, the following follows the command:
[I]'err:ole:CoGetClassObject class {00000507-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000507-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000507-0000-0010-8000-00aa006d2ea4} could be created for context 0x5
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b8373a2 (thread 0028), starting debugger...'[/I]
 - which is then followed by a lot a numbers and stuff..

I also tried directing to another file in the mounted folder called 'CoDWaW.exe' in a folder called 'Crack', so this might be the correct file. The command and the following error message is as follows:
'env WINEPREFIX="/home/freden/.wine" wine /media/rld-cod5/Crack/CoDWaW.exe
err:module:import_dll Library binkw32.dll (which is needed by L"Z:\\media\\rld-cod5\\Crack\\CoDWaW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\rld-cod5\\Crack\\CoDWaW.exe" failed, status c0000135'

As a last thing, I tried copying both the folder called 'Crack' (trying to follow the instructions giving by the uploader), and the entire mounted folder, and then directing to the file in the 'Crack' folder, but I then got the same error message as the last one above. 


**How can this 'import_dll' be found, and how can I get the launcher-icon to believe that I already have the disc inserted (Ubuntu seems to read the mounted iso as such)??**

Sorry for the long text, and the probably pretty amateurish tries, but I would really like to get all of this over with, and just start playing. Any help would be much appreciated. 
WHAT TO DO?

- freden

---

### Post by realzippy on 2011-08-27
For sure this is against the code of conduct of this forum.

---

### Post by overdrank on 2011-08-27
This is not supported on the forums. Thread closed.

---

