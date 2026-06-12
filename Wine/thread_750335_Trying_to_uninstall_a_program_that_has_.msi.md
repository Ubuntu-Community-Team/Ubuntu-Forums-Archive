---
title: "Trying to uninstall a program that has .msi"
date: 2008-04-09
forum: Wine
---

### Post by SlappyPappy on 2008-04-09
Apparently the built in uninstaller won't do this. I read the Wine FAQ and it told me so. It does not though give me a way to uninstall a program with .msi.

Does anyone here know how to remove a program that does have a .msi?

Would like to uninstall a program so that I can reinstall it.

Thanks for any help.

---

### Post by cogadh on 2008-04-09
I don't know where in the FAQ you read that, but the Wine uninstaller tool should be able to uninstall it just like any other windows software. If it doesn't, then you may just be able to run .msi file again and choose the "remove" option (if it is one of the installers that has that). If neither of those work, then you can try deleting the installed directory for the program, then run Wine's uninstaller tool. It will *usually* detect that the software has been removed and clean up any leftover registry entries for you.

---

