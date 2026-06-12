---
title: "Adobe Reader 8.1"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-10-09
Has anyone gotten it working on 64-bit Ubuntu?

Problem: It seems to require a complete installation of 32-bit Firefox (which I decline to do). Is there a workaround?

---

### Post by Bliepo32 on 2007-10-09
As far as I know, Ubuntu already contains a PDF reader. You could just use that one. If you really need Adobe Reader 8.1, you could try [WINE]("http://www.winehq.org/"). You could also read [HOWTO: Seamless MS Windows in Edgy with VirtualBox and Beryl!]("http://ubuntuforums.org/showthread.php?t=433359")

---

### Post by John Jason Jordan on 2007-10-09
> **Bliepo32 said:**
> As far as I know, Ubuntu already contains a PDF reader. You could just use that one. If you really need Adobe Reader 8.1, you could try [WINE]("http://www.winehq.org/"). You could also read [HOWTO: Seamless MS Windows in Edgy with VirtualBox and Beryl!]("http://ubuntuforums.org/showthread.php?t=433359")
Thanks for the observations. I do a lot of desktop publishing and the various open source PDF viewers all lack features that I need. I have been using Adobe Reader 7.0.9 and may be stuck with that if I can't get 8.1 to work.

Regarding WINE, you can't even get Adobe Reader 7.0.9 to run in WINE. I have Crossover Office, and it can't do it either. As for Virtualbox, I have that running on another computer and I do have the Windows version of 8.1 installed on it. However, I also need Adobe Reader on my laptop, where I can't spare the disk space for Virtualbox and Windows.

The problem with 8.1 on Feisty amd64 is that it requires a full install of 32-bit Firefox. The reason is that it has a new feature where you can conference with clients to get design approval over the internet, and so Adobe Reader 8.1 requires the libgtkembedmoz.so library and the rest of the 32-bit html libraries. As an alternative to 32-bit Firefox you can install 32-bit xulrunner. Unfortunately, I don't want 32-bit Firefox and I can't figure out how to install 32-bit xulrunner or where to get it.

If you want to print from it you won't be able to see all the printers you have installed in CUPS either, unless you install a bunch of 32-bit CUPS libraries. That is less of a concern to me because I think I know where I can get the list of 32-bit libraries and how to make Adobe Reader 8.1 see them. And failing that, I can send a print job through kprinter. It's the html rendering libraries that are the stumbling block.

---

### Post by stmiller on 2007-10-09
I just installed my own Firefox from mozilla.com, and ran the installer. It installs in /usr/local/firefox away from any system or ubuntu stuff. Then 32bit flash installs automatically, and you have Acrobat if you need that too.

To print from a 32bit Firefox (or any 32bit program) in 64bit, you can use the app called gtk-lp. (sudo apt-get install gtklp).

Then just have the 32bit Firefox print to "/usr/bin/gtklp" as a print command in the print dialog (you can even set this as the default printer action in Firefox), and it will launch gtklp with print options to print to your printer. No need for 32bit cups.

---

### Post by stmiller on 2007-10-09
BTW: if you don't need Reader 8.1 in your browser, you can just install the stand alone app and run it when you need to.

Download the .tar.gz version, extract the contents, then start the installer with
```

sudo linux32 ./INSTALL

```

Have it print to gtklp to print. :KS

---

### Post by John Jason Jordan on 2007-10-10
> **stmiller said:**
> I just installed my own Firefox from mozilla.com, and ran the installer. It installs in /usr/local/firefox away from any system or ubuntu stuff. Then 32bit flash installs automatically, and you have Acrobat if you need that too.

To print from a 32bit Firefox (or any 32bit program) in 64bit, you can use the app called gtk-lp. (sudo apt-get install gtklp).

