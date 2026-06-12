---
title: "Noob + RealPlayer 10"
date: 2006-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by mimart7 on 2006-11-04
Hi All:

     I have a 64 bit system (hence i am posting here), I am running both XP &  Ubuntu 6.10 (gnome).  XP is on 1 HD & Ubuntu is on another.  I have downloaded RealPlayer 10 to my desktop. I have tried using the "add/remove" option & I cannot find Real Player, I have tried Gnome Apt software manager both ng.  I have tried using a terminal (I am command line argument challenged @ the moment).  I have used the instructions on the Real Player website, all to no avail. The file appears as .bin file on my desktop.  Any help to a real novice would most appreciated.

Mike](*,)

---

### Post by ingo on 2006-11-05
ok, you have the bin file on your desktop, want to install and don't know what to do with it, right?

problem is that even though it is an executable file, you have not allowed it to be executable yet. reason behind this apparent "mistak"  is overall system security. 

so all you have to do is make it executable. there are hundreds of ways to do so, here is one. open a terminal and type

sudo chmod +x /home/'your_username'/Desktop/'name_of_RealPlayer_file

followed by

sudo ./home/'your_username'/Desktop/'name_of_RealPlayer_file

and it will install itself. 

hth

---

### Post by mimart7 on 2006-11-05
I have tried this in various ways, but now am getting and error message that states missing operand  after `+x/home/mike/Desktop/RealPlayer10GOLD' I have tried with the .bin ext & w/o.  Nothing rewarding is ever easy:)

Mike

---

### Post by ingo on 2006-11-06
yeah, there should be a space between -x and the file path. basic command structure is often like that.

command [space] option (in this case -x for making it executable) [space] file path

---

