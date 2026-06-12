---
title: "How do I stop Firefox/switch Default to Swiftweasel"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr_bleu on 2007-06-15
I've tried scanning the forums, but I've not come across the info I'm looking for.
Whenever I click a link in messenger <gaim> or in spades, Firefox opens.  Swiftweasel is set as my default web browser.   Thanks.  Any help is Appreciated.

---

### Post by Kilz on 2007-06-16
> **Mr_bleu said:**
> I've tried scanning the forums, but I've not come across the info I'm looking for.
Whenever I click a link in messenger <gaim> or in spades, Firefox opens.  Swiftweasel is set as my default web browser.   Thanks.  Any help is Appreciated.

You know, Im not really sure. Are you using the 32bit or 64bit version of Swiftweasel?

---

### Post by Mr_bleu on 2007-06-16
64 Bit version sir.  :KS

---

### Post by Kilz on 2007-06-16
Thank you for this oppertunity to learn something new . :D
After looking I learned how to set a default for the system. Open a terminal and type, or copy/paste in

```
sudo /usr/sbin/update-alternatives --install /usr/bin/x-www-browser \x-www-browser /usr/local/bin/swiftweasel 90
``` and 
 ```
sudo /usr/sbin/update-alternatives --install /usr/bin/mozilla mozilla /usr/local/bin/swiftweasel 0
```

It will ask you for your password and appear to not do anything.
Next type or copy pate in this.

```
sudo update-alternatives --config x-www-browser 
```
It will show you a list, and ask for a number. Put in the one for swiftweasel. Do the same with.
```
sudo update-alternatives --config mozilla 
```

That should do it. If you ever want to change back just enter in the commands again and pick firefox.

---

### Post by Mr_bleu on 2007-06-16
Thanks again Kilz!!!:popcorn:

---

### Post by Mr_bleu on 2007-06-16
I tried that.........still opens firefox instead of swiftweasel.  I selected swiftweasel both times.

---

### Post by Kilz on 2007-06-16
> **Mr_bleu said:**
> I tried that.........still opens firefox instead of swiftweasel.  I selected swiftweasel both times.

When you enter in
```
sudo update-alternatives --config x-www-browser
```
Where is the * by?

---

### Post by Mr_bleu on 2007-06-16
Password:

There are 4 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/firefox
          2    /usr/bin/epiphany
 +        3    /usr/bin/galeon
*         4    /usr/local/bin/swiftweasel

Press enter to keep the default[*], or type selection number:

---

### Post by Kilz on 2007-06-17
> **Mr_bleu said:**
> Password:

There are 4 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/firefox
          2    /usr/bin/epiphany
 +        3    /usr/bin/galeon
*         4    /usr/local/bin/swiftweasel

Press enter to keep the default[*], or type selection number:

It looks like everything is setup correctly. Lets try something. I have created a pdf. Click on the link in it, with all browsers closed and see what opens.

---

### Post by atlfalcons866 on 2007-06-17
try going to 
system->preferences>preferred applications

---

### Post by Cappy on 2007-06-17
Kilz, I tried your method and it didn't work for me either. I tried Opera instead of swiftweasel. 
I also tried setting it on "gnome-www-browser" but that didn't work either. There is one called "www-browser" but it was a text based browser called "w3m" there so I didn't change it from that.
Man page - "w3m - a text based Web browser and pager"

Anyway, it still opened my Firefox when I would click a link.

> **atlfalcons866 said:**
> try going to 
system->preferences>preferred applications

This worked for me.

I've always just let gaim open links in firefox and I never really tried to switch it until now =P

---

### Post by Kilz on 2007-06-17
> **Cappy said:**
> Kilz, I tried your method and it didn't work for me either. I tried Opera instead of swiftweasel. 
I also tried setting it on "gnome-www-browser" but that didn't work either. There is one called "www-browser" but it was a text based browser called "w3m" there so I didn't change it from that.
Man page - "w3m - a text based Web browser and pager"

Anyway, it still opened my Firefox when I would click a link.



This worked for me.

I've always just let gaim open links in firefox and I never really tried to switch it until now =P

This must be one of the differences between Dapper and Feisty. I dont get Swiftweasel in the system->preferences>preferred applications list. But the settings I gave earlier work.

---

### Post by Mr_bleu on 2007-06-17
I already have swiftweasel in my preferences:
/usr/local/swiftweasel/swiftweasel "%s"
Is what I found listed.

---

### Post by Kilz on 2007-06-17
> **Mr_bleu said:**
> I already have swiftweasel in my preferences:
/usr/local/swiftweasel/swiftweasel "%s"
Is what I found listed.

There is a user default list here
```
~/.local/share/applications/default.list
```
You could add this line to it
```
application/x-www-browser=swkde.desktop
```
But Im not sure if it will help.

If it comes down to it, you could always just copy the contents of the /usr/local/swiftfox folder, delete the contents of /usr/lib/firefox. Then paste in the swiftweasel files. The only thing is, that when you update firefox you will have to do it again as Ubuntu update will replace it with firefox again.

