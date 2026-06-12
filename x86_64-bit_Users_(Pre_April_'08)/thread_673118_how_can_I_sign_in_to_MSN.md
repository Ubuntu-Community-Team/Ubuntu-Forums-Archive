---
title: "how can I sign in to MSN"
date: 2008-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by xieu90 on 2008-01-20
hi everyone I used Pidgin to log in MSN, it worked normally until now, then I can not sign in to MSN anymore It always give me a message : unable to connect 
how can I solve this problem ?
AMSN won't work either
but I can still use meebo.com

---

### Post by novik420 on 2008-01-20
retype your email and password
maybe there is a typo

---

### Post by xieu90 on 2008-01-20
I tried that too, but it wont work

---

### Post by xieu90 on 2008-01-20
does anyone use pidgin or amsn and can still sign in in MSN ?

---

### Post by Lord Illidan on 2008-01-20
Sure I can..talking now.

---

### Post by XplOzIOn on 2008-01-22
> **xieu90 said:**
> does anyone use pidgin or amsn and can still sign in in MSN ?

There might some kind of network problem. Just recap what did you do in those days before it stoped working? try to reinstall it.
```
sudo apt-get --purge remove amsn
sudo apt-get install amsn
```

Also check for some active plugin in amsn or anything. Hope to hear back!

---

### Post by xieu90 on 2008-01-22
don't know why but I can sign into MSN now thank goodness !

---

### Post by XplOzIOn on 2008-01-22
> **xieu90 said:**
> don't know why but I can sign into MSN now thank goodness !

What did you do?

Hmmmm you might wanna dig into this, hope it doesnt happends again!

cheers

---

### Post by xieu90 on 2008-01-22
well it does happen again ! I went to have dinner and when I came back I had to use meebo.com

so I went to amsn and search but didn't find anything, only Ctrl + D and Ctrl + S in Amsn
and I got these thing here

I hope you can tell me what it is doing and what is tlc or tcl 8./4 and 5
mine is 8.4

here is code or whatever from amsn

20:28:32] ::Proxy::ProxyHTTP1
[20:28:32] < Connected to: 207.46.108.81 1863 >
[20:28:42] ->ns- OUT


[20:28:48] ::Proxy::ProxyHTTP3
[20:28:48] < Connected to: messenger.hotmail.com 1863 >
[20:28:58] ->ns- OUT


[20:29:03] ::Proxy::ProxyHTTP5
[20:29:03] < Connected to: messenger.hotmail.com 1863 >
[20:29:13] ->ns- OUT


[20:29:18] ::Proxy::ProxyHTTP7
[20:29:19] < Connected to: messenger.hotmail.com 1863 >
[20:29:29] ->ns- OUT


[20:29:34] ::Proxy::ProxyHTTP9
[20:29:34] < Connected to: messenger.hotmail.com 1863 >
[20:29:44] ->ns- OUT


[20:29:49] ::Proxy::ProxyHTTP11
[20:29:49] < Connected to: messenger.hotmail.com 1863 >
[20:29:59] ->ns- OUT


[20:30:05] ::Proxy::ProxyHTTP13
[20:30:22] ->ns- OUT


[20:30:27] ::Proxy::ProxyHTTP15
[20:30:27] < Connected to: messenger.hotmail.com 1863 >
[20:30:37] ->ns- OUT


[20:30:43] ::Proxy::ProxyHTTP17
[20:30:43] < Connected to: messenger.hotmail.com 1863 >
[20:30:53] ->ns- OUT


[20:30:58] ::Proxy::ProxyHTTP19
[20:30:58] < Connected to: messenger.hotmail.com 1863 >
[20:31:08] ->ns- OUT


[20:31:13] ::Proxy::ProxyHTTP21
[20:31:14] < Connected to: messenger.hotmail.com 1863 >
[20:31:24] ->ns- OUT


[20:31:29] ::Proxy::ProxyHTTP23
[20:31:29] < Connected to: messenger.hotmail.com 1863 >
[20:31:39] ->ns- OUT


[20:31:44] ::Proxy::ProxyHTTP25
[20:31:44] < Connected to: messenger.hotmail.com 1863 >
[20:31:54] ->ns- OUT


