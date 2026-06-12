---
title: "Could not download all repository indexes"
date: 2009-01-27
forum: x86 64-bit Users
---

### Post by vax on 2009-01-27
UBUNTU 8.04-2, AMD64 :Last week I started  getting warning message of the auto update system not being able to do its job
trying to reload manually the synoptic manager I am getting this message: 

"Failed to fetch [http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages.gz](http://repoubuntusoftware.info/dists/harty/all/binary-amd64/Packages.gz)  302 Moved Temporarily, Some index files failed to download, they have been ignored, or old ones used instead.

any idea what can be done?

---

### Post by drs305 on 2009-01-27
It doesn't appear the site is working any longer. To disable it, open Software Sources or Synaptic. Settings > Repositories. If it is listed in the *Third-Party Software* tab you can either untick it (if you want to check it later to see if the site was restored) or remove it completely.

You can also manually edit your sources.list and remove or comment out the entry:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list   # or use your preferred text editor instead of gedit

```

Remove the line or place a comment symbol # at the beginning of the line with the problem entry. Save the file and then hit *Reload* in Synaptic/Software Sources or run:
```

sudo apt-get update

```

---

### Post by vax on 2009-01-27
Solved and thanks
how can i know which packages that site was updating?

---

### Post by drs305 on 2009-01-27
> **vax said:**
> Solved and thanks
how can i know which packages that site was updating?

Since the repository has been disabled it will probably *not* appear in  listings in /var/lib/apt folder. If you want to check anyway: Normally each enabled repository's information is stored in this folder - there may be several entries for each repository (for instance, one for the security key, one for the package list, etc). You can open up the file for the specific repository - the filename probably ends with "*Packages*. If you can find a listing for the one you are interested in, you can see which packages it maintains.

You might find entries for the repository in /var/lib/dpkg/status 
You could do a search for "repobuntu" to see if any package is maintained by this source.

```

gedit /var/lib/dpkg/status  

```

---

