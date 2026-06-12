---
title: "How to reinstall WINE from sketch"
date: 2015-10-29
forum: Wine
---

### Post by luke40 on 2015-10-29
Can anybody teach me how to reinstall WINE from sketch? That is, not only reinstall WINE but also redownload its files again.
Because every time I remove and reinstall WINE, it won't download the files again but complete very quickly.

---

### Post by howefield on 2015-10-29
The .deb packages are cached in  /var/cache/apt/archives/ so until you clear that archive they will remain and be used. Why you would want to download them again is a bit of a mystery though ?

Is this post related to[ this one]("http://ubuntuforums.org/showthread.php?t=2300919") in some way ?

---

### Post by luke40 on 2015-10-29
> **howefield said:**
> The .deb packages are cached in  /var/cache/apt/archives/ so until you clear that archive they will remain and be used. Why you would want to download them again is a bit of a mystery though ?

Is this post related to[ this one]("http://ubuntuforums.org/showthread.php?t=2300919") in some way ?


Because I suspect that I didn't accept the [COLOR=#000000] ttf-mscorefonts-installer license(I remember that I just clicked the "Forward" button) so I got some problem when I want to run some program under WINE and it wont't ask me to accept it again when I reinstalled it. 
So, yes, this post relate to [that one]("http://ubuntuforums.org/showthread.php?t=2300919")[/COLOR][COLOR=#000000] as you said.
And how to clear the [/COLOR][COLOR=#000000].deb packages that are cached in /var/cache/apt/archives/ ?[/COLOR][COLOR=#000000]
Thanks.[/COLOR]

---

### Post by howefield on 2015-10-30
```
sudo apt-get clean
```

should remove all packages from your cache.

But first, perhaps you could try

```
sudo apt-get install --reinstall ttf-mscorefonts-intaller
```

If you didn't install it correctly first time around, it should this time. Or load up Libreoffice and look for these fonts.. Andale Mono, Arial, Arial Black, Comic Sans MS, Courier New, Georgia, Impact, Times New Roman, Trebuchet MS, Verdana and Webdings - if you see them, then the package did install.

---

### Post by luke40 on 2015-10-30
> **howefield said:**
> ```
sudo apt-get clean
```

should remove all packages from your cache.

But first, perhaps you could try

```
sudo apt-get install --reinstall ttf-mscorefonts-intaller
```

If you didn't install it correctly first time around, it should this time. Or load up Libreoffice and look for these fonts.. Andale Mono, Arial, Arial Black, Comic Sans MS, Courier New, Georgia, Impact, Times New Roman, Trebuchet MS, Verdana and Webdings - if you see them, then the package did install.

I entered the first instruction but the installation still didn't redownload the files. So I adopt the second instruction and got the following result:

```
$ sudo apt-get install --reinstall ttf-mscorefonts-intaller
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package ttf-mscorefonts-intaller
$
```

Should I add "WINE" or something in the instruction?

---

### Post by howefield on 2015-10-30
My apologies.. a typo in the command (I missed a letter)

Should be..

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Sorry about that.

---

### Post by luke40 on 2015-10-30
Don't be sorry and thanks for your help.
Now the "Configuring ttf-mscorefonts-installer" window appears and there is the "<Ok>" in the bottom.
How do I accept it? Because there is no response no matter I press Enter or space-bar.

---

### Post by howefield on 2015-10-30
Press the tab key to highlight the ok, then the left arrow to highlight the yes button on the following screen and press enter.

---

### Post by luke40 on 2015-10-30
There is the following line included in the output lines. I tried 2 times and it's the same. What does it mean?

```
IOError: [Errno socket error] [Errno 104] Connection reset by peer
```

The fonts are not in LibreOffice.

The whole outputs are:
```
$ sudo apt-get install --reinstall ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live ibus-chewing kde-l10n-engb kde-l10n-zhtw
  libchewing3 libchewing3-data libupstart1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
Need to get 0 B/27.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 468067 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu1_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu1) over (3.4+nmu1ubuntu1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 239, in process_download_requests
    dest_file = urllib.urlretrieve(files[i])[0]
  File "/usr/lib/python2.7/urllib.py", line 94, in urlretrieve
    return _urlopener.retrieve(url, filename, reporthook, data)
  File "/usr/lib/python2.7/urllib.py", line 240, in retrieve
    fp = self.open(url, data)
  File "/usr/lib/python2.7/urllib.py", line 208, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 359, in open_http
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 372, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 665, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 635, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 661, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 208, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 346, in open_http
    errcode, errmsg, headers = h.getreply()
  File "/usr/lib/python2.7/httplib.py", line 1123, in getreply
    response = self._conn.getresponse()
  File "/usr/lib/python2.7/httplib.py", line 1051, in getresponse
    response.begin()
  File "/usr/lib/python2.7/httplib.py", line 415, in begin
    version, status, reason = self._read_status()
  File "/usr/lib/python2.7/httplib.py", line 371, in _read_status
    line = self.fp.readline(_MAXLINE + 1)
  File "/usr/lib/python2.7/socket.py", line 476, in readline
    data = self._sock.recv(self._rbufsize)
IOError: [Errno socket error] [Errno 104] Connection reset by peer
Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ...
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu1) ...
$
```

The Software Center shows that WINE is not installed.

---

### Post by luke40 on 2015-10-30
I reconnect my connection and the fonts are succefully installed.
But why the Sotware Center don't show WINE is installed? Though there is an icon named "Uninstall Wine software" in "Search your computer and online sources."

---

### Post by howefield on 2015-10-30
The error would generally mean there is an issue with the sourceforge site that the package is trying to download the fonts from. Basically what happens is that apt will download the deb package (ttf-mscorefonts-installer) and install it, and as part of that install it needs to get some files (the fonts) from a third party server, in this case sourceforge.

"*IOError: [Errno socket error] [Errno 104] Connection reset by peer*" seems to be the servers way of hanging up on you.

Can you ping the server ?

```
ping downloads.sourceforge.net
``` 

Try that.. ctrl +c to stop it - you only need a couple of reponses to know that you can ping it.

Edit : Typed before seeing your last reply :)

---

### Post by howefield on 2015-10-30
> **luke40 said:**
> I reconnect my connection and the fonts are succefully installed.

Great :)

> But why the Sotware Center don't show WINE is installed? Though there is an icon named "Uninstall Wine software" in "Search your computer and online sources."

Presumably because it isn't installed, or at least, not fully installed.

You could use the command from earlier to test it..

```
sudo apt-get install wine
```

if it is installed, it will tell you that the latest version is already installed.

Alternatively, if you want to reinstall it..

```
sudo apt-get install --reinstall wine
```

---

### Post by luke40 on 2015-10-30
I think the reinstallation problem is basically solved.
Thanks very much for your help.

---

### Post by luke40 on 2015-10-30
I think the reinstallation problem is basically solved.
Thanks very much for your help.

EDIT: Sorry. My reply is too fast.

---

### Post by luke40 on 2015-10-30
> **howefield said:**
> Great :)



Presumably because it isn't installed, or at least, not fully installed.

You could use the command from earlier to test it..

```
sudo apt-get install wine
```

if it is installed, it will tell you that the latest version is already installed.

Alternatively, if you want to reinstall it..

```
sudo apt-get install --reinstall wine
```

I tried the first instruction and now the Software Center shows that WINE is installed.
Thanks very much for your help.

---