[20:31:59] ::Proxy::ProxyHTTP27
[20:32:00] < Connected to: messenger.hotmail.com 1863 >
[20:32:10] ->ns- OUT


[20:32:15] ::Proxy::ProxyHTTP29
[20:32:15] < Connected to: messenger.hotmail.com 1863 >
[20:32:25] ->ns- OUT


[20:32:30] ::Proxy::ProxyHTTP31
[20:32:30] < Connected to: messenger.hotmail.com 1863 >
[20:32:40] ->ns- OUT


[20:32:46] ::Proxy::ProxyHTTP33
[20:32:46] < Connected to: messenger.hotmail.com 1863 >
[20:32:56] ->ns- OUT


[20:33:01] ::Proxy::ProxyHTTP35
[20:33:01] < Connected to: messenger.hotmail.com 1863 >
[20:33:12] ->ns- OUT


[20:33:17] ::Proxy::ProxyHTTP37
[20:33:17] < Connected to: messenger.hotmail.com 1863 >
[20:33:27] ->ns- OUT


[20:33:32] ::Proxy::ProxyHTTP39
[20:33:32] < Connected to: messenger.hotmail.com 1863 >
[20:33:34] ->ns-sock8 OUT


[20:33:46] ::Proxy::ProxyDirect1
[20:33:46] < Connected to: messenger.hotmail.com 1863 >
[20:33:47] ->ns-sock7 VER 1 MSNP12 CVR0


[20:33:47] ->ns-sock7 CVR 2 0x0409 winnt 5.1 i386 MSNMSGR 8.0.0812 msmsgs [email]doandu90@hotmail.com[/email]


[20:33:47] ->ns-sock7 USR 3 TWN I [email]doandu90@hotmail.com[/email]