Then just have the 32bit Firefox print to "/usr/bin/gtklp" as a print command in the print dialog (you can even set this as the default printer action in Firefox), and it will launch gtklp with print options to print to your printer. No need for 32bit cups.
I don't need to install Firefox from mozilla.com. I have Firefox already installed and it runs fine and I don't want to change it. I will go back to Reader 7.0.9 before I will go to a 32-bit version of Firefox.
As for printing, I have no problems because all my apps are 64-bit apps, that is, except Reader. I have tried gtklp, but kprinter works better.

All I need to do is figure out how to install 32-bit xulrunner. I suppose the procedure would be dpkg -i --force-architecture *.deb, but I can't find the 32-bit .deb.

---

### Post by Kilz on 2007-10-10
Since you dont want the work around of a 32bit firefox, or dont want to use one of the fine native pdf readers (pdfedit kicks),  just live with an old acrobat. Even if you could get the 32bit xlrunner working you still will have printing dificulties as the 32bit xlrunner wont be able to use the 64 bit cups.

---

### Post by stmiller on 2007-10-10
> **John Jason Jordan said:**
> I don't need to install Firefox from mozilla.com. I have Firefox already installed and it runs fine and I don't want to change it. I will go back to Reader 7.0.9 before I will go to a 32-bit version of Firefox.


You can have both 32bit and 64bit Firefox at the same time. They do not conflict. So just install the 32bit, never use it, and leave it alone. Reader 8.1.1 will be happy, and you can continue using 64bit Firefox as normal.

And: gtklp is not the same thing as kprinter. :)

---

### Post by John Jason Jordan on 2007-10-10
> **Kilz said:**
> Since you dont want the work around of a 32bit firefox, or dont want to use one of the fine native pdf readers (pdfedit kicks),  just live with an old acrobat. Even if you could get the 32bit xlrunner working you still will have printing dificulties as the 32bit xlrunner wont be able to use the 64 bit cups.
I solved the problem. The confusion was the instructions from Adobe. You don't need to install 32-bit Firefox, although that is an option. Instead you can install xulrunner, but not the one in Synaptic. In fact, you don't need to install it as an application at all. All you need are the files which you can obtain from here:

[HTML]http://releases.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.1.3/contrib/linux-i686/[/HTML]

Untar it, which will create an xulrunner folder wherever you point Archive Manager to, then in Reader 8.1 go to Edit > Preferences and enter this folder in the box on the bottom.

The confusion is that the file ends in -686, which makes everyone think it is 64-bit, plus when you untar it there is no .deb file inside. The Adobe instructions say to "install" it, but you can't do that. Once you figure out that Adobe meant "untar" it works.

Having said that, Acrobat Connect doesn't work with 64-bit browsers and you can't start a meeting. But I have no need of that feature anyway. I will add another post for how to fix the printing problem.

---

### Post by John Jason Jordan on 2007-10-10
OK, here is how to fix printing with Adobe Reader 8.1 on 64-bit Ubuntu. The problem is that Feisty does not install certain 32-bit CUPS libraries, so here is what you need to do:

First, download the following libraries, being sure to pick the 386 versions:
[HTML]http://packages.ubuntu.com/feisty/libs/libcupsys2[/HTML]
[HTML]http://packages.ubuntu.com/feisty/libs/libgnutls13[/HTML]
[HTML]http://packages.ubuntu.com/feisty/libs/libgcrypt11[/HTML]
[HTML]http://packages.ubuntu.com/feisty/libs/libgpg-error0[/HTML]
[HTML]http://packages.ubuntu.com/feisty/libs/liblzo1[/HTML]
[HTML]http://packages.ubuntu.com/feisty/libs/libopencdk8[/HTML]
[HTML]http://packages.ubuntu.com/feisty/libs/libtasn1-3[/HTML]

I have Firefox set to download everything to ~/Desktop, so that's where they all ended up. Now make a folder to extract these into. I made one at ~/Desktop/Adobe-CUPS

mkdir ~/Desktop/Adobe-CUPS

Next, extract each of the above libraries to the folder you just created using:

