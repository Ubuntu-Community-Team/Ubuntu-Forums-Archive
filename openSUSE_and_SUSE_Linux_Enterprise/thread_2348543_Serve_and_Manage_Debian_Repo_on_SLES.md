---
title: "Serve and Manage Debian Repo on SLES"
date: 2017-01-04
forum: openSUSE and SUSE Linux Enterprise
---

### Post by King of Heart 4711 on 2017-01-04
So as the title says I'm looking to see what my options are hosting and managing a Debian Repo on SLES. The environment I work in has SLES (maybe RedHat soon) server infrastructure with no Debian/Ubuntu Servers. The workstation clients (which I manage) all run Ubuntu. 

Currently to have controlled updates I've managed to reverse engineer reprepro (in bash no less) to set up a rudimentary "trivial" Debian repo. This has worked OK but does not support secure apt so enabling --force-yes or --allow-unauthenticated is a must for this to work. However these types of repositories are deprecated and I don't know how long support will last in apt. So I need to move to something a bit more proper (and faster) than my bash script.

So far I can't seem to find any options for managing Debian repos on distros other than Debian/Ubuntu and their derivatives - and I don't have the bandwidth to write a fully featured management solution in bash (to slow) or otherwise. Is there any tools out there for the job or am I going to be forced to convince the powers-that-be to let me spin up a Debian/Ubuntu VM for the job?

---

