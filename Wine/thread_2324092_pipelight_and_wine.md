---
title: "pipelight and wine"
date: 2016-05-10
forum: Wine
---

### Post by Jorhel on 2016-05-10
Hi,
This is more curiosity than a problem.
I have installed pipelight
> sudo add-apt-repository ppa: pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update


sudo pipelight-plugin --create-mozilla-plugins
in order to be able to run flash videos in firefox.
I had temporary installed wine via the software centre then uninstalled it the same way.

Now when I get updates sometimes there is some libelled wine.
So my question is:WHY?
are those update specifics to pipelight or is there still some part of wine installed somewhere that didn't get cleaned up?
Should I accept these updates or untick them?
If I understund well pipelight is a wine ppa application?

Thanks for your input.
I'm running xubuntu Trusty Tahr on a pretty old desktop compaq presario.

---

### Post by SeijiSensei on 2016-05-10
Pipelight installs its own version of wine.  In my case it's in ~/.wine-pipelight.  Just let it update when it wants to.

---

