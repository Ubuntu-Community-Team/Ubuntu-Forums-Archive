---
title: "WinSock Issue"
date: 2008-05-24
forum: Wine
---

### Post by gibby213 on 2008-05-24
This post is in regards to the game located at [http://www.ezaccess.net/ognet/](http://www.ezaccess.net/ognet/)

I've been working with the guy who created that game to figure out a problem in connecting to his server, and I know (for sure this time!) HOW exactly it doesn't work.  The problem is I have no idea why this happens so I have no idea how to fix it.

Here is the debugging output (that matters):

```
       trace:winsock:WSAStartup verReq=101
       trace:winsock:WSAStartup succeeded
       trace:winsock:WS_socket af=2 type=1 protocol=0
       trace:winsock:WSASocketA af=2 type=1 protocol=0 protocol_info=(nil) group=0 flags=0x1
       trace:winsock:WSASocketW af=2 type=1 protocol=0 protocol_info=(nil) group=0 flags=0x1
       trace:winsock:WSASocketW     crea[CODE]
```ted 0068
       trace:winsock:WS_select read 0x43ee80, write (nil), excp (nil) timeout 0x43eb10
       trace:winsock:WSARecvFrom socket 0068, wsabuf 0x7e69da0c, nbufs 1, flags 0, from (nil), fromlen -1, ovl (nil), func (nil)
       trace:winsock:WSARecvFrom fd=26, options=0
       warn:winsock:wsaErrno errno 107, (Transport endpoint is not connected).
       warn:winsock:WSARecvFrom  -> ERROR 10057
       trace:winsock:WS_closesocket socket 0068
       trace:winsock:WS_connect socket 0000, ptr 0x43d7a0 { family 2, address x.x.x.x port x }, length 16[/CODE]

The interesting things to note is that there is only one socket created (confirmed by developer) and wine shows clearly that it is created as socket 0068.  But when the connect() function is called (which is where it fails, also confirmed by developer) the first argument is socket 0000.  Now, i know it's not a problem with the code itself because it works just fine in windoze (confirmed by me and plenty of people).  And to make sure that's believable, I even have those two lines of the source:

```
CSocket = socket(PF_INET, SOCK_STREAM, 0);
...
RC = connect(CSocket, (struct sockaddr *)&SA1, sizeof(SA1));
```

Any idea why wine is using a different socket number to connect than the one that was created and stored?

(If you download the game to test this yourself, use the OGN16.EXE program, as that one uses winsock 1.1 instead of 2.0)

---

### Post by gibby213 on 2008-05-25
Nevermind, developer fixed what was breaking it.

---

