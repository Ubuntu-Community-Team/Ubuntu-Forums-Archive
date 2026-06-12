---
title: "How to associate files with PlayOnLinux installed MS Office"
date: 2012-03-13
forum: Wine
---

### Post by forrestcupp on 2012-03-13
Preface: This is a howto, not a question.

Today, after beating my brains out trying to install Office 2007 with Wine 1.4 in Precise, I ended up resorting to using PlayOnLinux. What I learned about PlayOnLinux is that it makes installing things a dream, but it makes the general usability of those things an absolute nightmare. When I had Office 2007 installed with Wine, I could easily set filetype associations in Nautilus to Word and Excel. When I installed Office 2007 in PlayOnLinux, it didn't leave any way to associate filetypes. Also, PlayOnLinux created nice shortcuts to the apps on the desktop, but it didn't create any gnome-desktop launchers that will show up in Dash in Unity or Gnome Shell.

After a lot of hard work and headaches, I finally figured out how to do both of those things, so I thought I would share that experience for future reference, and for anyone else who might need it.

When you are preparing to do this, be aware that you will have to create two separate .desktop files for each Office program (Word, Excel, etc.). The first section creates a .desktop file so that a new instance of Word can be launched from the Dash. The second section creates a second .desktop file for associating file types.

_**Creating a .desktop launcher file**_

This creates a .desktop file so that a new instance your Office programs can be launched from Dash.

Open a terminal, and enter this command:
```
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```
In the window that comes up, first enter a name for your launcher. For Microsoft Word, we'll enter **Microsoft Word** as the name. Then in the "Command" box, for Word 2007, we'll enter this code
```
playonlinux --run "Microsoft Word 2007"
```For Excel 2007, you would enter "Microsoft Excel 2007" leaving the quotes in it. For anything else, you just would put whatever app name shows up in the PlayOnLinux window, and put that name in quotes. After this, you can click on the icon and use the file browser to point it to whatever icon you want to use for that launcher.

After doing this, your app launcher should show up by doing a Dash search.


_**Associating files with MS Office that was installed with PlayOnLinux**_

This creates a second .desktop file for associating your file types.

_Step 1 - creating a .desktop launcher for association_
Since PlayOnLinux installed apps don't show up in the "Open With" dialog in Nautilus, you have to create a custom command for Nautilus. This used to be easy to do with the GUI, but since they changed to Gnome 3 in 11.10, you can't do that anymore. Never fear, that's why we have the command line. Open a terminal, and **cd** to a folder that has a .doc or .docx file. Once you're in that folder, note the name of your Word document file, and type:
```
mimeopen -d *filename.doc*
```Of course you would type **.docx** if that's what type of file it is. When you type this, it will give you options of what you want the default app to be for that file. Enter whatever number says "Other" so that you can enter a custom command. For that custom command, enter the following for Word 2007:
```
playonlinux --run "Microsoft Word 2007" z:%f
```
Note, that it will try to open the file with Word, and at this point it will not work. By the time you're done, it will work properly when you double click it in Nautilus.

Now open up Nautilus, press Ctrl+H if hidden files aren't showing, and navigate to ~/.local/share/applications and find the .desktop launcher file with something like "playonlinux_userdefined" in the name. Change that name to something like **Word.desktop**. Now you can right-click on a .doc or .docx file, go to Properties, and go to the "Open With" tab, click "Show Other Applications" and find "Word.desktop" in the list. Now, that filetype is associated with Word, and you can go through all of those steps again substituting the right names for Excel and Powerpoint.

_Step 2 - making it work properly_
Unfortunately, what you just did won't work if there are spaces in the file or folder names. But we can fix that, too.

Open Nautilus and navigate to ~/.PlayOnLinux/shortcuts. Double click on each of the shortcuts that were made for Word, Excel, and Powerpoint, and choose to Display the file in Gedit. At the end of the script, you should find this code:
```
$@
```Change that code for the following code in each shortcut script, and save the files.
```
"$(echo "$@" | sed -e 's:/*/:\\:g')"
```Make sure you leave the quotes in. That code will take the path and filename and convert any spaces to be readable by Word, Excel, or Powerpoint when you open the file.

Since both desktop files will show up in a Dash search, I suggest not assigning an icon to this one to prevent confusion.

Now, you should be able to navigate to any MS Office file in Nautilus, double click on it, and it will open properly.

I'm not an expert, and this is just the findings of my experience. Hopefully it works for you, too.


