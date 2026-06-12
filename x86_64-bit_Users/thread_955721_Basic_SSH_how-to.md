---
title: "Basic SSH how-to?"
date: 2008-10-22
forum: x86 64-bit Users
---

### Post by CapTlnsano on 2008-10-22
Need some guidance here... 

Looking to use SSH protocol to tunnel into my machine from outside my LAN. I've done a lot of reading on this, seen quite a few 'guides' but im still having issues authenticating. If someone wouldnt mind breaking down the steps of using keys to authenticate, it would help. 

All I'm really trying to do is log in to this machine, via SSH from either a windows box using WinSCP/Putty or my Macbook Pro using Fugu or some other similar ssh client (correct me if im wrong in terminology so far). 

The ssh-server package and files are all installed, i can log in as localhost. When I try to log in from a remote machine i get hung up on the password step in authenticating. 

I've generated a pair of RSA keys with: 

ssh-keygen -t rsa

and that's been saved to the default /etc/.ssh directory. (still on the right track?)

I then use my password when prompted, and as far as i know it sets all this up correctly. 

When I try and log in though, that password is denied and i'm disconnected after 3 attempts. I assume its because i've not transferred a key of any sort along with that password to the remote machine.

I guess what i really need to know is, WHICH key file in that directory needs to go to the host, which needs to go to the remote machine and HOW do i do that (copy/paste and email or?). I'm not looking for a solution LIKE this to connect, but really just looking for the SIMPLEST way to connect and to try and learn the protocol from there. If this would be the way, then great...

As always, appreciate your help in my time of ignorance.

---

### Post by melojo on 2008-10-22
This thread is what I used to get it to work for me.

[http://ubuntuforums.org/archive/index.php/t-30709.html](http://ubuntuforums.org/archive/index.php/t-30709.html)

---

### Post by Nepherte on 2008-10-22
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by jmiller87 on 2008-10-22
I have been trying to set up SSH as well but I need a kind of beginners guide that can walk me through step by step anyone have ideas????

---

### Post by cariboo on 2008-10-22
It's pretty simple, this is just the basic setup.

1. Install openssh-server on your server.
2. Open a terminal on your desktop computer type:

```
ssh username@server
```

enter your password when asked. username = your user name on the server, server = server ip address or name.

3. On windows download and install Putty. Run putty fill in details and connect.

Jim

---

### Post by stmiller on 2008-10-22
If you want to set up a tunnel or proxy, do this:

```
ssh -D 9000 username@remoteserver.net
```

Then in Firefox configure a SOCKS proxy for localhost, port 9000. Any connections through Firefox are going through that encrypted tunnel.

---

### Post by CapTlnsano on 2008-10-23
Nice little guide here, I execute all the commands through copying the key to the remote computer but when I try to log in via the computer im still getting hung up password authentication. 

I edited the config file to turn password requirement off, and its noticeable when logging in via localhost, but not remote host. Anyone have ideas?

---

