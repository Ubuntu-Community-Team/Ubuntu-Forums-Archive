---
title: "Re: Close to Dreamweaver"
date: 2008-09-07
forum: Wine
---

### Post by Shobuz99 on 2008-09-07
I apologize for cross-posting this from the [Programming Talk]("http://ubuntuforums.org/showthread.php?p=5740674#post5740674") forum
I was told I should move this discussion to this forum.
Please let me know if I'm not supposed to do this.

Re: Close to Dreamweaver
> 
Originally Posted by pablo180 View Post
I use Gutsy 7.10 and Dreamweaver 8 so not really sure whether MX 2004 works, but all I did was install Wine:

Applications > Add/Remove.. > Searched for wine, ticked it and Applied Changes.

Then right-clicked on the setup (setup.exe) file for Dreamweaver and selected 'Open With Wine' - or something similar to that and then just installed it as if it were on Windows.

Once it was complete it worked fine. The version of Wine that installs through Ubuntu seems to be quite old so if it doesn't work you may want to check out the link that LaRoza gave you to see how to install a newer version of wine.

Also this link may have information on how to get MX 2004 working if you run into problems. According to the information there it should install and run on Hardy 8.04.

pablo180

Thanks for your advice. I took it:
I got the wine package installed ok.
I put the DWMX 2004 CD in the CDROM drive (D)
I opened Wine and selected "Configure Wine"..
In the configuration, under the "Applications"tab,
I added the DWMX 2004 install application using the
"add application" button.
I set the "windows version:" to Windows XP
I applied changes, and saw the DWMX 2004 install was now listed.
I clicked OK.
Nothing happened after that, so I went to the CDROm drive and selected
the DWMX 2004 install exe and opened it.
The DWMX splash appeared with the option to install DWMX 2004.
I clicked 'install'
It seemed to be intsalling until I got an error message:

"**An installation support file '%systemDrive%\Program files\Common files\InstallShield\engine\6\Intel 32\corecomp.ini' could not be installed (0x8000ffff)**"

Do I need to create some fake Windows folders and copy the corecomp.ini file from my windows drive with that path?

I'm a little bit lost... Would you help?
Thanks
Rick(shobuz99)

---

### Post by pablo180 on 2008-09-08
Unfortunately I am not sure that I can help, I just got lucky and Dreamweaver just worked. 

The only thing that I can suggest is to try running the install file in the terminal, I seemed to have had more success that way in the past than just right clicking and selecting open in wine. 

You have to open the terminal and then navigate to the cd drive:

```
$ cd /media/cdrom0/
```

Then type in dir to get a list of the files:

```
$ dir
```

Locate the installation file, either setup.exe or install.exe and simply type:

```
$ wine install.exe
```

That should get it installing. If it fails again the only other thing that I can think of is to remove the Dreamweaver installation file from the Applications tab in wine config, I think that you'd only need to do that once the program was installed (and then with the installed Dreamweaver.exe), but I am not sure it will make a difference either way. 

You shouldn't need to create any windows folders or anything, when wine is installed it should do that for you.

---

### Post by Shobuz99 on 2008-09-08
> **pablo180 said:**
> Unfortunately I am not sure that I can help, I just got lucky and Dreamweaver just worked. 

The only thing that I can suggest is to try running the install file in the terminal, I seemed to have had more success that way in the past than just right clicking and selecting open in wine. 

You have to open the terminal and then navigate to the cd drive:

```
$ cd /media/cdrom0/
```

Then type in dir to get a list of the files:

```
$ dir
```

Locate the installation file, either setup.exe or install.exe and simply type:

```
$ wine install.exe
```

That should get it installing. If it fails again the only other thing that I can think of is to remove the Dreamweaver installation file from the Applications tab in wine config, I think that you'd only need to do that once the program was installed (and then with the installed Dreamweaver.exe), but I am not sure it will make a difference either way. 

You shouldn't need to create any windows folders or anything, when wine is installed it should do that for you.

Pablo,
Well..thanks. I appreciate your effort.
I tried what you suggested and it failed. I had to point wine
at the autorun.exe because the "Install Dreamweaver MX.exe" listed on the CD would not work: here's what I tried from Terminal:
[B]
rick@rick-desktop:/media/cdrom$ wine Install Dreamweaver MX.exe
wine: could not load L"C:\\windows\\system32\\Install.exe": Module not found
rick@rick-desktop:/media/cdrom$ wine autorun.exe
rick@rick-desktop:/media/cdrom$ err: ole: marshal_object object doesn't expose interface {be6115a1-7de5-48dc-ad2a-25060e00fce2}, failing with error 0x80004002
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err: ole: ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
[/B]

I guess I'm OOL...unless you have another idea?
Thanks very much for all you have helped so far.
Rick (shobuz99)

---

### Post by ad_267 on 2008-09-08
You need quotation marks around the file name, i.e.:
```
wine "Install Dreamweaver MX.exe"
```

---

### Post by pablo180 on 2008-09-08
> **Shobuz99 said:**
> 
I guess I'm OOL...unless you have another idea?
Thanks very much for all you have helped so far.
Rick (shobuz99)

As ad_267 said you'd need quotes. I also found this thread which may be of use to you -  [HOWTO: Install Dreamweaver MX 2004 on wine]("http://ubuntuforums.org/showthread.php?t=200305") 

Not sure how up to date the information is, but it may help with any errors you have.

---

### Post by Shobuz99 on 2008-09-08
> **ad_267 said:**
> You need quotation marks around the file name, i.e.:
```
wine "Install Dreamweaver MX.exe"
```

You're right. forgot the quotes... duh!:oops:

---

### Post by Shobuz99 on 2008-09-08
> **pablo180 said:**
> As ad_267 said you'd need quotes. I also found this thread which may be of use to you -  [HOWTO: Install Dreamweaver MX 2004 on wine]("http://ubuntuforums.org/showthread.php?t=200305") 

Not sure how up to date the information is, but it may help with any errors you have.

thanks again for some great information.
I didn't try all the ideas on that forum, because
they were a bit dated..
I did try again using quotes, but got no further...same error
It's main downfall is that "InstallShield' pointer crap from windows...

well..I may just give up. I just came home from the hospital,
after a minor procedure, and I'm pretty tired... can't think clearly.

Thanks again for all you have done to help and advise me.
I do appreciate it.
I might just look into some other apps. 
God, I hate Windoze!!!
Rick (shobuz99)

---

### Post by ad_267 on 2008-09-08
Ok well hope you get it sorted out eventually. I've heard Quanta recommended as a Dreamweaver replacement and it's supposed to be pretty good for working with php. There's also Kompozer which is a bit more basic and more for WYSIWYG html stuff. I just use gedit, geany or vim myself though so don't have that much experience with these.

---

