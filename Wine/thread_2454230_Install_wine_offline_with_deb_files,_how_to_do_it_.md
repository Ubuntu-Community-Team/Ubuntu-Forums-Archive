---
title: "Install wine offline with deb files, how to do it correctly."
date: 2020-11-25
forum: Wine
---

### Post by kosmicgate on 2020-11-25
Hello!

I want to switch form win to ubuntu 20.04 and started to dl the wine latest stable version. My internet connection is very faulty and give lot
of breaks in connetion. I don't have option to dl it elsewhere via ubuntu. So I have downloaded all the files from Ubuntu/focal/amd 64
and want to make offline instalation in those steps that are described in manual of offline instalation here [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

My question is:

Put all the deb files only without any folder from Ubuntu/focal/amd64(i do have ubuntu 64/ amd computer) at usb stick and
put this command:  cp -R /var/cache/apt/archives/ /media/usb-drive/deb-pkgs/   
Or
sudo -i cd /media/user/flash_drive/ dpkg -i *.deb

???

Summary:
0.is that option possible
1.what to download in my case from wine server
2.what is correct folder naming and structure @ usb pen
3.what command to put in terminal?

Looking forward from You to help me!


Also if this option also work(maybe not), You also can write it in manual at your site. Not everyone do have good working net connction
or access to 2nd ubuntu comp elswhere. This is to less options, if You are thinking to enhance people to switch to ubuntu. I really
do want to enhance for my proposal, and ask for help!

Have nice day!
Lukas

---

### Post by DuckHook on 2020-11-25
Welcome to the forums, kosmicgate.

I'm afraid that your expectations are not realistic.

[list=1]
[*]What you are proposing is technically do&#8209;able, but it is not easy even for Linux veterans. It is simply unrealistic for someone new to Ubuntu.
[*]It is neither wise nor practical to simply follow a list of instructions like some kind of blind recipe. Before embarking on this, you really must educate yourself about system apps like **dpkg** and **sudo**. Given that they are so powerful and given your lack of knowledge, you can and will mess up your whole system using these system calls. You are almost guaranteed to brick your install.
[*]You need to first familiarize yourself with the Linux file structure and the way Ubuntu mounts internal and external media. You need to understand how to type something as simple as a path (i.e: it cannot contain spaces).
[*]It is not possible to walk you through something as complex as you are attempting. You must first understand much more about Linux basics. It is like trying to talk you through assembling a jet engine when you have never before seen a plane.
[/list]
This forum is comprised of end users just like yourself. Many of us have more experience and expertise, but we have no influence on how Ubuntu manuals are written or what they cover. In any case, it is not possible to cover all contingencies no matter who writes the manual. Your case is rare and the workaround that you have linked to assumes a level of Linux knowledge that is high. I cannot help you with it when you are missing so much basic Linux knowledge.

Here is the alternative that I recommend:

Instead of trying to install WINE over your unreliable connection, forget about WINE entirely until you have a better grasp of Linux fundamentals. Start with the links in my sig, especially *Linux is Not Windows*, *A Great CLI Guide* and *Resources for Newcomers*. If you are serious about replacing Windows with Linux, you cannot dream about running the Marathon before you have learned how to walk.

Only when you can navigate your way around Linux, execute commands properly and understand the dangers of **dpkg** and **sudo** should you try something as involved and dangerous as your proposal above.

---

### Post by mastablasta on 2020-11-26
1. this copies downloaded files to USB drive
```
cp -R /var/cache/apt/archives/ /media/usb-drive/deb-pkgs/

```
this is just command to copy the files. you can do that in file manager if it is easier for you.

this command install the files from the USB drive
```
sudo -i cd /media/user/flash_drive/ dpkg -i *.deb

```

you can double click the .deb file in file manager and should be about the same, but in this case command will run all files.
---

1. if connection is bad then talk to provider. why would you pay for a bad connection? if they say they provide 1mbps then that is what they have to provide. my colleague had bad connection. she was calling the provider nearly every day. i think they got tired of calls and fixed it by a relatively major network upgrade.
2. wine might have a snap file as well. snaps are self contained. might be easier option for offline install.
3. when you install windows stuff you will need to add various libraries. they are installed by pulling them off the internet (you usually need internet connection for that). installing wine is (usually) just half the task when you run windows apps on linux.
4. if you can't download apps for linux, how do you update windows then? those files are huge. or you just keep them unpatched with all security holes wide open?
5. you don't need another Ubuntu PC, you just need a USB key with ubuntu on it, then you just boot into a live session on another computer.

6. you could in theory download the whole repository.

---

### Post by DuckHook on 2020-11-26
Thanks for the follow-up mastablasta.

Upon reviewing my earlier post, it occurs to me that, without further explanation, it could come across as being a bit dismissive. Such was certainly not my intent.

However, the OP needs to understand that instructions in the Linux world are presented as templates, not recipes. It doesn't work to just cut and paste a given set of instructions into a terminal. For example, the instruction: ```
cp -R /var/cache/apt/archives/ /media/usb-drive/deb-pkgs/
```…won't work, because the OP's path to his USB drive will not be: ```
/media/usb-drive/deb-pkgs/
```…but something else. In my own case, a sample USB stick required: ```
/media/duckhook/0C99-619F/deb-pkgs/
``` In the template in question, the instructions are especially prone to misdirection and frustration because the -R flag will force the creation of a useless directory in the OP's directory tree that won't even be on his USB stick.

The OP cannot hope to arrive at the synthesis required to modify the template instructions to suit his own installation without at least a rudimentary understanding of Linux paths and mountpoints. Both subjects are beyond the scope of a forum thread.

Hence my recommendation to first brush up on Linux fundamentals.

@kosmicgate

I do wish you success and a happy experience in Ubuntu. But the best path to success consists of learning things one small step at a time. Biting off more than you can chew at the outset will only lead to choking.

The links in my sig that I pointed you to earlier are still excellent ways to start those first steps.

---

### Post by mastablasta on 2020-11-27
and instructions (in this case) are not quite clear that they use generic names.

sometimes you just need to dig in and install the app and move on before you can familiarise with the OS. many people buy smartphones without knowing anything about OS or how it works or similar. then they would use camera and phone dialing app. maybe some SMS messanger and preinstalled facebook app. i wish instruction would always include some form of GUI and CLI. or at least to give better explanation what is happening when typing in the commands.

---

