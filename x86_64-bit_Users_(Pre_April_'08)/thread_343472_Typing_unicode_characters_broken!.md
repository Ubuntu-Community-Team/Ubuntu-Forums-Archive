---
title: "Typing unicode characters broken!"
date: 2007-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-01-21
Just updated Dapper amd-64 to Edgy amd-64. I use OOo a lot and I was delighted to see that the upgrade also upgraded OOo 2.02 (Dapper) to 2.04. However, I just discovered that Ctrl+Shift+hex code no longer inserts a character. For example, Ctrl+Shift+1DD used to insert a schwa. Now nothing happens.

At first I assumed this was a problem with OOo, but checking my other applications it no longer works in any application. In other words, something has changed system-wide. The Character Map utility still works, as does OOo's Insert Special Character, but that's a pain.

What happened and how do I type special characters?

---

### Post by mesilliac on 2008-04-10
I realise this is a very old thread. It's also the first one I found when googling for how to easily insert unicode characters in ubuntu.

So here's the answer:

to quickly insert a unicode character press "CTRL-SHIFT-U" then type the code.
e.g. CTRL-SHIFT-U + b0 == ° (the degree symbol)

To set up a key on your keyboard to be used to easily type accented characters (like é), go to System>Prefs>Keyboard --> select "Layouts" tab and click "Layout Options". Set the "Compose Key" to something (e.g. right alt). Then you can for example press R.ALT-' then E to get é.

Also, If you haven't found it already, you probably want to check out Accessories>Character Map.

---

### Post by John Jason Jordan on 2008-04-10
> **mesilliac said:**
> I realise this is a very old thread....
Yes, the thread is very old. I am way far ahead of the problem. In fact, along with several other linguistics majors, I have created an extensive wiki for how to enter special characters (like IPA) on all platforms and all office applications and browsers. You may find the comments on the Windows and Microsoft Office pages amusing:

[http://ipa4linguists.pbwiki.com](http://ipa4linguists.pbwiki.com)

 But I'll shut up now because it's pretty off-topic for an Ubuntu forum.

---

### Post by Hendrik0 on 2008-06-08
Is it possible that ctrl+shift+u doesn’t work on Hardy any more? It doesn’t do anything on my system at least.

---

### Post by mesilliac on 2008-06-08
it still works for me in hardy...

You might have to go to System > Administration > Language Support and click the "Enable support to enter complex characters" checkbox?

---

### Post by Hendrik0 on 2008-06-19
I think it’s a keyboard problem. Ctrl+Alt+F[1..6] doesn’t work either, but Shift+F[1..6] drops to the console instead. I am using a .Xmodmap file. Does anyone know the keysym for unicode composition so I can use another combination for that?

---

### Post by kiflea1 on 2008-06-21
Ctrl + shift + alt + altGr + u + some number to enter one Unicode character?

I believe there is an easier way.

I don't know if Ubuntu allows copying and pasting Unicode text but this site has a simple tool to enter All Unicode Characters.

[www.2keystrokes.com](www.2keystrokes.com)

Check it out!

Take Care

---

### Post by simosx on 2008-07-14
To type characters by hex code, you use

1. Ctrl+Shift+u, 
2. then type the hex code, 
3. then press Space.

In previous versions, Step 1 was just Ctrl+Shift (without the u).

If you have changed the "input method" from the default to something like XIM or SCIM, then you probably do not have the Ctrl+Shift+u functionality, or you may have some other similar functionality (quite possible in SCIM).

However, the important issue is that you can type characters such as °
in Ubuntu 8.10.
For the full list of characters, see
[http://cgit.freedesktop.org/xorg/lib/libX11/tree/nls/en_US.UTF-8/Compose.pre](http://cgit.freedesktop.org/xorg/lib/libX11/tree/nls/en_US.UTF-8/Compose.pre)

---

