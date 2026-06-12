---
title: "Wine bluetooth com setup (and urgent help needed for overwritten file)"
date: 2008-02-18
forum: Wine
---

### Post by chezzo on 2008-02-18
I am trying to get "MyPhoneExplorer" working under Wine, as detailed in this forum:[http://www.fjsoft.at/forum/viewtopic.php?t=2838 ]("http://www.fjsoft.at/forum/viewtopic.php?t=2838")

I have managed to get the actual program running but am having trouble with the Bluetooth steps:

> Start the bluetooth-services:
Code:
[QUOTE]# /etc/init.d/bluetooth start


Then you have search for your mobile phone. For that you should turn of bluetooth at every other device, if there are any. Turn it on on your cell phone and make it visible. Then type the command:
Code:
> # hcitool scan

This command returns a hex-adress which should displace the "00:11:22:33:44:55" in the next command.
Code:
> # rfcomm bind 0 00:11:22:33:44:55

Usually you have to do this every time after restarting. To avoid this, we change a few things in the bluetooth-config file. Therefore open the file with your common texteditor, I'm using kwrite:
Code:
> # kwrite /etc/bluetooth/rfcomm.conf

My rfcomm.conf (I've changed my hex-adress!):
Zitat:
> #
# RFCOMM configuration file.
#

rfcomm0 {
# Automatically bind the device at startup
bind yes;

# Bluetooth address of the device
device 00:11:22:33:44:55;

# RFCOMM channel for the connection
channel 2;

# Description of the connection
comment "Example Bluetooth device";
}

Then you have to restart the bluetoot-services:
Code:
> # /etc/init.d/bluetooth restart


Now we're going to link the device file with a wine device:
Code:
> # cd ~/.wine/dosdevices

Code:
> # ln -is /dev/rfcomm0 com1

Code:
> # yes

Code:
> # chmod 777 com1


Now it should work, but it often doesn't. So start YaST > Hardware > Bluetooth. The Bluetooth-services should be activated and you should set the security-manager to "Local PIN..." und insert a user-defined PIN.

Now the great moments comes closer: the first contact with your mobile phone:
Code:
> # echo "ATZ" > /dev/rfcomm0

Then your phone should ask, if the incomming connection should be permitted. Say yes and if there are any other questions, say also yes. Then the phone should ask for a PIN: Now type the SAME PIN than in YaST. [/QUOTE]

I think the problem may be because the author of the post used SUSE, so some things may be different in Ubuntu. For starters, I do not have a file in /dev/ called rfcomm0... I did a search and found a file in /usr/bin/ called rfcomm and stupidly tried the steps with that instead, resulting in the file being replaced with an executable text file reading "ATZ" rather than the 26.2kb executable it was before. It doesn't seem to have broken anything and bluetooth still works, but i'm a bit worried...

Can anyone please:
a) tell me how to restore my rfcomm file
and
b) tell me how to do it properly

Thank you!

---

### Post by chezzo on 2008-02-18
The crisis is (hopefully) over - I copied the rfcomm file from the live CD back into my /usr/bin folder.

But I'm only back where I started, and still need help with actually making the bluetooth com settings work! Thanks in advance, helpful Ubuntu people :p

---

### Post by chezzo on 2008-02-19
Still haven't figured this out... help appreciated :)

---

### Post by chezzo on 2008-02-25
bump... :(

---

### Post by chezzo on 2008-02-28
bump

---

### Post by chezzo on 2008-03-23
in case anybody gets similar problems and finds themselves here, i should probably note that i fixed the issue (no thanks to these forums...)

Fixed it using this page: [http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/access-your-phone-via-bluetooth-with-ubuntu-gutsy/)

Before I run MyPhoneExplorer I have to run "rfcomm connect 0 XX:XX:XX:XX:XX:XX 2", but that's a minor inconvenience, and I've made a keyboard shortcut for it.

---

### Post by arkashkin on 2009-01-20
thank you! i will try your fix....

---

### Post by wmerrell on 2010-01-30
The link suggested above:

> 
Fixed it using this page: [http://ubuntology.com/2007/10/27/acc...-ubuntu-gutsy/](http://ubuntology.com/2007/10/27/acc...-ubuntu-gutsy/)

Does not work anymore. Does anyone know what it said? I have the problem the OP had and I need to know what he did to fix it.

For my specific problem see this thread: [this tread]("http://ubuntuforums.org/showthread.php?p=8751370&posted=1")

---

### Post by wmerrell on 2010-01-31
bump

---

