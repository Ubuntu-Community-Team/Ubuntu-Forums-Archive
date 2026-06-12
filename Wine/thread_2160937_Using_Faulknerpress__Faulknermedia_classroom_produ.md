---
title: "Using Faulknerpress / Faulknermedia classroom products"
date: 2013-07-08
forum: Wine
---

### Post by thatsmyboy on 2013-07-08
Just a quick post to say that I was able to get Faulkner online courses (like the [Age of Dinosaurs]("http://www.faulknerpress.com/dinosaurs.shtml") and [Global Perspectives in Biodiversity Conservation]("http://www.faulknerpress.com/conservation.shtml") ) working with a few simple tricks. First off you need to be able to download the software (after purchasing it of course) . 

The website uses browser headers to detect which operating system you are using. I downloaded the User Agent Switcher Firefox Add-On available [here]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/") .

Once that is installed, you can use it to spoof your browser headers as Internet Explorer 8 (Tools Menu > Mouseover 'Default User Agent' > scroll down to Internet Explorer > Internet Explorer 8). Now you should be able to download the software.

Now you should go to the ubuntu software center and download WINE, the Microsoft Windows Compatability Layer Meta Package. This may take a bit but wait for it to install. The basic program is all you'll need.

Once wine is installed, right click on the windows program executable and select 'Open with Wine Windows Program Loader' and follow the dialogs as requested. 

Finally, I found that the sound / video requires MOV and AAC codecs which are available by installing the GStreamer ffmpeg video plugin in Ubuntu Software Center. This should get you up and running.

---

### Post by thatsmyboy on 2013-08-07
Faulkner Press products are pretty antiquated and they tended to crash for me (I tested this out on a Win7 rig also and still lots of crashes). Unfortunately, my courses required the simultaneous use of the [ProctorU online proctoring system]("http://proctoru.com/index.php"). This system allows the proctor to have access to WebCam, Microphone, and shared access to the screen and pointer. When I proceeded to use Proctor U, the proctor could not access ( select with the mouse, type into forms) the Faulkner Media program, which is EXTREMELY frustrating in the midst of a timed exam. This may be something easy to work out, but I had to switch to the Win7 pc to complete the proctored exam. Be Aware, better to be safe than sorry. 

btw Sorry this couldn't be more of a success story - any further suggestions are certainly welcome.

---

