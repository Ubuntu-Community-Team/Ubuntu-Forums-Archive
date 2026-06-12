---
title: "how can clean the tbird - with ++ 11 k mails"
date: 2015-03-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by dilbert_one on 2015-03-05
hello run opensuse 13.1 with tbird and enigmail 

the notebook got 250 gb 

and i do only 40 % of this

but the tbird that fetches mails from the server is full of mails.


how can clean the tbird - with ++ 11 k mails 

what can i do here in this case?

hmm - i could do  empty the Trash folder?
- and afterwards i could compact the message folders

by the way: does it matter how the account is set up in Thunderbird, as POP or IMAP?  
i can check this out  using  menu path Tools->Account Settings->Server Settings->Server Type  at the top right of the dialogue.


[B]
update: [/B]
i have to emty the trash-folder 
i did not compact the messaes-folder yet 
it uses the imap.googlemail.com

what can i do now - are there ways to proceed with this 


i need your help


well one can think of different solutions 

i can do something like to empty the Trash folder?
and of course try to compact the message folders?  like the mozillafreaks describe here [Compacting folders - MozillaZine Knowledge Base]("http://kb.mozillazine.org/Thunderbird_:_Tips_:_Compacting_Folders")
the account setup in Thunderbird,it is IMAP

i found it out using menu path Tools->Account Settings->Server Settings->Servertype at the top right of the dialogue.

well to be frank; 
i have to emty the trash-folder
i did not compact the messaes-folder yet
i use the imap.googlemail.com



i could free up space on the  hard disk by only having a copy of the messages on the IMAP server 
In this case Thunderbird will fetch a message as needed to read it, but won't store it on the hard disk), 
This is described here in depth ://kb.mozillazine.org/Minimize_the_size_of_a_profile

And besides this: as a minimum i could eliminate the all mail folder which doubles the amount of space used to store your messages.

Well and there is another option;  i could decide to keep offline folders enabled and have a Gmail 
IMAP account, uncheck "All Mail" in Tools -> Account Settings -> Account Name -> Synchronization & Storage -> Advanced.

Exit Thunderbird and delete "All Mail." and "All Mail.msf" in the accounts local directory. 
The "All Mail" folder in a Gmail IMAP account has a copy of all messages for that account, 
doubling the number of messages downloaded for offline folder

What is the best way... i  think that that i have all (!!!) messages at gmail too. 
I need the tbird only as an encryption machine. 

note; the tbird runs with enigmail so i do all the pgp-crypted-corresponding with my friend via tbird. 
All the other messages are not necessaryly needed to go into the tbird


question; is there an option that i only fetch the messsages of my friend into the tbird? 
is this doable 

simply filter all the other messages out - and fetch only the messages of one guy from the imap at gmail

dear folks - i love to hear from you 


greetings


**update** : found some other solutions 

on a first glance your both solutions 


[https://webpg.org/](https://webpg.org/)
[https://www.mailvelope.com/](https://www.mailvelope.com/)

look great 
i guess that they will seamlessly integrate on my opensusemachine 
it was sometinmes a hassle to get openpgp and tb to work - 
years ago i had issues with the pinentry and some "assuan-encrypted" files and transfers.

hope that this times are gone. 
**note** i use kpgp to store the the keys - guess that the above mentioned programmes will work with this also... 

regards

---

