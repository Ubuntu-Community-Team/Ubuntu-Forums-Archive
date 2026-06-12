---
title: "courier imap fam/gamin problem"
date: 2007-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstefi on 2007-01-19
I have got problem with slow courier imap server on my Dapper 6.06 amd64 server box
(server x64 image). I have got virtual accounts in mysql.  Imap is very slow when I try to list folders or read the messages. After login I have to wait about 15 sec. to read folder with 3 messages. 

Installed packages:
ii  courier-authdaemon                 0.47-13ubuntu5.1      
ii  courier-authmysql                  0.47-13ubuntu5.1         
ii  courier-base                       0.47-13ubuntu5.1             
ii  courier-imap                       3.0.8-13ubuntu5.1            
ii  courier-imap-ssl                   3.0.8-13ubuntu5.1           
rc  courier-maildrop                   0.47-13ubuntu5.1         
rc  courier-pcp                        0.47-13ubuntu5.1             
ii  gamin                              0.1.7-2ubuntu1             
ii  libgamin0                          0.1.7-2ubuntu1

Strace for imap session:
connect(3, {sa_family=AF_FILE, path=@/tmp/fam--}, 110) = -1 ECONNREFUSED (Connection refused)
close(3)                                = 0
nanosleep({0, 50000000}, NULL)          = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
connect(3, {sa_family=AF_FILE, path=@/tmp/fam--}, 110) = -1 ECONNREFUSED (Connection refused)
close(3)                                = 0
nanosleep({0, 50000000}, NULL)          = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
...
...
...

I googled that it is gamin problem but gamin is already installed and running (no matter if gamin running or not, result is the same -> tooo slow :evil: ).

Any suggestions?

---

