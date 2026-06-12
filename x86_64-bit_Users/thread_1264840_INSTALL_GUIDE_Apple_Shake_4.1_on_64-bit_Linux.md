---
title: "INSTALL GUIDE: Apple Shake 4.1 on 64-bit Linux"
date: 2009-09-12
forum: x86 64-bit Users
---

### Post by Tibbar49 on 2009-09-12
*These installation directions combine the best of others' advice for installing Shake for Linux, borrowing heavily from scattered conversations on VFXTalk, CGTalk, and Ubuntu Forums. VMware Fusion was used to rapidly test Shake on various Linux distributions.*
           
                 [SIZE=3][COLOR=DarkSlateGray]**Distribution Compatibility**[/COLOR][/SIZE]
               
On some newer 32-bit Linux releases, an X11 library has changed in a way that makes Shake hang. For that reason, we will install a previous [FONT=Courier New]libX11.so[/FONT] version—and there may be other necessary replacements in the future—to circumvent the problem ([COLOR=DarkOrange]Step 2[/COLOR]).  Red Hat Enterprise and CentOS work without this modification.
               
                 Working **32-bit** distributions (this list is not exclusive):
[LIST]
[*]CentOS 5.3 / Red Hat Enterprise
[*]Fedora 7+
[*]Ubuntu 9.04, openSUSE 10+, and others (need an older X11 library, see [COLOR=DarkOrange]Step 2[/COLOR])
[/LIST]
For **64-bit** Linux you may need to install 32-bit legacy compatibility libraries ([COLOR=DarkOrange]Step 2[/COLOR] addendum).
          
           [SIZE=3][COLOR=DarkSlateGray]**Drivers**[/COLOR][/SIZE]
               
Depending on your video card brand, visit ATI, Nvidia, or your notebook manufacturer’s website for hardware OpenGL Linux drivers. You may need to edit the x.conf file for proper behavior. Search the web for more installation hints.
          
           [SIZE=3][COLOR=DarkSlateGray]   **Installing Shake**[/COLOR][/SIZE]   
               
                 [SIZE=3][COLOR=DarkOrange]**1.**[/COLOR][/SIZE] With root privileges create an installation directory.  Common choices are[INDENT]         [FONT=Courier New]/usr/nreal
                       /usr/apple
                       /usr/local/nreal
                       /usr/local/apple[/FONT]
              [/INDENT]Choose whichever convention you prefer but make sure that you adjust the environment variables properly in [COLOR=DarkOrange]Step 4[/COLOR].
               
                 [FONT=&quot]
                [/FONT]  [SIZE=3][COLOR=DarkOrange]**2.**[/COLOR][/SIZE] Depending on your installation media, move/unzip the Shake folder to the installation directory.
               
                 **Ubuntu:** [Download]("http://rpm.pbone.net/") the Fedora Core RPM package [FONT=Courier New]libX11-1.0.3-8.fc7.i386.rpm[/FONT] and extract [FONT=Courier New]libX11.so.6.2.0[/FONT]. Change its name to [FONT=Courier New]libX11.so.6[/FONT] and move it to Shake’s [FONT=Courier New]lib[/FONT] folder. This may work for other Linux distributions that have freezing troubles upon launching Shake. RPM packages can be opened with utilities such as [COLOR=Blue][7-Zip]("http://www.7-zip.org/")[/COLOR] or [COLOR=Blue][alien]("http://kitenet.net/%7Ejoey/code/alien/")[/COLOR].
               
                 **Ubuntu 64-bit:**  We need these shared compatibility libraries when running 32-bit programs under the Debian 64-bit kernel.[INDENT]     [FONT=Courier New]sudo apt-get install ia32-libs[/FONT]
            [/INDENT]A Fedora-based 64-bit OS may need the [FONT=Courier New]compat*[/FONT] libraries, but so far the default installations work.
               
            
                 [SIZE=3][COLOR=DarkOrange]**3.**[/COLOR][/SIZE] Set permissions for the Shake executables. If you don't do this, certain GUI functionality like thumbnail generation won't work.[INDENT]     [FONT=Courier New]chmod 755 * /[...*Shake directory*]/bin[/FONT]
            [/INDENT]**Note:**  Although some of the files in Shake’s [FONT=Courier New]bin[/FONT] directory have [FONT=Courier New].exe[/FONT] suffixes like Windows executables, they are still Linux binaries.
           
           
                 [SIZE=3][COLOR=DarkOrange]**4.**[/COLOR][/SIZE] Set your environment variables so that your system sees Shake properly.
               
                 Open a new shell in your home directory ([FONT=Courier New]/home/username[/FONT]).  For bash, type [FONT=Courier New]vi .bashrc[/FONT].  For tcsh, see the Shake documentation on setting environment variables.  Add the following lines to the bottom of [FONT=Courier New].bashrc[/FONT] and adjust the paths to match your configuration.  If any lines like [FONT=Courier New]PATH[/FONT] already exist, then append to them.  Afterwards, be sure to exit your desktop and re-log in or type source [FONT=Courier New].bashrc[/FONT].[INDENT]     [FONT=Courier New]PATH=$PATH:/usr/nreal/shake-v4.10.0606/bin
                 NR_SHAKE_LOCATION=/usr/nreal/shake-v4.10.0606
                 NR_ICON_PATH=$HOME/nreal/icons
                 NR_INCLUDE_PATH=$HOME/nreal/include
                 LD_LIBRARY_PATH=/usr/nreal/shake-v4.10.0606/lib
            
                 ### omit the next line if running 32-bit Linux ###
            LD_LIBRARYN32_PATH=/usr/nreal/shake-v4.10.0606/lib
            
                 ### always include this last line ###
                 export NR_SHAKE_LOCATION NR_ICON_PATH NR_INCLUDE_PATH
            [/FONT][/INDENT]**64-bit Linux:**  The [FONT=Courier New]LD_LIBRARYN32_PATH[/FONT] environment variable is necessary on 64-bit systems so that Shake knows where to find 32-bit libraries.
                
               
                 [SIZE=3][COLOR=DarkOrange]**5.**[/COLOR][/SIZE] *Optional.*  In your home directory ([FONT=Courier New]/home/username[/FONT]) create the following folders:[INDENT]     [FONT=Courier New]nreal
                 nreal/autosave
                 nreal/icons
                 nreal/include
                 nreal/include/startup
                 nreal/include/startup/ui
                 nreal/settings
            [/FONT][/INDENT]If your environment variables and Shake launch script are set up properly, I believe Shake will automatically create these directories as needed.
            
               
                 [SIZE=3][COLOR=DarkOrange]**6.**[/COLOR][/SIZE] Now open a new shell, type [FONT=Courier New]shake[/FONT], and it should run.  Alternatively, go to Shake's [FONT=Courier New]bin[/FONT] directory and type [FONT=Courier New]csh shake[/FONT] or [FONT=Courier New]./shake[/FONT].  If it hangs or there’s an error then review [COLOR=DarkOrange]Steps 2–4[/COLOR].
               
                 **Ubuntu:**  csh and tcsh aren’t included by default.  You’ll need to download and install the packages:[INDENT]     [FONT=Courier New]sudo apt-get install csh
                 sudo apt-get install tcsh
            [/FONT][/INDENT]**CentOS:  **Because Fedora, CentOS, and Red Hat have a security feature, SeLinux, the following error may appear in relation to a Shake library:[INDENT][FONT=Courier New]cannot restore segment prot after reloc[/FONT]
            [/INDENT]Either disable SELinux and restart, or register each offending Shake library with the security module using the [FONT=Courier New]chcon[/FONT] command.  You may need to log in as [FONT=Courier New]su[/FONT] for this operation.[INDENT][FONT=Courier New]chcon -t texrel_shlib_t [path to Shake library causing error][/FONT][/INDENT]

