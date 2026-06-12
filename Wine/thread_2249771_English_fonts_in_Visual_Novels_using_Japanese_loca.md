---
title: "English fonts in Visual Novels using Japanese locale look broken/skewed"
date: 2014-10-24
forum: Wine
---

### Post by mackycastillo on 2014-10-24
I need help with running visual novels through wine on Ubuntu. With every non-localized* visual novel I've tried, English characters never seem to be properly aligned. Like the image below, English characters on a per-character basis are randomly (at least looks random) moved too far either left or right of where they are supposed to be. Characters that would supposedly overlap from this get "cut" off.

[IMG]https://dl.dropboxusercontent.com/u/52756437/Screenshot%20from%202014-10-25%2001%3A08%3A46.png[/IMG]

Japanese locales and fonts are installed and the necessary env variables changed. For the latter, I use ```
LANG="ja_JP.utf8" LC_ALL="ja_JP"
```. My guess is that using a different font would fix it, but I don't know how to set a different set of Japanese system fonts for Wine.
[SIZE=1]
* - Uses Japanese locale. No official English version. Fans often make translation patches but will still have to use JAP locale.[/SIZE]

EDIT: Got it fixed by copying Windows' fonts into Wine's drive_c/windows/Fonts folder. Problem now is that the font eventually spreads out.

Although the font initially looks fine like so:

[IMG]https://dl.dropboxusercontent.com/u/52756437/Screenshot%20from%202014-10-25%2016%3A46%3A09.png[/IMG]

The effect is gradual and noticable, but after a certain number of pages of text:

[IMG]https://dl.dropboxusercontent.com/u/52756437/Screenshot%20from%202014-10-25%2016%3A46%3A27.png[/IMG]

The text gets spread out so wide that it gets really difficult to distinguish words from one another. Is there a way to address this?

---

### Post by bapoumba on 2014-10-24
*Thread moved to **Wine**.*

---

