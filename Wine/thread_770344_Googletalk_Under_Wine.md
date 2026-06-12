---
title: "Googletalk Under Wine"
date: 2008-04-27
forum: Wine
---

### Post by hannah187 on 2008-04-27
Ok.. I have installed Googletalk under Wine in my Ubuntu 8.04. When I try to sign in this is the error I am getting..[COLOR="Red"]**Connection Error: Could not authenticate with the server**[/COLOR]. Can you please suggest what I need to do. I have a fresh installation of 8.04. It's not that I want to run Googletalk under Wine as I have already configured Pidgin for chatting purpose, however I want to talk to people and not chat hence I want to run googletalk (pity that they do not have a Linux version). Quite happy for anyone to show if there is another way I can talk (not chat) to my gmail, msn and yahoo messenger friends.

Thanks heaps in advance.

---

### Post by kevin11951 on 2008-04-27
this should help with your server issues (are you on 64 bit hardy?)

[http://ubuntuforums.org/showthread.php?t=768021](http://ubuntuforums.org/showthread.php?t=768021)

---

### Post by Aesir09 on 2008-04-27
why use the google talk app for windows when you could:

**Use Pidgin**
1.start up pidgin
2.new account
3.enter google talk account info
4.walla

:guitar:

---

### Post by kevin11951 on 2008-04-27
> **Aesir09 said:**
> why use the google talk app for windows when you could:

**Use Pidgin**
1.start up pidgin
2.new account
3.enter google talk account info
4.walla

:guitar:

he already said he wants to "talk" not "chat"... whatever that means?

---

### Post by programmer8922 on 2008-04-27
I was not able to get gtalk to work in wine but, [Jabbin]("http://sourceforge.net/project/showfiles.php?group_id=166861") worked for me.

---

### Post by hannah187 on 2008-04-27
> **programmer8922 said:**
> I was not able to get gtalk to work in wine but, [Jabbin]("http://sourceforge.net/project/showfiles.php?group_id=166861") worked for me.

thanks again.. so are you saying that you can talk (not chat) with people who are using googletalk with Jabbin? 

I am using 32bit Hardy Desktop version.

---

### Post by programmer8922 on 2008-04-27
> **hannah187 said:**
> thanks again.. so are you saying that you can talk (not chat) with people who are using googletalk with Jabbin? 

I am using 32bit Hardy Desktop version.

Yes, Jabbin is a chat and VoIP client that uses the jabber protocol for voice(i.e. the same protocol as gtalk for the voice feature) and several different protocols for chat. You should be able to download the 32bit .deb file and be talking to your friends in no time.

---

### Post by hannah187 on 2008-04-27
thanks dude..will do that when I go home this eve..

---

### Post by Triscuit713 on 2008-04-27
The short answer is to add the hardy repositories for VOIP enabled Empathy from here:

[https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)

My long answer (and experiences) come at the tail of this thread:

[http://ubuntuforums.org/showthread.php?t=694447&highlight=gtalk](http://ubuntuforums.org/showthread.php?t=694447&highlight=gtalk)

I've never actually heard anyone use Jabbin to chat. It always comes up as a suggestion, but no one says how it worked for them for Gtalk/Jingle Audio Chat.

Plus, Jabbin hasn't been updated since 2007. That doesn't resemble a solution.

---

### Post by hannah187 on 2008-04-28
> **Triscuit713 said:**
> 


your point taken too..let's see..

---

### Post by hannah187 on 2008-04-29
Ok I now have installed Empathy through Synaptic and all the dependencies. However when I start Empathy, I get, "No accounts Configured:
To add a new account, you first have to install a backend for each protocol"

Would appreciate a suggestion what I need to do. Please treat me as a novice Linux user.

---

### Post by Triscuit713 on 2008-04-29
You have to install the appropriate plugins. Install telepathy-gabble. This will allow empathy to sign in to Jabber and Gtalk accounts.

To enable voice, install telepathy-stream-engine (or something to that effect, I can't remember the exact name).

---

### Post by dRock1286 on 2008-04-29
Pidgin works just fine with gtalk...why not use that?

---

### Post by programmer8922 on 2008-04-29
> **dRock1286 said:**
> Pidgin works just fine with gtalk...why not use that?
Because he/she wants to use gtalks voice functions and at this time pidgin doesn't not support VoIP.

---

### Post by hannah187 on 2008-04-29
I think I live another day..cheers guys

---

### Post by hannah187 on 2008-04-30
thanks a ton for all the advices. Now I am able to use Empathy to connect to Googletalk and can chat. However there is no sign of mic. I do not see any button saying call. Fact is I can chat but not able to call. What's next. Anyone..
cheers

---

### Post by Triscuit713 on 2008-05-01
Are you using Ubuntu Hardy Heron?
Did you add the appropriate repositories (i.e. you are not using the default Empathy available in the regular Ubuntu repositories)?
Did you install telepathy-stream-engine?

These questions aren't meant to be demeaning; I am just attempting to double check your steps.

---

### Post by whyette on 2008-05-01
Skype. Go to their website and download the Ubuntu version, and it should work pretty much immediately. It's a .deb, so install should be really easy. I'm testing that on my 64-bit machine now. It won't install for me, because it's an i386 architecture, and my 64 isn't happy about that. If you use a 32-bit, like you said, it will probably work.

---

### Post by Triscuit713 on 2008-05-01
This thread is about VOIP using Gtalk/Jingle. Skype is not compatible with Jingle.

---

### Post by hannah187 on 2008-05-01
> **Triscuit713 said:**
> Are you using Ubuntu Hardy Heron?
Did you add the appropriate repositories (i.e. you are not using the default Empathy available in the regular Ubuntu repositories)?
Did you install telepathy-stream-engine?

These questions aren't meant to be demeaning; I am just attempting to double check your steps.

hey thanks for asking..and totally understand that you are cross checking..
You are right ..I have installed default empathy from Hardy repository. Telepathy-stream-engine 0.4.0-2 is also installed from the repository. And so is telepathy-mission-control, telepathy-gabble, 


And please understand I am not trying to run Skype and do use Pidgin. I like to get connected to Googletalk engine and do voice talk (VOIP) through my Hardy. 

Thanks a lot to all the contributors.

---

### Post by Triscuit713 on 2008-05-01
Telepathy stream engine should be at 0.5.2. The 0.4 version is for Gutsy. However, synaptic should have taken care of this if the repositories were added correctly.

Check to see if your Empathy is version 0.22.1 (through synaptic, ideally). This is the version with VOIP enabled, and this is available for Hardy only.

Because I can't be sure if the repositories were added correctly, here are the instructions to do so:

Start "gksu synaptic" vis the terminal.
Go to Settings->Repositories
Go to Third Party Software
Hit add.
Hit custom.
Enter in this line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

After this information is added to synaptic, it should be reflected in the list of Third Party Repositories.

Close this dialog box.
Hit reload in the main synaptic gui.
You want to install Empathy 0.22.1, telepathy-gabble 0.7.4, and telepathy-stream-engine 0.5. Any versions older than these will not allow Gtalk/Jingle VOIP.

1st edit: Erroneously listed telepathy-gabble 0.7.3

---

### Post by hannah187 on 2008-05-01
am in the office.. sure that I will try this this eve..thanks for helping a new user.. will go a long way..will report my success or failure this eve

---

### Post by karona on 2008-05-02
> **Triscuit713 said:**
> Telepathy stream engine should be at 0.5.2. The 0.4 version is for Gutsy. However, synaptic should have taken care of this if the repositories were added correctly.

Check to see if your Empathy is version 0.22.1 (through synaptic, ideally). This is the version with VOIP enabled, and this is available for Hardy only.

Because I can't be sure if the repositories were added correctly, here are the instructions to do so:

Start "gksu synaptic" vis the terminal.
Go to Settings->Repositories
Go to Third Party Software
Hit add.
Hit custom.
Enter in this line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

After this information is added to synaptic, it should be reflected in the list of Third Party Repositories.

Close this dialog box.
Hit reload in the main synaptic gui.
You want to install Empathy 0.22.1, telepathy-gabble 0.7.3, and telepathy-stream-engine 0.5. Any versions older than these will not allow Gtalk/Jingle VOIP.

Tried it,I've got the right repositories but it doesn't seem to work. Problem from my end maybe?  I can log into gtalk but VOIP isnt enabled

---

### Post by hannah187 on 2008-05-02
same here.. got the most upto date versions now..

Empathy: 0.22.1
telepathy-gabble: 0.7.4-1
telepathy-mission-control: 4.65-1
telepathy-stream-engine: 0.5.2-1

can see the mic icon now however no VOIP as yet.. cannot talk or hear a thing through Googletalk..

---

### Post by amendt on 2008-05-02
> **Triscuit713 said:**
> Telepathy stream engine should be at 0.5.2. The 0.4 version is for Gutsy. However, synaptic should have taken care of this if the repositories were added correctly.

Check to see if your Empathy is version 0.22.1 (through synaptic, ideally). This is the version with VOIP enabled, and this is available for Hardy only.

Because I can't be sure if the repositories were added correctly, here are the instructions to do so:

Start "gksu synaptic" vis the terminal.
Go to Settings->Repositories
Go to Third Party Software
Hit add.
Hit custom.
Enter in this line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

After this information is added to synaptic, it should be reflected in the list of Third Party Repositories.

Close this dialog box.
Hit reload in the main synaptic gui.
You want to install Empathy 0.22.1, telepathy-gabble 0.7.3, and telepathy-stream-engine 0.5. Any versions older than these will not allow Gtalk/Jingle VOIP.
I did this, but I still get ** (empathy:7000): DEBUG: mission_control_get_presence_actual: MC not running.

Now if I just knew what "MC" stands for.

---

### Post by programmer8922 on 2008-05-02
Have you tried testing your mic in some other program to make sure it is working. I doubt that would be a problem, but you never know.

---

### Post by Triscuit713 on 2008-05-02
> 
can see the mic icon now however no VOIP as yet.. cannot talk or hear a thing through Googletalk..


Can you describe in more detail what happens?

Do you do the following?
1. Find a person who is "talk-enabled", for lack of a better term ,in your buddy list
2. Click the mic in the buddy list
3. The talk dialog pops up, stating the current status of the call. This dialog looks nothing like the chat dialog.
4. Eventually, the status changes from "Ringing" to "Connected"
5. At this point, each party should hear each other.


> 
I did this, but I still get ** (empathy:7000): DEBUG: mission_control_get_presence_actual: MC not running.

Now if I just knew what "MC" stands for.


This, I'm not sure about, since I've never had this error before. I have suggestions, but they're hunches and I can't back them up with reasons.

MC stands for mission-control. It connects your accounts online. If mission-control isn't running, then you can't connect online.

My first hunches are all the simple ones:
1. remove old config information from your home directory (I THINK they are in ~/.empathy and ~/.tapioca, but I am not sure. I will find out later)
2. Restart your user session

I will keep an eye out for other solutions, but the majority of my information comes from [http://live.gnome.org/Empathy]("http://live.gnome.org/Empathy") and the mailing list there.

---

### Post by hannah187 on 2008-05-02
> **Triscuit713 said:**
> Can you describe in more detail what happens?

Do you do the following?
1. Find a person who is "talk-enabled", for lack of a better term ,in your buddy list
2. Click the mic in the buddy list
3. The talk dialog pops up, stating the current status of the call. This dialog looks nothing like the chat dialog.
4. Eventually, the status changes from "Ringing" to "Connected"
5. At this point, each party should hear each other.



Ok.. again first of thanks heaps. I am attaching a screen shot here. To answer your query:
1. Yes My contacts are talk enabled. I can see mic against the contacts
2. I can click the mic aginst my buddies name.
3. Talk dialog pops up and starts ringing my buddy
4. Status never gets connected as I cannot hear them.
5. Cannot talk.

To add a bit more, my mic works as I have tried it in my other machine with XP and Googletalk installed. Also sound is enabled in my Ubuntu machine

thanks a ton again

---

### Post by Triscuit713 on 2008-05-02
> 
4. Status never gets connected as I cannot hear them.
5. Cannot talk.


The status should eventually say "Connected" regardless of whether you can hear the other party. This has to happen first before you can address audio issues. (Because you can't even try to talk to someone if they haven't picked up the phone, to use an analogy).
Is your buddy using the official Gtalk client? Ask him/her if they get the calling prompt. Are they accepting the call?


As to whether or not your mic inputs work in Ubuntu...

Empathy uses gstreamer to register mic input. The gstreamer input plugin I use to register sound is the pulseaudio plugin. You can test whether or not you are actually being recorded by doing the following:

0. Go to System->Preferences->Sound, and set sound capture to "Pulseaudio Server".

1. Open Applications->Sound & Video->Sound Recorder
2. Try recording from your mic.
3. Play back what you recorded

Alternatively, you can install the package padevchooser through synaptic. Then 

1. Go to Applications->Sound & Video->Pulseaudio Device Chooser. In your Notification Area, an audio plug will show up. 
2. Left click on it, and on the drop down menu, select "Volume Meter (recording)". 
3. Speak into your mic and you should see the meter jump.



And as for the config directories to remove to help get mission control running, they are 

.gnome2/Empathy/
.mission-control

---

### Post by hannah187 on 2008-05-05
> **Triscuit713 said:**
> 

Empathy uses gstreamer to register mic input. The gstreamer input plugin I use to register sound is the pulseaudio plugin. You can test whether or not you are actually being recorded by doing the following:

0. Go to System->Preferences->Sound, and set sound capture to "Pulseaudio Server".

1. Open Applications->Sound & Video->Sound Recorder
2. Try recording from your mic.
3. Play back what you recorded




Ok see my Volume control / sound preference as attached.. did record the sound but could not hear back anything when I played back.

---

### Post by Triscuit713 on 2008-05-09
Sorry I didn't reply soon.

Can you perform the second set of instructions I posted. (the set involving installing padevchooser). In fact, could you post a screenshot of "volume meter (recording" from padevchooser?

Also, can you make sure that your mic isn't muted. I assume it's attached to the "sound fusion cs46xx". It's in the recording tab of the volume control panel you posted before. You may have to enable it from the file menu.

I actually think this is your problem. Presuming, your mic is plugged into the correct jack (the pink/red one), then your mic is probably muted.

---

### Post by vigyani on 2008-05-14
> **Triscuit713 said:**
> The short answer is to add the hardy repositories for VOIP enabled Empathy from here:

[https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)

My long answer (and experiences) come at the tail of this thread:

[http://ubuntuforums.org/showthread.php?t=694447&highlight=gtalk](http://ubuntuforums.org/showthread.php?t=694447&highlight=gtalk)

I've never actually heard anyone use Jabbin to chat. It always comes up as a suggestion, but no one says how it worked for them for Gtalk/Jingle Audio Chat.

Plus, Jabbin hasn't been updated since 2007. That doesn't resemble a solution.


Hi
I installed Jabbin on 8.04. Chat works. Whenever I tried to make a voice call it crashes. Could not use.

I used jabbin_2.0.1-20080208-4_i386.deb from the website: [http://code.google.com/p/jabbin-svn-pack-kubuntu/]("http://code.google.com/p/jabbin-svn-pack-kubuntu/")

It installs on 8.04. 

I referred the website at [http://www.freesoftwaremagazine.com/columns/how_to_make_jabber_calls_using_jabbin]("http://www.freesoftwaremagazine.com/columns/how_to_make_jabber_calls_using_jabbin") 

On Ubuntu 8.04 updated version installed Empathy:

Added the following repository:

   deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

Then installed the following packages (latest version); 
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-engine

Voice works great; I can voice chat with all Google talk friends.
 
regards
Vig

---

### Post by niharsm on 2008-05-14
Hi all,

I got gtalk chat to work with empathy. I can make calls and voice works properly. However i have no option to answer call. I get a notification of the call but I am not able to answer it.

Thanks
Nihar

---

### Post by Triscuit713 on 2008-05-16
Answering calls has been problematic for me as well.

Clicking on the notification icon when someone is calling (and it has turned to a microphone) you opens the call window. Please note back if this works reliably for you.

---

### Post by niharsm on 2008-05-16
yeah it does open up the call window. However the call isn't answered.

---

### Post by rykel on 2008-05-19
People,

Thanks for starting this thread... I am trying to receive GoogleTalk calls in Linux also, and found out that all the SIP softphones (Wengo, Pidgin) can only IM, not talk with GoogleTalk.

I am trying to receive calls from gtalk2voip but without GoogleTalk or something similar, I cannot do so.

After reading this thread, am I right to say that there are 2 possible options to deal with this issue, namely Empathy with Telepathy, and Jabbin?

btw, for those who *still* do not get it, I am not trying to chat (ie. message) with GoogleTalk users, but to call (as in phonecall) them; and I am not using Skype for this purpose because Skype is CLOSED source and uses a CLOSED calling system.   :)

Thanks for all!

UPDATE 20 May 2008: When I tried "RADIO 100" (a service of gtalk2voip), Empathy flashes a Microphone icon in the task tray. BUT, upon clicking it (both left and right-clicks) nothing happens. No popup dialogs whatever. ie. CANNOT receive incoming calls.

---

### Post by Triscuit713 on 2008-05-24
> 
yeah it does open up the call window. However the call isn't answered.


Calls are not automatically answered. You have to press the "start call" button in the call prompt.

Unfortunately, there are moments for me when this doesn't work. The "start" and "stop" buttons are greyed out. I don't know the conditions that cause this to happen - and the only solution I have found is to log out of my session, log back in, and try again to be called.

---

### Post by whbarb on 2008-05-29
hello
I have the same problem. I managed to install empathy and connected to gtalk, voice calls work, but my mic doesn't work. I can record sounds fine in gnome-sound-recorder and can see record level in pulse audio meter (as above) also fine. But empathy doesn't send my voice to buddy. I has tried to delete anything related to empathy/telepathy in home directory. It has no effect.   

What could I try to enable outgoing voice in empathy?


thanks

---

### Post by d-_-b.za on 2008-06-01
> **Triscuit713 said:**
> Telepathy stream engine should be at 0.5.2. The 0.4 version is for Gutsy. However, synaptic should have taken care of this if the repositories were added correctly.

Check to see if your Empathy is version 0.22.1 (through synaptic, ideally). This is the version with VOIP enabled, and this is available for Hardy only.

Because I can't be sure if the repositories were added correctly, here are the instructions to do so:

Start "gksu synaptic" vis the terminal.
Go to Settings->Repositories
Go to Third Party Software
Hit add.
Hit custom.
Enter in this line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

After this information is added to synaptic, it should be reflected in the list of Third Party Repositories.

Close this dialog box.
Hit reload in the main synaptic gui.
You want to install Empathy 0.22.1, telepathy-gabble 0.7.4, and telepathy-stream-engine 0.5. Any versions older than these will not allow Gtalk/Jingle VOIP.

1st edit: Erroneously listed telepathy-gabble 0.7.3

Thanks,Triscuit713. It worked for me and I could make jingle calls using empathy.
  
> **whbarb said:**
> hello
I have the same problem. I managed to install empathy and connected to gtalk, voice calls work, but my mic doesn't work. I can record sounds fine in gnome-sound-recorder and can see record level in pulse audio meter (as above) also fine. But empathy doesn't send my voice to buddy. I has tried to delete anything related to empathy/telepathy in home directory. It has no effect.   

What could I try to enable outgoing voice in empathy?


thanks

But like whbarb I had problems setting up pulse audio after a bit of googling I found the following link: [Skype Microphone problem and complete pulse audio setup in Ubuntu]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")

Yes I know we don't want to run skype and rather gtalk/jingle ;) but just follow the tutorial to setup pulse audio correctly.

Regards,

---

### Post by whbarb on 2008-06-03
> **d-_-b.za said:**
> 

But like whbarb I had problems setting up pulse audio after a bit of googling I found the following link: [Skype Microphone problem and complete pulse audio setup in Ubuntu]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")

Yes I know we don't want to run skype and rather gtalk/jingle ;) but just follow the tutorial to setup pulse audio correctly.


Unfortunately, it doesn't work for me... Skype works well, but empathy mic stays not working :(

---

### Post by d-_-b.za on 2008-06-03
> **whbarb said:**
> Unfortunately, it doesn't work for me... Skype works well, but empathy mic stays not working :(

Ok whbarb I'm no expert but but maybe I can help. So you installed pulse audio and have the icon in your top panel?

[SIZE="4"]Step 1:[/SIZE]

Can you do playback on pulse audio? 

To test this click on the pulse audio icon. Select **"Manager..."**, the **"PulseAudio Manager"** will open and the last tab will be **"Sample Cache"**. Go to the tab and you will see a play button in the bottom left corner. Click it and you will hear a sample of music play.

If that works we know your playback is setup correctly now to test the mic.

[SIZE="4"]Step 2:[/SIZE]

In the** "Manager"** window again you will see a **"Devices"** tab. Select it and you will see a list of devices

[IMG]http://ubuntu-utah.ubuntuforums.org/attachment.php?attachmentid=72823&stc=1&d=1212524304[/IMG]

there should be a **"Sources"** drop down. Under that drop down you will find a **"*input*capture*"** device. Select it and go to properties.

Under the properties window you will see some basic info about the device and a **"Show volume meter"** button select it and a meter window will appear. 

[IMG]http://ubuntu-utah.ubuntuforums.org/attachment.php?attachmentid=72828&stc=1&d=1212524559[/IMG]

Now tap on your mic and look if it gets registered on the meter(Also make sure the mic work, by testing it on another computer or device).

[SIZE="4"]Step 3:[/SIZE]

If that doesn't work make sure your mic is selected as a input source. You do this by double clicking the default speaker icon in your top panel and the **"Volume Control"** window will open

[IMG]http://ubuntu-utah.ubuntuforums.org/attachment.php?attachmentid=72824&stc=1&d=1212524304[/IMG]

Now the there should be a **"options"** tab if not select the **"edit"** menu and choose **"preferences"**. 

[IMG]http://ubuntu-utah.ubuntuforums.org/attachment.php?attachmentid=72826&stc=1&d=1212524304[/IMG]

A window will open and select all the **"input sources"** and **"*Mic*"** items/tracks from the list.

Close the window and a **"Options"** tab should be available. in the options tab make sure all your "input sources"/tracks are selected to use the mic.

[IMG]http://ubuntu-utah.ubuntuforums.org/attachment.php?attachmentid=72825&stc=1&d=1212524304[/IMG]

After you done that go back to step 2 and see if you get input on the mic by now. If that doesn't work make sure you changed all your input sources and tracks as in step 3.

Hope it helps,

---

### Post by whbarb on 2008-06-04
Thank you, d-_-b.za, for helping. Yes I can hear from PulseAudio and can see PulseAudio Volume Meter correctly. As soon as I spell into mic I see progressbar moving. Also I can hear myself if I unmute mic in sounds settings (Playback tab), so it seems that everything is ok, but not in empathy...

---

### Post by d-_-b.za on 2008-06-04
> **whbarb said:**
> Thank you, d-_-b.za, for helping. Yes I can hear from PulseAudio and can see PulseAudio Volume Meter correctly. As soon as I spell into mic I see progressbar moving. Also I can hear myself if I unmute mic in sounds settings (Playback tab), so it seems that everything is ok, but not in empathy...

Ok this is just a wild stab in the dark. But make a call using empathy to a google talk buddy. As soon as you have a active connection, open your Pulse Audio Manager and go to the "Devices" tab. It should show a "Record stream" under your input sources.

[IMG]http://ubuntu-utah.ubuntuforums.org/attachment.php?attachmentid=72961&stc=1&d=1212616602[/IMG]

If you select the "Record Stream" and click on the "properties" button it will show you more info. Your client should be "telepathy-stream-engine"
" and you can also use the "Go to source" button to change the volume of your mic.

The above is not a solution but only a attempt from my side to diagnose the problem. So maybe attach a screen shot of your properties window.

Regards,

Ps. just to check again you made sure you removed all your old telepathy and empathy packages and only installed packages from "deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main"?

---

### Post by xebian on 2008-06-04
> **hannah187 said:**
> Ok.. I have installed Googletalk under Wine in my Ubuntu 8.04. When I try to sign in this is the error I am getting..[COLOR="Red"]**Connection Error: Could not authenticate with the server**[/COLOR]. Can you please suggest what I need to do. I have a fresh installation of 8.04. It's not that I want to run Googletalk under Wine as I have already configured Pidgin for chatting purpose, however I want to talk to people and not chat hence I want to run googletalk (pity that they do not have a Linux version). Quite happy for anyone to show if there is another way I can talk (not chat) to my gmail, msn and yahoo messenger friends.

Thanks heaps in advance.

I'm sure you may have heard of the Skype Linux version. If it doesn't suits you, I suggest virtual box/windows.  Works very well for me.  Never found a working solution for gtalk under wine.  Look in wineHQ forum too.

---

### Post by vigyani on 2008-06-05
I am using Empathy on Ubuntu 8.04 to voice chat with Googletalk user. It works fine.

For all the instructions at one place check:
[http://ubuntuforums.org/showpost.php?p=5118375&postcount=1]("http://ubuntuforums.org/showpost.php?p=5118375&postcount=1")

When I receive a call, on the panel mic icon flashes. Click on that and you should be able to receive a call.
Cheers

---

### Post by whbarb on 2008-06-05
Thanks for attention.

So I tried again and made everything you requested, this is my screenshot [http://picasaweb.google.ru/kirpublic/Screenshot]("http://picasaweb.google.ru/kirpublic/Screenshot")


By the way, now gnome-recorder has failed with recording too, when I try to play my voice it says something like "no sound tracks".

P.S. Yes I use "deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main" as source, there was no voice support with standard Ubuntu repository.

---

### Post by hannah187 on 2008-08-19
I am visiting this post of mine after a little while. Pretty much followed everything about Pulse Audio setup. Yes I have all the latest version of Empathy and do have Telepathy repository in my software sources under Synaptic. 

Do have the following repository:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

And have the latest version of the following packages (latest version);
Empathy
telepathy-gabble
telepathy-mission-control
telepathy-stream-enginetalk but they 

Have set up the Pulse Audio as well. Can hear my friends on Google talk but they cannot hear me. Same issue with Skype as well. I believe that input from my Mic is not working. By the way the hardware is fine as I cannot use googletalk in my Windows to speak these same friends.

Yeah.. still not much luck..
One of these days I suppose

---

### Post by hacunha on 2008-09-09
Hi Everyone. I have read the hole tread in order to setup a IM that would make voice calls using gtalk.
I have Ubuntu 8.04 installed on  my system. My Skype works fine if I use my default audio device.
I have a Bluetooth Motorola USB toogle and a Motorola HS820 headset. I bonded and connected the headset. But when I use skype, I can hear the ring sound but even when the contact answers the call I still only hear the ring sound.
On Empathy 2.23.6, the first call fine if using the default audio device. But the my internet connection went down and after that I could only be heard by the same user, and I could not hear him. I also tried to used the bluetooth headset on Empathy but I did not work.

Does any one have an ideia on how to use bluetooth headset on voip calls using Skype and Empathy?

Thanks for everyone help.
My contact on skype is hacunha. On Gtalk [email]hacunha@gmail.com[/email]. Feel free to contact me.

Thanks again
Hank.

---

### Post by himanshuprakash on 2009-02-23
pidgin does not support voice/vedio chat, i guess wine+gtalk enables us..

> **Aesir09 said:**
> why use the google talk app for windows when you could:

**Use Pidgin**
1.start up pidgin
2.new account
3.enter google talk account info
4.walla

:guitar:

---

### Post by 1kenthomas on 2011-11-10
You can install Google Talk as a Chrome plugin ... seems the best option ATM.

---

