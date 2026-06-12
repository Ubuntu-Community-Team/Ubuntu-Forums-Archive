---
title: "How to associate a wine application with pdf file types in Ubuntu Unity 16.04"
date: 2017-03-14
forum: Wine
---

### Post by bernnhugh on 2017-03-14
I am running pdf-xchange (tracker software) using Wine using the portable version of the pdf-xchange software.   Since it is a portable version it was not "installed" by Wine.
I created a .desktop file in my .local/share/applications directory:

```
[Desktop Entry]
Version=1.0
Name=PDF-Xchange
Comment=Portable Version 
Exec=/home/bhitch/pdfX/PDFXEdit.exe
Path=/home/bhitch/pdfX/
Icon=/home/bhitch/pdfX/pdf.ico
Terminal=false
Type=Application
Categories=Utility;Application;
MimeType=application/postscript;application/pdf;
```

This .desktop file worked to the extent that when I click on the Ubuntu search button (top of the task bar) and type in pdf, my application does show up under applications with the correct icon and runs when I click on it.  I am able to pin it to the taskbar and it launches correctly.

What I have not been able to do is get Ubuntu to use it as the default application for opening pdf files.
If I right click on a pdf file and select properties->Open With - my pdf-exchange application is not showing up in the list so I cannot select it as the default application.
What do I have to do to get my application into that list?

Thanks for any help,
Bernn

---

### Post by howefield on 2017-03-15
Thread moved to the "*Wine*" forum for a better fit.

---

