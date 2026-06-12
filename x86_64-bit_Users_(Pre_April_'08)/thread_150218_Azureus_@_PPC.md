---
title: "Azureus @ PPC?"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by phibxr on 2006-03-25
Is it possible to run Azureus under Ubuntu on a PPC? I read that IBMs JRE isn't compatible with Azureus.

Are there any other alternatives to bittorrent and bittornado? Those two applications are practically EATING my CPU.

---

### Post by pvz on 2006-03-26
You can run Azureus with IBM Java, but it is a memory hog. I have been using Ktorrent [http://ktorrent.pwsp.net](http://ktorrent.pwsp.net) for a while now and I'm very happy with it. You can download a Breezy PPC .deb that I compiled from their download section.

---

### Post by phibxr on 2006-03-28
KTorrent looks like a very nice alternative. And that comes from someone who dislikes QT to the death. ;)

---

### Post by Jawbreaker4Fs on 2006-03-28
any way to use this with gnome?

---

### Post by phibxr on 2006-03-28
I don't know if this is the optimal way of doing it, but since no-one else have answered yet, here is how I did it.

1. Install some KDE-app to get the dependencies right first, i.e. k3b (a CD/DVD-burner app)

```
sudo apt-get install k3b
```

2. Download and install KTorrent.

```
wget http://ktorrent.pwsp.net/downloads/1.2/ktorrent_1.2-1_powerpc.deb
sudo dpkg -i ktorrent_1.2-1_powerpc.deb
```

That should get it working for you at least. If you don't have a PPC, choose another package from the link provided a few posts earlier.

---