[20:33:47] <-ns-sock7 VER 1 MSNP12 CVR0
[20:33:47] <-ns-sock7 CVR 2 8.1.0178 8.1.0178 8.1.0178 [http://msgruser.dlservice.microsoft.com/download/1/A/4/1A4FEB1A-18E0-423A-B898-F697402E4F7F/Install_Messenger.exe](http://msgruser.dlservice.microsoft.com/download/1/A/4/1A4FEB1A-18E0-423A-B898-F697402E4F7F/Install_Messenger.exe) [http://get.live.com](http://get.live.com)
[20:33:47] <-ns-sock7 XFR 3 NS 207.46.108.64:1863 0 207.46.28.93:1863
[20:33:47] < Connected to: 207.46.108.64 1863 >
[20:33:47] ->ns-sock7 VER 4 MSNP12 CVR0


[20:33:47] ->ns-sock7 CVR 5 0x0409 winnt 5.1 i386 MSNMSGR 8.0.0812 msmsgs [email]doandu90@hotmail.com[/email]


[20:33:47] ->ns-sock7 USR 6 TWN I [email]doandu90@hotmail.com[/email]


[20:33:47] <-ns-sock7 VER 4 MSNP12 CVR0
[20:33:48] <-ns-sock7 CVR 5 8.1.0178 8.1.0178 8.1.0178 [http://msgruser.dlservice.microsoft.com/download/1/A/4/1A4FEB1A-18E0-423A-B898-F697402E4F7F/Install_Messenger.exe](http://msgruser.dlservice.microsoft.com/download/1/A/4/1A4FEB1A-18E0-423A-B898-F697402E4F7F/Install_Messenger.exe) [http://get.live.com](http://get.live.com)
[20:33:48] <-ns-sock7 USR 6 TWN S ct=1201030427,rver=5.0.3270.0,wp=FS_40SEC_0_COMPACT,lc=1033,id=507,ru=http:%2F%2Fmessenger.msn.com,tw=0,kpp=1,kv=4,ver=2.1.6000.1,rn=1lgjBfIL,tpf=b0735e3a873dfb5e75054465196398e0
[20:36:57] ->ns-sock7 OUT


[20:42:51] ::Proxy::ProxyHTTP41
[20:42:51] < Connected to: 207.46.108.64 1863 >
[20:43:01] ->ns- OUT


[20:43:06] ::Proxy::ProxyHTTP43
[20:43:06] < Connected to: messenger.hotmail.com 1863 >
[20:43:16] ->ns- OUT


[20:43:21] ::Proxy::ProxyHTTP45
[20:43:22] < Connected to: messenger.hotmail.com 1863 >
[20:43:32] ->ns- OUT


[20:43:37] ::Proxy::ProxyHTTP47
[20:43:37] < Connected to: messenger.hotmail.com 1863 >
[20:43:47] ->ns- OUT


[20:43:52] ::Proxy::ProxyHTTP49
[20:43:53] < Connected to: messenger.hotmail.com 1863 >
[20:44:03] ->ns- OUT


[20:44:08] ::Proxy::ProxyHTTP51
[20:44:08] < Connected to: messenger.hotmail.com 1863 >
[20:44:18] ->ns- OUT


[20:44:23] ::Proxy::ProxyHTTP53
[20:44:24] < Connected to: messenger.hotmail.com 1863 >
[20:44:34] ->ns- OUT


[20:44:39] ::Proxy::ProxyHTTP55
[20:44:39] < Connected to: messenger.hotmail.com 1863 >
[20:44:49] ->ns- OUT


[20:44:54] ::Proxy::ProxyHTTP57
[20:44:54] < Connected to: messenger.hotmail.com 1863 >
[20:45:04] ->ns- OUT


[20:45:09] ::Proxy::ProxyHTTP59
[20:45:10] < Connected to: messenger.hotmail.com 1863 >
[20:45:20] ->ns- OUT


[20:45:25] ::Proxy::ProxyHTTP61
[20:45:25] < Connected to: messenger.hotmail.com 1863 >
[20:45:35] ->ns- OUT


[20:45:40] ::Proxy::ProxyHTTP63
[20:45:40] < Connected to: messenger.hotmail.com 1863 >
[20:45:50] ->ns- OUT


[20:45:56] ::Proxy::ProxyHTTP65
[20:45:56] < Connected to: messenger.hotmail.com 1863 >
[20:46:06] ->ns- OUT


[20:46:11] ::Proxy::ProxyHTTP67
[20:46:11] < Connected to: messenger.hotmail.com 1863 >
[20:46:21] ->ns- OUT


[20:46:26] ::Proxy::ProxyHTTP69
[20:46:27] < Connected to: messenger.hotmail.com 1863 >
[20:46:37] ->ns- OUT


[20:46:42] ::Proxy::ProxyHTTP71
[20:46:42] < Connected to: messenger.hotmail.com 1863 >
[20:46:52] ->ns- OUT


[20:46:57] ::Proxy::ProxyHTTP73
[20:46:57] < Connected to: messenger.hotmail.com 1863 >
[20:47:07] ->ns- OUT


[20:47:13] ::Proxy::ProxyHTTP75
[20:47:13] < Connected to: messenger.hotmail.com 1863 >
[20:47:23] ->ns- OUT


[20:47:28] ::Proxy::ProxyHTTP77
[20:47:28] < Connected to: messenger.hotmail.com 1863 >
[20:47:38] ->ns- OUT


[20:47:43] ::Proxy::ProxyHTTP79
[20:47:44] < Connected to: messenger.hotmail.com 1863 >
[20:47:54] ->ns- OUT


[20:47:59] ::Proxy::ProxyHTTP81
[20:47:59] < Connected to: messenger.hotmail.com 1863 >
[20:48:09] ->ns- OUT


[20:48:14] ::Proxy::ProxyHTTP83
[20:48:15] < Connected to: messenger.hotmail.com 1863 >
[20:48:25] ->ns- OUT


[20:48:30] ::Proxy::ProxyHTTP85
[20:48:30] < Connected to: messenger.hotmail.com 1863 >
[20:48:40] ->ns- OUT


[20:48:45] ::Proxy::ProxyHTTP87
[20:49:06] < Connected to: messenger.hotmail.com 1863 >
[20:49:16] ->ns- OUT


[20:49:22] ::Proxy::ProxyHTTP89
[20:49:22] < Connected to: messenger.hotmail.com 1863 >
[20:49:32] ->ns- OUT


[20:49:37] ::Proxy::ProxyHTTP91
[20:49:37] < Connected to: messenger.hotmail.com 1863 >
[20:49:47] ->ns- OUT


[20:49:52] ::Proxy::ProxyHTTP93
[20:49:53] < Connected to: messenger.hotmail.com 1863 >
[20:50:03] ->ns- OUT


[20:50:08] ::Proxy::ProxyHTTP95
[20:50:08] < Connected to: messenger.hotmail.com 1863 >
[20:50:18] ->ns- OUT


[20:50:23] ::Proxy::ProxyHTTP97
[20:50:24] < Connected to: messenger.hotmail.com 1863 >
[20:50:34] ->ns- OUT


[20:50:39] ::Proxy::ProxyHTTP99
[20:50:39] < Connected to: messenger.hotmail.com 1863 >
[20:50:49] ->ns- OUT


[20:50:54] ::Proxy::ProxyHTTP101
[20:50:54] < Connected to: messenger.hotmail.com 1863 >
[20:51:04] ->ns- OUT


[20:51:09] ::Proxy::ProxyHTTP103
[20:51:10] < Connected to: messenger.hotmail.com 1863 >
[20:51:20] ->ns- OUT


[20:51:25] ::Proxy::ProxyHTTP105
[20:51:25] < Connected to: messenger.hotmail.com 1863 >
[20:51:35] ->ns- OUT


[20:51:40] ::Proxy::ProxyHTTP107
[20:51:41] < Connected to: messenger.hotmail.com 1863 >
[20:51:51] ->ns- OUT


[20:51:56] ::Proxy::ProxyHTTP109
[20:51:56] < Connected to: messenger.hotmail.com 1863 >
[20:52:06] ->ns- OUT


[20:52:11] ::Proxy::ProxyHTTP111
[20:52:11] < Connected to: messenger.hotmail.com 1863 >
[20:52:21] ->ns- OUT


[20:52:26] ::Proxy::ProxyHTTP113
[20:52:27] < Connected to: messenger.hotmail.com 1863 >
[20:52:37] ->ns- OUT


[20:52:42] ::Proxy::ProxyHTTP115
[20:52:42] < Connected to: messenger.hotmail.com 1863 >
[20:52:52] ->ns- OUT


[20:52:57] ::Proxy::ProxyHTTP117
[20:52:58] < Connected to: messenger.hotmail.com 1863 >
[20:53:08] ->ns- OUT


[20:53:13] ::Proxy::ProxyHTTP119
[20:53:13] < Connected to: messenger.hotmail.com 1863 >
[20:53:23] ->ns- OUT


[20:53:28] ::Proxy::ProxyHTTP121
[20:53:28] < Connected to: messenger.hotmail.com 1863 >
[20:53:38] ->ns- OUT


[20:53:43] ::Proxy::ProxyHTTP123
[20:53:44] < Connected to: messenger.hotmail.com 1863 >
[20:53:54] ->ns- OUT


[20:53:59] ::Proxy::ProxyHTTP125
[20:53:59] < Connected to: messenger.hotmail.com 1863 >
[20:54:09] ->ns- OUT


[20:54:14] ::Proxy::ProxyHTTP127
[20:54:15] < Connected to: messenger.hotmail.com 1863 >
[20:54:25] ->ns- OUT


[20:54:30] ::Proxy::ProxyHTTP129
[20:54:30] < Connected to: messenger.hotmail.com 1863 >
[20:54:40] ->ns- OUT


[20:54:45] ::Proxy::ProxyHTTP131
[20:54:46] < Connected to: messenger.hotmail.com 1863 >
[20:54:56] ->ns- OUT


[20:55:01] ::Proxy::ProxyHTTP133
[20:55:46] < Connected to: messenger.hotmail.com 1863 >
[20:55:56] ->ns- OUT


[20:56:01] ::Proxy::ProxyHTTP135
[20:56:01] < Connected to: messenger.hotmail.com 1863 >
[20:56:11] ->ns- OUT


[20:56:16] ::Proxy::ProxyHTTP137
[20:56:17] < Connected to: messenger.hotmail.com 1863 >
[20:56:27] ->ns- OUT


[20:56:32] ::Proxy::ProxyHTTP139
[20:56:32] < Connected to: messenger.hotmail.com 1863 >
[20:56:42] ->ns- OUT


[20:56:47] ::Proxy::ProxyHTTP141
[20:56:48] < Connected to: messenger.hotmail.com 1863 >
[20:56:58] ->ns- OUT


[20:57:03] ::Proxy::ProxyHTTP143
[20:57:03] < Connected to: messenger.hotmail.com 1863 >
[20:57:13] ->ns- OUT


[20:57:18] ::Proxy::ProxyHTTP145
[20:57:18] < Connected to: messenger.hotmail.com 1863 >
[20:57:28] ->ns- OUT


[20:57:34] ::Proxy::ProxyHTTP147
[20:57:34] < Connected to: messenger.hotmail.com 1863 >
[20:57:44] ->ns- OUT


[20:57:49] ::Proxy::ProxyHTTP149
[20:57:49] < Connected to: messenger.hotmail.com 1863 >
[20:57:59] ->ns- OUT


[20:58:04] ::Proxy::ProxyHTTP151
[20:58:05] < Connected to: messenger.hotmail.com 1863 >
[20:58:15] ->ns- OUT


[20:58:20] ::Proxy::ProxyHTTP153
[20:58:20] < Connected to: messenger.hotmail.com 1863 >
[20:58:30] ->ns- OUT


[20:58:35] ::Proxy::ProxyHTTP155
[20:58:35] < Connected to: messenger.hotmail.com 1863 >
[20:58:45] ->ns- OUT


[20:58:50] ::Proxy::ProxyHTTP157
[20:58:51] < Connected to: messenger.hotmail.com 1863 >
[20:59:01] ->ns- OUT


[20:59:06] ::Proxy::ProxyHTTP159
[20:59:06] < Connected to: messenger.hotmail.com 1863 >
[20:59:16] ->ns- OUT


[20:59:21] ::Proxy::ProxyHTTP161
[20:59:21] < Connected to: messenger.hotmail.com 1863 >
[20:59:31] ->ns- OUT


[20:59:37] ::Proxy::ProxyHTTP163
[20:59:37] < Connected to: messenger.hotmail.com 1863 >
[20:59:47] ->ns- OUT


[20:59:52] ::Proxy::ProxyHTTP165
[20:59:52] < Connected to: messenger.hotmail.com 1863 >
[21:00:02] ->ns- OUT


[21:00:08] ::Proxy::ProxyHTTP167
[21:00:08] < Connected to: messenger.hotmail.com 1863 >
[21:00:18] ->ns- OUT


[21:00:23] ::Proxy::ProxyHTTP169
[21:00:23] < Connected to: messenger.hotmail.com 1863 >
[21:00:33] ->ns- OUT


[21:00:38] ::Proxy::ProxyHTTP171
[21:00:39] < Connected to: messenger.hotmail.com 1863 >
[21:00:49] ->ns- OUT


[21:00:54] ::Proxy::ProxyHTTP173
[21:00:54] < Connected to: messenger.hotmail.com 1863 >
[21:01:04] ->ns- OUT


[21:01:09] ::Proxy::ProxyHTTP175
[21:01:10] < Connected to: messenger.hotmail.com 1863 >
[21:01:20] ->ns- OUT


[21:01:25] ::Proxy::ProxyHTTP177
[21:01:25] < Connected to: messenger.hotmail.com 1863 >
[21:01:35] ->ns- OUT


[21:01:40] ::Proxy::ProxyHTTP179
[21:01:40] < Connected to: messenger.hotmail.com 1863 >
[21:01:50] ->ns- OUT


[21:01:56] ::Proxy::ProxyHTTP181
[21:01:56] < Connected to: messenger.hotmail.com 1863 >
[21:02:06] ->ns- OUT


[21:02:11] ::Proxy::ProxyHTTP183
[21:02:11] < Connected to: messenger.hotmail.com 1863 >
[21:02:21] ->ns- OUT


[21:02:26] ::Proxy::ProxyHTTP185
[21:02:27] < Connected to: messenger.hotmail.com 1863 >
[21:02:37] ->ns- OUT


[21:02:42] ::Proxy::ProxyHTTP187
[21:02:42] < Connected to: messenger.hotmail.com 1863 >
[21:02:52] ->ns- OUT


[21:02:57] ::Proxy::ProxyHTTP189
[21:02:58] < Connected to: messenger.hotmail.com 1863 >
[21:03:08] ->ns- OUT


[21:03:13] ::Proxy::ProxyHTTP191
[21:03:13] < Connected to: messenger.hotmail.com 1863 >
[21:03:23] ->ns- OUT


[21:03:28] ::Proxy::ProxyHTTP193
[21:03:28] < Connected to: messenger.hotmail.com 1863 >
[21:03:38] ->ns- OUT


[21:03:43] ::Proxy::ProxyHTTP195
[21:03:44] < Connected to: messenger.hotmail.com 1863 >
[21:03:54] ->ns- OUT


[21:03:59] ::Proxy::ProxyHTTP197
[21:03:59] < Connected to: messenger.hotmail.com 1863 >
[21:04:09] ->ns- OUT


[21:04:14] ::Proxy::ProxyHTTP199
[21:04:14] < Connected to: messenger.hotmail.com 1863 >
[21:04:24] ->ns- OUT


[21:04:30] ::Proxy::ProxyHTTP201
[21:04:30] < Connected to: messenger.hotmail.com 1863 >
[21:04:40] ->ns- OUT


[21:04:45] ::Proxy::ProxyHTTP203
[21:04:45] < Connected to: messenger.hotmail.com 1863 >
[21:04:55] ->ns- OUT


[21:05:00] ::Proxy::ProxyHTTP205
[21:05:01] < Connected to: messenger.hotmail.com 1863 >
[21:05:11] ->ns- OUT


[21:05:16] ::Proxy::ProxyHTTP207
[21:05:16] < Connected to: messenger.hotmail.com 1863 >
[21:05:26] ->ns- OUT


[21:05:31] ::Proxy::ProxyHTTP209
[21:05:32] < Connected to: messenger.hotmail.com 1863 >
[21:05:42] ->ns- OUT


[21:05:47] ::Proxy::ProxyHTTP211
[21:05:47] < Connected to: messenger.hotmail.com 1863 >
[21:05:57] ->ns- OUT


[21:06:02] ::Proxy::ProxyHTTP213
[21:06:02] < Connected to: messenger.hotmail.com 1863 >
[21:06:12] ->ns- OUT


[21:06:17] ::Proxy::ProxyHTTP215
[21:06:18] < Connected to: messenger.hotmail.com 1863 >
[21:06:28] ->ns- OUT


[21:06:33] ::Proxy::ProxyHTTP217
[21:06:33] < Connected to: messenger.hotmail.com 1863 >
[21:06:43] ->ns- OUT


[21:06:48] ::Proxy::ProxyHTTP219
[21:06:49] < Connected to: messenger.hotmail.com 1863 >
[21:06:59] ->ns- OUT


[21:07:04] ::Proxy::ProxyHTTP221
[21:07:04] < Connected to: messenger.hotmail.com 1863 >
[21:07:14] ->ns- OUT


[21:07:19] ::Proxy::ProxyHTTP223
[21:07:19] < Connected to: messenger.hotmail.com 1863 >
[21:07:29] ->ns- OUT


[21:07:35] ::Proxy::ProxyHTTP225
[21:07:35] < Connected to: messenger.hotmail.com 1863 >
[21:07:45] ->ns- OUT


[21:07:50] ::Proxy::ProxyHTTP227
[21:07:50] < Connected to: messenger.hotmail.com 1863 >
[21:08:00] ->ns- OUT


[21:08:05] ::Proxy::ProxyHTTP229
[21:08:06] < Connected to: messenger.hotmail.com 1863 >

---

### Post by xieu90 on 2008-01-22
and still something, I tried both http mode and direct mode, but it won't work, but meebo does

---

### Post by xieu90 on 2008-01-22
suddenly I could login to amsn
no idea how 
I got these code there
[21:49:29] ->ns-sock7 PNG


[21:49:29] <-ns-sock7 QNG 47

---

