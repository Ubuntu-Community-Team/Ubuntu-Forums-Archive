---
title: "Cannot run apllication beacause it's open"
date: 2007-12-25
forum: Wine
---

### Post by Orfintain on 2007-12-25
I can't run my application in wine because it thinks it's already running ,
I check the task manager in wine and ubuntu and it wasn't i rebooted rechecked reinstalled to no avail, I know there are some open GL issues but that's just graphics right?

 I have Thunderbird installed on both Linux and Wine because I'm trying to get all my old emails back..

---

### Post by Marc Higgins on 2007-12-25
I know this doesn't exactly answer your question but you should be able to just copy your windows thunderbird files into ubuntu & they should just work

1) make sure thunderbird is not running on either the windows or the linux machine.

2) Copy everything from the directory 

C:\Documents and Settings\(THE_USER_NAME)\Application Data\Thunderbird\

(USB drives, cdroms or network shares are good for this)

3) paste everything to the followinf directory 
\home\(THE_USER_NAME)\.thunderbird\

(you may need to make this if you haven't already run thunderbird under ubuntu)

& if everything went well you should be able to just start thunderbird  & have your email up & running on linux, just as it was on windows.

Please let me know if this helps

---

### Post by cogadh on 2007-12-25
Why do you need Thunderbird running in Wine and Linux to get your old emails back? Just copy the e-mail data files from Windows into the Linux client directories, they are in exactly the same format and will just work.

---

### Post by Orfintain on 2007-12-26
I've tried that a couple times and I end up with the can't run application because it's open error in ubuntu after messing with the files (possible incorrectly..),

Generally there is information in both the home\user\app data\thunderbird
, and
home\user\.thunderbird\defaults\
 data directory,

 the {choas}.default, the profiles.ini and regestry dat file too...

I got it working so i have an old thurderbird to look up lost emails when needed
and new linux version getting the new e-mail...

---

