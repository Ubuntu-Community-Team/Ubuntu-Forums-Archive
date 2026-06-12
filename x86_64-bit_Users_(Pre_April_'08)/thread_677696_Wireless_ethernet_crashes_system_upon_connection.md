---
title: "Wireless ethernet crashes system upon connection"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by DTXBrian on 2008-01-25
I've got a Gateway MX3414 laptop, which is famous for it's inability to run Ubuntu properly.  Indeed, in late 2006, I attempted to make the switch, only to be discouraged from the lack of sound-driver support.  I saw a thread last week with a solution to the ALSA problem, so I tried again, and managed to get the sound working.  I was stoked!

But now, there are other issues.  I installed Ubuntu 7.10 x64 on my system.

My wireless ethernet chipset is a Realtek RTL8185.

I am logging into a system with WEP protection.

If I click on the wireless ethernet symbol in the upper right, choose my ESSID, and use the prompts to put in the WEP security information, the icon will then spin like it's trying to connect, and after a couple of seconds, it will freeze.  At which point, the Caps Lock light will continuously flash on my keyboard.

I did as much research as I could find, and even attempted to install the Linux drivers for this chipset from Realtek's web-site:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352)

Nothing seems to work, except a tremendously tedious procedure, where I select the option to manually configure the ethernet, turning off the browsing feature.  I then have to turn back on the browsing feature.  Then, I choose to connect to another net work, and type in my network name, plus WEP key... and it shows the bars for the signal... but upon opening Firefox, there is still no connection.

So once again, I select the wlan0 icon, and choose my ESSID off of the list... and lo-and-behold, it works, without freezing.  I am utterly, entirely stumped.  And frustrated horribly by the situation.

Setting my ESSID and key as defaults in iwconfig, and to no avail.  My computer freezes upon seeking the networks.  Damnedest thing I've seen in ages.

Any assistance would be much appreciated.  Thank you for any help you can offer.

---

### Post by DTXBrian on 2008-01-25
I tried to configure things to log-in automatically with iwconfig, to see if that might help with the matter, but no... it's simply caused problems.  Now Ubuntu won't even boot... even in recovery mode.

I did, however, get the last few lines of text on the screen before it froze...  Anybody help decypher it?

> [   42.305058]  [<ffffffff88193f06>] :ieee80211_rtl:rtl_ieee80211_xmit+0x516/0x980
[   42.305116]  [<ffffffff803b0369>] sock_wmalloc+0x29/0x60
[   42.305158]  [<ffffffff803cb071>] __qdisc_run+0x71/0x220
[   42.305200]  [<ffffffff803ba8be>] dev_queue_xmit+0x1fe/0x300
[   42.305245]  [<ffffffff882932da>] :af_packet:packet_sencmsg_spkt+0x1ea/0x250
[   42.305290]  [<ffffffff803ac0b6>] sock_sendmsg+0x136/0x150
[   42.305335]  [<ffffffff8024b2b0>] autoremove_wake_function+0x0/0x30
[   42.305382]  [<ffffffff802a480c>] do_path_lookup+0xbc/0x230
[   42.305425]  [<ffffffff80422c44>] unix_find_other+0x54/0x1e0
[   42.305469]  [<ffffffff8032313f>] _atomic_dec_and_lock+0x4f/0x70
[   42.305512]  [<ffffffff803ac586>] sys_sendto+0x146/0x1b0
[   42.305554]  [<ffffffff8024b1ac>] bit_waitqueue+0x1c/0xb0
[   42.305595]  [<ffffffff8024b288>] wake_up_bit+0x18/0x40
[   42.305643]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[   42.305685]  
[   42.305718]  
[   42.305719] Code: ff 50 10 4c 89 e7 e8 c2 a7 08 f8 48 89 c7 48 c1 ef 0c e8 06
[   42.306272] RIP  [<ffffffff88198d23>] :ieee80211_rtl:prism2_wep_encrypt+ox1e3/0x2a0
[   42.306351]  RSP <ffff810035b6fa48>
[   42.306387] CR2: 000000000000000e
[   42.306425] Kernel panic - not syncing: Aiee, killing interrupt handler!

The last line scares the hell out of me...

---

