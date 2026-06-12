---
title: "I'm so completely baffled (ssh question)"
date: 2008-07-01
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-07-01
So basically, I've got a desktop running Hardy 64; on it is running an open ssh server. This open ssh server is set to only accept my key, no passwords.

I've got a laptop; on this laptop I'm able to connect to the ssh server using Hardy 32 bit, but when I use Intrepid 64 bit it doesn't work. The interesting thing is that using Intrepid, both sides seem to think it worked just fine. For example on the server, /var/log/auth.log says that it has accepted my public key, and on the laptop's side netstat -t says that the ssh connection is established, and also the output of ssh -v -v is exactly as expected. The only problem is I never get a $USER@host:~$ prompt. The terminal just hangs and ctrl+c/z/whatever doesn't do anything. Here's some output that may be very helpful:```
ryan@ubuntu:~$ md5sum /etc/ssh/ssh_config && md5sum /media/hardy/etc/ssh/ssh_config && md5sum /home/ryan/.ssh/identity && md5sum /media/hardy/home/ryan/.ssh/identity 
eb59056334fffc55e9f308f0e2315c38  /etc/ssh/ssh_config
eb59056334fffc55e9f308f0e2315c38  /media/hardy/etc/ssh/ssh_config
cfa*they're the same ;)a9  /home/ryan/.ssh/identity
cfa*they're the same ;)a9  /media/hardy/home/ryan/.ssh/identity
ryan@ubuntu:~$ ssh -v -v 192.168.0.102
OpenSSH_4.7p1 Debian-12ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.102 [192.168.0.102] port 22.
debug1: Connection established.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/ryan/.ssh/identity type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-12ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 132/256
debug2: bits set: 519/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.102' is known and matches the RSA host key.
debug1: Found key in /home/ryan/.ssh/known_hosts:1
debug2: bits set: 516/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ryan/.ssh/identity ((nil))
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ryan/.ssh/identity
debug1: read PEM private key done: type DSA
debug2: we sent a publickey packet, wait for reply
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
*Then like 5 minutes later comes*
Read from remote host 192.168.0.102: Connection timed out
Connection to 192.168.0.102 closed.

Also /var/log/auth.log on the server says that it's accepted my public key. Additionally, netstat -t shows that I've established an ssh connection to the machine. 

Both sides say everything went perfectly, but I never get a $USER@host:~$ prompt and the terminal just hangs (ctrl+c/z/etc does nothing)
```

Any help would be tremendously appareciated!

edit: I've tried using other terminal emulators, xterm, the gnome-terminal, tty1, etc, all do the same thing. Also, I'm well aware that Intrepid is Alpha 1 and not exactly production ready, but this is a pretty substantial bug (maybe?) and I also have no idea even remotely why things are failing in the way they are.

---

### Post by pixel :-) on 2008-07-01
Intrepid is beta,it could be a zillion things.Theres very little chance that somebody will be willing to respond, on top of it you problem seems complicated.Try [Intrepid Ibex Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=346").

---

### Post by ilrudie on 2008-07-01
> **pixel :-) said:**
> Intrepid is beta,it could be a zillion things.Theres very little chance that somebody will be willing to respond, on top of it you problem seems complicated.Try [Intrepid Ibex Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=346").

+1 except Intrepid is alpha i believe.  Might want to report it as a bug.

---