Edit: I found all of this information scattered all over the net, but I need to give credit to **wojox** for [helping me fix a problem with the bash code I found for the shortcut script](http://ubuntuforums.org/showthread.php?t=1940462).

---

### Post by johnnybegood on 2012-04-14
This tutorial is very helpful indeed. Now I'm having Microsoft Office 2010 up and running with PlayOnLinux. I can use LibreOffice or Microsoft Office with a click of the mouse. Thanks a lot!;)

---

### Post by forrestcupp on 2012-04-16
I'm glad it helped someone other than me! :)

Maybe someday, they'll just change PlayOnLinux to do this stuff automatically.

---

### Post by zorbama on 2012-04-20
That worked great! Thank you very much! :p

---

### Post by amishafi on 2012-05-02
Brother Let me tell you this "You are AWESOME" :)

It's Working................ COOL

---

### Post by whochismo on 2012-05-02
Thank you, it works!

But... just a couple of things:

- If the new .desktop file that we've created doesn't include an icon, when you open an office document with it, it will appear with an invisible icon in the unity bar. In order to avoid this, you should include a line like this in each of the .desktop files:
```
Icon=/home/*username*/.PlayOnLinux//icones/full_size/Microsoft Word 2007
```
(remember to replace the "Word" with "Excel" and "Powerpoint" when needed, and make sure that you change the *username* with your real username)

- Because we told the shortcut to open the *z:%f* file, I receive an error every time I try to use that shortcut without specifying any file. (for example, If i use that shortcut in the Unity bar). Is there any way to avoid that?

---

### Post by forrestcupp on 2012-05-03
> **whochismo said:**
> Thank you, it works!

But... just a couple of things:

- If the new .desktop file that we've created doesn't include an icon, when you open an office document with it, it will appear with an invisible icon in the unity bar. In order to avoid this, you should include a line like this in each of the .desktop files:
```
Icon=/home/*username*/.PlayOnLinux//icones/full_size/Microsoft Word 2007
```
(remember to replace the "Word" with "Excel" and "Powerpoint" when needed, and make sure that you change the *username* with your real username)

- Because we told the shortcut to open the *z:%f* file, I receive an error every time I try to use that shortcut without specifying any file. (for example, If i use that shortcut in the Unity bar). Is there any way to avoid that?I think you slightly misunderstood the HowTo. Because of what you said at the end, you actually have to create two desktop files. I've tried to think of a way around that, and you just have to do it because of the script error you're talking about.

In the HowTo, the first section makes a plain .desktop file just for launching Word, etc., from Dash. That's the one you should set an icon for, and in my instructions, I just said to use the GUI to set that.

The second section of the HowTo is for making another .desktop file that will include the script, and this one is for associating file types with Office. Since they will both appear in a Dash search, I recommend not assigning an icon to this file so it won't be confusing.

Thanks for pointing out the confusion. I'll edit the first post to make it a little clearer.

---

### Post by harishsudharsan on 2012-05-06
Thank you very much. That was perfect.

---

### Post by 3ill on 2012-05-28
forestcupp, your tutorial is thorough and it works flawlessly.

thank you.


here's another option using mimetypes:
[LIST]
[*] just paste the whole thing into the terminal after installing MS Office with PlayOnLinux
[*] works for 2010 & 2007
[*] only sets Excel, Word, and/or Powerpoint as default application(s)
[*] rewrites the main and context menu shortcuts  

