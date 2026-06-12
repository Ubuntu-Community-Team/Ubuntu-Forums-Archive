---
title: "Wine Multiple Entries In &quot;Open With&quot; dialog.  (Fix/Workaround)"
date: 2012-02-07
forum: Wine
---

### Post by cbanakis on 2012-02-07
Not sure if anyone has ever figured this out, but I did, and it was a pretty simple fix.
So I figured I would share.

This is to remove the many many many duplicate entries wine adds to the "open with" menu.

All I did was... 

1. Go to /home/.local/share/applications (".local" is a hidden directory. Control-H to reveal)
2. Select all the files with a .desktop extension
3. Right-Click/Properties/Permissions
4. Check "Allow executing as a program

Now when you look in the folder, you'll notice that things make a lot more sense.

Don't just delete things though.  Do a little experimenting.

You may notice that sometimes when you open a file with an app, the app will open, but not the file.

What I ended up doing was opening all the links 1 at a time.
When I got to one that opened the app, but then gave an error about not being able to fine the file, those were the ones I kept.  (This is actually a good thing)

It gives the error, because its assuming that your trying to open a file in the app, and not just opening the app.

Then I deleted everyone except I kept 1 copy for each app I had that gave the error.

And vuala, now I only see 1 listing for each app, and they all work.

Let me know if this works out for you.

If you want more details, let me know, Id be happy to help.

---

