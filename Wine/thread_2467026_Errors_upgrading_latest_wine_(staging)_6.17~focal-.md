---
title: "Errors upgrading latest wine (staging) 6.17~focal-1"
date: 2021-09-13
forum: Wine
---

### Post by stinkypants on 2021-09-13
```
[FONT=monospace][COLOR=#000000]Err:1 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main amd64 winehq-staging amd64 6.17~focal-1 [/COLOR]
  File has unexpected size (1932 != 1928). Mirror sync in progress? [IP: 199.232.78.217 443] 
  Hashes of expected file: 
   - SHA512:dbd4301fc46570f00731408ddeac02561977ae5ab8b08d8f5f3c2c6852818dddeec717d8f67f4da21f2507ed51da6
61a73d70dac7a1a2e0a5dc02f3b74278dda 
   - SHA256:b0aed899399d66fc5a2c37ddc670f305e0ca148041055f03c5f56df3f23c55b7 
   - SHA1:9197ca14a5691dbf764eb40f86a63258aa998dc7 [weak] 
   - MD5Sum:7847b322ca146f4da687d7e1fbe85d10 [weak] 
   - Filesize:1928 [weak] 
Get:2 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main amd64 wine-staging amd64 6.17~focal-1 [3,621 kB
] 
Err:2 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main amd64 wine-staging amd64 6.17~focal-1 
  File has unexpected size (3623076 != 3620848). Mirror sync in progress? [IP: 199.232.78.217 443] 
  Hashes of expected file: 
   - SHA512:6abbdc0fbccc1720f2d286c0c9f60fbb056fe2bba649fded660f6cceff13058bf33b421e1c417ac9500bd78bb5b2b
b48842ea9a7829e11bd1cae2c6365299b88 
   - SHA256:3394091590d2e143c1e4769b91966214d80360a126b4096bee53e6c0e9e09a1c 
   - SHA1:7d6d24f31a331445e201e0edf4f5df1d740fd026 [weak] 
   - MD5Sum:6b5039ef73e5cb968108199ff69fbbe5 [weak] 
   - Filesize:3620848 [weak] 
Get:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main i386 wine-staging-i386 i386 6.17~focal-1 [81.7 
MB] 
Err:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main i386 wine-staging-i386 i386 6.17~focal-1 
  File has unexpected size (81675616 != 81686648). Mirror sync in progress? [IP: 199.232.78.217 443] 
  Hashes of expected file: 
   - SHA512:15ecee1d18684bfe81eeff78c260a94d4246b00f49d671df75a45ca5ef1372d17357587c751638f7a4e66a0757681
046ea800d647d75477c528d1ce09714f632 
   - SHA256:f9ba3563fbe79c652bdeabab9db7bca085741c80ef92ba770c7bc8b91b7c2964 
   - SHA1:8d3071e2f05b1c05a53594179d2a985eecb9ae69 [weak] 
   - MD5Sum:0b24400a2cda869352297f32ba395745 [weak] 
   - Filesize:81686648 [weak] 
Get:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main amd64 wine-staging-amd64 amd64 6.17~focal-1 [85
.3 MB] 
Err:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) focal/main amd64 wine-staging-amd64 amd64 6.17~focal-1 
  File has unexpected size (85280536 != 85266380). Mirror sync in progress? [IP: 199.232.78.217 443] 
  Hashes of expected file: 
   - SHA512:2004e42ecc066120ace39ddb2f0c89556eca37170e9d29cbabb98c8607ff38d9110ca144a32143220f7b3f7930919
218c5f95b722dfd2c1b659654cf4345ebf7 
   - SHA256:9d4c8a8fa45107023dcf395c7c0b32da3015671ab59b6a22d2a26a266235d3de 
   - SHA1:c6062245aa568957b5ec8c601bb434ce1411df3c [weak] 
   - MD5Sum:6bfc8126094d932d00ef56e8a6b02068 [weak] 
   - Filesize:85266380 [weak]

```

I manually downloaded the files and they are the correct size and the hashes are correct?
EDIT: Using Kubuntu 20.04
I have been using wine-stable since about 4.8 with no problems.
[/FONT]

---

### Post by deadflowr on 2021-09-13
Mirror sync in progress usually means the mirror is being updated.
So usually good to wait a moment and try again.
Run the s*udo apt update* command first though.

---

### Post by stinkypants on 2021-09-14
OK now. You were right. I was just impatient and like I said the files I downloaded were the correct size & the hashes were correct.

---