[*] i wrote this for kubuntu but it should work for gnome,unity,yadda,yadda...
[*] although, in Unity, user mimetypes are suppose to be set in ~/.local/share/applications/mimeapps.list, but whatever...
[*] for mimetype info on other apps, go here [http://filext.com/file-extension](http://filext.com/file-extension)

[*] There's a bug where PlayOnLinux might not double quote POWERPNT.EXE and $@ for Excel in ~/.PlayOnLinux/shortcuts/, so if you get an error, just manually do forestcupp's trick.
[/LIST]
```

Word_mimetypes='application/msword;application/vnd.openxmlformats-officedocument.wordprocessingml.document;application/vnd.openxmlformats-officedocument.wordprocessingml.template;application/vnd.ms-word.document.macroEnabled.12;application/vnd.ms-word.template.macroEnabled.12;';Excel_mimetypes='application/vnd.ms-excel;application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;application/vnd.openxmlformats-officedocument.spreadsheetml.template;application/vnd.ms-excel.sheet.macroEnabled.12;application/vnd.ms-excel.template.macroEnabled.12;application/vnd.ms-excel.addin.macroEnabled.12;application/vnd.ms-excel.sheet.binary.macroEnabled.12;';Powerpoint_mimetypes='application/vnd.ms-powerpoint;application/vnd.ms-powerpoint;application/vnd.ms-powerpoint;application/vnd.ms-powerpoint;application/vnd.openxmlformats-officedocument.presentationml.presentation;application/vnd.openxmlformats-officedocument.presentationml.template;application/vnd.openxmlformats-officedocument.presentationml.slideshow;application/vnd.ms-powerpoint.addin.macroEnabled.12;application/vnd.ms-powerpoint.presentation.macroEnabled.12;application/vnd.ms-powerpoint.template.macroEnabled.12;application/vnd.ms-powerpoint.slideshow.macroEnabled.12;';echo ; echo -n '    Which year of Microsoft Office have you installed? (2010/2007) : '; read office_year; echo ; for i in $( ls ~/.PlayOnLinux/shortcuts | grep -owE '(Word|Excel|Powerpoint)' ); do echo '[Desktop Entry]
Encoding=UTF-8
Categories=Office;
Comment=Microsoft Office '"$i $office_year"'
Exec=/usr/share/playonlinux/playonlinux --run "Microsoft '"$i $office_year"'" z:%f
Icon=~/.PlayOnLinux//icones/full_size/Microsoft '"$i $office_year"'
InitialPreference=3
Name=Microsoft '"$i $office_year"'
MimeType='$(eval "echo \$${i}_mimetypes")'
Type=Application' > ~/.local/share/applications/Microsoft\ "$i"\ "$office_year".desktop && sed --in-place 's/$@/$(echo "$@" | sed -e '\''s:\/*\/:\\\\:g'\'')/g' ~/.PlayOnLinux/shortcuts/Microsoft\ "$i"\ "$office_year" && echo '    Success - ' "$i" "$office_year" set as a default application; done; echo "    Done.\n";

```

---

### Post by AlexanderDGreat on 2012-06-12
Works like a charm!

It's the super tutorial!

---

### Post by Zquezie on 2012-06-21
Thanks a lot, i've been looking for this a long time :)

---

### Post by nostredummasid on 2012-06-29
Unbelievably frustrating that so many options are being bled away from Linux. What was once a multi-faceted pleasure is now an exercise in annoyance and strains my patience on a daily basis.   It is especially retarded to remove the option to "open with" any application of ones choice from Nautilus. Whoever dreamed this beauty up is a complete and total idiot!!!    Forgive my candor...but this is after days of trying to open a simple .pdf file with Acrobat Reader. When Linux lags WAY behind Windows in something as simple as the option to choose ones default applications....you have to know it's going in entirely the wrong direction.    I have to wonder if there isn't some hidden plot or agenda...or another Microsoft conspiracy...once again attempting to sabotage my beloved OS.    From being forced to download 3rd party applications to execute simple tasks like changing themes and icons etc...to this incredible gaf...Linux is increasingly alienating those who've found a home away from the great patriarchal corporate monsters represented by Windows and Mac.    I personally deeply resent having almost EVERY configuration option stripped progressively away on the release of each "progressive" distro. Hopefully a solution will be found that can accommodate BOTH what seems to be an attempt to infantilize the user interface, and those who require a more interactive experience.     Thankfully there are those who still understand the nuts and bolts....and we can still get the answers we need (yup...I CAN finally open my pdf's) Even if those options have been stripped from the GUI itself.

---

### Post by changing on 2012-06-30
Thanks for the instructions. It works like a charm.
I changed the last line into the following, and no need to use two .desktop scripts for one program.
"$(echo "$@" | sed -e 's:/*/:\\:g' | sed -e 's/^z:$//')"

---

### Post by jzl003 on 2012-08-05
I followed this and it helped me so much(thanks) but when i made the first gnome desktop edit i didnt change the icon. i did that now but how do i remove those old applications so when i search for word it doesnt show more then one response

---

### Post by danielmac123 on 2012-08-08
Even easier, just open an office program and make a document and save it anywhere you like. Then right click on the file you saved and choose open with other application. Then choose use a custom command and type in

playonlinux --run "Microsoft Word 2007"
Or put in 2010 depending on your version. Or put in Excel or PowerPoint, etc.
:D

---

### Post by number4please on 2012-08-26
thank you very very much, worked awesome:)

---

### Post by dochc on 2012-08-29
This is fantastic!! I think I found an older thread of this and was having some trouble with it, but this works a treat.
I have all kinds of versions of MS files for Word, Powerpoint and Excel and was wondering whether I have to go through each file type and associate to the application. Is there a way to list them all and have any of them (e.g .doc, .dot, .docx, .dotx .....etc). opened by the correct application?
Easy explanations please; if you're no expert then I'm still a piece of slime mould on the Ubuntu evolutionary scale! I'm sure it will, I followed the last one with ease :D

---

### Post by l0nd0n on 2012-09-15
When I open terminal and enter the first command, it says in need to install gnome-panel first. I assume it is because I use the Unity desktop and not gnome. Is there a workaround or different command? Do I install it, follow the tutorial, and then remove gnome-panel?

---

### Post by opg on 2012-10-28
> Open Nautilus and navigate to ~/.PlayOnLinux/shortcuts. Double click on each of the shortcuts that were made for Word, Excel, and Powerpoint, and choose to Display the file in Gedit. At the end of the script, you should find this code:
```
$@
```Change that code for the following code in each shortcut script, and save the files.
```
"$(echo "$@" | sed -e 's:/*/:\\:g')"
```


