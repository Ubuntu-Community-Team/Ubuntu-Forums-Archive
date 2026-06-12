---
title: "Skype Help amd64 MIC issues... please help"
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by Bigb12 on 2009-11-04
I need some help with Skype. I have it installed... the only thing is that It seems that my mic isn't recording... I have tried a few fixes that i have read here and there and still no luck. I have All of the Mic settings turned all the way up in volume control... I have tried everything i can think of. I really need this to work bros... please help me... If it helps I am using 9.04 64bit with amd and nvidia chip sets... Also it is an hp laptop i'm working with and the mic is built in.

---

### Post by Bigb12 on 2009-11-04
bump for justice

---

### Post by Crispin_101 on 2009-11-04
I had the same problem. Went to Sound Recorder and looked at the mic selections. Found Mic 1 selected which didn't work [maybe there wasn't one] so selected Mic2 instead. Cranked up the gain setting slider {File/Open Volume Control/Input} and tried the adjustments available. Test by Recording something and then play back. Easier than making test calls on Skype. When you find out what works, make the same selection using Skype Options.

Hope the above helps.

C.

---

### Post by TheBuzzSaw on 2009-11-04
You have the 64-bit Skype installed, yes?

---

### Post by Bigb12 on 2009-11-05
Correct, I got it from the skype website... It's the 64bit version installed via .deb package installer. Also I went to audio recorder and it doesnt record there either so its not just in skype i guess.... will take screen shots of my mic options in a bit

---

### Post by Bigb12 on 2009-11-05
[http://i35.tinypic.com/2a8mexi.png](http://i35.tinypic.com/2a8mexi.png)
[http://i37.tinypic.com/9lfxo5.png](http://i37.tinypic.com/9lfxo5.png)
[http://i36.tinypic.com/2roolly.png](http://i36.tinypic.com/2roolly.png)
[http://i34.tinypic.com/1117a6w.png](http://i34.tinypic.com/1117a6w.png)
[http://i33.tinypic.com/2q0n34i.png](http://i33.tinypic.com/2q0n34i.png)

---

### Post by Bigb12 on 2009-11-05
bump

---

### Post by timgood on 2009-11-05
When you go into Skype Options and look at sound devices, does it show Pulse Audio as the device? If so you will need to install Pulse Audio Device Chooser and Pulse Audio Volume Control which will allow to to stream output and input to all installed sound devices. This may help.

---

### Post by Bigb12 on 2009-11-05
The only capture options are pulse audio..... Where do i find these  Pulse Audio Device Chooser and Pulse Audio Volume Control... edit: alright i downloaded chooser and contol and they are .tar.gz files..... what do i do from here? Ok I installed it using the apt-get command..... is there anything that i need to change now?

---

### Post by Bigb12 on 2009-11-05
I still cant get any sound to record, this is what it looks like... Its not picking any noise i make..... mic works on windows so its not hardware.... [http://i35.tinypic.com/2l9jms3.png](http://i35.tinypic.com/2l9jms3.png)

---

### Post by timgood on 2009-11-05
In your picture the monitor is showing as having some input and both are muted. Start Skype and make a test call with Pulse Audio Volume Control running. It should show up in both input and output devices. Click on the arrow and choose stream to device (where device is the one you want to use). Also make sure that the levels are set both on the input and output devices and that the channels are not muted. Here is what is looks like in my setup, streaming audio input to USB phone for Skype:

[http://twitpic.com/odatk]("http://twitpic.com/odatk")

---

### Post by Lee2eel on 2009-11-05
I'm not sure if this will solve your problem, but I had the same issue with skype 2.1 and I could not get my mic to work.  The solution:  Uninstall skype 2.1, then install skype 2.0.  Once you do that you will see that you have other options for your input and output.

---

### Post by Bigb12 on 2009-11-06
bump

---

