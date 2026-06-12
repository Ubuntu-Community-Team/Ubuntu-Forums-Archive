---
title: "[SOLVED] pdf-cups failed"
date: 2008-12-05
forum: x86 64-bit Users
---

### Post by woelf on 2008-12-05
8.10 Intrepid Ibex 64bit

I install cups-pdf ( sudo apt-get install cups-pdf ) but wen I want to print a pdf nothing happens. 
All I get is /usr/lib/cups/backend/cups-pdf failed

---

### Post by Thelasko on 2008-12-05
> **woelf said:**
> All I get is /usr/lib/cups/backend/cups-pdf failed

Where do you see this message?

Are you aware that cups-pdf simply puts the file in /home/pdf  without a prompt?

---

### Post by woelf on 2008-12-06
here

---

### Post by Thelasko on 2008-12-08
This problem is a new one to me.  I'll give this a bump and maybe someone else will have the answer.

---

### Post by Aearenda on 2008-12-12
I have just discovered that manually creating the PDF folder in your home directory allows cups-pdf to work on 8.10.

---

### Post by woelf on 2008-12-12
thanks it works

---

### Post by mikehenson on 2009-01-14
I found that the configure file was creating PDFs in the home directory. Which was giving me the pdf-cups failed error.

Find this section in the /etc/cups/cups-pdf.conf
The ${HOME} and ${USER} were not working for me.

### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out /home/username/PDF

---

### Post by haritia on 2009-01-16
Is there any way to make it so that it prompts for a location (and a filename would be cool too) everytime I print?

---

### Post by kaibob on 2009-01-23
> **haritia said:**
> Is there any way to make it so that it prompts for a location (and a filename would be cool too) everytime I print?
The best way to do what you want is to use the print-to-file option. But, you can configure cups-pdf to prompt for a file name as follows: 

1) Create a script similar to the sample script below and place it in a folder in your path (~/bin is good). 

2) Open the file /etc/apparmor.d/usr.sbin.cupsd in a text editor and add the path to the script at the end of this file just before the final } symbol. After the path append uxr,. An example is:

> /home/kaibob/bin/cupscript.sh uxr,

3) Open the file /etc/cups/cups-pdf.conf in a text editor, remove the # symbol before the line that begins with postprocesssing, and add the path to the script after postprocessing. An example is:

> PostProcessing /home/kaibob/bin/cupscript.sh 

4) Restart apparmor (ignore warning messages):

> sudo /etc/init.d/apparmor restart 

5) Restart your computer (seems to be necessary).

The sample script contained below works but is intentionally barebones--you will want to gussy it up a bit to fit your needs. Also, be sure to back up all files before editing them. 

SAMPLE SCRIPT 
> #!/bin/bash
CURRENT_PDF="${1}"
CURRENT_USER="${2}"
DISPLAY=:0.0
export DISPLAY
XAUTHORITY=/home/${CURRENT_USER}/.Xauthority
export XAUTHORITY
PDFNAME=$(zenity --file-selection --save --confirm-overwrite)
mv "$CURRENT_PDF" "$PDFNAME"

SOURCES - CREDIT
[http://ubuntuforums.org/showthread.php?t=750426](http://ubuntuforums.org/showthread.php?t=750426)
[http://ubuntuforums.org/showthread.php?t=837257](http://ubuntuforums.org/showthread.php?t=837257)

---

### Post by LAKOSWOLF on 2009-05-02
> **Aearenda said:**
> I have just discovered that manually creating the PDF folder in your home directory allows cups-pdf to work on 8.10.

Just thought I'd say this also works for Jaunty Jackalope 32bit, I would imagine it would also work with the 64bit version.

Thanks for such a simple solution!

---

### Post by zeppomanx on 2009-06-30
opening a terminal and typing 

sudo aa-complain cupsd

solved this problem for me.

---

### Post by cirorodrigues on 2009-07-10
> **woelf said:**
> thanks it works

it works for me also. Thanks. :p

---

### Post by litster on 2009-07-24
> **Aearenda said:**
> I have just discovered that manually creating the PDF folder in your home directory allows cups-pdf to work on 8.10.

I would say that this is a BUG. ;) (but who do i submit to, ubuntu, or the cups people?)

This should really be fixed in a "backport" and added to the package (mkdir /home/*/PDF)

Either that, or cups-pdf should check to see if /home/<user>/PDF exists and create the directory if it doesn't, both on printing test pages and printing for real.

The current behavior is very unintuitive.

It is broken in both Hardy and Jaunty, BTW.

---

### Post by Aearenda on 2009-07-24
If you have some spare time, read [this bug]("https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/147551").

---

### Post by robertj20112 on 2009-08-30
> **zeppomanx said:**
> opening a terminal and typing 

sudo aa-complain cupsd

solved this problem for me.

And it solved it for me, too, though I sure don't understand how it worked!

Many thanks.

---

### Post by Boynas on 2009-09-03
complain mode worked for me too.

---

### Post by kickwin on 2009-09-03
Just curious. Is this cups-pdf better for printing PDFs than Print to File --> PDF option? Is yes, how? Thanks!

---