---

### Post by theZoid on 2009-09-12
Could you give us some information on Shake's functionality...i.e. what it is, what it does, etc.

thanks

---

### Post by falconindy on 2009-09-12
An Apple Shake is a delicious fruit smoothie made mostly with apples. Add a dash of cinnamon for an extreme flavor rush.

No, really. It's video editing software that was discontinued as of about 3 years ago. Any reference to Shake on Apple's website now redirects to Final Cut Pro.

---

### Post by theZoid on 2009-09-12
> **falconindy said:**
> An Apple Shake is a delicious fruit smoothie made mostly with apples. Add a dash of cinnamon for an extreme flavor rush.

No, really. It's video editing software that was discontinued as of about 3 years ago. Any reference to Shake on Apple's website now redirects to Final Cut Pro.

OK...I found that out....:)

---

### Post by muckst3r on 2009-09-18
Loving this - it works a treat. Well done Tibbar49!

---

### Post by Saxcore on 2009-09-18
Awesome thread. Just what i needed; my friend set Shake up for me last time, but i wasn't taking notes.:D

I'm almost there now, but I'm getting a segmentation fault when i execute.. I swear I've followed this guide to the letter, multiple times. Any suggestions?

---

### Post by muckst3r on 2009-10-12
> **Saxcore said:**
> 
I'm almost there now, but I'm getting a segmentation fault when i execute.. I swear I've followed this guide to the letter, multiple times. Any suggestions?

Hello there, I had this happen one one of my installs as well. The cure was for me to re-install the Nvidia drivers from scratch using the latest Linux installer found on their site. It's important to answer 'yes' to the option to build the '32-bit compatibility' libraries.

Try that....

/m

---

### Post by darkman088 on 2009-11-05
Hello everybody,

I'm sorry that I have to post here, but I was not able to find any place, which could be more proper for my problem and some other discussion, which comes closer to my situation.

I'm running Fedora 11, 32 bit and I am trying to install shake.
I have fulfilled ALL the requirements and strictly followed the instructions in this guide and double and trice checked it, but I am still not able to run shake.

I simply write ./shake or csh shake and it just hangs. No window appears, no error. I also tried disabling compiz and the situation is still the same.

PLEASE PLEASE PLEASE help me !! Thanks a lot !!

---

### Post by santx on 2009-11-10
Hi,

Having the same kind of troubles that *darkman088* is talking about, using Apple Shake 4.1 under GNU/Linux Debian Lenny (or/and Sid). I solved my problem by **copying an old** *libX11.so.6* (like it was specified above in the thread, and the one from Debian Etch in my case) in the *./lib* directory from Shake directory.

After that, Shake's main window finally appears, and the software seems to work properly.

---

### Post by AntonyAnimator on 2009-11-10
I think I'm doing something wrong.

I've followed the steps but when I type in shake it says: No test files found

Any ideas would be helpful, i'm fairly new to ubuntu, Thanks

---

