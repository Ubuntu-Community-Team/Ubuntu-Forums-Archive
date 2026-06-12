---
title: "Trouble Copying Wine folder from one computer to another (with a different username)"
date: 2016-10-14
forum: Wine
---

### Post by jdo300 on 2016-10-14
Hi Everyone,

I'm working on making a batch script that will auto-install some software I need on to a bunch of IBM blades running Ubuntu 14.04 LTS. Two of the programs I'm running, FEMM and LTSpice XVII, are windows applications which can run well under Wine. In the section of my script that installs wine, I first install the basic packages (I'm using the older version from the Ubuntu repository due to issues I had - mentioned in [this post here]("https://ubuntuforums.org/showthread.php?t=2339647")).

Here's the commands I'm using for the wine install:```
# Pre-install microsoft fonts package and pre-accept MS EULA licence agreement
echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | sudo debconf-set-selections
sudo apt-get -y install ttf-mscorefonts-installer

# Install Wine
sudo apt-get -y install --install-recommends wine
```

Next, I copy the .wine folder, which I made previously on another Ubuntu 14.04 box running the same version of wine, and change the permissions to the current user:```
# Copy wine folder to home directory
${YELLOW}; echo "Transferring Wine Program Files..."; ${RESET}
cp -r ./wine/.wine ~/.wine

# Change the ownership of the .wine directory from root to the current user
sudo chown -R $USER: ~/.wine
```

The last chunk of code takes some pre-made desktop links (again, from the other machine that I originally installed wine on manually), and copies them to the ~/.local/share/applications and ~/Desktop folders for quick access later:```
# Copy the shortcut files for FEMM and LTSpice to the Desktop
cp ./'wine/FEMM 4.2.desktop' ~/'Desktop/FEMM 4.2.desktop'
cp ./'wine/LTspice XVII.desktop' ~/'Desktop/LTspice XVII.desktop'

# Replace the Username placeholders in the file paths with the current username
sed -i -re 's/\$USER/'$USER'/g' ~/'Desktop/FEMM 4.2.desktop'
sed -i -re 's/\$USER/'$USER'/g' ~/'Desktop/LTspice XVII.desktop'

# Activate the execute bit for the shortcut files
chmod +x ~/'Desktop/FEMM 4.2.desktop'
chmod +x ~/'Desktop/LTspice XVII.desktop'

# Change the ownership of the shortcuts from root to the current user
sudo chown $USER: ~/'Desktop/FEMM 4.2.desktop'
sudo chown $USER: ~/'Desktop/LTspice XVII.desktop'

# Install the shortcuts into the app launcher
desktop-file-install --dir="$HOME/.local/share/applications" ~/'Desktop/FEMM 4.2.desktop'
desktop-file-install --dir="$HOME/.local/share/applications" ~/'Desktop/LTspice XVII.desktop'
```

Now, here comes the fun part. I did a test where I created two identical Ubuntu 14.04 VMs, went through the usual update/upgrade commands. On the first VM, I logged in under a user called rgcluster3blade2; I manually installed wine using the above commands, and then downloaded and ran the installers for the two windows programs, FEMM, and LTspice XVII. I then took the .wine folder that was on that machine, along with the desktop icons, and put them onto a USB flash drive formatted with an ext4 partition to preserve the file permissions. Also on this flash drive was the above script.

Then, I booted up the second VM and logged in under a user called rgcluster3blade1 (point is different username than the first), and then ran the script above to install wine, and copy the .wine folder and desktop shortcuts to the new machine.

When I found was that when clicking the desktop icons, FEMM opened up and worked fine, but when I clicked on the LTspice XVII icon, nothing happened. I then opened up a terminal and typed:

```
wine "C:\Program Files\LTC\LTspiceXVII\XVIIx86.exe"
```

to directly execute the program, but nothing happens. I just pauses for a second and then returns back to the command prompt with no errors or status messages.

So my next suspicion was that it could be related to the fact that the user account names are different, so I booted up a third VM and created a user with the same name as the VM where I manually installed the files. I ran the bash script on it to install wine, and this time, I was able to get both FEMM and LTSpice XVII to open via the desktop icons and terminal.

So my problem *appears* to be related to the difference in user account names, but I'm not sure what to do to fix it. So far, I have tried searching though all the files in the .wine folder and changing all instances of the old username to match the new one, but it didn't appear to work so far. Is there anything else that I'm missing here?

Thanks,
Jason O

---

### Post by jdo300 on 2016-10-15
Hi Everyone,

I found a workaround for my odd problem. As it turns out, the easiest way to handle this situation is to have wine create the .wine folder for you once you install it by calling ```
wineboot --init
```
Next, copy only the specific folders containing the programs you want to run (in my case, I copied the LTC folder from the Program Files directory) over to the new wine folder. Doing it this way, I was able to get LTspice to boot properly. FEMM also had to be treated this way, so I copied its program folder also, but included the mfc90.dll file in the /bin folder since it was complaining about not having it when I tried to launch it.

Problem solved.

- Jason O

---

### Post by howefield on 2016-10-16
Thread moved to the "*Wine*" forum.

---