dpkg -x ~/Desktop/name-of-i386.deb-file ~/Desktop/Adobe-CUPS

There's probably a more efficient way to run that command instead of doing it over seven times, but I'm dumb and it's faster just to do it seven times than to take the time to learn a new command line trick.

Now you have to change the permissions on libcups.so.2

chmod +x ~Desktop/Adobe-CUPS/usr/lib/libcups.so.2

And finally, before launching reader you have to run the following command:

export LD_LIBRARY_PATH=~/Desktop/Adobe-CUPS/usr/lib:/usr/lib:$LD_LIBRARY_PATH

I have Reader 8.1 installed in /home/jjj/software/Adobe/Reader8/bin/acroread, so that is the command I use to launch it. When it comes up and I open a PDF file in it, I can open the print dialog box and all the printers I have installed in CUPS are there in the drop-down box the same as for any other application.

I hope someone tests this to make sure my instructions work, 'cause I did a lot of copying and pasting from Adobe e-mails and my terminal window and I may have missed a step.

---

### Post by John Jason Jordan on 2007-10-10
And one final finishing touch: To make it all work without having to run the EXPORT command from a terminal before launching acroread I made the following little script:

#!/bin/bash
# Run this script to launch Adobe Reader 8.1
export LD_LIBRARY_PATH=~/Desktop/Adobe-CUPS/usr/lib:/usr/lib:$LD_LIBRARY_PATH
/home/jjj/software/Adobe/Reader8/bin/acroread

Copy and paste the above into Gedit (or your favorite text editor), save it in your home folder or wherever you like, open your file browser, right click on it, then on Properties, and set it to "run as application." Now open Accessories > Main Menu, find the launch item for Adobe Reader 8.1 and change its launch properties to the name of your script.

---

### Post by Kilz on 2007-10-10
All that just to run Acrobat?

---

### Post by John Jason Jordan on 2007-10-10
> **Kilz said:**
> All that just to run Acrobat?
LOL.

Well, I am a graduate student of linguistics and to pay the bills I run a publishing company, and I want to use nothing but Linux, and nothing but 64-bit Linux at that. I need to be able to:

1) Use the new PDF print engine that high end laser printers are now coming out with, and which will one day replace PostScript as the main page description language of the print world.

2) Be able to use editable PDFs without crash-happy Cabaret or pdfedit.

3) Be able to print without having to use Ghostscript as the imaging engine, because I have lost a bunch of money in the past when it fails to render the image properly.

4) Be able to view and print PDFs sent to me by others and be able to send PDFs to them and not have them say "oh, we can't guarantee that your job will print properly unless you proofed it in Adobe Reader." And I don't blame them for saying that, considering my experiences with KPDF/Ghostscript.

So I understand and appreciate your sentiments, but it is worth it to me, and probably for some others here as well. And besides, the more bandwidth that gets devoted to problems fixing 32-bit Adobe Reader 8.1 the faster Adobe will get off their corporate posterior and really support 64-bit Linux.

---

### Post by Kilz on 2007-10-10
> **John Jason Jordan said:**
> LOL.

Well, I am a graduate student of linguistics and to pay the bills I run a publishing company, and I want to use nothing but Linux, and nothing but 64-bit Linux at that. I need to be able to:

1) Use the new PDF print engine that high end laser printers are now coming out with, and which will one day replace PostScript as the main page description language of the print world.

2) Be able to use editable PDFs without crash-happy Cabaret or pdfedit.

3) Be able to print without having to use Ghostscript as the imaging engine, because I have lost a bunch of money in the past when it fails to render the image properly.

4) Be able to view and print PDFs sent to me by others and be able to send PDFs to them and not have them say "oh, we can't guarantee that your job will print properly unless you proofed it in Adobe Reader." And I don't blame them for saying that, considering my experiences with KPDF/Ghostscript.

