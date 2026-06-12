---
title: "Rhythmbox continues play after last item in play queue"
date: 2009-08-05
forum: x86 64-bit Users
---

### Post by timgood on 2009-08-05
This is an annoyance - after Rhythmbox has finished playing items in the play queue it will continue with the first item found in the music library. I would like it to stop after the play queue is finished, but can't seem to find a way to do it. Any ideas? Or is this a bug?

---

### Post by ajgreeny on 2009-08-05
You must have clicked on the Repeat button on the toolbar.  Click again to deselect it and you should not get the repeated play.

---

### Post by timgood on 2009-08-05
It does not repeat. It gets to the end of the play queue and then starts playing the first song in the library - and will continue to go through the whole of the library until it is stopped. Repeat is not selected.

---

### Post by ajgreeny on 2009-08-05
Sorry, I misunderstood your problem.  Very odd and I can't offer any help, I'm afraid, other than deleting/renaming the rhythmbox config files in your /home/username/.gconf/apps folder

---

### Post by timgood on 2009-08-06
Deleting the config files does not help and apparently I am not the only one with this problem. The developer claims it as a feature rather than a bug!

---

### Post by ajgreeny on 2009-08-06
I have just tried this and it has not helped solve the problem.  I have several Playlists saved both in rhythmbox and as .pls files in a playlists folder in /home.  After selecting and playing one of those playlists my rhythmbox stops, and plays nothing more until I set it to do so.  Similarly when I right click a track and choose "Add to play queue" and play it or them, the player stops when they have all finished.  Your system seems to act differently for some reason, so I am still a bit baffled.

---

### Post by timgood on 2009-08-08
You are using playlists, not the play queue. Try adding several songs to the play queue and see what happens after the last one has finished. Playlists are a different kettle of bridges in the hands of birds and like banging your head against the corner of a vicious circle.

---

### Post by ajgreeny on 2009-08-08
If you read my last post again you will see > Similarly when I right click a track and choose "Add to play queue" and play it or them, the player stops when they have all finished. Your system seems to act differently for some reason, so I am still a bit baffled.I have tried out your problem with the "Add to play queue" and when it gets to the end of the queue rhythmbox stops, quiet, no sound, nothing, just as you want.  Perhaps I am still misunderstanding your situation.

---

### Post by timgood on 2009-08-09
Aha! After further experimentation I am now able to duplicate the behaviour on your machine. 'Browse' must be deselected and then RBox restarted. After restart, items added to play queue play and then glorious silence once they have finished. I don't know why this is the case, but at least I have back the behaviour expected.

---

