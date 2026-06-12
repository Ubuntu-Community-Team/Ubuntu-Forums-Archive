---
title: "How do I install hplip-3.9.4b.run?"
date: 2009-05-02
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2009-05-02
I need to install the file *hplip-3.9.4b.run* in order to get the most recent version of the HP printer support driver.

I've previously installed the version available in the Synaptic Package Manager (v3.9.2), but it didn't get my printer to work.

NO LINKS, please! I'd only appreciate a simple and short step-by-step guide. =)

---

### Post by cariboo on 2009-05-02
Open an Applications-->Accessories-->Terminal and type:

```
cd ~/Desktop
```

assuming you file is located on the desktop, next make the file executeable:

```
chmod +x hplip-3.9.4b.run
```

Next run the file:

```
sudo ./hplip-3.9.4b.run
```

That's all there is to it.

---

### Post by n6yga on 2009-05-03
I did it today without having to chmod on the file. just use sh hplip-3.9.4b.run. DO NOT run it as root. If you do you will receive a warning about running as root and given an option to quit and restart as a regular user.

Mark.

---

### Post by Linux user 66 on 2009-05-03
> **cariboo907 said:**
> Open an Applications-->Accessories-->Terminal and type:

```
cd ~/Desktop
```

assuming you file is located on the desktop, next make the file executeable:

```
chmod +x hplip-3.9.4b.run
```

Next run the file:

```
sudo ./hplip-3.9.4b.run
```

That's all there is to it.

> **n6yga said:**
> I did it today without having to chmod on the file. just use sh hplip-3.9.4b.run. DO NOT run it as root. If you do you will receive a warning about running as root and given an option to quit and restart as a regular user.

Mark.

Thanks a lot for your replies! =)

---

