---
title: "Wine - Excel and Word error"
date: 2012-08-03
forum: Wine
---

### Post by SweetGAPeach on 2012-08-03
Ok, please don't bust me for reposting.  I was advised in another forum to post my question here.  

Please help me.  I am getting the following error message when attempting to launch Microsoft program like Word, Excel, etc.:

**There was an error launching the application.**
Details: Failed to execute child process "/home/chambers/.cxoffice/Microsoft Office 2007/desktopdata/cxmenu/StartMenu.C^5E3A^5Fusers^5Fcrossover^5FStart^2BMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2007" (Permission denied)

Thank you for any help you can provide.  Again, I would told in the other forum that I could not be helped because the person was not an expert in Crossover.  He advised me to move my question here.  Thanks and Elvis has left the building!:guitar:

---

### Post by howefield on 2012-08-03
Post moved to both its own thread and also to the *"Wine"* forum.

---

### Post by Sandertje on 2012-08-03
Looks like that file is set to non-executable. What you can try to do is the following:

Open a terminal 
Then do:
```
cd /home/chambers/.cxoffice/Microsoft Office 2007/desktopdata/cxmenu/StartMenu.C^5E3A^5Fusers^5Fcrossover^5FStart^2BMen u/Programs/Microsoft+Office/
sudo chmod 777 ./Microsoft+Office+Word+2007 
```

---

### Post by SweetGAPeach on 2012-08-03
Thanks, I get an error msg when using this code:

bash: cd: /home/chambers/.cxoffice/Microsoft: No such file or directory
chambers@chambers-System-Product-Name:~$ sudo chmod 777 ./Microsoft+Office+Word+2007

---

### Post by Sandertje on 2012-08-04
Sorry.. didn't notice the spaces in the folder name! 

Here's what should work

```
cd /home/chambers/.cxoffice/Microsoft\ Office\ 2007/desktopdata/cxmenu/StartMenu.C^5E3A^5Fusers^5Fcrossover^5FStart^2BMenu/Programs/Microsoft+Office/

```
then:
```

sudo chmod 777 ./Microsoft+Office+Word+2007
```

---

### Post by SweetGAPeach on 2012-08-04
> **Sandertje said:**
> Sorry.. didn't notice the spaces in the folder name! 

Here's what should work

```
cd /home/chambers/.cxoffice/Microsoft\ Office\ 2007/desktopdata/cxmenu/StartMenu.C^5E3A^5Fusers^5Fcrossover^5FStart^2BMenu/Programs/Microsoft+Office/

```then:
```

sudo chmod 777 ./Microsoft+Office+Word+2007
```

\\:D/\\:D/
OMG!  OMG! OMG!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you! 

THIS WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Thanks for all your help!  You have saved my life!!!!!

Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank  you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!   Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks  you!  Thank you!  Thanks you!  Thank you!  Thanks you! 

Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!  Thank  you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks you!   Thank you!  Thanks you!  Thank you!  Thanks you!  Thank you!  Thanks  you!  Thank you!  Thanks you!  Thank you!  Thanks you!

---

