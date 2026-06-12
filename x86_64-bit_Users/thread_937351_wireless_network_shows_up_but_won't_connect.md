---
title: "wireless network shows up but won't connect"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by poadshaw on 2008-10-03
Preloge: hey all.  I am having trouble with my wireless.  I have followed the tutorials and got everything working yay!  It worked at home but did not work at school... so i fiddled and now it doesn't work anywhere.

Issue: I can see my network and several others when I click on the wireless network connection icon.
I have 4/4 bars (sometimes 3/4 but that worked before just fine)
When I input my wireless Passphrase my icon just thinks for a while and then askes for it again.  I know I am inputting the correct "passphrase" and have selected each of the four drop down "Wireless Securtiy" options.  I believe I should be using "WEP 128-bit Hex"

here is the output:

:~$ iwconfig
lo    no wireless extensions.

eth0  no wireless extensions.

wlan0 IEEE 802.11g  ESSID:off/any
      Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated
      Bit Rate: 54Mb/s
      Power Management:off
      Link Quality:0  Signal level:0  Noise level:0
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0 Missed beacon:0



I know enough to output iwconfig but that's about as far as my linux / bash experience goes.  So please be gentle and thank you in advance for any information you can impart.

I did spend several hours searching for related issues.  I'm wondering about the  "Mode:managed" part.

---

### Post by Sef on 2008-10-04
What is your version of Ubuntu?

---

