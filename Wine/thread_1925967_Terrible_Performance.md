---
title: "Terrible Performance"
date: 2012-02-15
forum: Wine
---

### Post by lolwhatz on 2012-02-15
Hi guys i need help... 

All wine versions runs so laggy in Starcraft, cursor lags a lot... 

I have latest drivers 

Specs: 

- Phenom ii x4 955 

- Radeon 5770 

- Ubuntu 11.10 64 bit

help!!!

---

### Post by lolwhatz on 2012-02-17
nobody can help me??

---

### Post by 23dornot23d on 2012-02-17
From a google search the radeon 5770 seems to be a problem .....

[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#pq=radeon+5770+&hl=en&gs_nf=1&tok=LHn09bnq9x_9ALhEh77LMQ&cp=4&gs_id=y1&xhr=t&q=linux+radeon+5770&pf=p&client=ubuntu&hs=o5h&channel=fs&sclient=psy-ab&pbx=1&oq=linyRadeon+5770&aq=0l&aqi=g-l1g-jl1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#pq=radeon+5770+&hl=en&gs_nf=1&tok=LHn09bnq9x_9ALhEh77LMQ&cp=4&gs_id=y1&xhr=t&q=linux+radeon+5770&pf=p&client=ubuntu&hs=o5h&channel=fs&sclient=psy-ab&pbx=1&oq=linyRadeon+5770&aq=0l&aqi=g-l1g-jl1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499)

not seeing many good results for success with it ..... but the thing to do is make sure
that the drivers are working and using it ..... additional drivers.

Best information I can find at this moment in time .... solved threads below


[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=linux+Radeon+5770+solved&pbx=1&oq=linux+Radeon+5770+solved&aq=f&aqi=&aql=&gs_sm=3&gs_upl=319826l328519l2l328836l17l12l5l0l0l0l705l2516l0.9.1.1.6-1l17l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=linux+Radeon+5770+solved&pbx=1&oq=linux+Radeon+5770+solved&aq=f&aqi=&aql=&gs_sm=3&gs_upl=319826l328519l2l328836l17l12l5l0l0l0l705l2516l0.9.1.1.6-1l17l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499)

---

### Post by Dlambert on 2012-02-17
I would maybe try installing the latest BETA driver from AMD

---

### Post by phibxr on 2012-02-17
> **lolwhatz said:**
> Hi guys i need help... 

All wine versions runs so laggy in Starcraft, cursor lags a lot... 

I have latest drivers 

Specs: 

- Phenom ii x4 955 

- Radeon 5770 

- Ubuntu 11.10 64 bit

help!!!

Use the proprietary Radeon-drivers, and do NOT run a compositing window manager (like Unity 3D/2D).

Install XFCE and disable the compositing. Having compositing active will easily eat more than two thirds of your possible FPS.

---

### Post by lolwhatz on 2012-02-18
> **phibxr said:**
> Use the proprietary Radeon-drivers, and do NOT run a compositing window manager (like Unity 3D/2D).

Install XFCE and disable the compositing. Having compositing active will easily eat more than two thirds of your possible FPS.

I have Old Gnome desktop and compositing IS disabled

Anyway i tried XFCE but i had same issues...

ati drivers sucks!! :(

thanks for the help...

---

### Post by Dlambert on 2012-02-19
> **lolwhatz said:**
> I have Old Gnome desktop and compositing IS disabled

Anyway i tried XFCE but i had same issues...

ati drivers sucks!! :(

thanks for the help...

Nvidia all the way, but the latest AMD drivers are a necessary evil

---

### Post by Dlambert on 2012-02-19
> **23dornot23d said:**
> From a google search the radeon 5770 seems to be a problem .....

[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#pq=radeon+5770+&hl=en&gs_nf=1&tok=LHn09bnq9x_9ALhEh77LMQ&cp=4&gs_id=y1&xhr=t&q=linux+radeon+5770&pf=p&client=ubuntu&hs=o5h&channel=fs&sclient=psy-ab&pbx=1&oq=linyRadeon+5770&aq=0l&aqi=g-l1g-jl1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#pq=radeon+5770+&hl=en&gs_nf=1&tok=LHn09bnq9x_9ALhEh77LMQ&cp=4&gs_id=y1&xhr=t&q=linux+radeon+5770&pf=p&client=ubuntu&hs=o5h&channel=fs&sclient=psy-ab&pbx=1&oq=linyRadeon+5770&aq=0l&aqi=g-l1g-jl1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499)

not seeing many good results for success with it ..... but the thing to do is make sure
that the drivers are working and using it ..... additional drivers.

Best information I can find at this moment in time .... solved threads below


[https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=linux+Radeon+5770+solved&pbx=1&oq=linux+Radeon+5770+solved&aq=f&aqi=&aql=&gs_sm=3&gs_upl=319826l328519l2l328836l17l12l5l0l0l0l705l2516l0.9.1.1.6-1l17l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499](https://www.google.com/search?client=ubuntu&channel=fs&q=Radeon+5770+&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&channel=fs&sclient=psy-ab&q=linux+Radeon+5770+solved&pbx=1&oq=linux+Radeon+5770+solved&aq=f&aqi=&aql=&gs_sm=3&gs_upl=319826l328519l2l328836l17l12l5l0l0l0l705l2516l0.9.1.1.6-1l17l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=19b47237870fde75&biw=976&bih=499)

Phoronix has done benchmarks of the 5770 in Ubuntu, it works fine.

---