---

### Post by Angelbeast on 2007-06-17
Mine keeps asking me if i want to et swiftweasel as my default every single time i start it up...i alwys click yes...and i even tried that bit of code...and i tried the link in the pdf file and nothing at all happened...help *LOL*

---

### Post by Kilz on 2007-06-17
> **Angelbeast said:**
> Mine keeps asking me if i want to et swiftweasel as my default every single time i start it up...i alwys click yes...and i even tried that bit of code...and i tried the link in the pdf file and nothing at all happened...help *LOL*

Click Edit > Preferences > Main tab. Uncheck box by "Always check to see if Swiftwease is the default browser on startup"

---

### Post by atararx on 2007-06-17
I am not sure what the difference between swiftweasel and swiftfox is, but I installed swiftfox and it opens up instead of firefox every time.

From the description, it appears to be quite similar to swiftweasel.

---

### Post by Angelbeast on 2007-06-18
> **Kilz said:**
> Click Edit > Preferences > Main tab. Uncheck box by "Always check to see if Swiftwease is the default browser on startup"

hey i remember you...how you doin?

if i uncheck the box then it won't check to see if swiftweasel is the default browser and i want it to be...it doesn't even open external links right now either...when i click on a link nothing happens...maybe i would be better off using swiftfox...i wanted to give this a go though coz it's open sourced...

---

### Post by Kilz on 2007-06-18
> **Angelbeast said:**
> hey i remember you...how you doin?

if i uncheck the box then it won't check to see if swiftweasel is the default browser and i want it to be...it doesn't even open external links right now either...when i click on a link nothing happens...maybe i would be better off using swiftfox...i wanted to give this a go though coz it's open sourced...

Doing ok, you?
All the tips on this thread should make it see external links. I also posted this on the swiftweasel site and stickk, the person doing swiftweasel, said he would look into it.

> **atararx said:**
> I am not sure what the difference between swiftweasel and swiftfox is, but I installed swiftfox and it opens up instead of firefox every time.

From the description, it appears to be quite similar to swiftweasel.

The major differences can be [read about here. ]("http://community.linux.com/article.pl?sid=07/04/09/1833235&tid=5")

---

### Post by Angelbeast on 2007-06-19
> **Kilz said:**
> Doing ok, you?
All the tips on this thread should make it see external links. I also posted this on the swiftweasel site and stickk, the person doing swiftweasel, said he would look into it.



The major differences can be [read about here. ]("http://community.linux.com/article.pl?sid=07/04/09/1833235&tid=5")

i'm doin good now that i'm all finished with school *LOL* ... i went back to regular firefox for now..i tried everything on here but it just wouldn't work quite right and honestly as much as i like Ubuntu i'm a little tired of having to mess with everything to get it to work like it's supposed to  :-P

---

### Post by Kilz on 2007-06-19
> **Angelbeast said:**
> i'm doin good now that i'm all finished with school *LOL* ... i went back to regular firefox for now..i tried everything on here but it just wouldn't work quite right and honestly as much as i like Ubuntu i'm a little tired of having to mess with everything to get it to work like it's supposed to  :-P

Even completely replacing the contents of the Firefox folder with the contents of a Swiftweasel one didnt work?

---

### Post by Angelbeast on 2007-06-23
> **Kilz said:**
> Even completely replacing the contents of the Firefox folder with the contents of a Swiftweasel one didnt work?

i didn't ee that part on here...will that  overwrite my bookmarks and stuff?

---

### Post by Rui Pais on 2007-06-23
> **Angelbeast said:**
> i didn't ee that part on here...will that  overwrite my bookmarks and stuff?

yes it will, but you can make a temporary move just to check if it works or you can backup your bookmarks.
you can do 
```
mv .mozilla/firefox .mozilla/firefox_BAKUP
```
or
```
mv .mozilla/swiftweasel .mozilla/swiftweasel_BAKUP
```
to backup a profile and start from a freshone.

To backup bookmarks, in menus go Bookmarks->Organize Bookmarks On Organize windows File->Export.

---

### Post by stickk on 2007-06-23
> **Angelbeast said:**
> i didn't ee that part on here...will that  overwrite my bookmarks and stuff?

Swiftweasel should not overwrite your bookmarks. But backing them up is a good idea from time to time. You may wish to try the new release instead of overwriting the firefox directory.

---

### Post by Angelbeast on 2007-06-24
Okay the new folder seems to have done the trick...but now how do i import all of my saved passwords? and my extensions too if possible...

---

### Post by Kilz on 2007-06-24
> **Angelbeast said:**
> Okay the new folder seems to have done the trick...but now how do i import all of my saved passwords? and my extensions too if possible...

That should be done, if it has not delete only the ~/.mozilla/swiftweasel folder, Do not rename the ~/.mozilla/firefox folder or change it back if you have. Then restart swiftweasel. It will import your firefox settings folder.

---

