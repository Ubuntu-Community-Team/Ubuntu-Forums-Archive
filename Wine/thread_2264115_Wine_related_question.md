---
title: "Wine related question"
date: 2015-02-05
forum: Wine
---

### Post by mandarpowale on 2015-02-05
Hi

Is there any danger to my hardware due to 'WINE' ? I just ran a test for a game on [www.canyourunit.com]("http://www.canyourunit.com") and it shows my my GPU as I-5 quad core 3.4 GHz (it is just an Athlon II X2 3.2 ghz). ALso my card is shown as 7900 series (it is 7750 series)

I hope that the wine is not overclocking my system because i don't wanna lose my warranty . I can't afford it.

I await your reply eagerly.

Thanks in advance'
Mandar

---

### Post by Penguin360 on 2015-02-05
> **mandarpowale said:**
> Hi

Is there any danger to my hardware due to 'WINE' ? I just ran a test for a game on [www.canyourunit.com]("http://www.canyourunit.com") and [SIZE=4]_**[COLOR=#ff0000]it[/COLOR]**_[/SIZE] shows my my GPU as I-5 quad core 3.4 GHz (it is just an Athlon II X2 3.2 ghz). ALso my card is shown as 7900 series (it is 7750 series)

I hope that the wine is not overclocking my system because i don't wanna lose my warranty . I can't afford it.

I await your reply eagerly.

Thanks in advance'
Mandar

As far as I know, WINE will not change your hardware. The online tool that shows the hardware information may not be correct, use Ubuntu native tool to display your hardware information.

---

### Post by mandarpowale on 2015-02-05
By **'IT'** i meant that the website 'www.canyourunit.com' shows me so and so.

ADD: I also felt that the website detected thing incorrectly but i needed confirmation.

By **'IT'** i meant that the website 'www.canyourunit.com' shows me so and so. When I used 'hardinfo', it shows me accurate description of hardware though.

---

### Post by Bucky Ball on 2015-02-05
*Thread moved to **Wine**.*

---

### Post by Penguin360 on 2015-02-05
> **mandarpowale said:**
> By **'IT'** i meant that the website 'www.canyourunit.com' shows me so and so. When I used 'hardinfo', it shows me accurate description of hardware though.

As I said before, the online tool may not detect the correct information of your hardware. I trust "hardinfo". You can also use:
```
lspci -nnk | grep VGA -A1
```

Or:
```
sudo lshw | less
```

to confirm your hardware information is correctly displayed.

---

### Post by mandarpowale on 2015-02-06
Thanks everyone. 

I will boot to UBUNTU and try these commands out.

---

