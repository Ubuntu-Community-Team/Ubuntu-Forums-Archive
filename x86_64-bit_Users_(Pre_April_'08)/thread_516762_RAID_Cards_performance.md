---
title: "RAID Cards performance"
date: 2007-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by MMoudry on 2007-08-03
Hi,
I bought an adaptec 2420SA controller and setup a RAID 6 with 4 500 GB WD5000YS Caviar RE2. This gives me two drive failure safety and should give some decent performance, however bonnie gives me this :
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
moudry.com       4G 30348  47 35023   5 12701   2 30363  49 44790   6 165.0   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  2140  12 +++++ +++  1716  10  2166  13 +++++ +++  1507   9
moudry.com,4G,30348,47,35023,5,12701,2,30363,49,44790,6,165.0,0,16,2140,12,+++++,+++,1716,10,2166,13,+++++,+++,1507,9

where as this gentlemen from [https://listman.redhat.com/archives/ataraid-list/2007-January/msg00009.html](https://listman.redhat.com/archives/ataraid-list/2007-January/msg00009.html) got this : 

Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec  %CP /sec   %CP
adaptec5         2G 45114 86  80970 33  35300 12  50267 79  119029 15  296.3  0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP /sec %CP
                 16  4130  15 +++++ +++ 30544 100 26745  94 +++++ +++ +++++ +++


Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec  %CP /sec  %CP
sii10            2G 43516  83 53765  27 30708 12  45898 76  111066 17  310.6 1
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP /sec %CP
                 16 15515  97 +++++ +++ +++++ +++ 28323 100 +++++ +++ +++++ +++


Now even though this gentleman uses RAID 5, his scores are much better than mine. I am no expert but can anybody give his input?

Thank you very much,

MM

---

