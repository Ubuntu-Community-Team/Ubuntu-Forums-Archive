---
title: "totem unable to play movies in firefox"
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-29
I am unable to play the video here.

[http://people.ubuntu.com/~asac/pfs/test/2_multicontent.html](http://people.ubuntu.com/~asac/pfs/test/2_multicontent.html)

I do have the mozilla-totem package, and I am using totem with xine, not gstreamer. I ran Firefox from gnome-terminal to see what errors I would get. What does this mean? How can this be fixed?

```
** Message: URLNotify URL 'http://people.ubuntu.com/~asac/pfs/test/test-NONEXISTENT.mpeg' reason 1
** Message: totem_embedded_set_error_logo called by browser plugin
** Message: Viewer state: STOPPED
** Message: totem_embedded_set_error: 'An error occurred', 'The movie could not be read.'
** Message: StopStream signal received
** Message: totem_embedded_set_error: 'An error occurred', 'There is no plugin to handle this movie.'
** Message: StopStream signal received

** (totem-plugin-viewer:32710): WARNING **: Error in bacon_video_widget_play: There is no plugin to handle this movie.

** (totem-plugin-viewer:32710): WARNING **: Error in bacon_video_widget_play: There is no plugin to handle this movie.

```

---

### Post by daengbo on 2007-10-29
Opening the URL in the first line (also visible in the HTML source), I get a 404 error. The name of the file is test-NONEXISTENT.mpeg, so that could mean that it was never intended to exist at all.

Anyway, there's no video to play.

BTW, why do you need Totem-Xine these days? GStreamer is a great and mature library now. If you have the w32codecs package installed, standard Totem will play just about everything.

---

### Post by go_beep_yourself on 2007-10-29
> **daengbo said:**
> Opening the URL in the first line (also visible in the HTML source), I get a 404 error. The name of the file is test-NONEXISTENT.mpeg, so that could mean that it was never intended to exist at all.

Anyway, there's no video to play.

BTW, why do you need Totem-Xine these days? GStreamer is a great and mature library now. If you have the w32codecs package installed, standard Totem will play just about everything.

The video is there. You must not be able to play it because you are using Totem with gstreamer and not xine. Check the html code.

```
<html>
<body>

<embed TYPE="video/mpeg"
       SRC="test-NONEXISTENT.mpeg"
       NAME="MediaPlayer"
       WIDTH="240"
       HEIGHT="197"
       autostart="1"
       showcontrols="1" />

<embed TYPE="application/x-shockwave-flash"
       SRC="test-NONEXISTENT.swf"
       NAME="FlashPlayer"
       WIDTH="240"
       HEIGHT="197"
       autostart="1"
       showcontrols="1" />

</body>
</html>
```

---

### Post by daengbo on 2007-10-30
No. I manually entered the mpeg's address and got a 404.

danielbo2@danielbo-laptop:~$ wget [http://people.ubuntu.com/~asac/pfs/test/test-NONEXISTENT.mpeg](http://people.ubuntu.com/~asac/pfs/test/test-NONEXISTENT.mpeg)
--13:06:02--  [http://people.ubuntu.com/~asac/pfs/test/test-NONEXISTENT.mpeg](http://people.ubuntu.com/~asac/pfs/test/test-NONEXISTENT.mpeg)
           => `test-NONEXISTENT.mpeg'
Resolving people.ubuntu.com... 91.189.90.132
Connecting to people.ubuntu.com|91.189.90.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:06:03 ERROR 404: Not Found.

Can't get simpler than wget. The file isn't there or isn't accessible.

---

