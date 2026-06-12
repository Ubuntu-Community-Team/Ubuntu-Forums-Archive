---
title: "64bit mysql on edgy 6.10 (64bit kernel 2.17-10)"
date: 2007-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghosthand on 2007-04-16
I've been experiencing some intermittent connection problems on mysql5.0.24a-9ubuntu2.  The only way I know that there are any problems going on is that my php scripts can't connect to the mysql server.  I set them up to email me when this is happening and if I'm luck enough to be near a computer I can verify that the mysql server is not accepting connections from anywhere - connections just time out.  I've turned on all logging for mysql and nothing strange shows up during these periods.  The logs always show the last connection terminating normally and then nothing else.  Strangest thing is that after about 10 to 15 minutes the server starts accepting connections again without anyone having done anything.  Manually restarting the server during these periods fixes the problem too, but you have to go through and kill the server using its pid.  The normal /etc/init.d/mysql restart just sits there.  Trying to use mysqladmin to query the processlist doesn't work, it just times out.  I was wondering if anyone else has experienced anything similar, or if anyone has any ides of what else to try.  This problem was occurring on the last version of mysql5.0.24a-9ubuntu too.  Upgrading to mysql5.0.24a-9ubuntu2 didn't help.

I just upgraded to kernel 2.6.17-11 from edgy-proposed, but the problem is so intermittent that the only way I can know if this fixed anything is by simply waiting to see if the problem crops back up.

---

