---
title: "Error with MS Outlook 2003"
date: 2011-07-25
forum: Wine
---

### Post by JacquesPotter on 2011-07-25
This is my second thread. My first one was dealing with MS Access 2003 and this one is dealing with MS Outlook 2003. They are both having the same error ("Microsoft Office Access has encountered a problem and needs to close. We are sorry for the inconvenience.") but Outlook runs into the error when I try and import my previous contacts/folders/emails and I'm not able to view all the options when setting up a new email account rendering Outlook useless.
Does anyone have a solution for the problem. Please, my career depends on having easy access to my emails and the calender in Outlook.

---

### Post by IHeequ5i on 2011-07-25
Same advice, same questions.

Go to WineHQ and see what they've got for you. 

Is your Outlook server set up to use POP, IMAP or Exchange? If POP, then you should be able to use any of a variety of email clients. I'm NOT sure about connecting to IMAP or Exchange servers.

---

### Post by Mark Phelps on 2011-07-25
Save yourself the trouble -- ALL the ratings for ALL the versions of outlook posted on the WineHQ site are "Garbage" -- meaning, it's NOT going to work, no matter what you do.

IF you don't believe me, check out the link yourself:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=34]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=34")

---

### Post by haqking on 2011-07-25
> **JacquesPotter said:**
> This is my second thread. My first one was dealing with MS Access 2003 and this one is dealing with MS Outlook 2003. They are both having the same error ("Microsoft Office Access has encountered a problem and needs to close. We are sorry for the inconvenience.") but Outlook runs into the error when I try and import my previous contacts/folders/emails and I'm not able to view all the options when setting up a new email account rendering Outlook useless.
Does anyone have a solution for the problem. Please, my career depends on having easy access to my emails and the calender in Outlook.

If you really want to use MS products then it is best to dual boot or use virtualisation if you experience such problems.

---

### Post by e79 on 2011-07-25
Or you could also try [CrossOver]("http://www.codeweavers.com/products/crossover/"), it is a 'front-end' for Wine but they take care of the prerequisites and hassles for you. I tested/ran Office 2007 with their trial for a month I think and it was working pretty well I must say.

---

### Post by amjjawad on 2011-07-26
Again ... My personal opinion about that was, still and will always be that it's much better to run/install each program/application on its native environment.

Having that said, I will not bother to install something for Microsoft on Linux and vice versa but again, that's only me

---

### Post by Anuovis on 2011-07-26
Thunderbird might be an alternative to Outlook, at least for reading emails. Unless you are really really sure no other software is suitable for the work. Calendars might be incompatible but it doesn't make much of a difference for the mail management.

---

### Post by JacquesPotter on 2011-07-31
I just recently came back to the forum after being too busy this week and I checked with Wine and you are all correct; MS Office 2003 has bad scores all around. 

So, how do I "dual boot or use virtualisation"?  I really need to use MS Office and I only have the license for 2003.

I do have two hd's now, one that I will need to wipe because I think it had a virus.

Also, do I need to start a new thread?

---

### Post by JacquesPotter on 2011-07-31
> **Anuovis said:**
> Thunderbird might be an alternative to Outlook, at least for reading emails. Unless you are really really sure no other software is suitable for the work. Calendars might be incompatible but it doesn't make much of a difference for the mail management.

Does Thunderbird allow you to have multiple folders for different emails? I'm having a problem with Evolution allowing me to have more then one main folder and I can't figure out how to make sure it doesn't delete the emails from the online email service. I have multiple businesses that I work with and I like to be able to have one email addy for each company showing me that I have new email in each one.

---

### Post by e79 on 2011-07-31
> **JacquesPotter said:**
> I just recently came back to the forum after being too busy this week and I checked with Wine and you are all correct; MS Office 2003 has bad scores all around. 

So, how do I "dual boot or use virtualisation"?  I really need to use MS Office and I only have the license for 2003.

I do have two hd's now, one that I will need to wipe because I think it had a virus.

Also, do I need to start a new thread?

Depends on what you want to achieve. Dual boot would give you 2 operating systems but only one OS would be usable at the same time. Installing a virtualization product like [VirtualBox]("http://www.virtualbox.org/") or [VMware Player]("http://www.vmware.com/products/player/") would allow you to use Office 2003 in a Windows virtual machine on your desktop.

