---
title: "[SOLVED] Openoffice.org writer documents get set to read-only"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by Deus42 on 2008-06-24
I may be doing something really stupid, but I looked around the forums and can't seem to find an answer.

Openoffice.org writer on 8.04 seems to set a document to read-only for some unknown reason. I tried going to format -> sections and removing the protected status, but it still will not let me edit the doc.

I double checked the file permissions as well.

The specific error is "Readonly content cannot be changed. No modifications will be accepted"

I only seem to have this problem on my 64 bit box

---

### Post by Deus42 on 2008-06-24
It turns out that I haven't had this break using the native odt format.

Also, I attached the document. It was just a basic linux tutorial for some co-workers.

---

### Post by pixel :-) on 2008-06-25
It's a bug.The automatic table of contents,is protected from manual changes,this is interpreted that the hole document is read only.

The only workaround - right click in Table of contents, menu "Edit Index/Table", uncheck check box "Protected against manual changes".Restart openoffice.

---

### Post by indikid on 2008-06-26
> **Deus42 said:**
> I may be doing something really stupid, but I looked around the forums and can't seem to find an answer.

Openoffice.org writer on 8.04 seems to set a document to read-only for some unknown reason. I tried going to format -> sections and removing the protected status, but it still will not let me edit the doc.

I double checked the file permissions as well.

The specific error is "Readonly content cannot be changed. No modifications will be accepted"

I only seem to have this problem on my 64 bit box
  
Not sure if it will work but Try this: 
Open the document, go to Tools>Options>Openoffice.org>Security and see if the option open this document in read-only mode is checked. If yes remove the ckeck mark and then click OK. Open the document again.

---

### Post by Deus42 on 2008-06-26
The read-only box was not checked, so I had to go with pixel's method, which worked great.

Thanks!

---

### Post by janek0 on 2008-08-17
For anyone interested - same bug appears also in case of indices, The solution is just the same - uncheck the protection option available under "edit table of contents" in context menu. Quite obvious but took me about an hour to figure out. Ubuntu 8.04 64bit/OO 2.4.0-3ubuntu6

---

### Post by shadfurman@hotmail.com on 2008-11-13
I had this same problem on my HP Pavilion dv5 laptop running Vista 64bit home. I don't know which part of what I did got around it but this is what I did and one or more of the steps unlocked the read only.

1. In openoffice with the file open I click FILE>PROPERTIES and clicked RESET in the dialog box (in the GENERAL tab)

2. I opened the containing directory in explore and (right clicked)>PROPERTIES on the file and unchecked the READ ONLY box

3. I reopened and resaved it as a different filename

Hope this works for someone else.

---

### Post by ThomasNovin on 2008-11-28
I could not get rid of this problem in OOo 3.0 (from Ubuntu PPAs). I downgraded to the 2.4.1-version in Intrepid and the documents worked normally again.

---

### Post by cajunlibra on 2009-01-26
Pixel's solution didn't work for me as I am unable to find "Edit Index/Table".  That isn't in my context menu nor the "Edit" menu.

---

