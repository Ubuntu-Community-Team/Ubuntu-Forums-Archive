---
title: "Please help me to install nvidia drivers !"
date: 2008-10-29
forum: x86 64-bit Users
---

### Post by rcmadawala on 2008-10-29
hi guys,

I am totally new to ubuntu and got free cd today via post.i already using windows vista and my nvidia 8500GT is working perfectly with it.so i installed ubuntu 8.04 "in windows".Then i tried to install nvidia drivers from typing this in terminal window.

"sudo apt-get install envyng-gtk"

Then i got following lines in terminal window.

Readig package lists....Done
Bulding dependency tree
Reading state information...Done
E: Couldn;t find package envyng-gtk

So i downloaded envyng-gtk.deb file from ubuntu web site and paste it to my E: Drive ad tried to install again.(i installed ubuntu in E: drive).But i still have same problem.the terminal window showing same lines as above mentioned.Pls Help Me ! :confused:

---

### Post by Nepherte on 2008-10-29
The reason why it doesn't find envyng-gtk is because you probably haven't enabled the necessary repository. You will have to enable the universe repository in system > administration > software repositories or something alike.

When you try to use "sudo apt-get install envyng-gtk" after you downloaded the deb file already, it will still attempt to download it from the repository. Just double click the .deb file and you should be set. Another way is:
```
sudo dpkg -i /path/to/debfile
```

---

### Post by rcmadawala on 2008-10-29
i double clicked that .deb file and then package installer shows this error.

[COLOR="Red"]"Error: Dependency is not satisfiable: envyng-core"[/COLOR]

PLS HELP ME !

---

### Post by grondinmf on 2008-10-29
try it this way it worked great for me...go to the nvidia site and download theire latest driver and the xconfig util. place them anywhere then open a terminal and change into the folder where you placed the files and follow instructions quoted on post 14 then post 16.pm me if you need help i should be able to help you with this...

[http://ubuntuforums.org/showthread.php?t=944503&page=2](http://ubuntuforums.org/showthread.php?t=944503&page=2)

---

### Post by rcmadawala on 2008-10-29
I downloaded NVIDIA-Linux-x86_64-177.80-pkg2.run file and nvidia-xconfig-1.0.tar.gz file.Then i put them in to the G: Partition from vista.after that i reboot to the ubuntu and double clicked the .run file in terminal.In there i got following error.

[COLOR="Red"]"Error:- nvidia - installer must be run as root"[/COLOR]

PLS HELP ME !

---

### Post by Nepherte on 2008-10-29
Did you try to enable the repository as I told you?

Forget about the drivers on the nvidia site for now, it will only complicate things for you.

---

### Post by Spinalcracker on 2008-10-29
There are two ways to do this.  The first method is much easier.

**_Method 1._**

-Go to System->Administration->Software Sources

-Enter your root password if you are prompted

-Check the boxes next to “Community-maintained Open Source software (universe)” and “Software restricted by copyright or legal issues (multiverse)”

-Click on close 

-A dialog will prompt you to reload the package information. Click the “reload” button.

Now to install the drivers

-Open System->Administration->Synaptic Package Manager

-Search for nvidia-glx-new and install it

-Once installed close all windows and press Ctrl-Alt-Backspace and log back in.  Should be good to go.  

*If it is not working go to System > Administration > Restricted Drivers Manager and make sure Nvidia Drivers are checked.  If not check them and restart.


**_Method 2._**

-Download the driver from Nvidia's website

-Press ctrl-alt-F1, a text login screen will appear

-Login

-Type "sudo /etc/init.d/gdm stop" without the quotes and hit enter

-move to the directory you saved the driver file to using "cd" command.  ie  cd /tmp  if you had of saved it to the /tmp folder

-type "sudo sh NVIDIA....pkg.run" without quotes and using the full name of the driver and hit enter

-say yes to all the prompts

-once you return to the command prompt type "sudo /etc/init.d/gdm start" without the quotes and hit enter

You should now be good to go.  This method allows you to download beta drivers etc, but be warned!!!  Any time there is a kernel update the driver will have to be reloaded and if you are unsure of what to do when Ubuntu fails to boot to a gui, it may not be a good option for you.

Good luck :)

---

### Post by felker2 on 2008-10-30
Ubuntu will automatically take care of installing the proprietary Nvidia drivers. All via standard procedures and repositories. A blue icon will popup in the right upper corner of your screen, proposing to install the proprietary driver.

I myself would not play with external sources.

---

