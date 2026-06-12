---
title: "Can't get Spotify to work using Wine"
date: 2011-09-29
forum: Wine
---

### Post by z_smalls on 2011-09-29
Hi All, 

I'm trying to run Spotify in Ubuntu with Wine. I downloaded the latest version of Wine, downloaded Spotify, opened it...it lets me log in, but as soon as the program opens I get an error message saying: 

"The program spotify.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. 

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application. 

If this problem is not present under Windows and has not been reported yet, etc etc." 

I have no idea what's going on. I've been unable to find anyone online with the same problem. I've uninstalled and reinstalled everything. Please help.

---

### Post by mekwall on 2011-09-30
Hey!

You'll probably have better luck with their Linux client, even though it's in beta. I'm running it myself with very minor issues.

Check it out: [http://www.spotify.com/se/download/previews/](http://www.spotify.com/se/download/previews/)

```
# 1. Add this line to your list of repositories by 
#    editing your /etc/apt/sources.list
deb http://repository.spotify.com stable non-free

# 2. If you want to verify the downloaded packages,
#    you will need to add our public key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

# 3. Run apt-get update
sudo apt-get update

# 4. Install spotify!
sudo apt-get install spotify-client-qt
```

Regards,
Marcus

---

### Post by bikewrecker on 2011-12-05
I'm having the exact same problem. I'm trying the linux preview version spotify has out, but I get the same error. I put that line of code in the repositories like it said but idk where in there I should put it. When i type sudo apt-get install spotify-client-qt i get the error message
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package spotify-client-qt

```
idk what I'm doing wrong. I'd think by now I'd at least be able to install something on ubuntu that gives step by step instructions... 

More info: running 11.10 64bit; wine version 1.3.28.

Anybody who can help the helpless ubuntu noob would be greatly appreciated!

---

### Post by stangdaman on 2011-12-06
Won't the Linux preview only work for Spotify Premium users? I had the same problem that you're seeing with Spotify in Wine. It was working fine for quite a while but one of Spotify's updates broke it and I have not been able to get it to work since.

---

### Post by Simon_WM on 2011-12-07
> **stangdaman said:**
> Won't the Linux preview only work for Spotify Premium users? I had the same problem that you're seeing with Spotify in Wine. It was working fine for quite a while but one of Spotify's updates broke it and I have not been able to get it to work since.

Nop i got it working under Free User

---

