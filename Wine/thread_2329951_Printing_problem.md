---
title: "Printing problem"
date: 2016-07-06
forum: Wine
---

### Post by m0f0m on 2016-07-06
Hi,

My setup is like this:

Lubuntu 16 LTS server with LTSP. 
Thin client which boots from that server, parallel printer is connected to that client.
Cups is installed. Printer is added on the server (with proper port redirection).

Whenever user starts his thin client terminal and logs in, he can start LibreOffice write something and print it on the printer mentioned above with no problem.

Quote from WineHQ page:
> 
**4.3.4. Printers**

          Wine can interact directly with the local CUPS printing system to           find the printers available on your system.  Configuring           printers with Wine is as simple as making sure your CUPS           configuration works


So it looks like nothing more to do here.

I have Win32 console app written in Clipper/Harbour (I think).
When user tries to print from this app nothing happens.

How can i trace/debug this.

TIA
m0f0m

---

