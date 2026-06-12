---
title: "Trash Problem"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by Arasfang on 2008-05-05
Hi!

I have a very strange problem. I have deleted some files which has ended up in my Trash but everytime I empty the trash these files stay.

I use Ubuntu Hardy x64.

The files is in Trash Can but not in my filesystem. I have checked out every solution I found in these forums but none of them helps me.

When I empty Trash, some files goes away but these stays. If I open Trash and try to remove the files it says the files doesnt exsists?!?

/Mattias

---

### Post by soxs on 2008-05-05
Use search: [http://ubuntuforums.org/showthread.php?t=777006](http://ubuntuforums.org/showthread.php?t=777006)

---

### Post by Arasfang on 2008-05-05
Hmm,

"I have checked out every solution I found in these forums but none of them helps me."

Read my post maybe?

---

### Post by Arasfang on 2008-05-05
The solution on the problem was to use terminal and go to the correct folder where the files was. I thought all trash was saved in my homefolders trash.

Anyways, I went to the correct folder then ran
```
rm -rf *
```

---

### Post by erginemr on 2008-05-05
> **Arasfang said:**
> The solution on the problem was to use terminal and go to the correct folder where the files was. I thought all trash was saved in my homefolders trash.

Anyways, I went to the correct folder then ran
```
rm -rf *
```

Before anyone else with a similar problem try this **dangerous **command which will delete all files in the "current" folder if you have enough permissions, I'd like to clarify the solution you have found as:

1. Open a terminal.
2. See in which folder you are with: 
```
pwd
```
3a. Either change to your trash folder with:
```
cd ~/.Trash
```
where ~ is a shortcut for your home folder.
and delete your trash with:
```
rm -r *
```
3b. Or without cd'ing to your .Trash, from where you are, point to the directory to delete:
```
rm -r ~/.Trash/*
```

---

### Post by aheckler on 2008-05-05
I don't think the user's trash is in ~/.Trash anymore. It's now in ~/.local/share/Trash/files

---

### Post by soxs on 2008-05-05
A. I did not want to abuse anyone.
B. Another way to be able to clear the user-trash
```
sudo chmod 0777 -Rvf ~/.local/share/Trash/*
```
I guess afterwards the user should be able to just purge trash, shouldn't he?

---

### Post by Kilz on 2008-05-05
> **soxs said:**
> A. I did not want to abuse anyone.
B. Another way to be able to clear the user-trash
```
sudo chmod 0777 -Rvf ~/.local/share/Trash/*
```
I guess afterwards the user should be able to just purge trash, shouldn't he?

Yes that would work, as well as this command
```
sudo chown -R YourLoginName:users ~/.local/share/Trash
```
This way you avoid the dangerous rm command with a wildcard *.

---

### Post by Arasfang on 2008-05-05
> **erginemr said:**
> Before anyone else with a similar problem try this **dangerous **command which will delete all files in the "current" folder if you have enough permissions, I'd like to clarify the solution you have found as:

1. Open a terminal.
2. See in which folder you are with: 
```
pwd
```
3a. Either change to your trash folder with:
```
cd ~/.Trash
```
where ~ is a shortcut for your home folder.
and delete your trash with:
```
rm -r *
```
3b. Or without cd'ing to your .Trash, from where you are, point to the directory to delete:
```
rm -r ~/.Trash/*
```

Well clarification is always good. But I did say I moved to the correct folder before I used the command. And remove all files with a wildcard isnt a bad thing when you are in a trash-folder :P
And my trash-problem wasnt in the regular trash-folder, it was in another partition in a folder named Trash-1000.

And the reason I couldnt remove these files just by emptying the trash was probably because the files had odd names which Gnome didnt like.

/Mattias

---

### Post by Kilz on 2008-05-05
> **Arasfang said:**
> Well clarification is always good. But I did say I moved to the correct folder before I used the command. And remove all files with a wildcard isnt a bad thing when you are in a trash-folder :P
And my trash-problem wasnt in the regular trash-folder, it was in another partition in a folder named Trash-1000.

And the reason I couldnt remove these files just by emptying the trash was probably because the files had odd names which Gnome didnt like.

/Mattias

The reason you couldnt remove them was probably because the files were owned by root. The rm command with a wildcard can be very dangerous. I remember wiping out a virtual machine one time when working on a shell script. While you may feel safe using it, I dont recommend it for new users. One slip up and you can wreck your install if you think you are in a folder but you are not. Better to not use the wildcard with that command..

---

### Post by ASULutzy on 2008-05-05
> **Arasfang said:**
> Well clarification is always good. But I did say I moved to the correct folder before I used the command. And remove all files with a wildcard isnt a bad thing when you are in a trash-folder :P
And my trash-problem wasnt in the regular trash-folder, it was in another partition in a folder named Trash-1000.

And the reason I couldnt remove these files just by emptying the trash was probably because the files had odd names which Gnome didnt like.

/Mattias

That's not entirely true. If you issued the wrong command while rm'ing you could escape your current directory and erase everything above that director recursively. For example if you tried to erase all hidden folders recursively and mistakingly did

DON'T RUN THIS
```
rm -r .*
```
DON'T RUN THIS

You could potentially delete everything if you had root privileges since this will go to .. which is directory up and delete everything there.

In general, be very very very careful when you you rm -rf anything. Glad everything was fixed for you, but even linux pros screw things up on occasion by doing things like that, so just a heads up

---

### Post by Arasfang on 2008-05-05
> **Kilz said:**
> The reason you couldnt remove them was probably because the files were owned by root. The rm command with a wildcard can be very dangerous. I remember wiping out a virtual machine one time when working on a shell script. While you may feel safe using it, I dont recommend it for new users. One slip up and you can wreck your install if you think you are in a folder but you are not. Better to not use the wildcard with that command..

No the files was owned by my user. And I used rm command as my user, not as root. Yea wildcards can be dangerous but I wouldnt have used it if I didnt know I was in the correct folder. I am pretty new to Ubuntu but deleting files is about the same as in windows :)

/Mattias

---

### Post by Arasfang on 2008-05-05
> **ASULutzy said:**
> That's not entirely true. If you issued the wrong command while rm'ing you could escape your current directory and erase everything above that director recursively. For example if you tried to erase all hidden folders recursively and mistakingly did

DON'T RUN THIS
```
rm -r .*
```
DON'T RUN THIS

You could potentially delete everything if you had root privileges since this will go to .. which is directory up and delete everything there.

In general, be very very very careful when you you rm -rf anything. Glad everything was fixed for you, but even linux pros screw things up on occasion by doing things like that, so just a heads up

Yea I would never use that command recursively, only in current folder. And I did not use it as root, only as my regular user.

Yea anyone can screw up ofcourse and i dont argue with the clarification at all. Just telling my experience here :P

/Mattias

---

### Post by Arthur Archnix on 2008-05-24
> And my trash-problem wasnt in the regular trash-folder, it was in another partition in a folder named Trash-1000.

Awesome. This has been bugging me and it solved it. Thanks.

---

