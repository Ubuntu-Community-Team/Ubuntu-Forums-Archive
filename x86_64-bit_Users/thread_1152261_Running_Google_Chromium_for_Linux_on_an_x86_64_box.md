---
title: "Running Google Chromium for Linux on an x86_64 box"
date: 2009-05-07
forum: x86 64-bit Users
---

### Post by mhenriday on 2009-05-07
Despite the explicit warning on the **Launchpad** PPA page ([https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)) to the effect that «no native 64bit debs planed for now. The amd64 package is using ia32-libs.» and the bright red cross after the «**chromium-browser - 2.0.179.0~svn20090507r15556-0ubuntu1~ucd1~intrepid**» package, I was foolish enough to go ahead and download and installed the latter on my **Jaunty** box, seemingly successfully - I see it both in Synaptic and under «Applications/Internet». But when I attempt to run it, I get the following error message in a terminal :
> mhenriday@mhenriday-skrivbord:~$ chromium-browser
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: fel ELF-klass: ELFCLASS64
[12619:12619:12197818987:ERROR:/build/buildd/chromium-browser-2.0.179.0~svn20090507r15556/build-tree/src/chrome/common/temp_scaffolding_stubs.cc(140)] Not implemented reached in static bool FirstRun::IsChromeFirstRun()
[12619:12619:12197978141:ERROR:/build/buildd/chromium-browser-2.0.179.0~svn20090507r15556/build-tree/src/chrome/browser/metrics/metrics_service.cc(707)] Not implemented reached in static std::string MetricsService::GenerateClientID()
[12619:12619:12204882894:ERROR:/build/buildd/chromium-browser-2.0.179.0~svn20090507r15556/build-tree/src/chrome/browser/tab_contents/tab_contents_view_gtk.cc(80)] Not implemented reached in virtual void TabContentsViewGtk::CreateView()
[12619:12619:12204921330:ERROR:/build/buildd/chromium-browser-2.0.179.0~svn20090507r15556/build-tree/src/chrome/browser/renderer_host/render_widget_host_view_gtk.cc(205)] Not implemented reached in virtual void RenderWidgetHostViewGtk:: DidBecomeSelected()
[12619:12619:12204921540:ERROR:/build/buildd/chromium-browser-2.0.179.0~svn20090507r15556/build-tree/src/chrome/browser/tab_contents/tab_contents_view_gtk.cc(195)] Not implemented reached in virtual void TabContentsViewGtk::RestoreFocus() Need to restore the focus position on this page.
[12619:12619:12205172304:FATAL:/build/buildd/chromium-browser-2.0.179.0~svn20090507r15556/build-tree/src/chrome/app/chrome_dll_main.cc(177)] Gtk: /usr/lib32/gtk-2.0/2.10.0/immodules/im-scim.so: kan inte öppna delad objektfil: Filen eller katalogen finns inte [target file cannot be opened : the file or catalogue doesn't exist]
Spårningsfälla [Trace trap]
Should I uninstall the AMD64 package and install one of the others - e g, «**chromium-browser - 2.0.179.0~svn20090507r15556-0ubuntu1~ucd1**» - found on the **Launchpad** page, or is there some
workaround which will enable to present installation to run ?...

Henri

---

### Post by mhenriday on 2009-06-06
It seems that my *cri de cœur* above has been viewed som 248 times, but garnered no responses. In any event, with the passage of time, the problem has resolved itself in that **Google** has now released a dev channel version (currently **3.0.183.1**) of **Google Chrome** for both **Linux** and **Mac**, which can be downloaded [**_[COLOR="Blue"]here[/COLOR]_**]("http://dev.chromium.org/getting-involved/dev-channel") (scroll down to the bottom of the page). Lots of bugs remain to be crunched, but now we're on our way !...

Henri

---

### Post by philinux on 2009-06-06
Hi,

Did you install 

ia32-libs-chromium-browser

---

### Post by mhenriday on 2009-06-06
Tried installing it, but removed it when I found it to be of no help. In any event, with the release of the dev version of **Chrome** for **Linux**, which installs as easy as pie on 64-bit **Ubuntu**, the original problem is now *post festum*....

Henri

---

### Post by cybrsaylr on 2009-06-06
That said, how do you rate the browser?

Is it any better than FF or Opera? 
Opera 10b seems to be the fastest browser out right now.

---

### Post by mhenriday on 2009-06-06
**Cybrsaylr**, my impression - I haven't attempted to measure this objectively - is that on **Windows** boxes, the latest versions of **Google Chrome** are faster than **Opera 10b**, and at least as reliable. On Linux boxes, however, the **Chrome** build is far from ready for production, as is strongly emphasised on the download page. Myself, I tend to use **Firefox**/**Swiftweasel** (an **FF** build specially configured for **Linux**) **3.5b4**  most, even if it is not as fast as **Opera**, due to the plethora of useful/indispensable extensions available for the former....

Henri

---

### Post by dinudinu on 2009-06-15
Okay, you can forget chromium for now .. try google chrome's official release, ( dev version ) released last week .....  it has both 64bit and 32 bit

---

### Post by mhenriday on 2009-06-15
I probably wasn't sufficiently explicit in my last posting above, **din**, but I have, indeed, tried **Chrome** for **Linux** (v **3.0.187.0**). So far I have found it very fast and very stable, but lacking in features, which is why I continue to use **Firefox**/**Swiftweasel** (now in the latest version, **3.5b99**) as my main browser on **Jaunty**. Thanks, by the way, for the link to the [_[COLOR="Blue"]Google Chrome Support Forum[/COLOR]_]("http://chromestory.com/forum/") ; I'm sure it will prove useful for straightening out problems that arise when using the browser. One query I have already is whether the **Linux** version will be automatically updated as, for example, **Windows** versions are in the dev channel - perhaps I should post to the Support Forum ?...

Henri

---

### Post by whistlerspa on 2009-06-15
Chrome for linux doesn't seem to support Flash as yet and has few customisation options. Seems like a toy browser for now to me.

---

### Post by mhenriday on 2009-06-15
Whistlerspa, «toy browser» seems a bit ungenerous, given that the relevant posting on the [_[COLOR="Blue"]Chromium Blog[/COLOR]_]("http://blog.chromium.org/") specifically states :
> In order to get more feedback from developers, we have early developer channel versions of Google Chrome for Mac OS X and Linux, but whatever you do, please DON'T DOWNLOAD THEM! Unless of course you are a developer or take great pleasure in incomplete, unpredictable, and potentially crashing software.

How incomplete? So incomplete that, among other things , you won't yet be able to view YouTube videos, change your privacy settings, set your default search provider, or even print.

In my book, that's a pretty explicit «*Caveat emptor*», not least as the price for trying the browser is null....

Henri

PS : See also Mike Pinkerton's commentary, «The Plausible Promise», dated 9 June on the blog....

---

### Post by whistlerspa on 2009-06-16
Fair point - but on a different tack, it does irk me that Google seem to  always leave it so late to support Linux. 

I realise that we're a minority market but Windows and MAc have had Chrome for a long while now.

---

### Post by mhenriday on 2009-06-16
I have to admit, **whistlerspa**, that I also thought it took a long time to get the **Chrome** to **Linux**, but when I attempt to regard the matter more objectively, I can't but agree that **Google** had its priorities right - it was important to get **Chrome** out (and functioning) to **Windows** users first. As regards **Chrome** for **Macs**, my understanding is that **Chrome** was released for **OS X** at precisely the same time that it was for **Linux** distros. If I'm not mistaken, **Power PC** users are complaining that a version compatible with their OS has not yet been released. In any event, I'm hoping that the updates will soon give us access to the features presently missing from the **Linux** version....

Henri

---

### Post by tomdkat on 2009-06-18
> **mhenriday said:**
> In any event, with the passage of time, the problem has resolved itself in that **Google** has now released a dev channel version (currently **3.0.183.1**) of **Google Chrome** for both **Linux** and **Mac**, which can be downloaded [**_[COLOR="Blue"]here[/COLOR]_**]("http://dev.chromium.org/getting-involved/dev-channel") (scroll down to the bottom of the page). Lots of bugs remain to be crunched, but now we're on our way !...
You rock!  Thanks for the link!  It's running splendidly on my system now!  :)

Peace...

---

### Post by mhenriday on 2009-06-19
Glad to have been of help, **tomdcat** !...

Henri

---

