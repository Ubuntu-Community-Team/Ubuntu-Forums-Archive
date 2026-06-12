---
title: "Space Engineers Instalaltion on Headless VPS"
date: 2015-01-11
forum: Wine
---

### Post by Macro_User on 2015-01-11
Install Ubuntu Server 14.04 on both server and client 
Copy space engineers (non-64-bit) to an external link, like dropbox.

On Windows:
Use steam to download your copy of Space Engineers. Use your file browser to browse into the Space Engineer's folder, and look for the folder DedicatedServer.

 Use your favorite compression program to compress the non-64 bit version of the dedicated server. 

Run the dedicated server on your local computer, and generate a world. Start the instance, and exit by pressed Ctrl+C when asked. I setup a Steam Group ID.

Go into the directory C:\Users\user\AppData\Roaming and compress the directory of SpaceEngineersDedicated. Upload this file to dropbox, or somehow transfer it to your server.

Use WinSCP to copy this to your client, or use dropbox to make a shared link (you might want to password encrypt if you create a shared link).


You need a working/generated world. In windows, open up space engineers

On Client
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install p7zip-full nano
ssh-keygen
ssh-copy-id your_ssh_user@your_public_ip.com
ssh root@your_public_ip.com
adduser space
adduser space sudo
exit
ssh space@you_public_ip.com

sudo apt-get install wine1.6
sudo apt-get install lubuntu-desktop
sudo apt-get install virtualbox-guest-x11
sudo apt-get install p7zip-full
export WINEARCH=win32
winetricks -q dotnet40

cd ~/.wine/drive_c/users/
cd user
cd Application\ Data


wget -O SpaceEngineersDedicated.7z https://www.dropbox.com/s/REDACTEDLINK/SpaceEngineersDedicated.7z?dl=0
7z x SpaceEngineersDedicated.7z
cd SpaceEngineersDedicated

nano SpaceEngineers-Dedicated.cfg
##Change the line to look like  <LoadWorld>C:\Users\user\Application  Data\SpaceEngineersDedicated\Saves\Tau Ceti</LoadWorld>
##Set your server ip.

cd ~/
wget -O DedicatedServer.7z https://www.dropbox.com/s/REDACTEDLINK/DedicatedServer.7z?dl=0
7z x DedicatedServer.7z
cd DedicatedServer
wine ~/DedicatedServer/SpaceEngineersDedicated.exe -console

```

---

