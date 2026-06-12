---
title: "Nautilus not working"
date: 2009-08-24
forum: x86 64-bit Users
---

### Post by anafshalom on 2009-08-24
After upgrading to Jaunty Jackalope nautilus does not work I get this message:

[SIZE="1"][INDENT]Nautilus cannot be used now. Running the command "bonobo-slay" from the console may fix the problem. If not, you can try rebooting the computer or installing Nautilus again.

Bonobo could not locate the Nautilus_shell.server file. One cause of this seems to be an LD_LIBRARY_PATH that does not include the bonobo-activation library's directory. Another possible cause would be bad install with a missing Nautilus_Shell.server file.

Running "bonobo-slay" will kill all Bonobo Activation and GConf processes, which may be needed by other applications.

Sometimes killing bonobo-activation-server and gconfd fixes the problem, but we do not know why.

We have also seen this error when a faulty version of bonobo-activation was installed.
[/INDENT][/SIZE]

I've Tried bonobo-slay, Ive tried purging Nautilus and reinstalling it.  I've tried uninstalling ubuntu-desktop and reinstalling.

Everything else I do works fine, but I'd like to get Nautilus working again.

---

### Post by Thelasko on 2009-08-24
Did you try deleting or renaming the .nautilus file in your home directory?

---

### Post by anafshalom on 2009-08-24
> **Thelasko said:**
> Did you try deleting or renaming the .nautilus file in your home directory?

I tried renaming it, I tried deleting it.  A new empty one appears, but Nuatilus still does not work.

Any other suggestions?

---

### Post by Thelasko on 2009-08-25
> **anafshalom said:**
> I tried renaming it, I tried deleting it.  A new empty one appears, but Nuatilus still does not work.

Any other suggestions?

Renaming and deleting those folders does effectively the same thing.

My only other suggestion is to rename/delete the following files one at a time.
[LIST]
[*].gnome
[*].gnome2
[*].gnome2_private
[*].metacity
[/LIST]
Restart your X-server after each.  If it doesn't solve the problem, you can restore the old file if you like.

**Explanation:** These are all configuration files that your system uses.  They are specific to each user, but when you upgraded, they were not changed.  Therefore, I suspect one of these files isn't compatible with your upgrade.  By deleting or renaming these files your system returns to it's default configuration automatically (which is why the folder gets regenerated).

---

### Post by anafshalom on 2009-08-25
> **Thelasko said:**
> Renaming and deleting those folders does effectively the same thing.

My only other suggestion is to rename/delete the following files one at a time.
[LIST]
[*].gnome
[*].gnome2
[*].gnome2_private
[*].metacity
[/LIST]
Restart your X-server after each.  If it doesn't solve the problem, you can restore the old file if you like.

**Explanation:** These are all configuration files that your system uses.  They are specific to each user, but when you upgraded, they were not changed.  Therefore, I suspect one of these files isn't compatible with your upgrade.  By deleting or renaming these files your system returns to it's default configuration automatically (which is why the folder gets regenerated).

I don't have a .gnome or a .metacity folder.
I tried to delete the other two, but same result:(

---

