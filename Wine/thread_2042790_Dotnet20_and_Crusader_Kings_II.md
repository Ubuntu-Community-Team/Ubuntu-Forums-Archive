---
title: "Dotnet20 and Crusader Kings II"
date: 2012-08-15
forum: Wine
---

### Post by Orago on 2012-08-15
Hello.

I am attempting to play the game Crusader Kings II via the latest version of Wine on Ubuntu 12.04 LTS.

I have successfully and without problem installed some of the prerequisites for the game, including DirectX9 and the C++ 2010 redistributable.

I made the game work pretty successfully, but if anyone is familiar with the game, there is an optional "launcher" that requires Microsoft .net 2.0 in order to select mods, check for updates for the game, etc.

How can I install dotnet20 in Wine? Upon typing "bash winetricks dotnet20" into the terminal (and after making sure Wine was configured to be in Windows 2000 mode), I get a 404 error when trying to download .net via the previous command. It appears the url the command "bash winetricks dotnet20" is using to download it is no longer good.

I could Google .net 2.0 and download it from Microsoft, but is it a good idea to install something like that? I read that it is not. Is there a way to properly install .net 2.0 in Wine manually? (Also, I read wininet is also a prerequisite for the game, so I'd need that too.)

Thanks!

---

### Post by ander001 on 2012-08-16
I have the same problem to install dotnet20. I receive a 404 not found code as a response

---

### Post by Azrael3000 on 2012-08-16
See: [http://forum.winehq.org/viewtopic.php?f=2&t=16492](http://forum.winehq.org/viewtopic.php?f=2&t=16492)

---

### Post by Azrael3000 on 2012-08-17
Okay here is some hack to make it work:
```
cd /home/username/
# Get the file from the web archive
wget http://web.archive.org/web/20110608113838/http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe
# Get the latest winetricks:
wget http://winetricks.googlecode.com/svn/trunk/src/winetricks
chmod +x winetricks

```Now open winetricks and go to line 4604, comment it and replace it by
```
w_download /home/username/dotnetfx.exe
```Next start winetricks normally
```
./winetricks dotnet20
```It actually starts the installer for me but then crashes with:
```

fixme:storage:create_storagefile Storage share mode not implemented.
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x451d7c
------------------------
Note: command 'env WINEDLLOVERRIDES=mscoree,fusion=n wine dotnetfx.exe' returned status 5. Aborting
```

[edit]
In order to fix the bug above you need to add the registry key that is described in the following link:
[http://bugs.winehq.org/show_bug.cgi?id=30845#c5](http://bugs.winehq.org/show_bug.cgi?id=30845#c5)

In case you encounter any problems which say "bad exe" simply delete ~/.cache/winetricks/dotnet20

So my installation (on Fedora 16 x86_64) was successful.
[/edit]

---

### Post by Orago on 2012-08-17
Thank you for the advice!

Dotnet20 installed flawlessly after going through every step you posted, and the application I was trying to run (the Crusader Kings II launcher) works.

---

### Post by Azrael3000 on 2012-08-17
You are welcome. I was just sending some emails back and forth with Dan who is responsible for winetricks and the latest svn version should be working (you will need to manually download dotnetfx.exe from cnet, but it will give you the link). So the workaround presented above will no longer be required.

---

### Post by Clanket on 2012-08-19
Hi,

Sorry but I'm a complete noob to Ubuntu and Linux in general.

How exactly do I do this:-

"Now open winetricks and go to line 4604, comment it and replace it by"

Thanks a million.

---

### Post by Azrael3000 on 2012-08-20
No problem, everybody has to start at some stage.

So first let me tell you that this workaround is no longer required. Simply do the following:
```

cd
wget http://winetricks.googlecode.com/svn/trunk/src/winetricks
chmod +x winetricks
./winetricks dotnet20

```
Then you will be prompted to download a file and place it somewhere. Do that. After that run winetricks again
```

./winetricks dotnet20

```

So since you're new I'll explain a bit further.
"cd" goes to a directory, if you don't supply a second argument it will always go to your home directory
"wget url" downloads whatever url you want
"chmod +x filename" makes the file "filename" executable
"./filename" executes a file, the second argument is then just to tell winetricks that you want dotnet20 installed.

---

### Post by fantasticmuse on 2012-08-20
Everything as updated as it gets, still not working. :(

ashley@ashley-NV51B:~$ wget [http://winetricks.googlecode.com/svn/trunk/src/winetricks](http://winetricks.googlecode.com/svn/trunk/src/winetricks)
--2012-08-19 23:24:52--  [http://winetricks.googlecode.com/svn/trunk/src/winetricks](http://winetricks.googlecode.com/svn/trunk/src/winetricks)
Resolving winetricks.googlecode.com (winetricks.googlecode.com)... 74.125.129.82, 2001:4860:8005::52
Connecting to winetricks.googlecode.com (winetricks.googlecode.com)|74.125.129.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 613406 (599K) [text/plain]
Saving to: `winetricks.2'

100%[============================================================================================>] 613,406     1.19M/s   in 0.5s    

2012-08-19 23:24:52 (1.19 MB/s) - `winetricks.2' saved [613406/613406]

ashley@ashley-NV51B:~$ chmod +x winetricks
ashley@ashley-NV51B:~$ ./winetricks dotnet20
Executing w_do_call dotnet20
Executing load_dotnet20
Executing w_do_call fontfix
Executing load_fontfix
Setting Windows version to win2k
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg
Executing mkdir -p /home/ashley/.cache/winetricks/dotnet20
Executing unzip -o -q -d /home/ashley/.wine/dosdevices/c:/windows/syswow64 l_intl.zip
Executing mkdir -p /home/ashley/.cache/winetricks/dotnet20
Downloading [http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe](http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe) to /home/ashley/.cache/winetricks/dotnet20
--2012-08-19 23:25:53--  [http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe](http://download.microsoft.com/download/5/6/7/567758a3-759e-473e-bf8f-52154438565a/dotnetfx.exe)
Resolving download.microsoft.com (download.microsoft.com)... 209.165.150.34, 209.165.150.8
Connecting to download.microsoft.com (download.microsoft.com)|209.165.150.34|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-08-19 23:25:53 ERROR 404: Not Found.

---

### Post by mcchots on 2012-08-20
Your SVN download was saved as winetricks.2

Rename it to winetricks and replace the original or just run that one.

---

### Post by fantasticmuse on 2012-08-20
*facepalm*

---

