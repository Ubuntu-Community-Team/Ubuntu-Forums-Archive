---
title: "Ubuntu 9.04 64bit and Web Browser problems"
date: 2009-10-23
forum: x86 64-bit Users
---

### Post by drdos2006 on 2009-10-23
I installed Ubuntu 9.04 64 bit on my computer.
Ran Firefox but it was taking minutes to come back and say something like “the server is not allowing a connection” when I connected to my home page. Forget about trying to connect to the Home page forum. It was not happening. Edited Preferences > Advanced > Network > Settings to Automatically detect proxy settings, saved, closed and reran Firefox. Did not fix anything at all.
I went to Privacy > Accept cookies from sites > added always for ISP Home Page in the Exceptions. Did not fix anything at all.

So I installed Konqueror and it had the same problem. Pages not loading etc.
So I went to Settings, changed to Automatically detect the proxy configuration and tried Connect to the Internet directly. Both settings were hopeless.
I changed settings in the cache, cleared the cache etc. I got into the Cookies section and altered settings to accept all cookies as session cookies etc but this time I got a more detailed error code.
Once the cache had loaded aaNet Home Page I tried to connect to the Australian ABC. 

[error]
The requested operation could not be completed
Connection to Server Refused
Details of the Request:
URL: [http://www.abc.net.au](http://www.abc.net.au)
Protocol: http
Date and Time: Friday 23 October 2009 18:50
Additional Information: [www.abc.net.au:](www.abc.net.au:) Unknown error
Description:
The server [www.abc.net.au](www.abc.net.au) refused to allow this computer to make a connection.
Possible Causes:
The server, while currently connected to the Internet, may not be configured to allow requests.
The server, while currently connected to the Internet, may not be running the requested service (http).
A network firewall (a device which restricts Internet requests), either protecting your network or the network of the server, may have intervened, preventing this request.
Possible Solutions:
Try again, either now or at a later time.
Contact the administrator of the server for further assistance.
Contact your appropriate computer support system, whether the system administrator, or technical support group for further assistance.
[/End of error]
Until the Home page for my ISP was loaded into the cache, I was getting the same error connecting to ISP Home Page.

So I ran Sun's Virtualbox, installed an XP OS into virtualbox, installed Firefox and connected to ISp's Home page. Ran like a dream. The Network settings for XP Firefox was set at No Proxy.

Does anybody have any ideas as to what the problem might be that Ubuntu does not allow the web browsers to run properly ?
What settings do I need to change ?

:)

---

### Post by masux594 on 2009-10-23
Some questions.. 
> What version of firefox have u installed?
> Firefox always [since u have installed it(if u have installed another version)] raise this error or raise this error from few time?

Because firefox gave me the same error when i try to install FF3.5 in a "wrong" way.. So, found another way to install it and then run as a rabbit =)

Sysc, A

---

### Post by sahabcse on 2009-10-23
have you enable any firewall and check your proxy setting also, For installing firefox 3.5 please follow below url


[http://ubuntulinux.co.in/Firefox-3-5-in-Ubuntu-9-04-Jaunty-Jackalope.php](http://ubuntulinux.co.in/Firefox-3-5-in-Ubuntu-9-04-Jaunty-Jackalope.php)

---

### Post by RaveJunkie on 2009-10-23
to install firefox 3.5  -  [http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)

or 

[http://ubuntuforums.org/showthread.php?t=1200446](http://ubuntuforums.org/showthread.php?t=1200446)

then just get flash alpha 10 from adobe and put into your Plugins folder under .mozilia

after you install it it will be called like "shirkto" cause its "too new" and ubuntu goes with the super stable one.

---

### Post by drdos2006 on 2009-10-23
Hi people.
Thanks for the replys, I tried both suggestions and am unable to run Version 3.5. I had Version 3.0 installed. I have reinstalled Firefox 3.0 via Package installer.

Because it is happening with both Firefox and Konqueror, I am thinking that it is the nVidia card. I shall remove the AGP card and use the on board video, see if that makes a difference.
I'll be back real soon.
:)

---

### Post by drdos2006 on 2009-10-23
Thanks people
I checked in the /var/logs/syslog file and found that 'No AGP bridge found'.
So I removed the nVidia AGP card, found an old VGA monitor, connected via onboard motherboard video output. Rebooted, changed BIOS to see onboard video, increased video memory to 8 megs, ran Ubuntu, changed video to lower graphics and viola ! Forum connects in a flash.
Now to look at updating nVidia drivers
:) :)

---

