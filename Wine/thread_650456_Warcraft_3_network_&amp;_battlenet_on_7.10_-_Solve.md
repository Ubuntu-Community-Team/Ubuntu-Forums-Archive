---
title: "Warcraft 3 network &amp; battlenet on 7.10 - Solved"
date: 2007-12-26
forum: Wine
---

### Post by snadrus on 2007-12-26
1. I used the link:
[http://appdb.winehq.org/appview.php?iAppId=897](http://appdb.winehq.org/appview.php?iAppId=897)
then clicked "Frozen Throne" and followed those instructions. They basically say to 
   a. Install Wine (Synaptic)
   b. Install Warcraft 3
   c. Rename the movies folder. Use ctrl-H in the home folder to find .wine
   d. run regedit   (using applications -- accessories -- terminal 
           add a dword to 
       HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III 
       called Gfx OpenGL   and set to 1

2. Then I installed Frozen Throne (the expansion pack). The regular gameplay was great, but network games froze when you tried to join them. 

3.  I learned to use terminal to run it, so that I could see debugging which I used to look up a problem specific to my system. 
   applications -- accessories -- terminal
   cd  ~/.wine/drive_c/Program\ Files/Warcraft\ III/
   wine Frozen\ Throne.exe 

4. I updated to the latest Wine which still has the problem:
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

5. I found that I'm seeing Wine bug 9787. So I downloaded and extracted the Wine source:
[http://winehq.org/?announce=latest](http://winehq.org/?announce=latest)      
(top link)

6. A few rounds of    ./configure    in the terminal (in that folder) told me I needed Synaptic for:   
   build-essential    
   bison   
   flex      
   opengl  dev      (I'm not sure which one, so I got many and that worked)

7. **Here's the important part.** A patch exists for this (it's in the bug report), I'm not good at applying diffs, so I read it and tried to do the same thing. 

  a. I went to DLLs (folder)  then kernel32  then sync.c
  b. Find:   CreateIoCompletionPort
  c. below there, comment out the first "if" and after the close-bracket add an #if 0   so it looks like this:

   /*if (hExistingCompletionPort && hFileHandle == INVALID_HANDLE_VALUE)*/
    {
        SetLastError( ERROR_INVALID_PARAMETER);
        return NULL;
    }
#if 0

   d.  Scroll down 1 pg to the line that only as } on it at the very left. 
        Just before it, put an   #endif  so that you see:

fail:
    if (ret && !hExistingCompletionPort)
        CloseHandle( ret );
    SetLastError( RtlNtStatusToDosError(status) );
    return 0;
**#endif**

}


8. Save & close. Do another  ./configure    and then   make depend && make
    Wait an hour

9. sudo make install        After this, everything work like expected. 
10. Since this was a network game, I had to do this on 2 PCs. The other one ran the same Ubuntu 7.10 i386, so I copied the wine source folder over to the other machine and did the same ( sudo make install ) to fix that one. 

Future note, if you have updates coming from WineHQ, it may overwrite this in the future (when another version is released). In that case, if the bug still is not fixed, you may need to repeat 4 - 9 again.

---