For wiping your HD before resusing it, I suggest a hard-drive wiper such as [DBAN]("http://sourceforge.net/projects/dban/") (Darik Boot and Nuke). Boot with it and re-write zeros all over your drive, erasing effectively everything that is on it. You can get DBAN on the '[Ultimate Boot CD]("http://www.ultimatebootcd.com/")' as well.

Hope this helps

---

### Post by amjjawad on 2011-07-31
> **JacquesPotter said:**
> So, how do I "dual boot or use virtualisation"? 

[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by walt.smith1960 on 2011-07-31
If your career truly depends on having Outlook, I would dual boot.  Make sure the Windows  install is absolutely reliable.  Then you can experiment with another install/partition.  I have no personal experience but if you're looking for an Outlook replacement that will work with an Exchange server, does anyone know anything about the this?

[http://davmail.sourceforge.net/thunderbirdmailsetup.html](http://davmail.sourceforge.net/thunderbirdmailsetup.html)

Might be something for the "experimental" partition/install.

---

### Post by JacquesPotter on 2011-07-31
OK. Thanks again everyone. I'm going to give the virtual terminal a try. Ill let you know later today. This is going to be my to-do list for the day.

---

### Post by amjjawad on 2011-07-31
> **JacquesPotter said:**
> OK. Thanks again everyone. I'm going to give the virtual terminal a try. Ill let you know later today. This is going to be my to-do list for the day.

All the best and let us know what will happen with you ;)

---

### Post by Anuovis on 2011-08-02
> **JacquesPotter said:**
> 
 I'm having a problem with Evolution allowing me to have more then one main folder and I can't figure out how to make sure it doesn't delete the emails from the online email service. 

I have multiple businesses that I work with and I like to be able to have one email addy for each company showing me that I have new email in each one.

I think these are two different problems.

1. You don't want the mail deleted, moved or altered on your mailbox when you check it remotely. It's possible.

You can use POP protocol that downloads your email to the computer or just copies it. In this case, you have to warn the program through the settings to leave your original messages as they were and don't delete them. I think it removes them by the default, so be careful.

You could use IMAP which is basically an interface on your PC to access the mailbox. In this case, the folders on your computer and on the mailbox are just synchronized. Probably a better way to do things for you.

This link explains it: [http://www1.umn.edu/adcs/guides/email/imapvspop.html](http://www1.umn.edu/adcs/guides/email/imapvspop.html)
*(note that POP doesn't necessarily remove your messages, it can just copy them to the PC)*

2. You want to access more than one email address and have them neatly  sorted into different folders. Thunderbird can manage multiple mailboxes and  display them separately, they are called *email accounts*.

I also think Evolution is capable of working just as well for you. It also has better out-of-the-box integration with Ubuntu 11.04.

---

### Post by JacquesPotter on 2011-08-02
OK, I have two things to report.

1.  I've finally found a place where I can download a bootable xp so. I'm not too sure on the legal aspect so I won't put down where, but since I have already purchased it I'm not violating any copyrights. I'm just waiting to finish downloading it and I will try the virtual terminal. If I don't like that I will go with a dual boot and use my old hd as a slave to the new one. This will probably take me another few days, but I will let you all know how it goes.

2. As for the Thunderbird/Evolution issue. Thunderbird does just about everything I need it to without being a real hassle to set up like Evolution. So, thanks for the tip on that one.  I've got all my necessary email clients on there now and it seems to be working fine. I still need to set it up so that it doesn't delete the emails on the actual email client, but that's a lot easier then creating a new rule for each email that comes in to go to a specific folder, etc, etc, etc like I have to do in Evolution.  So, between the two, I think Thunderbird get a two thumbs up.

Question to throw out there while we are talking about email programs. Does anyone know of a freeware version of that allows me to create several different emails that would allow me to place a new client's/prospect's email into it and it will shoot an several emails to him/her on a date.

Let me give you an example. I get a new prospect and I have a list of different tutorial emails that I want to send him/her every other day. I would like a program that all I need to do is put the prospects name and email into and the program would automatically send them the emails so I don't have to worry about whether I sent the emails.  

Just a question. Let me know if I should put this in a new thread to receive some good answers since it really doesn't apply to this thread... at least not completely.

Thanks again for all the help and I'll keep you all informed on the other topics.

---

### Post by JacquesPotter on 2011-08-05
> **e79 said:**
> Depends on what you want to achieve. Dual boot would give you 2 operating systems but only one OS would be usable at the same time. Installing a virtualization product like [VirtualBox]("http://www.virtualbox.org/") or [VMware Player]("http://www.vmware.com/products/player/") would allow you to use Office 2003 in a Windows virtual machine on your desktop.

For wiping your HD before resusing it, I suggest a hard-drive wiper such as [DBAN]("http://sourceforge.net/projects/dban/") (Darik Boot and Nuke). Boot with it and re-write zeros all over your drive, erasing effectively everything that is on it. You can get DBAN on the '[Ultimate Boot CD]("http://www.ultimatebootcd.com/")' as well.

Hope this helps

It does. I just got the cd's to download XP 2003. So I will let you know if that works. It may be a couple of days. So don't hold your breath. I've been having to use a friends comp to get my work done which makes for 14+ hr days this week. But this is my only off time project that I've been trying to get done. I haven't had a chance to enjoy the sunshine we've been having around hear. Bummer. But, it is what it is. Thank again for your help and I agree with the install of software with it's native environment. If I could download all the knowledge I need to get around the software issues it would be no problem. But.... ya, I'm sure you understand. So, thanks again for your help.

---

### Post by e79 on 2011-08-06
Ok let us know how it goes for your Office 2003 project. Sorry for the late reply as I was away from home for a couple of days.

 As for the question regarding the automation of sending emails to your prospects, I honestly don't have the answer at the moment but will look into it as soon as I have time.

Cheers

---

### Post by JacquesPotter on 2011-08-06
> **e79 said:**
> Ok let us know how it goes for your Office 2003 project. Sorry for the late reply as I was away from home for a couple of days.

 As for the question regarding the automation of sending emails to your prospects, I honestly don't have the answer at the moment but will look into it as soon as I have time.

Cheers

So far the Office 2003 project isn't going so well. I thought I found a torrent that provided me with a bootable download but I must be doing something wrong because it won't work. I keep getting the black screen of death with the flashing curser in the top left screen. }:| But, I'm still trying.  I'm going to be posting a new thread on Oracle because I can't get it to start either. Damn I'm having the worst luck (lack of skill really) with Ubuntu. Wish I could wave the magic Harry Potter wand and get it fixed. lol.
Thanks for your help and I'll keep y'all posted.

---

### Post by amjjawad on 2011-08-07
> **JacquesPotter said:**
>  Damn I'm having the worst luck (lack of skill really) with Ubuntu. Wish I could wave the magic Harry Potter wand and get it fixed. lol.


You don't need that, you just need to:

- Read More
- Learn from your mistakes
- Time

Good luck ;)

P.S.
If you need, [Luffy ]("http://onepiece.wikia.com/wiki/Monkey_D._Luffy")could help too :P

---

### Post by Elfy on 2011-08-07
Thread moved to Wine.

---

### Post by JacquesPotter on 2011-08-07
I've just posted a new thread ( [http://ubuntuforums.org/showthread.php?p=11128485#post11128485](http://ubuntuforums.org/showthread.php?p=11128485#post11128485) )if any one want's to help. It's related to this thread and the thread [http://ubuntuforums.org/showthread.php?t=1812042](http://ubuntuforums.org/showthread.php?t=1812042).

And, No the thread has not been moved to Wine. I've been there and back again. They informed me to come back here. Thanks though.

---

### Post by JacquesPotter on 2011-08-15
OK, sorry everyone for my absence the last week. I've been busy with many other things that take up more of my time then I can deal with because I don't have my calendering/emailing system and my db. I think we've tried all the ways to get me working. So, even though we have not solved the problem I will mark this thread as solved and move onto the next set of problems in life. 

I do want to sincerely thank everyone for your help. It truly is appreciated!!! I've learned a lot about Ubuntu over the past few weeks that will help me through the times ahead. Thanks again!!

---

