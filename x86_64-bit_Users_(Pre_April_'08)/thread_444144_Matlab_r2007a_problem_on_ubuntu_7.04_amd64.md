---
title: "Matlab r2007a problem on ubuntu 7.04 amd64"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by uri hertz on 2007-05-15
hello!!

I am trying to install MATLAB(R2007a) Unix edition on my Ubuntu 7.04 AMD64.

Problem Symptoms:
After installation, when running matlab from terminal, it seems fine but the entire set of toolbars/menu bars above the command window (FILE, EDIT, etc... as well as the shortcuts below
them) seems to be missing and the little START button in the bottom left corner is missing as
well. When trying to randomly click on them the buttons response, so it just a display problem.

Another symptom:
Opening the editor or the help docs actually opens the editor/ help doc but there is a big grey blank space where one should be able to type/read instructions....

do you have any suggestions?

---

### Post by uri hertz on 2007-05-19
the display came back when i stopped the "Desktop Effect". now i know that the problem was with the display properties... 
does anyone has a solution on how to make them both live happily together?

---

### Post by Cappy on 2007-05-19
```
gedit ~/.beryl/settings
```

Change "s_legacy_maximize_fix=false" to "s_legacy_maximize_fix=true"
I've used that with a horrible Java IDE called JGrasp.

---

### Post by monoufo on 2007-07-10
the suggested solution did not help for me.  Anyone have any other ideas?  I'm not using 64bit, but that doesn't seem to matter for this problem.  I can live with temporarily disabling beryl while using MATLAB, but a better fix would be appreciated for the long term.

---

### Post by carpex on 2007-07-26
I have the same problem on the same platform and with Compiz Fusion. Hope we can find a fix for this.

CP

---

### Post by theicyj on 2007-08-18
I found a fix as Hordan suggests here: [https://bugs.launchpad.net/ubuntu/+bug/120342](https://bugs.launchpad.net/ubuntu/+bug/120342) . 

1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste  "export AWT_TOOLKIT=MToolkit"  into the first line of the file.
3. Save the file.

Easy fix.  Worked great for me.

---

### Post by kolibri on 2007-08-21
> **theicyj said:**
> I found a fix as Hordan suggests here: [https://bugs.launchpad.net/ubuntu/+bug/120342](https://bugs.launchpad.net/ubuntu/+bug/120342) . 

1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste  "export AWT_TOOLKIT=MToolkit"  into the first line of the file.
3. Save the file.

Easy fix.  Worked great for me.

When you say first line ,which line do you mean?  The first uncommented line my file is:
f [ "$OS" = "Windows_NT" ]; then

Running export AWT_TOOLKIT=MToolki in the terminal before opening matlab didn't work for me,  I have no toolbar and blank help  screens in Matlab (this is after restarting after turning off desktop effects and beryl.

---

### Post by kolibri on 2007-08-21
Okay, so I plugged in that line to the file before the first line, and now Matlab looks okay and seems to run.

Could someone explain to me what I just did?  Sorry to be so needy.

---

### Post by carpex on 2007-08-27
This doesn't work for me. I get :

 Failed to start the Desktop: Failure loading desktop class

and Matlab won't open

CP

---

### Post by marko_4454 on 2007-08-30
> **theicyj said:**
> I found a fix as Hordan suggests here: [https://bugs.launchpad.net/ubuntu/+bug/120342](https://bugs.launchpad.net/ubuntu/+bug/120342) . 

1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste  "export AWT_TOOLKIT=MToolkit"  into the first line of the file.
3. Save the file.

Easy fix.  Worked great for me.

Thanks for posting this, it worked perfectly.
I can run matlab :)

---

### Post by tvst on 2007-09-04
FYI: if you don't have admin privileges you can "export AWT_TOOLKIT=MToolkit" from your ~/.bashrc

---

### Post by jw5801 on 2007-09-27
This solution doesn't work for me, I get the same error that was mentioned earlier in the thread,```
$ export AWT_TOOLKIT=MToolkit
$ matlab
 Failed to start the Desktop: Failure loading desktop class
```If anyone has a more general solution to the issue, I would be very intrigued! I have a few Java apps that I would like to run, so a solution on the java side of things rather than application specific, would be nice. I would try the beryl settings suggestion, but since I'm using Compiz-Fusion rather than beryl I'm not sure where the equivalent settings file would be. I've had a look around but I can't seem to see it.
Also, from what I've read this is apparently more of a Java issue than a Compiz issue and should be fixed in the latest Java version, but since I'm already using sun-java6, I'm not quite sure where to get a newer version from.

---

### Post by 00l0 on 2007-09-28
> **theicyj said:**
> I found a fix as Hordan suggests here: [https://bugs.launchpad.net/ubuntu/+bug/120342](https://bugs.launchpad.net/ubuntu/+bug/120342) . 

1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste  "export AWT_TOOLKIT=MToolkit"  into the first line of the file.
3. Save the file.

Easy fix.  Worked great for me.

THANK YOU!

working fine with compiz fusion and all   ;D

---

### Post by karel.007 on 2007-10-06
Hello,

I experienced the same kind of problem you describe. The solution is very simple: rename folder motif21 to motif12 similar to this

sudo mv /usr/local/matlab701/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif21/ /usr/local/matlab701/sys/java/jre/glnxa64/jre1.5.0/lib/amd64/motif12

then do the trick with export and it should work :-)

---

### Post by jw5801 on 2007-10-06
Success! No idea why that works... but karel's suggestion is a good one!

---

### Post by rajesh0975 on 2007-10-31
thanx. "export AWT_TOOLKIT=MToolkit" worked for me. I can now run Matlab with desktop effects ON..

---

### Post by uri hertz on 2007-11-26
thanks all!!
i renamed my folder as suggested and it seems to work!
i can finally use desktop effect (i turned it off because i use matlab a lot...)
\\:D/

---

### Post by rambomedic on 2007-11-28
Actually, I just found the Desktop drop down menu and selected:

Desktop Layout > Default

Became mint afterwards. Always good for a simple fix.

Actually, funnily enough it only works if you do that above fix.

Well, actually, I lied, I don't know what that worked...

---

### Post by neurostu on 2008-02-29
When I installed matlab on ubuntu gutsy gibbon my toolbar and start button were missing. Thanks to this post I was able to fix them. Thanks!


> 1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste "export AWT_TOOLKIT=MToolkit" into the first line of the file.
3. Save the file.

Also something else I had to do not sure was set the MATLAB_JRE variable which I did by:
```

$MATLAB_JRE=/usr/lib/jvm/java-6.0-sun/jre

```
where /usr/lib/jvm/java-6.0-sun/jre was the pathway to the jre dir, yours might be different

---

### Post by Balk2K on 2008-03-05
The export trick worked for me, I wonder why now it only works from the terminal.
When I use a launcher to run 'matlab' it shows the splash screen and then exits.
When you type 'matlab' in the terminal it works.
***Update*** I found a thread about it: [http://ubuntuforums.org/showthread.php?t=548947]("http://ubuntuforums.org/showthread.php?t=548947")

---

### Post by Bungler on 2008-03-05
Like I said in a different topic:

--------------------------------------------------------------------------------

I had the same problem, but I found a different solution on the net:

Matlab uses its own JRE to viualize the menu's. However you can also use JRE from your own specified place. You have to have JRE installed of course. I have version 1.6 installed and in this version Matlab works fine.

You can just add an export command referring to you JRE environment in the matlab.sh file.
You should specify the folder which contains the file "rt.jar", but than one folder level up. So in my case the "rt.jar" file is in the folder:

/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib, so I have to use:

/usr/lib/jvm/java-6-sun-1.6.0.03/jre

The command to be added on the first uncommented line becomes (in my case):

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre


good luck!

---

### Post by uri hertz on 2008-03-08
thanks!!!

this is what i have been looking for. i used the other methods just fine, but this solution seems to really solve the problem!

:guitar:

---

### Post by mahbub.red_devil on 2008-03-25
hi, i've tried that process

 1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste "export AWT_TOOLKIT=MToolkit" into the first line of the file.
3. Save the file. 

but when i run MATLAB, it shows me "Segmentation fault (core dumped)" message.

i am using the beta version of the new Ubuntu. please help me...

---

### Post by ashu9uf on 2008-04-29
> **theicyj said:**
> I found a fix as Hordan suggests here: [https://bugs.launchpad.net/ubuntu/+bug/120342](https://bugs.launchpad.net/ubuntu/+bug/120342) . 

1. Open the executable Matlab script, ~/matlab/bin/matlab in gedit.
2. Copy and paste  "export AWT_TOOLKIT=MToolkit"  into the first line of the file.
3. Save the file.

Easy fix.  Worked great for me.

I installed 2007b on Ubuntu 7.10, and it would show only the start button/menu and nothing else. Adding this line fixed it.

Thanks.

---

