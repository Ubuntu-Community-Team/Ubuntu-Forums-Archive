---
title: "Clear temp files of Wine's IExplorer on exit/shutdown?"
date: 2012-10-01
forum: Wine
---

### Post by MrsUser on 2012-10-01
In Wine, I had a software installed, called RaySource, which is used to download files from China (Rayfile - which is like the Chinese version of Rapidshare).

This software, however, created literally hundreds of thousands of files in Wine's temp folder of Internet Explorer. All this within a few months. I was shocked discovering this. It took ages to delete all these files, even via terminal.

[IMG]http://i.imgur.com/UCwrn.png[/IMG]

Now I'm looking for a way to cleanse out the temp files of IE on Wine exit or on Ubuntu shutdown.

Second, I'm looking for a way to have that Windows app and all its components really exit. I noticed that even after closing the Windows app, two exe files (peer.exe & PeerAdapter.exe) of that app keep running in the background and hogging net bandwidth. And I have to kill them in terminal with killall.

Any help is appreciated.

---

### Post by Stonecold1995 on 2012-10-01
First off, I wouldn't trust Chinese filehosting software, especially if it's cluttering your temp folder.

I don't know how to clear them at application close, but for Ubuntu shutdown I suppose you could create a script that deletes the temporary files and put it in your shutdown directory (I don't know where it is in Unity, as I only use KDE).

Windows processes are suppose to manage themselves, it's not Wine's job.  Wine has no way to know if a process is running because it's suppose to run, or if it hasn't closed properly.

I can't stress enough, I really wouldn't trust a Chinese filehosting application that puts huge amounts of files in your temp folder, that is constantly using internet bandwidth, and that leaves perpetually running processes in the background.  Remember that even if you are using Linux, Wine can present a major security risk.  Wine strives to be compatible with as many Windows programs as it can, and that includes malware.

---

### Post by MrsUser on 2012-10-02
Thank you for your response.

Meanwhile I've done some research about Rayfile/Raysource.
The software is used by millions of Chinese people. It seems to be adware, because on Windows it displays flash ads at the bottom of the software, but nothing harmful. I also found out why it creates these files and hogs net bandwidth. It's because it secretly mirrors the downloaded files on your computer in order to provide it to other users who use Rayfile too.

I looked into these files. They are merely simple text files with some sort of xml description of file chunks. I've discovered many file names in there of files I downloaded through Raysource. I guess that's how it manages its peer functionality.

Basically, it's a file hosting service which isn't a real file hosting service, but rather a mixture between file hosting and peer-to-peer. After you downloaded a file from their servers, their software makes sure your computer provides bandwidth to upload that file to others as well. So Rayfile saves bandwidth on their users' expense.

Therefore, on Chinese websites they give the advice to kill all of the Raysource tasks after exiting the software, in order to prevent described bandwidth hog. And I'd like to do the same in Ubuntu. I can use "sudo killall peer.exe" and "sudo killall PeerAdapter.exe" to kill those tasks manually. But it'd be nice to have it down automatically with a script. However, I'm still a total newb and don't know how to write scripts in Ubuntu.

---

### Post by Stonecold1995 on 2012-10-02
To kill the leftover processes and clean up the temporary files created, put this in a text file:
```
#!/bin/bash

name="your name"
raysource="/path/to/raysource.exe"

cd ~/".wine/drive_c/users/$name/Local Settings/"
mv "Temporary Internet Files" "Temporary Internet Files-bak"
mkdir -p "Temporary Internet Files"
wine "$raysource"
killall -w peer.exe PeerAdaptor.exe
rm -rf "Temporary Internet Files"
mv "Temporary Internet Files-bak" "Temporary Internet Files"
exit 0

```

Save this script as "raysource.sh" (or something like that), and in Terminal, mark it as executable by running this:
```
chmod a+x raysource.sh
```