So I understand and appreciate your sentiments, but it is worth it to me, and probably for some others here as well. And besides, the more bandwidth that gets devoted to problems fixing 32-bit Adobe Reader 8.1 the faster Adobe will get off their corporate posterior and really support 64-bit Linux.

I have had to edit a good number of pdf's. I have yet to have pdfedit crash. Did you report your experiences to the people working on the applications? 
Also I wouldnt hold my breath waiting for Adobe to produce any 64bit anything. Especially if they think you can run their 32bit application with a work around.

---

### Post by John Jason Jordan on 2007-10-10
> **Kilz said:**
> I have had to edit a good number of pdf's. I have yet to have pdfedit crash. Did you report your experiences to the people working on the applications? 
Also I wouldnt hold my breath waiting for Adobe to produce any 64bit anything. Especially if they think you can run their 32bit application with a work around.
No, I did not report my experiences. It crashed several times while I was trying it out. However, I deleted it from my computer anyway, because it does not really do what I need to do. I need a PDF viewer that will allow me to fill in fields in editable PDFs. I create the editable PDFs in OOo or Scribus for others to use, fill in, print out, and give back to me. I need to see what they are going to see on the screen so I can be sure I created the form correctly. Pdfedit is for a whole different scene. It might be useful for other purposes, but I don't need the functionality that it provides.

Re Adobe, I don't disagree. Their goal is to look good. It doesn't matter if they really are good. "Yes we have a version of Adobe Reader for Linux because we respect blah blah blah." The purpose of creating Adobe Reader 8.1 for Linux was to create nice sounding ad copy. 

I have to add one more thing - evidently I spoke too soon earlier. My fix for printing on amd64 is not working. My printers do appear in the drop-down, and when I send a print job from Adobe Reader 8.1 to the printer it appears to go, but the print job does not end up at the printer. Looking at the CUPS window of installed printers, the job never appears. I suppose there is yet another library somewhere that I need to add. But I have a paper due tomorrow that I have to finish, so sleuthing that out will have to wait.

---

### Post by stmiller on 2007-10-10
> **John Jason Jordan said:**
> OK, here is how to fix printing with Adobe Reader 8.1 on 64-bit Ubuntu. The problem is that Feisty does not install certain 32-bit CUPS libraries, so here is what you need to do:

Just install gtklp, and have any 32bit application print to /usr/bin/gtklp as the print command. Bingo, and you can print to your 64bit cups printer. :KS

---

### Post by Kilz on 2007-10-10
> **John Jason Jordan said:**
> No, I did not report my experiences. It crashed several times while I was trying it out. However, I deleted it from my computer anyway, because it does not really do what I need to do. I need a PDF viewer that will allow me to fill in fields in editable PDFs. I create the editable PDFs in OOo or Scribus for others to use, fill in, print out, and give back to me. I need to see what they are going to see on the screen so I can be sure I created the form correctly. Pdfedit is for a whole different scene. It might be useful for other purposes, but I don't need the functionality that it provides.

Re Adobe, I don't disagree. Their goal is to look good. It doesn't matter if they really are good. "Yes we have a version of Adobe Reader for Linux because we respect blah blah blah." The purpose of creating Adobe Reader 8.1 for Linux was to create nice sounding ad copy. 

I have to add one more thing - evidently I spoke too soon earlier. My fix for printing on amd64 is not working. My printers do appear in the drop-down, and when I send a print job from Adobe Reader 8.1 to the printer it appears to go, but the print job does not end up at the printer. Looking at the CUPS window of installed printers, the job never appears. I suppose there is yet another library somewhere that I need to add. But I have a paper due tomorrow that I have to finish, so sleuthing that out will have to wait.

I think we as users of FOSS applications need to let people working on projects know of problems or needs we have or experience. How else will they ever improve or ad things that may be important to us. 
This is something I have begun to notice about Ubuntu in general. While we have a great community. No one seems to want to file bug reports. Thinking that the post on a forum that no developer sees is enough.

