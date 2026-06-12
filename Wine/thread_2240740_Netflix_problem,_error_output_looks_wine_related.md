---
title: "Netflix problem, error output looks wine related"
date: 2014-08-21
forum: Wine
---

### Post by Jesse_Pahman on 2014-08-21
I recently performed clean installs of Ubuntu 14.04(.1?) LTS on my desktop and laptop computers. I installed Netflix-desktop on both using the same method:

```

sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install pipelight-multi

sudo pipeline-plugin --enable silverlight

sudo apt-get install netflix-desktop

```

On my desktop (AMD Athlon 64 X2, 4 Gb RAM, ATI HD5770 graphics card), it works perfectly, on my laptop (Lenovo R61, Intel Core2Duo, 4Gb RAM, Nvidia graphics) it doesn't work so well. The only way I can get the Netflix-desktop to run is by executing:
```

sudo -H netflix-desktop

```

When I run:
```

netflix-desktop --showdebug

```

I get the following:
[IMG]https://lh6.googleusercontent.com/a-WVBdPWHk_ARZNHjJvV5rUB6ZMI4Rg2J58_Qz1TIFCVjMDzOn1Rm5GG9fMIghSe_c3gBapoSio=w1256-h571[/IMG]

[IMG]https://lh5.googleusercontent.com/xhgsUqfxYnAC-WjLPFdqSkUPZpc-5mBCIeEeXM-WXey8PaKtPznbuZyuOGQlvsLU_wspGKAA58o=w1256-h571[/IMG]

I have researched as much as I know how to; everything from those that say never to run Wine as root, to trying a User Agent Switcher. I cannot make this work without the -H switch on sudo. Help? I'd love to be able to just click on the icon in unity and watch Netflix instead of launching though the terminal, it makes me think something is wrong.

---

