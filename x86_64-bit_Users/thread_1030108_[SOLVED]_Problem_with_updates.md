---
title: "[SOLVED] Problem with updates"
date: 2009-01-04
forum: x86 64-bit Users
---

### Post by EzEraL on 2009-01-04
Yesterday i try to update by ubuntu 8.10 and see if there are available updates.BUt when i write my pass to update manager it try to download indexed but in number 18 it failed

What should i do?

Sorry for my english

---

### Post by Sef on 2009-01-04
To make sure I understand your message:

1) You have Ubuntu 8.10 installed.

2) Your update failed with number 18.

3) If that is correct, could you please post what #18 says.

---

### Post by EzEraL on 2009-01-04
Method gave invalid 400 URI Failure messageMethod gave invalid 400 URI Failure message

---

### Post by PeeZz on 2009-01-04
Can you specify what program is being downloaded (#18 ).

Maybe you can post the output of the terminal here..

---

### Post by namdung on 2009-01-04
Are u able to connect to internet/ping google.com?

Paste output of the following in terminal
```
sudo apt-get update
```

---

### Post by EzEraL on 2009-01-04
Yes i can connect to internet

When i press in terminal sudo apt-get update i see this

Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid Release.gpg
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release.gpg                      
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Translation-en_US     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid Release                              
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US            
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
E: Method gave invalid 400 URI Failure message                      
E: Method gave invalid 400 URI Failure message

---

### Post by namdung on 2009-01-04
Seems like server issue. 
In *System-->Admin-->Software Sources*, pls change the sources, preferably to **Main Server** instead of the German Server.

This can also be edited in the following file:
```
sudo gedit /etc/apt/sources.list
```

Update repository list after the change
```
sudo apt-get update
```

---

### Post by EzEraL on 2009-01-04
I sude greek server however i change to main server and the same problem exists

Edit:Problem solved.I remove one custom repo that i added  one week ago and now works...

Thx in advance all people

---

