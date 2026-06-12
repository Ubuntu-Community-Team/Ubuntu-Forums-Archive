---
title: "why wont java runtime install?!?!"
date: 2007-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by -=Viper=- on 2007-07-12
ok here is the deal...every time i click it it says it is in the wrong formating.  There is a picture of what it says that i linked.  can someone explain how to fix this??

---

### Post by -=Viper=- on 2007-07-12
screw it...i think i will just downgrade to the i386...it maes more sense.   My only problem is i lose my wireless AGAIN.  does anyone have a solution...i will start the reload in 20-30 min if i dont get some help :P

---

### Post by bluemech on 2007-07-12
Have you run this from the command line?

```
cd ~/Desktop
./jre-6ul-linux-amd64.bin
```

As far as I know you don't run bin files in gedit. You may have changed the default program for opening bin files somehow.

---

### Post by -=Viper=- on 2007-07-12
if i cant run bin then how do people get java on tehre machines?? i kinda need it :S

---

### Post by bluemech on 2007-07-12
> **-=Viper=- said:**
> if i cant run bin then how do people get java on tehre machines?? i kinda need it :S

I forgot a line there earlier, this should do it:

```
cd ~/Desktop
sudo chmod +x jre-6ul-linux-amd64.bin
./jre-6ul-linux-amd64.bin
```

---

### Post by -=Viper=- on 2007-07-12
nope...it just said

```
ernesto@Ernesto-laptop:~$ cd ~/Desktop
ernesto@Ernesto-laptop:~/Desktop$ sudo chmod +x jre-6ul-linux-amd64.bin
Password:
chmod: cannot access `jre-6ul-linux-amd64.bin': No such file or directory
ernesto@Ernesto-laptop:~/Desktop$ 




```

---

### Post by YoG%*@ on 2007-07-12
hi,

> **-=Viper=- said:**
> nope...it just said

```
ernesto@Ernesto-laptop:~$ cd ~/Desktop
ernesto@Ernesto-laptop:~/Desktop$ sudo chmod +x jre-6ul-linux-amd64.bin
Password:
chmod: cannot access `jre-6ul-linux-amd64.bin': No such file or directory
ernesto@Ernesto-laptop:~/Desktop$ 

```


well, is the file still on your desktop? did you spell it correctly? 

mux

---

### Post by kuja on 2007-07-12
Why install with the bin anyway? You can always just "sudo apt-get install sun-java6-jre" afterall.
Also, I've seen that (very, very rare) weird problem before. It seems to only effect .bin files. Try running it with a different shell (ie: ash, csh, zsh - just something else).

---

### Post by mhenriday on 2007-07-12
> **bluemech said:**
> I forgot a line there earlier, this should do it:

```
cd ~/Desktop
sudo chmod +x jre-6ul-linux-amd64.bin
./jre-6ul-linux-amd64.bin
```

**Bluemech**, I tried to use this method on **Sun**'s latest **JRE** update (using the **bin** file because that is what **Sun** itself provides), which I had downloaded to my desktop, with the following results :```
mhenriday@mhenriday-desktop:~$ cd ~/Desktop
mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod +x jre-6u2-linux-amd64.bin
mhenriday@mhenriday-desktop:~/Desktop$ ./jre-6u2-amd64.bin
bash: ./jre-6u2-amd64.bin: Filen eller katalogen finns inte
mhenriday@mhenriday-desktop:~/Desktop$ ./jre-6u2-linux-amd64.bin./jre-6u2-linux-amd64.bin: line 1: syntax error near unexpected token `<'
./jre-6u2-linux-amd64.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

```

I fail to understand wherein the «syntax error» consists ; can you - or some other kind reader - help me out ?...

Henri

---

### Post by Mr_bleu on 2007-07-12
The name of  java file Should be jre-6u1-linux-amd64.bin.   It looks to me that you've mistyped the file name.  "***./jre-6u2-amd64.bin***"  I've downloaded from Sun's website. 
 "[B][I]
mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod +x jre-6u2-linux-amd64.bin[/I][/B]" 
The command I've seen and used is:
$sudo chmod a+x jre-6u1-linux-amd64.bin
(that could be the syntax error you're getting)
Hope this helps, there are tons on java in this forum if you type it into the search box.

---

### Post by jpkotta on 2007-07-12
[Use the wiki.]("https://help.ubuntu.com/community/Java")

Even though it's unintuitive to chmod a file to run it, as opposed to just double clicking it, it is most definiately a Good Thing.  It should not be easy to run arbitrary executables, make the user think about it first.

---

### Post by bluemech on 2007-07-12
> **-=Viper=- said:**
> nope...it just said

```
ernesto@Ernesto-laptop:~$ cd ~/Desktop
ernesto@Ernesto-laptop:~/Desktop$ sudo chmod +x jre-6ul-linux-amd64.bin
Password:
chmod: cannot access `jre-6ul-linux-amd64.bin': No such file or directory
ernesto@Ernesto-laptop:~/Desktop$ 




```

Oh crap. I'm sorry. Did you copy what was in the code box? I made a mistake... again. I thought the **1** in the *jre-6u**1**-linux-amd64.bin* filename was an **L**... it looked like that at first glance. :/

That's why if you copied my code, it couldn't find it, because there was no file named like that to begin with. That's what I get for using the tab key to autocomplete my command line inputs. But here, I'm sure this should do it now, unless your system has some funky specialized problem we don't know about. ;)

```
cd ~/Desktop
sudo chmod +x jre-6u1-linux-amd64.bin
./jre-6u1-linux-amd64.bin
```

**mhenriday**, **Mr_bleu** is right. Check the filenames of the things you type in. Look what happened to me.

---

### Post by mhenriday on 2007-07-14
> **Mr_bleu said:**
> The name of  java file Should be jre-6u1-linux-amd64.bin.   It looks to me that you've mistyped the file name.  "***./jre-6u2-amd64.bin***"  I've downloaded from Sun's website. 
 "[B][I]
mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod +x jre-6u2-linux-amd64.bin[/I][/B]" 
The command I've seen and used is:
$sudo chmod a+x jre-6u1-linux-amd64.bin
(that could be the syntax error you're getting)
...
Thanks **Mr_bleu** och **bluemech**, for your speedy replies ! But as I tried to indicate in my origial message, the latest update from **Sun** is number 2, which is the one I downloaded to my desktop. Moreover, just to avoid the type of error which **bluemech** discusses, when I filled in the java file in the command line, I copied it directly from my desktop. Thus I am pretty sure that **jre-6u2-linux-amd64.bin** is the correct name. Besides, if the file I was trying to install didn't exist, I think the error message I received would not have been of the type > syntax error near unexpected token `<'
./jre-6u2-linux-amd64.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'
Alas, I don't understand to what the «unexpected token `<'» can refer - I can't seem to find any '<' anywhere !...

**Mr bleu** indicated that permissions should be extended to _all_ users ; i e, **sudo chmod a+x jre-6u1-linux-amd64.bin** rather than **sudo chmod +x jre-6u1-linux-amd64.bin**. Even if I had difficulty understanding how this could make any difference, I decided to try it, but alas, the result was not entirely encouraging :> mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod a+x jre-6u2-linux-amd64.bin
Password:
mhenriday@mhenriday-desktop:~/Desktop$ ./jre-6u2-linux-amd64.bin
./jre-6u2-linux-amd64.bin: line 1: syntax error near unexpected token `<'
./jre-6u2-linux-amd64.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'Where do I go from here ?...

Henri

PS : As to why one should be interested in maintaining **Java**-programmes as updated as possible, here's the word from the **[horse's mouth]("http://sunsolve.sun.com/search/document.do?assetkey=1-26-102934-1")**....

---

### Post by jpkotta on 2007-07-15
Are you sure you downloaded a bin file and didn't save the webpage as a file named ...bin?  That gibberish looks like HTML.  You may need to right click the link and do "Save Target As" (or similar).

Edit: On second thought, it looks like an error webpage.  Try downloading again.

---

### Post by Mr_bleu on 2007-07-15
At my last posting, jre version was 1, not 2, from www.java.com's website.  Please post the link where you're downloading jre2 from.  I'd like to try that version to see if I get the same error message.

---

### Post by mhenriday on 2007-07-17
> **Mr_bleu said:**
> At my last posting, jre version was 1, not 2, from www.java.com's website.  Please post the link where you're downloading jre2 from.  I'd like to try that version to see if I get the same error message.Here's the [*link*]("http://tinyurl.com/39nnp7") to  **Sun**'s download centre. Scroll down to near the bottom to pick up the download for **Linux x64 Platform - Java(TM) SE Development Kit 6 Update 2**. Note the name change - the first time I visited this page, the [*Linux x64 self-extracting file (build 05)*]("http://192.18.108.206/ECom/EComTicketServlet/BEGINF82B6BA7E3D1878C4973BFAC151784EE/-2147483648/2246474847/1/838358/838334/2246474847/2ts+/westCoastFSEND/jdk-6u2-oth-JPR/jdk-6u2-oth-JPR:14/jdk-6u2-linux-amd64.bin") was referred to as «**jre-6u2-linux-amd64.bin**», whereas now it is called « **jdk-6u2-linux-amd64.bin**». Be that as it may, I still get that charming «syntax error» when trying to install :> mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod +x jdk-6u2-linux-amd64.binPassword:
mhenriday@mhenriday-desktop:~/Desktop$ ./jdk-6u2-linux-amd64.bin
./jdk-6u2-linux-amd64.bin: line 1: syntax error near unexpected token `<'
./jdk-6u2-linux-amd64.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'Not encouraging at all ! Still, to the dull, learning comes hard - I hope you can come with some suggestion that can help me to resolve the problem and advance my understanding of **Linux** a millimetre or two....

Henri

---

### Post by sel on 2007-07-17
> **mhenriday said:**
> Here's the [*link*]("http://tinyurl.com/39nnp7") to  **Sun**'s download centre. Scroll down to near the bottom to pick up the download for **Linux x64 Platform - Java(TM) SE Development Kit 6 Update 2**. Note the name change - the first time I visited this page, the [*Linux x64 self-extracting file (build 05)*]("http://192.18.108.206/ECom/EComTicketServlet/BEGINF82B6BA7E3D1878C4973BFAC151784EE/-2147483648/2246474847/1/838358/838334/2246474847/2ts+/westCoastFSEND/jdk-6u2-oth-JPR/jdk-6u2-oth-JPR:14/jdk-6u2-linux-amd64.bin") was referred to as «**jre-6u2-linux-amd64.bin**», whereas now it is called « **jdk-6u2-linux-amd64.bin**». Be that as it may, I still get that charming «syntax error» when trying to install :Not encouraging at all ! Still, to the dull, learning comes hard - I hope you can come with some suggestion that can help me to resolve the problem and advance my understanding of **Linux** a millimetre or two....

Henri

The JDK is more useful as it contains the development stuff that you'll probably find you need sooner or later.

I get the following for a valid arhive:

```
$ md5sum jdk-6u2-linux-amd64.bin 
a7f163495497e926068d8cd086dc312e  jdk-6u2-linux-amd64.bin
```

What do you get?

---

### Post by jespdj on 2007-07-17
> mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod a+x jre-6u2-linux-amd64.bin
Password:
mhenriday@mhenriday-desktop:~/Desktop$ ./jre-6u2-linux-amd64.bin
./jre-6u2-linux-amd64.bin: line 1: syntax error near unexpected token `<'
./jre-6u2-linux-amd64.bin: line 1: `<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'
I bet you did this: You went to Sun's Java download page and then you **right-clicked on the link and chose Save As**.

Don't do that. The link does not point directly to the *.bin file. It points to an HTML page. What you have done is you've downloaded that HTML page and saved it in a file named "jre-6u2-linux-amd64.bin". What is the size of the file on your system? Is it just a few kilobytes or is it more than 10 MB?

Go back to the download page and just click on the link with the left mouse button - don't right-click it.

---

### Post by mhenriday on 2007-07-18
Thanks, **sel** and **jespdj** for your kind replies ! This has been an interesting experience, even if I'm not quite sure what it is I've learned from it ! After cd-ing into ./Desktop, I performed an md5sum check, as follows :```
mhenriday@mhenriday-desktop:~/Desktop$ md5sum jdk-6u2-linux-amd64.bin
e4ac22af4157acdd63c57e67b654b7fc  jdk-6u2-linux-amd64.bin
``` My sum thus differed from the one mentioned by **sel**, but I found and find myself unable to interpret that fact....

I then turned to **jespdj**'s suggestion that, instead of downloading the ***bin**-file in question, I had inadvertently downloaded a **HTML** file instead. As I remembered it, however, I had left-clicked rather than right-clicked the **Sun** link ; to test my hypothesis I re-performed the operation, making sure to left-click this time, and succeeded in downloading something called jdk-6u2-linux-amd64(2).bin to my desktop. When I checked the files using the commands ```
file jdk-6u2-linux-amd64.bin
jdk-6u2-linux-amd64.bin: HTML document text
``` and ```
file jdk-6u2-linux-amd64(2).bin
``` respectively, however, I received two very different answers :> jdk-6u2-linux-amd64.bin: HTML document text and > bash: syntax error near unexpected token `('I then started checking around on the web and found indicationsthat there could be a bug in the **jdk-6u2** update. As I often do in situations of this type, I decided to start again from scratch, and went back and downloaded the jre-6u2 file (17.23 MB) from **Sun**'s [*download page*]("http://www.java.com/en/download/manual.jsp"). I then proceeded to execute ```
mhenriday@mhenriday-desktop:~/Desktop$ sudo chmod a+x jre-6u2-linux-amd64.bin
Password:
mhenriday@mhenriday-desktop:~/Desktop$ ./jre-6u2-linux-amd64.bin
``` and lo and behold, instead of the expected message regarding a syntax error, I found that the installation of **jre-6u2-linux-amd64.bin** had commenced ! During the process I was once asked if I wished to proceed, to which I answered in the affirmative, and after a plethora of files were inflated, created, and extracted, I ended up with the following :> Creating jre1.6.0_02/lib/rt.jar
Creating jre1.6.0_02/lib/jsse.jar
Creating jre1.6.0_02/lib/charsets.jar
Creating jre1.6.0_02/lib/ext/localedata.jar
 
Done.So it looks as if, after many trials and tribulations, I have in fact managed to install the latest **jre**-update. My only remaing question is the following - in **Windows**, earlier versions of **jre** have to be uninstalled manually, as, for some strange reason, the **Windows**/**Java** installer does not perform this task. But when I check in **Synaptic**, I am informed that I have the latest version - **6.00-2ubuntu2** of the relevant **Java** packages installed. Can I thus let this sleeping dog lie ?...

Henri

---

### Post by fakie_flip on 2007-07-19
> **-=Viper=- said:**
> ok here is the deal...every time i click it it says it is in the wrong formating.  There is a picture of what it says that i linked.  can someone explain how to fix this??

How did you get your volume icon to look like that in the top left of your screenshot?

---