Now any time you want to run RaySource, just run this script instead.  It'll run raysource.exe, then when you close the program, it'll kill those two pesky processes, then it'll remove all the files in "Temporary Internet Files" that were created by RaySource, while leaving any temporary files created before by other programs intact.  Replace "your name" with your name (the name under ".wine/drive_c/users/"), and replace the path with the actual path to the executable (e.g. "/home/user_name/cool stuff/raysource.exe").

This is just one solution.  Other people might have other ideas.

---

### Post by MrsUser on 2012-10-02
OMG! This is so nice of you! Exactly what I need.

It took me a while to find out why it did not start Raysource. But Google helped. Wine expects the Windows fake path, not the Unix path. So I had to put "C:\Program Files\RaySource\RaySource.exe\" and now it looks like this:

```
#!/bin/bash

name="username"
raysource="C:\Program Files\RaySource\RaySource.exe"

cd ~/".wine/drive_c/users/$name/Local Settings/"
mv "Temporary Internet Files" "Temporary Internet Files-bak"
mkdir -p "Temporary Internet Files"
wine "$raysource"
killall -w peer.exe PeerAdapter.exe
rm -rf "Temporary Internet Files"
mv "Temporary Internet Files-bak" "Temporary Internet Files"
exit 0
```Works like a charm. Thank you so much for your help!!! You made my day :):):)

Oh, and I really need to learn how to write bash scripts. This will be my next task ^^

---

### Post by Toz on 2012-10-02
Moved to the Wine sub-forum.

---

### Post by Stonecold1995 on 2012-10-02
> **MrsUser said:**
> Wine expects the Windows fake path, not the Unix path.

You don't need to use the Window's path, you can use the normal path if you remember to specify the full path ([example]("http://www.pictureshack.us/images/54619_path.png")).  Personally I prefer using the normal path scheme because it's easier to remember, and because I can specify a location outside of .wine (I keep all my Windows programs outside .wine in case I need to delete the whole .wine folder, I'll still have all my programs and settings).

---

### Post by MrsUser on 2012-10-04
Meanwhile, I made a few more tests. I installed the software on a real Windows XP (in VirtualBox) to see if it writes out these files as well. Strangely, it doesn't. I was wondering what happens there. In Ubuntu, it writes permanently files named 'peer[0]', 'peer[1]', 'peer[2]' etc and deletes them again, just to write them again and again and delete them again and again. I opened some of them to see if they contain anything. And indeed they're only text files, containing simply the text 'OK'. So I'm confused now. But I'm pretty sure it has to do with Wine. Also, those files are different than the ones it used to write before my re-install. But back then I used Wine 1.4. Now I'm using Wine 1.5.

It looks as if peer.exe writes to disc instead to RAM when running through Wine. As I said, in Windows it does not have such behavior. Now I have two options. Figure out how to make it not write these files when running through Wine (perhaps it misses some DLLs and thus writes temp data to disk instead) or I have to run it in a VM. I also think about running the whole wineprefix in a RAM drive. Because this writing of peer[0] etc files wears off my hard disk.

EDIT:
I noticed that it needs a lot of CPU when running it in Wine. My fan is whirring a lot. If I run it in Windows XP in VirtualBox, I need much less CPU, none of these high cpu usage peaks and my fan stays silent. So I guess I'll let it run in VirtualBox. In this case it's not inconvenient, because all I do with this software is downloading. So I rarely have to switch to VirtualBox. I just let it run in the background. Also, the guest system can write to a shared folder - which is really nice and easy. This way I don't have to copy it after download. The Raysource client accepts the download path to the shared folder, because it's nothing else than a drive letter. It's absolutely transparent. I can even make symlinks in that shared folder and then write directly to Ubuntu's download folder for example. VirtualBox is really awesome. I use VirtualBox 4.2 for this. As far as I remember, in earlier versions I ran into problems choosing the shared folder as a download path, because it pointed to a network path then, not a drive letter.

---