---

### Post by John Jason Jordan on 2007-10-11
> **Kilz said:**
> I think we as users of FOSS applications need to let people working on projects know of problems or needs we have or experience. How else will they ever improve or ad things that may be important to us. 
This is something I have begun to notice about Ubuntu in general. While we have a great community. No one seems to want to file bug reports. Thinking that the post on a forum that no developer sees is enough.
First, I finished the paper and just now posted a query to the CUPS e-list that I subscribe to. Hopefully someone there will have the answer to the printing problem.

Regarding the issue above, again I do not disagree with your observation. I am as guilty as others. However, I have a couple of observations. First, on the several occasions when I did file bug reports I either noticed no activity whatsoever with respect to the bug or, in one case, one of the people in charge of bug reports decided it wasn't important and marked it closed (it was a serious problem with OpenOffice on Edgy amd64 but it affected only a handful of users). 

Second, it takes extra effort to find the place to report the bug and then figure out how to explain it. Most people have a hard time filling out a preconfigured form; very few are adept at writing coherent prose. It is hard work for them.

And finally, this issue is becoming off-topic for this thread, so I suggest we discontinue it here and continue it in a more appropriate forum before someone bitches at us. :)

---

### Post by John Jason Jordan on 2007-10-11
I think I solved the print problem. Using Nautilus I selected the folder where I put all the libraries (with the dpkg -x commands). Right-clicking on it I selected Properties, then Permissions, and I noted that several permissions were not set. I set them so jjj (me) could read, write, execute and do anything his pea-pickin' little heart wanted with them, and then clicked on the option to apply the permission to the folder and all its contents. 

Then I launched Reader 8.1, opened a file, sent a print job to a printer and IT PRINTED! Yay!

---

### Post by SanGimignano on 2007-10-11
Hi John 

The libgtkembedmoz.so and related libraries are not required for Adobe Connect to work . It is only required for Beyond Reader, Review tracker and Help to display correctly . For Connect to work , the minimum requirements are mentioned at [http://www.adobe.com/products/connect/productinfo/systemreqs/](http://www.adobe.com/products/connect/productinfo/systemreqs/). 
The instructions at [http://blogs.adobe.com/acroread/2007/09/adobe_reader_811_faqs.html](http://blogs.adobe.com/acroread/2007/09/adobe_reader_811_faqs.html) suggest to have firefox/xulrunner/mozilla . Also , installing/untaring xulrunner is the same thing . In fact , firefox browser is also originally available as tar.gz package. So I don't think they are wrong in saying that you need to install xulrunner . Installing xulrunner has been suggested as the first solution as  firefox and mozilla are heavy packages and the link to it is present in the FAQ.
Also , packages having 686 in their name simply mean that they will run on later x86 based systems and their is no guarantee that they will work on 386 based sytems if there have been too many processor based optimisations implemented by the developer. AMD 64 bit packages generally have " amd64" in their name .

---

### Post by olgias on 2007-10-21
I downloaded the 32bit version of libgtkembezmoz.so and
I set Preferences->Internet->libgtkembedmoz folder to point to this new file.

But I've the same problem!
Maybe the only libgtkembezmoz.so 32bit is not enough??

---

### Post by olgias on 2007-11-15
No one had the same problem?

---

### Post by John Jason Jordan on 2007-11-15
> **olgias said:**
> No one had the same problem?
What problem?

---

### Post by hutxubix on 2007-11-16
Hi!!

3 things:

1) I was trying to install adobe reader in my 64 bit gutsy but I could't. I downloaded AdobeReader_enu-8.1.1-1.i386.deb (as I don't see any for 64bit) and try to install it but I get an error for wrong arquitecture. What did I do wrong?

2) The reason why I want to install it is because I have found that the quality I get in printed documents from and pdf viewer/editor in ubuntu is quite poorer than that I get from Windows Adobre Reader, and I DO NOT LIKE THIS, so I am trying to get it installed on my computer just to test if it is really a question of the PDF viewers or of the printer drivers. (P.D. The document is created in ubuntu).

