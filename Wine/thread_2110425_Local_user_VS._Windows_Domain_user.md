---
title: "Local user VS. Windows Domain user"
date: 2013-01-30
forum: Wine
---

### Post by mrstaun on 2013-01-30
I succesfully added a Ubuntu to our Windows domain with the 
following AD-bridges
 

• Centrify Express
• Likewise-Open
• Powerbroker IS
 

But for all of them there seem to be an issue with Wine when logged in as a domain user. I can successfully install Wine and install my Windows App. etc. 

 
The problem is now that this application uses the logged in username to verify that the user may start this application and this "fails" and I get the message from our application that this user does not have access.

 
The weird part is then, if I create a local user (with the same username) on the Ubuntu and install Wine, our app. and run it - no worries, works like a charm.

 
If I make a Wine CMD and type SET I have the exact same output regarding username etc.

is there a difference on how Wine works with local created users and a logged on domain user?

---

