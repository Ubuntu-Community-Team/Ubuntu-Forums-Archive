---
title: "Java pugin-6"
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by Kohl on 2009-03-28
Hi,
I am new user to ubuntu and i cant get my java pugin6 to work on my amd64 and i am n need of help.

thanks,Kohl

---

### Post by Chemical Imbalance on 2009-03-28
If you want to use the sun-java6-plugin, you should uninstall the iceadtea plugin.

---

### Post by Kohl on 2009-03-28
ihave and it still will not load runescape....


o wait i have the icetea but i still cant get the java6 ill unintsall it and see 1 sec

---

### Post by kruegger on 2009-03-28
Open a terminal up

sudo aptitude install package-name

To find out the proper package name

sudo aptitude search java 

and read the output.

---

### Post by Kohl on 2009-03-28
this is what it says about the reg pugin


Sun Java 6.0 Plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.
Canonical does not provide updates for Sun Java 6.0 Plugin. Some updates may be provided by the Ubuntu community.

---

### Post by Kohl on 2009-03-28
wait so,
what is the code that i need to get the java6-pugin?

---

### Post by kruegger on 2009-03-28
Well, it's clear at least.
Won't you try what I told you before?
It might work :).

---

### Post by Chemical Imbalance on 2009-03-28
uninstall the icedtea plugin and install the sun-java6-plugin.


sudo apt-get remove icedtea6-plugin
sudo apt-get install sun-java6-plugin

---

### Post by Kohl on 2009-03-28
kohl@kohl-desktop:~$ sudo apt search java
sudo: apt: command not found
kohl@kohl-desktop:~$ sudo aptitide search java
sudo: aptitide: command not found
kohl@kohl-desktop:~$

---

### Post by Kohl on 2009-03-28
i cant install the java6 i have 64bit...

---

### Post by Chemical Imbalance on 2009-03-28
> **Kohl said:**
> i cant install the java6 i have 64bit...

Are you using Jaunty or Intrepid?  Because I'm on Jaunty 64-bit and it installs fine.

---

### Post by Kohl on 2009-03-28
holy.... 
what am i looking for in the term?

---

### Post by kruegger on 2009-03-28
Are you shaking?.:lolflag:
Write the commands well.

It's aptitude not aptitide

---

### Post by presence1960 on 2009-03-28
for 64bit java plugin try this- it is the most recent version and is quite snappy in performance. BTW I would like to thank Zika for turning me onto this:

