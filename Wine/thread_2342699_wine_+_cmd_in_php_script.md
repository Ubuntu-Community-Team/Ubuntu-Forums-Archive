---
title: "wine + cmd in php script"
date: 2016-11-09
forum: Wine
---

### Post by tarvids on 2016-11-09
[SIZE=2]Hello.
 I am installing wine in ubuntu and I want run cmd command through php script with exec().
For testing, terminal command is "mkdir /home/$USERNAME/.wine/dosdevices/c:/test_folder 2>&1" (2>&1 - show me errors after executing command)
I run script in php: echo exec("mkdir /home/$USERNAME/.wine/dosdevices/c:/test_folder 2>&1");
But there is something wrong with folders permissions, script shows me following:[/SIZE]
[FONT=Helvetica Neue]
[/FONT][SIZE=3][FONT=arial]mkdir: cannot create directory '/home/$USERNAME/.wine/dosdevices/c:/test_folder': Permission denied[/FONT][/SIZE][FONT=Helvetica Neue]

[SIZE=2][FONT=arial]but if i run this command from terminal, it successfully create [/FONT][/SIZE][/FONT][SIZE=2][FONT=arial]test_folder[/FONT]
AND 
[FONT=arial]if i run: echo exec("mkdir test_folder 2>&1"); through php script, it successfully create test_folder "/var/www/MY_PROJECT_NAME/public/test_folder"[/FONT][/SIZE]

Some notes:
I am using nginx.
All programs installed under 2nd created user (non-root user).
.wine folder located in /home/$MY_USERNAME

Please help.

---

### Post by howefield on 2016-11-09
Thread moved to the "*Wine*" forum.

---