Simply putting quotes around %@ worked for me.

---

### Post by JohnH on 2012-11-01
Thank you for this "how to". I'm running the very latest POL which has an option under Actions called Settings. Here it is possible to define the file extension type to open with the app. BUT it didn't work for me.

Thank you for your efforts - it is much appreciated.

John

---

### Post by thunder686 on 2013-01-24
Here is a slightly modified version based on forrestcupp post to make it work on kubuntu 12.04:
•    Go to your home folder then press Alt-. to see the hidden files then go to .local/share/applications
•    In the applications folder right click-->Create New-->Link to Application.
Click the application tab and in the name field enter the desired name of the file for example ‘**Microsoft Word 2007**’ and in the command field enter 
```
playonlinux --run "Microsoft Word 2007" z:%f
```and click OK.
•    Go to ~/.PlayOnLinux/shortcuts and right click on the file ‘**Microsoft Word 2007**’ then open with then Kate.
•    Replace ```
$@
``` located at the end of the file with ```
"$(echo "$@" | sed -e 's:/*/:\\:g')"
``` and DO NOT LEAVE OUT THE QUOTES. 
•    Now right click on the file you want to open with word 2007 then properties then click on the wrench icon then click add. You should find the ‘**Microsoft Word 2007**’ file you created before under the ‘Lost & Found’ tab.
•    Click OK and you are done.

---

### Post by rockxell on 2013-03-21
thks very clear

---

### Post by AllenMc on 2013-04-12
> **changing said:**
> Thanks for the instructions. It works like a charm.
I changed the last line into the following, and no need to use two .desktop scripts for one program.
"$(echo "$@" | sed -e 's:/*/:\\:g' | sed -e 's/^z:$//')"

How can I do it without 2 .desktop scripts? Its not a big deal just a little annoying having 2 Words show up in dash and I'm probably gonna accidentally click on the wrong one at somepoint when I'm not paying attention.

Otherwise, this is awesome! Thank you!

---

### Post by hg088 on 2013-06-09
Thanks a lot, works Perfectly!

btw, you can use a package called alacarte to create the .desktop files  more easily

---

### Post by mitsumits on 2013-09-13
Thanks a lot. It works fine, even with filenames inclusing space.

---

### Post by Dinosawer on 2013-09-14
Thanks for the guide, it was very helpful! :)
I noticed recently that PlayOnlinux has file association functionality now, in Settings->File Associations, might be worth a try too. (Didn't try it myself since I had already done it like described here.)
Edit: I just tried the option today - you have to update to the newest version of Playonlinux from the website (the one in the ubuntu softwarecenter is older) for it to work though. Then you can easily configure them, and after that you have to right-click on your files, do "open with", set "playonlinux" as default and it will work from then. (Also works with filenames with spaces and strange characters here).

---

### Post by max18 on 2013-12-11
Great tutorial and info above, in my case I performed in a different way which worked perfectly for me:

1) Firstly, I created the shortcuts based upon the PlayOnLinux shortcut:
cd /usr/share/applications
sudo cp PlayOnLinux.desktop PlayOnLinux-msword.desktop
sudo cp PlayOnLinux.desktop PlayOnLinux-msexcel.desktop
sudo cp PlayOnLinux.desktop PlayOnLinux-mspowerpoint.desktop


2) Then, I changed the content of each .desktop file and adjusted the contents as follows (In my example, I used MS-Word)
Also, notice that I changed the Category to 'Office' which makes more sense for me):

sudo gedit PlayOnLinux-msword.desktop

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Microsoft Word 2010
GenericName=Office
Comment=Microsoft Word 2010
Type=Application
Exec=playonlinux --run "Microsoft Word 2010" %F
Icon=/home/max/.PlayOnLinux/icones/full_size/Microsoft Project 2010
Categories=Office;


3) Using Nautilus, enter into any directory which you have all different file-types (.doc, .docx, .ppt, .pptx, .xls, .xlsx)

4) Point your mouse over any MS-document, press the right button, click on "Properties" and then select the tab "Open With"
Select your desire MS application in the list and click on "Set as default"

5) Repeat the step 4 for each file-type (.doc, .docx, .ppt, .pptx, .xls, .xlsx)


That's it !! Enjoy !

:popcorn:

---

### Post by Adt2u2s2 on 2014-06-04
thanks ! very helpful

---

### Post by valeriancafe on 2014-08-15
Cool it worked in debian wheezy

---

### Post by finechap on 2014-10-02
**3ill** - thanks for your suggestion, it worked for me on 14.04 64 bit. Once I had run your script, I then had the option of changing mime defaults in Nautilus. Full marks to both, or more of you.

---

