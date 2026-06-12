---
title: "FreeNX SSH Keys"
date: 2008-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jiffyman on 2008-03-15
I don't know if it really matters, but I am trying to use FreeNx on 64bit machine. All I really need to do is get the SSH keys for the client, but I can't find them. Could someone point me in the right direction?

Thanks,

Giffyman

---

### Post by Jiffyman on 2008-03-15
O.k. let me answer my own question.

Using custom SSH keys

/!\ This is NOT supported by the FreeNX developers - only do this if you have no other option

   1.

      Generate the DSA private-public key pair.

       ssh-keygen -t dsa

      By default this key is places in ~/.ssh/id-dsa. You can leave the passphrase empty, this will not pose a security risk.
   2.

      Install the public key in the FreeNX serving machine. The key should be placed in the file authorized_keys2 in the .ssh dir of the user named nx.

      cat ~/.ssh/id_dsa.pub | sudo -u nx tee -a ~nx/.ssh/authorized_keys2

   3.

      Install the private key in the NX client software. When creating a session, press the button labeled "Key" and select your new key in the window that pops up.

Created a custom SSH key watched where it was saved and authorized the key with the second step and now it works.

The full documentation can be found here:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Although a little outdated it was obviously still useful.

---

### Post by leroyc on 2008-03-20
Actually, for SSH keys, you need to make absolutely sure the key is inserted with:

cat key >> authorized_keys 

Inserting it with any kind of pico/vim software can render the key unuseful.

Also, the key can be added with the ssh-agent function. 

Its a basic automatization so you don't need to type your key password every time. However the problem is this works only for one terminal.

I have created a solution how to make it work for every single terminal you open. 

You can read it here:

[http://top-web-solutions.com/ssh-keys/](http://top-web-solutions.com/ssh-keys/)

---

