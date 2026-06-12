---
title: "dial-up troubles"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by mohansai on 2007-07-22
Dear friends:
I use a bsnl dial-up (sancharnet) connection. Eversince, the ISP announced speeding up the dial-up connection from 56kbps to 256kbps a few months back, ironically my UBUNTU linux based dial-up started giving troubles. Following is the summary of my attempts to successfully connect
(1) I modified my wvdial.conf by adding Stupid Mode = yes, this enabled me to login but the connection was UNSTABLE (disconnecting on its own)
(2) I modified the mtu to a lower value 296 (in the file /etc/ppp/options file), result --> better than after (1) but still unstable.
(3) Modified wvdial.conf in the following manner 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ----> (UNSTABLE) to 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +MS=90 ----> (UNSTABLE as well) so later to 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +MS=34 ---> connection was very stable but very very slow.

The connection became slower than before the ISP announced speeding up their service. Infact, I found that dial-up under Win-XP was now faster than LINUX.
The only other doubt that I have in my mind is about any compression tools/software which the ISP has deployed and UBUNTU is not supporting. By now, wasted a lot of money on phone calls on connection failures/trials (phone bills equivalent to my entire phone usage for internet during the previous year) raising the fury of my family members & I eagerly look forward to some intelligent and kind person to suggest me a solution.

best regards,
Mohan Sai:guitar:

[email]mohan.sai@rediffmail.com[/email]

---

### Post by Bartender on 2007-07-22
mohan -
Are we talking plain old dial-up?
I don't know where you are on the planet, but here in the States anything above 56K is an illusion.  As you mentioned, the ISP will use various compression algorithms.  Then they'll say their dial-up is "as fast as" 256K or whatever.
I'm under the impression that Linux doesn't work well with these compression techniques.  I assume you've already contacted the ISP and asked them about turning it off?  From what you said it sounds like they just did it to everyone?  Usually (here anyway) the ISP offers compression for a higher fee and allows the end user to stick with plain old dial-up if they so choose.
Do you have any other choices for ISP's?

---

