---
title: "Adding repos"
date: 2008-06-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by sayakb on 2008-06-05
I added: [http://en.opensuse.org/Package_Repositories](http://en.opensuse.org/Package_Repositories)
I added OSS, non OSS, Update, KDE Core, KDE Community and KDE Backports.
After adding, I pressed Finish. Now its indefinitely downloading packages.
Did I do right? Is this like Ubuntu's package/sources information Reload?
I hope it's not downloading all the packages from the resource.
Sorry, I haven't used Suse..

---

### Post by 67GTA on 2008-06-06
Yast has to download the metadata files in those repos. It is very similar to apt-get update, but a lot slower. After the first initial download session, it will refresh them a little faster.

---

