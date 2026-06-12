---
title: "Help wanted: killall wine key shortcut..."
date: 2007-08-17
forum: Wine
---

### Post by tomplast on 2007-08-17
Hi everyone.

I'm seeking an answer for the problem that I (or rather my cousin) have, he isn't a user who likes to fiddle with the terminal so I got this idea.

Sometimes when wine hangs it would been have a lot easier if there was a key shortcut to kill it (wineserver I assume). I wonder if creating a new script based upon /etc/event.d/ctrl-alt-delete would be a good start but I tried and changed it into ctrl-alt-home (both the name and the content of the file) but so far no luck.

Do I have to restart some process or something? Help would be much appreciated. Thank you :)

---

### Post by jim_p on 2007-08-18
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

The above, taken from ubuntuguide.org, binds Ctrl+Alt+Del to the system monitor.
So, with some minor changes, you can do this

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Space"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "killall wineserver"
```

I cant say it will work for sure. It's just a random thought

---

### Post by cogadh on 2007-08-18
I would suggest changing one thing. Instead of "killall wineserver" use "wineserver -k", that way Wine handles the winserver stop on its own, rather than letting the system kill it (helpful for troubleshooting).

---