3) Printing from the GNOME document viewer, the PDF gets mistakes with line tipes and more. I do not know if it is a problem of mine, if it is a problem of printer drivers o a problem of the program (in Kpdf, it prints OK but with poor quality). Do you think I should try anything else or report a bug?. How?

P.D. Printer> HP OfficeJet Pro K5400

Thanks

---

### Post by John Jason Jordan on 2007-11-16
> **hutxubix said:**
> Hi!!
3 things:
1) I was trying to install adobe reader in my 64 bit gutsy but I could't. I downloaded AdobeReader_enu-8.1.1-1.i386.deb (as I don't see any for 64bit) and try to install it but I get an error for wrong arquitecture. What did I do wrong?

2) The reason why I want to install it is because I have found that the quality I get in printed documents from and pdf viewer/editor in ubuntu is quite poorer than that I get from Windows Adobre Reader, and I DO NOT LIKE THIS, so I am trying to get it installed on my computer just to test if it is really a question of the PDF viewers or of the printer drivers. (P.D. The document is created in ubuntu).

3) Printing from the GNOME document viewer, the PDF gets mistakes with line tipes and more. I do not know if it is a problem of mine, if it is a problem of printer drivers o a problem of the program (in Kpdf, it prints OK but with poor quality). Do you think I should try anything else or report a bug?.
First, I agree with the issue that there are no open source PDF viewers that work as well as Adobe Reader. KPDF comes close, but I have had incorrect print output from it,  plus it cannot handle editable PDF forms (e.g., tax return forms available from the US Internal Revenue Service). 

As for how to install Adobe Reader, do not use the .deb file. Instead, go to:

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

And select the Linux -x86 tar.gz file. Once you have downloaded it, open it in Archive Manager and untar it (extract it) to a folder of your choice. I prefer to install such software in my home folder, so I made a /home/jjj/Software folder and I untarred the -x86.tar.gz file into it. That created subfolders. In one of them there is a file called INSTALL. Open a terminal, navigate to your folder (for me, "cd ~/Software/AdobeReader") and then type ./INSTALL. The INSTALL file is a script that Adobe wrote that will install it on your computer. The INSTALL script doesn't care about 32-bit or 64-bit.

The above procedure should create a launch item under Applications in your Gnome panel. It should launch just fine, but if it does not, post back. I wrote this from memory without checking it and I might have forgotten a step.

One more thing: Assuming you get it installed, open a PDF file (any file will do) and click on File > Print. When the print dialog box comes up, check to see that the printer(s) you have installed on your Ubuntu computer appear. If you see only (custom), post back and I can help you figure out what is wrong (missing libraries).

---

### Post by hutxubix on 2007-11-16
:guitar:

It worked. It even prints directly!! I love it.

Just two things:

a) At the beginning I get a message saying that it cannot find libgtkembezmoz.so. I do not see it in synaptic. Where can I get it?

b) I have done a print test and is better but I still get lines thicker than they really are. Can it have something to do with libgtkembezmoz.so. Any clue?

Thanks

---

### Post by John Jason Jordan on 2007-11-16
> **hutxubix said:**
> :guitar:
It worked. It even prints directly!! I love it.
Just two things:
a) At the beginning I get a message saying that it cannot find libgtkembezmoz.so. I do not see it in synaptic. Where can I get it?
b) I have done a print test and is better but I still get lines thicker than they really are. Can it have something to do with libgtkembezmoz.so. Any clue?Thanks
The libgtkembezmoz.so file has to do with Firefox displaying PDF files in a browser tab instead of launching Acroread outside of Firefox (the acroread plugin). It has nothing to do with printing. If your print output is wrong it must be in the printing. It's either a setting in your print dialog boxes (your error), a bug or misconfigured driver in CUPS, or a bug in Acroread. I'd try the print dialog boxes first. If you are sure you are sending the job correctly, then I'd check CUPS and try installing the printer differently. For example, there are numerous ways to install a printer in CUPS. Try some of the other options. I have several printers and each one I have installed various ways.

