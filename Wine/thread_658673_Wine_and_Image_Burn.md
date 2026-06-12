---
title: "Wine and Image Burn"
date: 2008-01-04
forum: Wine
---

### Post by hellssharpshooter on 2008-01-04
I installed wine so I could use a program called Image Burn.  Wine installed OK but Image Burn will not recognize my drives.  Could someone give me some advice.

---

### Post by hikaricore on 2008-01-05
I really don't recommend using cd/dvd burning software via WINE.

Why not just use a native program such as K3B?

---

### Post by caricc on 2008-01-05
I have used program call deep burner (free version) with wine and it works without a problem. ([www.deepburner.com](www.deepburner.com))

---

### Post by Jail on 2008-01-07
I also had problems with ImgBurn(2.3.2.0).
First I needed to turn off "SPTI - Use 'CdRom' Class", in ImgBurn menu Tools->Settings->I/O.
Second I needed to set DVD-RW in wine manually as described in "Wine User Guide" chapter 3.1.4 [http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN288]("http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN288")
In my case it was command: **ln -s /media/cdrom0 ~/.wine/dosdevices/e:**.
After that ImgBurn could detect my DVD-RW. Maybe in your case first step is enough.

---

### Post by hellssharpshooter on 2008-01-07
> **Jail said:**
> I also had problems with ImgBurn(2.3.2.0).
First I needed to turn off "SPTI - Use 'CdRom' Class", in ImgBurn menu Tools->Settings->I/O.
Second I needed to set DVD-RW in wine manually as described in "Wine User Guide" chapter 3.1.4 [http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN288]("http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN288")
In my case it was command: **ln -s /media/cdrom0 ~/.wine/dosdevices/e:**.
After that ImgBurn could detect my DVD-RW. Maybe in your case first step is enough.

Thanks for the Input I will try your solution.

---

### Post by hellssharpshooter on 2008-01-07
> **caricc said:**
> I have used program call deep burner (free version) with wine and it works without a problem. ([www.deepburner.com](www.deepburner.com))

If I can't get Image burn to work, I will try your solution.  Thanks

---

### Post by bclarky12 on 2010-04-14
go to winecfg and manually input the mount point of your cdrom drive under the devices tab. Imgburn works under wine

---

### Post by Rasa1111 on 2010-04-14
can i ask a newb Q?

Brasero burns images, does it not? 

or is this for something different? 

 I know ive burned quite a few image files/discs using it. 

Sorry if im way off base here. lol

---

### Post by bapoumba on 2010-04-15
This thread is rather old, please start a new one if you feel like to.

---

