---
title: "mldonkey segmentation fault at startup"
date: 2004-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuser on 2004-12-01
Hi,

I installed mlnet and mlgui from synaptic.
Ever I start mlnet or mlgui, I have a segmentation fault after initializing and enabling  p2p protocols.
I have 512Mb ram.

Here is the trace:
TigerTree: Exception File "src/utils/lib/md4.ml", line 0, characters 502-10: Assertion failedUnable to compute correct Tiger trees.
Send a bug report with your configuration
and how you obtained this executable.
Running with Tiger tree corruption detection disabled.
(used only if you run the Gnutella plugin)
Resolving [ubuntu] ...done
Network Global Shares registered
Network Gnutella registered
Network G2 registered
Network FileTP registered
Network BitTorrent registered
Network Donkey registered
Updating options to level 1
Updating options to level 2
LOADING SHARED FILES AND SOURCES
Network.load_complex_options not implemented by BitTorrent
Network.load_complex_options not implemented by FileTP
Network Donkey enabled
Network BitTorrent enabled
Network FileTP enabled
Network G2 disabled
Network Gnutella disabled
Erreur de segmentation  (that is in english Segmentation fault as you surely guessed :))


uname -a :
Linux ubuntu 2.6.8.1-3-amd64-k8 #1 Thu Nov 18 12:12:57 UTC 2004 x86_64 GNU/Linux

Thanks for you attention.

---