### Post by Angelbeast on 2007-06-24
> **Kilz said:**
> That should be done, if it has not delete only the ~/.mozilla/swiftweasel folder, Do not rename the ~/.mozilla/firefox folder or change it back if you have. Then restart swiftweasel. It will import your firefox settings folder.

i already went and installed fresh extensions...is there any way to just import the passwords? and if not...there are two firefox folders...one that was changed to bakup and a new one that was made when swiftweasek was installed...now do you mean that i should change the one that was changed to bakup BACK to 'firefox' and delete the new one? here's a screenshot of what i'm tlking about...

---

### Post by Kilz on 2007-06-24
> **Angelbeast said:**
> i already went and installed fresh extensions...is there any way to just import the passwords? and if not...there are two firefox folders...one that was changed to bakup and a new one that was made when swiftweasek was installed...now do you mean that i should change the one that was changed to bakup BACK to 'firefox' and delete the new one? here's a screenshot of what i'm tlking about...

Ok, 
A. the Firefox-Backup is the orignal Firefox settings folder you renamed , if you followed the instructions above.
B. Swiftweasel does not in any way use the Firefox folder, or create it, it creates and uses the swiftweasel folder.
C. The other Firefox folder must have been created when you started Firefox at some point.

There is no way I know of to just pick and chose what swiftweasel imports. I again recommend you 
1. Delete the Firefox folder and rename Firefox-backup back to firefox.
2. Shut down all swiftweasel browsers open
3. Delete the swiftweasel folder. You could move the extensions folder out first and save it some place.
3. Restart swiftweasel. It will make a new swiftweasel folder and import all settings, passwords, extensions and themes . 
4. If for some reason the extensions didnt transfer (for example some error made them not transfer) when you restart swiftweasel. Close it down and copy the contents of the extensions folder you saved above to the one inside the swiftweasel folder. Do not do this if they copied as duplicate extensions may mess things up.

---

### Post by Angelbeast on 2007-06-24
> **Kilz said:**
> Ok, 
A. the Firefox-Backup is the orignal Firefox settings folder you renamed , if you followed the instructions above.
B. Swiftweasel does not in any way use the Firefox folder, or create it, it creates and uses the swiftweasel folder.
C. The other Firefox folder must have been created when you started Firefox at some point.

There is no way I know of to just pick and chose what swiftweasel imports. I again recommend you 
1. Delete the Firefox folder and rename Firefox-backup back to firefox.
2. Shut down all swiftweasel browsers open
3. Delete the swiftweasel folder. You could move the extensions folder out first and save it some place.
3. Restart swiftweasel. It will make a new swiftweasel folder and import all settings, passwords, extensions and themes . 
4. If for some reason the extensions didnt transfer (for example some error made them not transfer) when you restart swiftweasel. Close it down and copy the contents of the extensions folder you saved above to the one inside the swiftweasel folder. Do not do this if they copied as duplicate extensions may mess things up.

okay i'm off to give it a try...wish me luck  *LOL*  :-)

---

### Post by Angelbeast on 2007-06-28
Everything is working just fine now...thanks guys  :-)

---

### Post by abrichr on 2007-07-18
The commands

```
sudo update-alternatives --config x-www-browser
```

and

```
sudo update-alternatives --config mozilla
```

Show only firefox; no swiftweasel.  I installed swiftweasel using the attached script.

This got so frustrating I actually uninstalled Firefox (and its dependencies).  Now those commands show nothing, although swiftweasel opens whenever I want to open an internet shortcut.

I'd like to fix this, as I'd like to reinstall firefox and its dependencies--one of them was the help program that comes with ubuntu, and now no help dialogues will open.  Does anyone know the name of this program?

---

### Post by abrichr on 2007-07-18
Ok, so I got a dialogue telling me that the program's name was "Yelp", which I installed, and which installed firefox along with it, which is AGAIN my default browser.

Now:

```
sudo update-alternatives --config x-www-browser

There is only 1 program which provides x-www-browser
(/usr/bin/firefox). Nothing to configure.

```

Although clearly swiftweasel is installed.  I guess I'll have to overwrite the directory contents, as suggested earlier.

---

### Post by abrichr on 2007-07-18
So I overwrote the firefox folder, and now swiftweasel is my default browser... but yelp won't open!  

```
$ yelp
yelp: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory

```

---

### Post by Kilz on 2007-07-18
> **abrichr said:**
> So I overwrote the firefox folder, and now swiftweasel is my default browser... but yelp won't open!  

```
$ yelp
yelp: error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory

```

That is a problem, reinstall firefox or yelp for now. There should be a new version of swiftweasel in a day since firefox2.0.0.5 was just released, perhaps it will fix your issue.

---

### Post by dr_james2k on 2007-09-11
Ok, I found the solution to this.  The thing is gaim uses a html file to redirect, so not only do you need to change the default browser using the previously mentioned methods but also you need to set the default program for html file types to your preffered browser.  
Sorted - and only a year and a half late.

---

