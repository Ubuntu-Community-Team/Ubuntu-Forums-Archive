---
title: "Wine can not find a release file or index files"
date: 2017-06-10
forum: Wine
---

### Post by omnivorous-octopus on 2017-06-10
I am using Ubuntu 17.04 and I am trying to install Wine.  I am fairly comfortable with using Ubuntu, but don't know much at all about package management.  When running > sudo apt-get update I get the following:

> 
W: The repository 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/zesty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/zesty/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Dennis N on 2017-06-10
There are no zesty packages in that PPA. You can see that here:

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/)

Perhaps you could install the version in the regular Ubuntu repos?

---

### Post by howefield on 2017-06-11
+1 to using the repository builds or otherwise use the builds detailed at the [winehq]("https://wiki.winehq.org/Ubuntu") website.

The ppa above has been deprecated.

---

