---
title: "[SOLVED] Help Locked myself out!"
date: 2008-12-21
forum: x86 64-bit Users
---

### Post by mickt on 2008-12-21
Hi
I set up a new user account, and adjusted the permissions in the properties tab of my original account so it could not be read by others - at least that what i was trying to do!

Now I can not log in on my original account - where all my files are.....

When i try to log in i get the following messages come up - 

'User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved, File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.'

followed by -

'Could not update ICEauthority file/home/mickt/.ICEauthority.'

followed by - 

'There is a problem with the configuration server.
(/user/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256.'

I have sent this from my new user account - but all my work is in the main user account so i am completely lost at the moment.
Can anyone help?

Ps i have Kubutu installed on the pc too - but cannot see my home files on the Ubuntu partition from that either now - so feeling very worried here............

Thanks - hopefully

mickt

---

### Post by wd5gnr on 2008-12-21
Go to a working terminal and try this (replace ME with your original user ID):

sudo chown -R ME:ME /home/ME
sudo chmod -R 644 /home/ME

Then log out and try to log back in. I'd think that would fix it.

---

### Post by sisco311 on 2008-12-21
> **wd5gnr said:**
> Go to a working terminal and try this (replace ME with your original user ID):

sudo chown -R ME:ME /home/ME
...

Then log out and try to log back in. I'd think that would fix it.

it's *chmod 755 /home/username*

be careful with the chmod and chown commands.

OP:
drs305 has a detailed tutorial here:

[http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610")

---

### Post by wd5gnr on 2008-12-21
Whoops. Typed too fast. In spirit of teaching fishing instead of fish, what I put would mess things up because you really need the x bit on your home directory. However, wouldn't want to use the -R flag with a  mask containing a 7 -- but then you'll need to manually chown/chmod each directory in your home directory (the -R applies it to all directories under the one you name).

The permission bits are 3 digits ranging from 0 to 7. The first digit is for you. The second digit is for anyone in your group (which these days is probably just you). The last digit is for everyone else. You can also have a fourth digit up front but that's outside the scope of what we are talking about here.

Each digit is made of 3 bits which can be 1 or 0. 

0 - No permission

4 - Read permission
2 - Write permission
1 - Execute permission (on files) or search permission (on directories)

Add these up. So All permissions is 4+2+1 = 7. Read and write is 4+2 = 6. And so on.  You can also use symbolic names (man chmod to learn how).

Your home directory could be 700 for example if you really wanted no one other than you and super users to see your directory. 744 is typical (everything for me, read for everyone else).

So sisco is right (sorry about that) but in addition to what he has said, you'll want to go apply 644 or 640 or 600 to all the files in your directories and 744 740 or 700 to all the subdirectories (and so on for all the files and directories in each of them) -- which may be ok depending on exactly how you borked up your permissions.

---

### Post by mickt on 2008-12-22
Back again - no luck with any of the suggestions, i tried them all! - terminal comes back with -

'missing operand after' when I type the lines - cant remember if its after everyline but did see it for - 

missing operand after 755/home/mickt' 

I am fairly new to all this so am really struggling - did not realise that changing a permission in a property box would be so devastating - seems a little knowledge can be very dangerous...

Any other suggestions to let me get at all my files again - there are some files i need! - most of them are not backed up - i know they should be.....

Help!!

---

### Post by SeanHodges on 2008-12-22
> **mickt said:**
> missing operand after 755/home/mickt'

You have not put a space between the permissions number and the path. It should be:

```
sudo chmod 755 /home/mickt
```

---

### Post by mickt on 2008-12-22
Hi

just added the space, logged out and in again and it worked - i'm amazed! i can get to all my files again!

Thank you all for your time and patience.

mickt

---

### Post by sisco311 on 2008-12-22
Cool!

Please mark the thread **[SOLVED]** by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

Marking threads as **[SOLVED]**, after a solution has been found will help
others to find an expedient solution for their own issues.

---

