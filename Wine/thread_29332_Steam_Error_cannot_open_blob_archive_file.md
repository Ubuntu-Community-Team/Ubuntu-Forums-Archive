---
title: "Steam Error: cannot open blob archive file"
date: 2005-04-23
forum: Wine
---

### Post by Daz_Man on 2005-04-23
hi there, im a bit of a linux newbie and i have been trying to steam working for a few days now. i have got steam installed on my windows hard drive and am trying to use cedega to get it working in linux. when i try and run steam it gives me this error:

```
Steam.exe (main exception): Cannot open
blob archive file:
CMultiFieldBlob(mem-mapped file): Failed to
open file
```

any suggestions as to how to fix this as i really miss CS.

Thanks

---

### Post by telmo on 2005-04-24
I've never seen that error before...  :???: 
Try running Steam from the command line.
```
cd /<steam install path>
cedega steam.exe
```

Or try re-installing...  O:)

---

### Post by Daz_Man on 2005-04-24
i have tried running cedega steam.exe and cedega STEAM.exe from the steam folder but that didnt work. i will try installing steam again and let you know how it goes. thanks

---

### Post by telmo on 2005-04-24
Anytime... ;)

---

### Post by mYl1ttl3PWNY on 2007-12-03
I've recently ran into the exact same problem... I had a problem just like it on my windows machine and all I had to do was delete the /ClientRegistry.blob
and it worked fine. For some reason I cannot delete it...something about I don't have permissions.!?

Uninstall doesn't work and if I try to install it says I need to manually turn off steam because another one is running. Any Ideas on how I can turn it off in wine ?

---

### Post by dudeofthedead on 2007-12-04
Try and delete ClientRegistry.blob as a super user.

If that doesn't solve the problem, change the access permission with chmod by running:

```
chmod ugoa+rwx ClientRegistry.blob
```

Then delete it again.

---

### Post by maxxel on 2008-06-06
well.. even deleting the .blob file, it still getting the error
i was getting this error in windwos vista, but i resolved by executing as administrator... (right-click>open as..>Admnistrator)

See the Terminal error
> [B]fixme:spoolsv:serv_main (0 (nil))
err:service:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
err:virtual:map_file_into_view shared writable mmap not supported, broken filesystem?
err:virtual:NtMapViewOfSection map_file_into_view 0x870000 101000 000000000 failed[/B]


---

### Post by bobpaul on 2008-07-02
It runs fine on my 32bit machine, but I'm getting the same error on 64bit. I even tried the 32bit wine .deb package from winehq, and that didn't resolve the issue. I guess we just need to do a 32bit Ubuntu install for Steam :\

**Edit:** I was experiencing an issue with a fuse mounted folder, see [post #13](http://ohioloco.ubuntuforums.org/showpost.php?p=5368445&postcount=13). 64bit Wine is not an issue.

---

### Post by cogadh on 2008-07-02
Wow, this is an old thread that just keeps coming back.

If you are all trying to run a copy of Steam that was installed in Windows (like the OP), then that is your problem. Wine is not meant to be used that way and Steam won't work that way since it doesn't have access to the Windows registry while being run in Wine. Install Steam in Linux through Wine (like you are supposed to) and then run it locally from within Linux and you won't have this issue at all.

---

### Post by bobpaul on 2008-07-02
> **cogadh said:**
> Install Steam in Linux through Wine (like you are supposed to) and then run it locally from within Linux and you won't have this issue at all.

I don't own windows, so installing through is my only option and the option I used.

64bit Ubuntu 8.04 installed this way does not work.

32bit Ubuntu 8.04 installed through wine works fine.

**Edit:** 64bit machine was also using a fuse mounted file system. That was the issue.

---

### Post by TronBoRG on 2008-07-04
I managed to resolve this by installing steam to an ext3 partition. I had the error you are talking about when installing it to my NTFS partition. :)

Hope this helps

---

### Post by ZpiX on 2008-07-11
I have same problem but after TronBoRG said he resolve the problem by installing it on a ext3 partition insted of a ntfs partition it tryed to install it on my other harddisk (cant remember the partition XD put prolly ext3 too) i resolve the problem too :)

Installed whit wine...

---

### Post by bobpaul on 2008-07-12
TronBoRG and Zpix's replies got me thinking. I don't have windows, so no NTFS or anything like that, but on my laptop (64bit) I do use encfs--uses fuse, just like ntfs3g--to encrypt my home folder. Since the default wine prefix is ~/.wine, my wine folder was encrypted, too.

