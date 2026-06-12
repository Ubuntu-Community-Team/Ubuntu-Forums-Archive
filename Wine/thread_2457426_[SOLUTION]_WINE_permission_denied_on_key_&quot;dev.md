---
title: "[SOLUTION] WINE: permission denied on key &quot;dev.i915.perf_stream_paranoid&quot;"
date: 2021-02-01
forum: Wine
---

### Post by ception on 2021-02-01
Hey there everyone.

First time poster, relatively newer user, have been dabbling in Linux for some years now but recently made it my primary OS. Any who, after banging my head against the wall and lots and lots of research into this issue that arises with INTEL platforms while using WINE, I was unable to come up with a simple solution. So to save (hopefully someone) time and energy, here is a solution for the following WINE issue that comes up when running it in terminal.

[U][I][B]ISSUE:

[/B][/I][/U][INDENT=2]```
INTEL-MESA: warning: Performance support disabled, consider sysctl dev.i915.perf_stream_paranoid=0
```[/INDENT]

The problem is that by default, the **stream_paranoid=0** is actually set to 1, to change this you need to perform the following command in terminal:

[U][I][B]COMMAND:

[/B][/I][/U][INDENT=2]```
echo dev.i915.perf_stream_paranoid=0 > /etc/sysctl.d/60-mdapi.conf
```[/INDENT]

_***UNFORTUNATELY***_.. you will always come up with the same issue:[INDENT=2]```
permission denied on key "dev.i915.perf_stream_paranoid"
```
[/INDENT]

The simple solution to this is to simply allow root on your user. However after looking around I realised that the terminal command SU ROOT is not enabled by default on Ubuntu. The following 3 steps will fix all your problems.

[U][I][B]SOLUTION:
[/B][/I][/U]
[LIST=1]
[*=2]```
sudo -i
```
[*=2]```
echo dev.i915.perf_stream_paranoid=0 > /etc/sysctl.d/60-mdapi.conf
```
[*=2]```
sudo reboot
```
[*=2]Run the following code after reboot to confirm that the stream_paranoid has been changed to 0 ```
sysctl -n dev.i915.perf_stream_paranoid
```
[/LIST]

I'm hoping that this post will eventually be cached by Google's search engine, and that it will save some newbie like myself a lot of time and frustration.. I hope this helps, I know it's kind of a ridiculous post, but it's with good helping intention. Cheers!

**[COLOR=#a9a9a9]*NOTE: MODS I was not sure which section this belonged too so please feel free to move it to the appropriate section. I figured this was a better place to start.*[/COLOR]**

---

### Post by QIII on 2021-02-01
Moved to the Wine sub-forum, as that would certainly be the best for a question about Wine.

Please note the tag line for the Resolution Centre, where you first posted this:

> Forum: Resolution Centre
This is the place to contact a forum admin concerning problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse.

Please note that posting permissions are restrictive in this sub-forum. You may start a thread, but you can only post to your own, not to others' threads. Forum moderators and admins are the only forum members who can post to any thread. Nor can you edit your posts. This latter is to prevent any dispute over what might or might not have been said.

For your own security, please do not post your email in threads, thanks.

Please follow the forum Code of Conduct when posting.

Also note:

> Account queries following change to SSO login
Please read this sticky BEFORE posting your request in the Resolution Centre.

Username change requests
Please read this sticky BEFORE posting your request in the Resolution Centre.

---

### Post by sjuk on 2021-08-30
Doesn't work for me on Ubuntu 20.04.3. I did it exactly as described in the solution. But dev.i915.perf_stream_paranoid keeps beeing 1 instead of 0.
```
$ sysctl -n dev.i915.perf_stream_paranoid
1
```

---

### Post by sjuk on 2021-08-30
Digging deeper I found something unexpected.
```
$ journalctl -g dev.i915.perf_stream_paranoid
systemd-sysctl[376]: Couldn't write '0' to 'dev/i915/perf_stream_paranoid', ignoring: No such file or directory
```
Seems like systemd-sysctl has some trouble configure this kernel setting on boot. Perhaps the setting will be created later on boot.

But if you need a stable workaround for that issue please check [URL="https://software.intel.com/content/www/us/en/develop/articles/enabling-vulkan-vk-intel-performance-query-extension-in-ubuntu.html"]https://software.intel.com/content/www/us/en/develop/articles/enabling-vulkan-vk-intel-performance-query-extension-in-ubuntu.html
[/URL]
Step 7.2: An automated approach to do this is to add a cron job that executes whenever the platform reboots, as follows:
```
$ sudo crontab -e # Add the following line at the end or as the 1st no comment line:
@reboot /sbin/sysctl -q -w dev.i915.perf_stream_paranoid=0
```

I hope this helps.

---

### Post by Franky75 on 2021-09-09
For me it helped to add two spaces around the =

```
echo dev.i915.perf_stream_paranoid = 0 > /etc/sysctl.d/60-mdapi.conf
```

then do a 

```
[FONT=monospace][COLOR=#000000]systemctl restart systemd-sysctl[/COLOR][/FONT]
```

to activate the changes.

@ception: thank you! this pointed me in the right direction!

---

### Post by shantiq on 2022-07-16
i can corroborate good results here too on 22.04 in July 2022

```
shan@shan-Aspire-XC-780:~$ sysctl -n dev.i915.perf_stream_paranoid
0



```


so thanx to you all   ;   also had to have the spaces around ```
echo dev.i915.perf_stream_paranoid = 0 > /etc/sysctl.d/60-mdapi.conf
```

---

### Post by TheFu on 2022-07-16
```
echo dev.i915.perf_stream_paranoid = 0 > /etc/sysctl.d/60-mdapi.conf
```
needs quotes.
```
echo "dev.i915.perf_stream_paranoid = 0" > /etc/sysctl.d/60-mdapi.conf
```

If you are using that method.  My laptop that uses the i915 driver isn't booted, so I haven't tested it, specifically.
The cleaner answer is to use sysctl or edit the /etc/sysctl.conf file adding the new setting to the end of that file, with an empty blank line after it.
[/code]dev.i915.perf_stream_paranoid = 0[/code]
The i915 kernel driver must be loaded before the setting is processed.  The /etc/sysctl.d/60-.... controls the order it is processed like the old rc.d/ startup files.

> Warning: The restrictive defaults of the perf_event_paranoid family of options exists because there is risk associated with allowing applications to access performance data [20]. With this being said, dev.i915.perf_stream_paranoid only influences access to GPU performance counters, which carry less risk than e.g. CPU architectural execution context registers.
There are risks. Beware.


And using the [SOLUITION] label is nice, but it would be better to use the "Thread Tools" button near the top and mark this thread as "SOLVED". That's a field in the DB and how people search forums.

---

