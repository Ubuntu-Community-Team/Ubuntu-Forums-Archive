---
title: "interesting speed comparison"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by tweston on 2008-01-22
I ran these tests on a year-old Acer with an AMD Athlon 64 X2 Dual Processor 4200+ @ 2.20 GHz

The code, replete with timer, is straight from this web page: "JavaScript speed test"
 url: [http://www.jorendorff.com/articles/javascript/speed-test.html](http://www.jorendorff.com/articles/javascript/speed-test.html)
```

+-------------+
| Test 1:     |
+-------------+
    var a;
    var x = {};
    %%
    a = [];
    for (var i = 0; i < 1000; i++)
        a.push(x);
-------------------------------------------------------------
OS                            Browser                 Time
-------------------------------------------------------------
Linux   Ubuntu 7.10 amd64     Firefox 2               1.58 ms
Windows Vista HomePremium     Firefox 2               1.78 ms
Linux   Ubuntu 7.10 i386      Firefox 2               2.18 ms
Windows Vista HomePremium     IE 7                    2.23 ms

```
```

+-------------+
| Test 2:     |
+-------------+
    var text = document.documentElement.innerHTML;
    var regex = /<([\w-]+)/g;
    var matchArray;
    var match;
    var count = 0;
    %%
    while ((matchArray = regex.exec(text)) !== null) {
        match = matchArray[1];
        count++;
    }
-------------------------------------------------------------
OS                            Browser                 Time
-------------------------------------------------------------
Linux   Ubuntu 7.10 amd64     Firefox 2               4.72 ms
Windows Vista HomePremium     IE 7                    5.56 ms
Windows Vista HomePremium     Firefox 2               5.74 ms
Linux   Ubuntu 7.10 i386      Firefox 2               5.97 ms

```
Conclusion
The 64 bit verison of Linux is approximately 20% faster than either the 32 bit Linux or the 
Windows (which is only available as 32 bit)

---

### Post by NightwishFan on 2008-01-22
I think you can get Vista in 64-bit. However 64-bit Ubuntu simply owns. ^^V

---

### Post by tweston on 2008-05-30
Yes, a vista 64 bit is available, but it's not installed by most manufactures because of driver incompatibility issues. So you buy an AMD64 box, but it comes with 32bit Vista!

---