[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

---

### Post by Kohl on 2009-03-28
idk what that is but i am an amd64 runing ubuntu

---

### Post by Chemical Imbalance on 2009-03-28
> **Kohl said:**
> idk what that is but i am an amd64 runing ubuntu

post the output of

uname -a

---

### Post by Kohl on 2009-03-28
i am stuip where do i put the code on that page?

---

### Post by Kohl on 2009-03-28
what???

---

### Post by Kohl on 2009-03-28
kohl@kohl-desktop:~$ sudo chmod +x jre-6u14-ea-bin-b01-linux-amd64-03 feb 2009.bin
chmod: cannot access `jre-6u14-ea-bin-b01-linux-amd64-03': No such file or directory
chmod: cannot access `feb': No such file or directory
chmod: cannot access `2009.bin': No such file or directory
kohl@kohl-desktop:~$

---

### Post by kruegger on 2009-03-28
Copy and paste this in a terminal, line by line:

cd /opt/java

wget [http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar](http://www.java.net/download/jdk6/6u14/promoted/b03/binaries/jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar)

java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar


It comes from the post above.
The author says it doesn't always work but it is easier.

---

### Post by Kohl on 2009-03-28
kohl@kohl-desktop:~$ sudo chmod +x jre-6u14-ea-bin-b01-linux-amd64-03 feb 2009.bin
chmod: cannot access `jre-6u14-ea-bin-b01-linux-amd64-03': No such file or directory
chmod: cannot access `feb': No such file or directory
chmod: cannot access `2009.bin': No such file or directory
kohl@kohl-desktop:~$ cd /opt/java
bash: cd: /opt/java: No such file or directory
kohl@kohl-desktop:~$ wget [http://www.java.net/download/jdk6/6u...0_mar_2009.jar](http://www.java.net/download/jdk6/6u...0_mar_2009.jar)
--2009-03-28 20:50:17--  [http://www.java.net/download/jdk6/6u...0_mar_2009.jar](http://www.java.net/download/jdk6/6u...0_mar_2009.jar)
Resolving [www.java.net](www.java.net)... 64.125.132.37, 64.125.132.39
Connecting to [www.java.net|64.125.132.37|:80](www.java.net|64.125.132.37|:80)... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://download.java.net/jdk6/6u...0_mar_2009.jar](http://download.java.net/jdk6/6u...0_mar_2009.jar) [following]
--2009-03-28 20:50:17--  [http://download.java.net/jdk6/6u...0_mar_2009.jar](http://download.java.net/jdk6/6u...0_mar_2009.jar)
Resolving download.java.net... 72.5.124.114
Connecting to download.java.net|72.5.124.114|:80... connected.
HTTP request sent, awaiting response... 404 Not found
2009-03-28 20:50:18 ERROR 404: Not found.

kohl@kohl-desktop:~$ java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
Unable to access jarfile jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
kohl@kohl-desktop:~$ 
kohl@kohl-desktop:~$

---

### Post by Kohl on 2009-03-28
i think i got it...

:(

---

### Post by Kohl on 2009-03-28
nvm what now?


100%[===========================================================>] 20,083,063   123K/s   in 2m 43s  

2009-03-28 20:54:11 (120 KB/s) - `jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin?e=1238291787&h=4335ef1794f62aa60c96d893d0840388' saved [20083063/20083063]

kohl@kohl-desktop:~/Desktop$ sudo chmod +x jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
chmod: cannot access `jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin': No such file or directory
kohl@kohl-desktop:~/Desktop$ sudo chmod +x jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
chmod: cannot access `jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin': No such file or directory
kohl@kohl-desktop:~/Desktop$ :(:(

---

### Post by Kohl on 2009-03-28
i am in need of some remote assistaice....

---

### Post by kruegger on 2009-03-28
Check out the location of the file you downloaded. Should be at your desktop directory. 

You were doing well. Try and find that file. 

If you do, then move to the same directory it is in and 

sudo java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar

(choose /opt/java as install directory when asked)

---

### Post by Kohl on 2009-03-28
omg y so hard??!?!?!?:(:(:(:(

kohl@kohl-desktop:~/Desktop$ java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
Unable to access jarfile jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
kohl@kohl-desktop:~/Desktop$ java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
Unable to access jarfile jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
kohl@kohl-desktop:~/Desktop$ sudo java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
Unable to access jarfile jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
kohl@kohl-desktop:~/Desktop$ sudo java -jar jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
Unable to access jarfile jre-6u14-ea-bin-b03-linux-amd64-10_mar_2009.jar
kohl@kohl-desktop:~/Desktop$

---

### Post by Kohl on 2009-03-28
wait what is a directory....

---

### Post by ahbart on 2009-03-29
Let start again:

download the x64 bin file from this site: [link](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u13-oth-JPR@CDS-CDS_Developer).
Select the: jre-6u13-linux-x64.bin file, and not the rpm. 
and download it to your /home/username (/home/kohl) folder.

open a terminal.
type:
```
chmod +x ./jre-6u13-linux-x64.bin
```
Or change the name to the name of the file you downloaded.

type: ```
sudo ./jre-6u13-linux-x64.bin
```
And follow the directions.

Close firefox and reopen it. Type:
```
about:plugins
```
in the address bar. Do you see the java plugin in the list?
I afraid not, but we go on after you reply.

---

### Post by pac2715 on 2009-03-29
from the java site:
	Linux x64 *  filesize: 18.74 MB 	Instructions
	Linux x64 RPM * filesize: 18.20 MB 	Instructions
* Please use the 32-bit version for Java applet and Java Web Start support. 

is this your problem?

---

### Post by NewDisciple on 2009-03-29
The reason it isn't working for him is because it is downloading as:jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin?=1233etc
By right clicking and select rename, remove everything after bin so that it reads as:jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
then it will work with those commands.

---

### Post by Kohl on 2009-03-29
well when i download something then type in a code its says no such dir/file

---

### Post by NewDisciple on 2009-03-29
It can't read it because of the extra stuff on the name.  If you rename it as in my previous comment then it will be able to read it as /dir/file.

---

### Post by ahbart on 2009-03-29
> **Kohl said:**
> kohl@kohl-desktop:~$ sudo chmod +x jre-6u14-ea-bin-b01-linux-amd64-03 feb 2009.bin
chmod: cannot access `jre-6u14-ea-bin-b01-linux-amd64-03': No such file or directory
chmod: cannot access `feb': No such file or directory
chmod: cannot access `2009.bin': No such file or directory
kohl@kohl-desktop:~$

Kohl, Now I see what is going wrong here. Try:
```
sudo chmod +x "jre-6u14-ea-bin-b01-linux-amd64-03 feb 2009.bin"
```
There are spaces between the 3 feb and 2009.bin. Strange.

---

### Post by Kohl on 2009-03-29
This is what happens [http://img525.imageshack.us/my.php?image=screenshotytq.png](http://img525.imageshack.us/my.php?image=screenshotytq.png) idk if can see it but the file is in the right corner of home/kohl and it cant find the file or dir...:confused::confused:

---

### Post by Kohl on 2009-03-29
kohl@kohl-desktop:~$ su
Password: 
root@kohl-desktop:/home/kohl# chmod +x ./jre-6u13-linux-x64.bin
chmod: cannot access `./jre-6u13-linux-x64.bin': No such file or directory
root@kohl-desktop:/home/kohl# sudo chmod +x "jre-6u14-ea-bin-b01-linux-amd64-03 feb 2009.bin"
chmod: cannot access `jre-6u14-ea-bin-b01-linux-amd64-03 feb 2009.bin': No such file or directory
root@kohl-desktop:/home/kohl# 



How about this i going to detle all the java files i have then lets start over....

---

### Post by Kohl on 2009-03-29
Can 1 of you remotely view my desktop and help me?

---

### Post by SuperSonic4 on 2009-03-29
[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/) 

^ worked perfectly for me

---

### Post by ahbart on 2009-03-29
This screenshot helps a bit. There is a sub-directory with the name: 
jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
try:
```
cd jre-6u14-ea-bin-b01-linux-amd64-03_feb_2009.bin
```
and then:
```
chmod +x ./jre-6u13-linux-x64.bin
```
and then
```
sudo ./jre-6u13-linux-x64.bin
```

---

### Post by Kohl on 2009-03-29
Why does it all ways come up as a white page that i cant open??(the jre download)

---

### Post by NewDisciple on 2009-03-29
The other problem I just noticed is your command path.  At the commandline ~$ will be your home.  If you wget to home you don,t need to cd ~/desktop.  You cd ~desktop to wget (download there). In your terminal you wrote ~$Desktop: cd /home (or something like that) it won't work that way.  
 It looks like you are trying to use two separate sets of instructions at the same time.
Copy and paste the instructions that way you will avoid all of the commandline errors you have.

---

### Post by Kohl on 2009-03-29
Can someone go to here:[http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)
and open with wine download it then connect to me

Ip:247 138 479
after that it will ask for a password my is
Password:2595

---

### Post by ahbart on 2009-03-29
> **NewDisciple said:**
> The other problem I just noticed is your command path.  At the commandline ~$ will be your home.  If you wget to home you don,t need to cd ~/desktop.  You cd ~desktop to wget (download there). In your terminal you wrote ~$Desktop: cd /home (or something like that) it won't work that way.  
 It looks like you are trying to use two separate sets of instructions at the same time.
Copy and paste the instructions that way you will avoid all of the commandline errors you have.
Good point.
You can paste in the terminal with a right click of your mouse, or by pressing [shift]+[Ins]

---

### Post by Kohl on 2009-03-29
anbart,
Can you post a thing i can follow to make this work??

---

### Post by Kohl on 2009-03-29
I did all the stuff you told me on page 3 and the plugin is not there...

---

### Post by Chemical Imbalance on 2009-03-29
Hey Kohl, please don't post your IP and password on a public forum.  Google caches everything to be available in searches.  Everybody on the internet now knows your password.  I suggest you change it and only PM people you really trust to remotely view your desktop.

---

### Post by ahbart on 2009-03-29
> **Chemical Imbalance said:**
> Hey Kohl, please don't post your IP and password on a public forum.  Google caches everything to be available in searches.  Everybody on the internet now knows your password.  I suggest you change it and only PM people you really trust to remotely view your desktop.
It's an ID, not a IP. ;) Typo I think.

---

### Post by ahbart on 2009-03-29
Kohl, I'd like to give Teamviewer a try if you want.

---

### Post by Kohl on 2009-03-29
lol ty guys but i got it to work so 


[SIZE="7"][/SIZE]CASE CLOSED

---