I made a folder /home/steam and did 'WINEPREFIX=/home/steam wine start SteamInstall.msi'. Now it works.

So it appears to be fuse and not NTFS specifically that causes the problem.

---

### Post by ZpiX on 2008-07-12
XD hope some can help me here XD

I just change to linux 2days ago (thats why my second HDD is NTFS)
and the only things i have been doing atm is install WoW, D2 and steam so im still noob to linux XD

But bobpaul u saying that before u installed it in the floder /home/user/.wine? and it encrypted (they are encrypted when there are a "." in front of the word fx .wine??)

and then u tryed install it on an other location /home/steam

and then it worked?

Am i right? or is it all wrong?

because the floder i installed it on when i got the problem was on my second HDD /media/HDD2/Games/Steam but then i tryed install in it default floder it wanna save it in when u install it /home/Username/.wine/drive_c/Program Files/Steam

And then it worked..

So if im right in the first part.. my part sounds wierd :)

hope someone can get me understand :P

---

### Post by bobpaul on 2008-07-12
> **ZpiX said:**
> XD hope some can help me here XD

I'm not sure what XD means. Is that important?

> **ZpiX said:**
> But bobpaul u saying that before u installed it in the floder /home/user/.wine? and it encrypted (they are encrypted when there are a "." in front of the word fx .wine??)

No, folders are hidden if you place a . in front of them. Mine was encrypted because I did something special to encrypt my entire home folder. ([Encrypted Home Folder](https://wiki.ubuntu.com/EncryptedHomeFolder))

> **ZpiX said:**
> because the floder i installed it on when i got the problem was on my second HDD /media/HDD2/Games/Steam but then i tryed install in it default floder it wanna save it in when u install it /home/Username/.wine/drive_c/Program Files/Steam

You had problems with /media/HDD2/... because that location is an NTFS drive. On linux, NTFS is not a filesystem format that can be read and written to by the linux kernel. The filesystem driver for it actually runs in userspace through the fuse library (fuse stands for filesystem in user sapce). The setup I used to encrypt my home folder is also written as a fuse driver (encfs). As a result, I could have installed anywhere in my home folder and still had problems whereas you could have installed anywhere in /media/HDD2/ and still had problems. Normally the default location (~/.wine) should be perfectly fine. In *my* case it was not.

---

### Post by ZpiX on 2008-07-12
Hehe, that helped me alot :)

But what is the most normal partition in linux? for games, movies, music, pictures and all that?

And is there a place were i can see what the diffents is?

---

### Post by bobpaul on 2008-07-12
> **ZpiX said:**
> Hehe, that helped me alot :)

But what is the most normal partition in linux? for games, movies, music, pictures and all that?

And is there a place were i can see what the diffents is?

We're beginning to get off topic. If you'd like to start a new thread with a well reasoned question I'd be happy to continue the discussion. There might be further issues with the steam blob error and I'd rather not muddy up the thread with off topic chatter.

If you start a new thread, PM a link to it. Or if you prefer, we can just chat via private messages.

---

### Post by enbuyukfener on 2008-08-11
bobpaul, I doubt there is much more to this issue anyway. If the thread gets out of hand, a mod can split the thread. Anyway, I had this problem after reinstalling Steam to an NTFS partition and this thread confirmed the partition type was the issue. And XD is a cartoon happy face as far as I know.

ZpiX, the partition to use for such content is a gray area. It depends on interaction with Windows computers for one as I don't trust the third party utilities for ext2/3 reading from Windows. As a result, I have 3 partitions (plus one for Windows), they are root (/), home (/home) and data (/media/data). The latter is by far the largest and has multimedia, downloads, server files and documents, basically anything that might be shared or need to be synced across the network (the data drives - D:\ or /media/data - on the computers here basically mirror each other). /home/username contains symlinks to directories on the data partition for convenience such as /home/username/Documents, /home/username/Downloads etc. /home also stores settings and virtual machines.

Games, however, are not very easy. The size of them presents a problem as does running them on a dual boot system and wanting to have them available on both Windows and Linux (I run a dual boot system). My solution for Steam was to install the client on Windows and Linux separately, and then to share the SteamApps directory. For Linux, this was simply a matter of using a symlink.

---

