---
title: "i need to run SSH on Opensuse  - what do i need to do?"
date: 2014-11-25
forum: openSUSE and SUSE Linux Enterprise
---

### Post by dilbert_one on 2014-11-25
i need to run SSH on Opensuse  - what do i need to do?


i have to enable SSH on OpenSuSE 13.1

according to this hints i need to do following: [http://wiki.aoxoa.com/Enabling_SSH_on_OpenSuSE_13.1](http://wiki.aoxoa.com/Enabling_SSH_on_OpenSuSE_13.1)


```

martin@linux-70ce:~>   netstat -an | grep :22
udp        0      0 fe80::221:63ff:fed1:123 :::*                                
martin@linux-70ce:~> 

```

furthermore i did the folloiwng steps: 

```
su - 
  systemctl enable sshd.service

```

see the results: 
  
```

martin@linux-70ce:~> kgpg -k
martin@linux-70ce:~>   netstat -an | grep :22
udp        0      0 fe80::221:63ff:fed1:123 :::*                                
martin@linux-70ce:~>   su -
Passwort: 
linux-70ce:~ # 
linux-70ce:~ #   systemctl enable sshd.service
ln -s '/usr/lib/systemd/system/sshd.service' '/etc/systemd/system/multi-user.target.wants/sshd.service'
linux-70ce:~ # ^C
linux-70ce:~ # 

```


    well - as it seems i am ready - am i !?

    i need to port forward now - can i go for it..!? 

love to hear from you

---

### Post by slickymaster on 2014-11-25
*Moved to the ***openSUSE and SUSE Linux Enterprise*** sub-forum*

---

