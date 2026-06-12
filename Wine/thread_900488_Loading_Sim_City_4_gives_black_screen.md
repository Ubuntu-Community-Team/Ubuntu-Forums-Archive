---
title: "Loading Sim City 4 gives black screen"
date: 2008-08-25
forum: Wine
---

### Post by david sousa on 2008-08-25
Hey!

I installed sim city 4 in my ubuntu through wine and all the process is well done but when i load it i get a black screen and nothing happens. Then i have to turn off the laptop because a can't do anything!

Does someone have a clue?

---

### Post by prince_niceguy on 2008-08-25
how are you starting it? from terminal or clicking wine icon?

Try adding -d:software like in [this post]("http://tombuntu.com/index.php/2007/04/06/simcity-4-on-ubuntu-with-wine/") about simcity4.

---

### Post by david sousa on 2008-08-26
I'm starting it from the icon! I don't understand the other way... could you explain please?

---

### Post by prince_niceguy on 2008-08-26
OK. First you need to find out where your Simcity installation is done. mostly it would be in .wine/drive_c/Program Files/Simcity ... etc

You need to open a terminal Applications --> Accessories --> terminal

Now type

```
cd [the path you copied in double quote]
```

e.g. cd "/home/xyz/.wine/drive_c/Program Files/..."

cd to the apps directory in Simcity folder

Now type the command 

wine ./SimCity4.exe -d:software

It should work. I am also using simcity4 and it works flawlessly.

---

### Post by Joeb454 on 2008-08-26
Moved to Wine sub-forum

---

### Post by david sousa on 2008-08-26
This is what i got...

[email]david@David:~/.wine[/email]/drive_c/Programas/Maxis/SimCity 4 Deluxe/Apps$ wine SimCity 4.exe -d:software
wine: could not load L"C:\\windows\\system32\\SimCity.exe": Module not found
david@David:

 Something wrong?

---

### Post by prince_niceguy on 2008-08-26
yes. you need to type the following command

wine ./SimCity\ 4.exe -d:software

two problems in your command.

One no ./, a ./ means run the command found in this directory, \ in front of 4 as the space is creating a problem.

---

### Post by david sousa on 2008-08-26
Perfect!!! Thanks very much!!!!

---

### Post by prince_niceguy on 2008-08-26
Better still, make an alias in your .bashrc for simcity. So, you just need to open terminal and type simcity and it will open simcity. How to do it? Follow as below.

Open your .bashrc using gedit, it could be found in your home directory.

Go to the last line in the file.

Now, make alias like

alias simcity='cd [directory to simcity in double quotes];wine ./Simcity\ 4.exe -d:sofware'


Save the file and now open a new terminal. Now, type simcity, and your simcity should start.

Note: if you are changing .bashrc then you should open a new terminal for running a command.

Also, please mark the thread as solved.

---

