---
title: "WINE programs/processes isolation"
date: 2014-11-15
forum: Wine
---

### Post by Javapraca on 2014-11-15
I would like to completely isolate from each other two Windows programs  running in WINE. I intend to block them from sharing memory,  interprocess communication, files and using any possible communication  mechanism.

I have already checked (using ProcessExplorer) that  programs run in different environments (defined using WINEPREFIX) do not  see their processes and cannot read their memory. But how about other  interprocess communication - can processes communicate/see each other  using different mechanisms? If yes, then how to block them? Using  different WINEPREFIX'es would be enough in this case? 

My other  idea is to use LXC (LinuX Containers) to enhance safety and processes  separation. Is it worth (or even possible) to run WINE in LXC to assure  complete programs separation?


Thanks in advance.

---