---

### Post by olgias on 2007-11-16
> **John Jason Jordan said:**
> The libgtkembezmoz.so file has to do with Firefox displaying PDF files in a browser tab instead of launching Acroread outside of Firefox (the acroread plugin). It has nothing to do with printing. If your print output is wrong it must be in the printing. It's either a setting in your print dialog boxes (your error), a bug or misconfigured driver in CUPS, or a bug in Acroread. I'd try the print dialog boxes first. If you are sure you are sending the job correctly, then I'd check CUPS and try installing the printer differently. For example, there are numerous ways to install a printer in CUPS. Try some of the other options. I have several printers and each one I have installed various ways.

---------
**Does anyone has a solution for The libgtkembezmoz.so problem??**
---------



p.s. you can find acroread in the medibuntu repository

---

### Post by ricardoatb-linux on 2007-11-17
To fix the *"libgtkembedmoz"* problem, just execute this:

**# aptitude install libgtk-mozembed-ruby**

---

### Post by hutxubix on 2007-11-18
> **ricardoatb-linux said:**
> To fix the *"libgtkembedmoz"* problem, just execute this:

**# aptitude install libgtk-mozembed-ruby**

It didn't work for me because it instal mozembed instead of embedmoz.

?

Another thing, How can I add the medibuntu repository?

---

### Post by John Jason Jordan on 2007-11-18
> **hutxubix said:**
> It didn't work for me because it instal mozembed instead of embedmoz.
Another thing, How can I add the medibuntu repository?
I don't have a solution for the mozilla problem. The purpose is to make Adobe Reader open PDF files in a tab in Firefox, instead of launching Reader outside of Firefox. However, either way it has to launch Reader, so it takes the same amount of time whether you do it inside Firefox or not. I just let it launch Reader outside of Firefox. 

To add repositories, go to System > Administration > Software Sources. However, last I checked the version of Reader that was available there was 7.0.9. If so, the only way to get 8.1 is to download the tar.gz file, untar it, and install it with ./INSTALL.

---

### Post by shane2peru on 2008-02-03
> **John Jason Jordan said:**
> First, I agree with the issue that there are no open source PDF viewers that work as well as Adobe Reader. KPDF comes close, but I have had incorrect print output from it,  plus it cannot handle editable PDF forms (e.g., tax return forms available from the US Internal Revenue Service). 

As for how to install Adobe Reader, do not use the .deb file. Instead, go to:

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

And select the Linux -x86 tar.gz file. Once you have downloaded it, open it in Archive Manager and untar it (extract it) to a folder of your choice. I prefer to install such software in my home folder, so I made a /home/jjj/Software folder and I untarred the -x86.tar.gz file into it. That created subfolders. In one of them there is a file called INSTALL. Open a terminal, navigate to your folder (for me, "cd ~/Software/AdobeReader") and then type ./INSTALL. The INSTALL file is a script that Adobe wrote that will install it on your computer. The INSTALL script doesn't care about 32-bit or 64-bit.

The above procedure should create a launch item under Applications in your Gnome panel. It should launch just fine, but if it does not, post back. I wrote this from memory without checking it and I might have forgotten a step.

One more thing: Assuming you get it installed, open a PDF file (any file will do) and click on File > Print. When the print dialog box comes up, check to see that the printer(s) you have installed on your Ubuntu computer appear. If you see only (custom), post back and I can help you figure out what is wrong (missing libraries).


Ha ha!  Wonderfull, worked like a charm and printed!  Thanks for the info.

Shane
**Edit:**  I noticed it is a lot faster opening than in my 32 bit system.  Wow I'm impressed!

---