### Post by 080818jk on 2008-10-30
&#31532;&#19977;&#27493;&#65306;&#26159;&#21542;&#35201;&#26377;&#22812;&#35270;&#21151;&#33021; &#22312;&#36208;&#24266;&#12289;[**&#30417;&#25511;**](http://www.wcon.net/jk.htm)&#38376;&#21381;&#12289;&#36807;&#36947;&#12289;&#24211;&#25151;&#31561;&#20809;&#32447;&#27604;&#36739;&#26263;&#30340;&#22320;&#26041;&#65292;&#21487;&#20197;&#32771;&#34385;&#32418;&#22806;&#22812;&#35270;&#21151;&#33021;&#30340;&#25668;&#20687;&#26426;[**&#30417;&#25511;**](http://www.wcon.net/jk.htm)&#65292;&#38656;&#35201;&#27880;&#24847;&#30340;&#26159;&#65292;&#32418;&#22806;&#25668;&#20687;&#26426;&#38500;&#19987;&#19994;&#22812;&#35270;&#25110;&#29305;&#21035;&#35746;&#21046;&#20197;&#22806;&#65292;[**&#30417;&#25511;**](http://www.wcon.net/jk.htm)&#32418;&#22806;&#25668;&#20687;&#26426;&#20063;&#38656;&#35201;&#29616;&#22330;&#26377;&#28783;&#20809;&#36741;&#21161;&#20116;&#25351;&#30340;&#26465;&#20214;&#19979;&#65292;&#32418;&#22806;&#36317;&#31163;&#20250;&#25104;&#20493;&#32553;&#30701;&#12290;&#29616;&#22330;&#22914;&#26524;&#20026;&#33457;&#22253;&#33609;&#22378;&#65292;&#32418;&#22806;&#25928;&#26524;&#26356;&#24046;&#12290;     &#31532;&#22235;&#27493;&#65306;&#26159;&#24067;&#32447;&#36824;&#26159;&#37319;&#29992;&#26080;&#32447; &#38500;&#20102;&#26114;&#36149;&#30340;&#20215;&#26684;&#20197;&#22806;&#65292;[**&#30417;&#25511;**](http://www.wcon.net/jk.htm)&#26080;&#32447;&#32593;&#32476;&#30830;&#23454;&#30465;&#21435;&#25668;&#20687;&#26426;&#24067;&#32447;&#30340;&#40635;&#28902;&#19982;&#19981;&#32654;&#35266;&#65292;[**&#30417;&#25511;**](http://www.wcon.net/jk.htm)&#20294;&#38656;&#35201;&#27880;&#24847;&#30417;&#25511;&#36317;&#31163;&#19982;&#38556;&#30861;&#30340;&#38382;&#39064;&#12290;&#21407;&#21017;&#19978;&#27700;&#27877;&#24314;&#26448;&#20250;&#32553;&#30701;&#26080;&#32447;&#30340;&#20256;&#36865;&#36317;&#31163;&#65292;,&#37329;&#23646;&#26448;&#26009;&#21017;&#20250;&#23436;&#20840;&#36974;&#34109;&#26080;&#32447;&#35759;&#21495;&#65292;&#21457;&#23556;&#22120;(&#22312;&#25668;&#20687;&#26426;&#31471;)&#19982;&#25509;&#25910;&#22120;(&#22312;&#20027;&#26426;&#31471;)&#35201;&#36828;&#31163;&#20854;&#20182;&#30340;&#30005;&#22120;&#20197;&#36991;&#20813;&#24178;&#25200;&#65292;&#22914;&#35201;&#37319;&#29992;&#26080;&#32447;&#32593;&#32476;,&#23601;&#35201;&#26377;&#36127;&#25285;2&#20493;&#20197;&#19978;&#20215;&#26684;&#30340;&#20934;&#22791;&#12290;&#25105;&#20204;&#24314;&#35758;&#38500;&#38750;&#24517;&#35201;&#65292;&#23613;&#37327;&#20351;&#29992;&#26377;&#32447;&#20256;&#36755;

---

### Post by philinux on 2008-10-30
System>Admin>Hardware Drivers.

---

### Post by rcmadawala on 2008-10-30
I Tried to add downloaded nvidia driver package from "synaptic package Manager".i clicked on "add downloaded packages" and browsed to nvidia package file.but i cant select the package(it showen the file like disabled).

i tried system->administration->hardware drivers.in there it shown,

nvidia_new         enabled([COLOR="Blue"]cheked[/COLOR])        ([COLOR="Red"]a red mark[/COLOR])not in use

PLS HELP ME GUYS !

---

### Post by rcmadawala on 2008-10-30
hey, any one there?

---

