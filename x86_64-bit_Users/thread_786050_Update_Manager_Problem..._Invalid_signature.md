---
title: "Update Manager Problem... Invalid signature?"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by Grone1985 on 2008-05-07
I got this error today when checking for updates:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Can I get some help here please?

Thanks!

---

### Post by millie95 on 2008-05-07
I am also getting the error

---

### Post by Grone1985 on 2008-05-07
I just noticed that if I try to check updates it will hang for a long time on the 11th file out of 52, and then, after a while the error message comes up... BTW all of this is on Hardy clean install.

Help please! Thanks!

---

### Post by Grone1985 on 2008-05-08
Now I'm getting this errors when checking for new updates:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

Please help!!

---

### Post by gdi2k on 2008-05-09
Same here.

---

### Post by godber on 2008-05-09
> **Grone1985 said:**
> I got this error today when checking for updates:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Can I get some help here please?

Thanks!

I have this same issue.  Does anyone know of a place that officially repots mirror status, health or anything like that?  Clearly the us.archive.ubuntu.org mirrors have all been suffering under the hardy release load, but something like this is not load related but a data problem.
:confused:

Austin

---

### Post by SomethinSnappy on 2008-05-09
bump

same issue here.

---

### Post by bridgidpnh on 2008-05-10
this is the message I got and now synaptic package manager won't work!
'E:Type '—21:25:04--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

---

### Post by jbr6700 on 2008-05-10
Check your software sources. They should look something like this: *[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)* Try this:**System-Administration-Software Sources**

---

### Post by Aearenda on 2008-05-13
I have just had to work around a similar issue. It seems that some ISPs transparently cache the files, so that we receive out of date or mismatched control data for the updates. Waiting for the cache to expire is one way to fix it, and Bug 24061 ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)) contains a workaround:
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and if that does not work:
```
sudo apt-get update -o Acquire::BrokenProxy=true
```

For me, the first one works. You can make this permanent by creating /etc/apt/apt.conf with the following contents (or adding the relevant bit if your apt.conf was already created):
```

APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}

```

---

### Post by gdi2k on 2008-05-15
Neither worked for me: 

```
gdi2k@ubuntu:~$ sudo apt-get update -o Acquire::http::No-Cache=True
[sudo] password for gdi2k: 
Hit http://archive.ubuntu.com hardy Release.gpg                     
Hit http://free.nchc.org.tw feisty Release.gpg                                                  
Get:1 http://security.ubuntu.com hardy-security Release.gpg [191B]                              
Ign http://archive.ubuntu.com hardy/main Translation-en_US                                     
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US     
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com hardy-updates Release.gpg [191B]     
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US   
Get:3 http://security.ubuntu.com hardy-security Release [44.0kB]     
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US 
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US   
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US   
Hit http://archive.ubuntu.com hardy Release                                 
Get:4 http://archive.ubuntu.com hardy-updates Release [51.2kB]                                                               
Ign http://archive.ubuntu.com hardy-updates Release                                                
Hit http://archive.ubuntu.com hardy/main Packages                                                  
Ign http://free.nchc.org.tw feisty/main Translation-en_US                                               
Ign http://free.nchc.org.tw feisty/restricted Translation-en_US                                         
Ign http://free.nchc.org.tw feisty/universe Translation-en_US                                           
Hit http://archive.ubuntu.com hardy/restricted Packages                     
Ign http://free.nchc.org.tw feisty/multiverse Translation-en_US                                         
Get:5 http://free.nchc.org.tw drbl Release.gpg [189B]                                                   
Hit http://archive.ubuntu.com hardy/main Sources                            
Ign http://free.nchc.org.tw drbl/stable Translation-en_US                                               
Hit http://free.nchc.org.tw feisty Release                                                              
Hit http://archive.ubuntu.com hardy/restricted Sources                                                                      
Get:6 http://free.nchc.org.tw drbl Release [106kB]                                                      
Hit http://archive.ubuntu.com hardy/universe Packages                                                   
Get:7 http://security.ubuntu.com hardy-security/main Packages [11.5kB]                                                                                      
Hit http://archive.ubuntu.com hardy/universe Sources                                                                                                        
Get:8 http://security.ubuntu.com hardy-security/restricted Packages [14B]                                                                                   
Hit http://archive.ubuntu.com hardy/multiverse Packages                                                                                                     
Get:9 http://security.ubuntu.com hardy-security/main Sources [4022B]                                                                                        
75% [9 Sources bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)] [Waiting for headers] [6 Release 53277/106kB 50%]                      20.0kB/s 2s
bzip2: (stdin): trailing garbage after EOF ignored
Get:10 http://security.ubuntu.com hardy-security/restricted Sources [14B]                                                                                   
Hit http://archive.ubuntu.com hardy/multiverse Sources                                                                                                      
Get:11 http://security.ubuntu.com hardy-security/universe Packages [8134B]                                                                                  
Get:12 http://archive.ubuntu.com hardy-updates/main Packages [44.9kB]                                                                                       
Hit http://security.ubuntu.com hardy-security/universe Sources                                                                                              
Get:13 http://security.ubuntu.com hardy-security/multiverse Packages [14B]                                                                                  
Get:14 http://security.ubuntu.com hardy-security/multiverse Sources [14B]                                                                                   
Get:15 http://archive.ubuntu.com hardy-updates/restricted Packages [14B]                                                                                    
Hit http://archive.ubuntu.com hardy-updates/main Sources                                                                                                    
Hit http://free.nchc.org.tw feisty/main Packages                                                                                                            
Hit http://free.nchc.org.tw feisty/restricted Packages                                                                                                      
Get:16 http://archive.ubuntu.com hardy-updates/restricted Sources [14B]                                                                                     
Get:17 http://archive.ubuntu.com hardy-updates/universe Packages [22.4kB]                                                                                   
Hit http://free.nchc.org.tw feisty/universe Packages                                                                                                        
Get:18 http://archive.ubuntu.com hardy-updates/universe Sources [4325B]                                                                                     
Get:19 http://archive.ubuntu.com hardy-updates/multiverse Packages [14B]                                                                                    
Get:20 http://archive.ubuntu.com hardy-updates/multiverse Sources [14B]                                                                                     
Hit http://free.nchc.org.tw feisty/multiverse Packages                                                                                                      
Get:21 http://free.nchc.org.tw drbl/stable Packages [9098B]                                                                                                 
Fetched 251kB in 13s (18.3kB/s)                                                                                                                             
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
gdi2k@ubuntu:~$ sudo apt-get update -o Acquire::BrokenProxy=true
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg                                       
Hit http://free.nchc.org.tw feisty Release.gpg                                                                               
Ign http://security.ubuntu.com hardy-security/main Translation-en_US                                                                                     
Ign http://archive.ubuntu.com hardy/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security/main Packages          
Get:1 http://archive.ubuntu.com hardy-updates Release.gpg [191B]     
Hit http://security.ubuntu.com hardy-security/restricted Packages                                 
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US                                
Get:2 http://security.ubuntu.com hardy-security/main Sources [4022B]                              
Hit http://security.ubuntu.com hardy-security/restricted Sources     
99% [2 Sources bzip2 0] [Waiting for headers] [Connecting to security.ubuntu.com (91.189.88.37)] [Waiting for headers]
bzip2: (stdin): trailing garbage after EOF ignored
Hit http://security.ubuntu.com hardy-security/universe Packages                                                       
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US                          
Hit http://security.ubuntu.com hardy-security/universe Sources                                    
Hit http://security.ubuntu.com hardy-security/multiverse Packages                                 
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US                            
Hit http://security.ubuntu.com hardy-security/multiverse Sources                                  
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release    
Get:3 http://archive.ubuntu.com hardy-updates Release [51.2kB]                                  
Ign http://free.nchc.org.tw feisty/main Translation-en_US                  
Ign http://archive.ubuntu.com hardy-updates Release                   
Hit http://archive.ubuntu.com hardy/main Packages                     
Ign http://free.nchc.org.tw feisty/restricted Translation-en_US            
Hit http://archive.ubuntu.com hardy/restricted Packages                    
Ign http://free.nchc.org.tw feisty/universe Translation-en_US              
Ign http://free.nchc.org.tw feisty/multiverse Translation-en_US            
Hit http://free.nchc.org.tw drbl Release.gpg                               
Hit http://archive.ubuntu.com hardy/main Sources                          
Ign http://free.nchc.org.tw drbl/stable Translation-en_US                                             
Hit http://free.nchc.org.tw feisty Release                                                            
Hit http://free.nchc.org.tw drbl Release                                                                                   
Hit http://free.nchc.org.tw feisty/main Packages                                                                            
Hit http://free.nchc.org.tw feisty/restricted Packages                                                
Hit http://free.nchc.org.tw feisty/universe Packages                                                  
Hit http://free.nchc.org.tw feisty/multiverse Packages                                                
Hit http://free.nchc.org.tw drbl/stable Packages                                                      
Hit http://archive.ubuntu.com hardy/restricted Sources                                                
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/universe Sources                                                                                                        
Hit http://archive.ubuntu.com hardy/multiverse Packages                                                                                                     
Hit http://archive.ubuntu.com hardy/multiverse Sources                                                                                                      
Hit http://archive.ubuntu.com hardy-updates/main Packages                                                                                                   
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                                                                                             
Hit http://archive.ubuntu.com hardy-updates/main Sources                                                                                                    
Hit http://archive.ubuntu.com hardy-updates/restricted Sources                                                                                              
Hit http://archive.ubuntu.com hardy-updates/universe Packages                                                                                               
Hit http://archive.ubuntu.com hardy-updates/universe Sources                                                                                                
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                                                                                             
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources                                                                                              
Fetched 193B in 7s (25B/s)                                                                                                                                  
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Having said that, I do live in a country that sensors the Internet so there are a bunch of strange proxies in place, most of which are probably misconfigured.

---

### Post by mambazo on 2008-06-03
THANK YOU SO MUCH. This fixed a LONG standing bug I've been having for over a month.

---

### Post by NeQaSh on 2008-06-07
> **Aearenda said:**
> I have just had to work around a similar issue. It seems that some ISPs transparently cache the files, so that we receive out of date or mismatched control data for the updates. Waiting for the cache to expire is one way to fix it, and Bug 24061 ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)) contains a workaround:
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and if that does not work:
```
sudo apt-get update -o Acquire::BrokenProxy=true
```

For me, the first one works. You can make this permanent by creating /etc/apt/apt.conf with the following contents (or adding the relevant bit if your apt.conf was already created):
```

APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}

```

THNX ALOT dear,Aearenda ur solution 100% solve my same problem

AS u when i use first command 

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

every thing now work when i reload my Synaptic pkg mngr like Crystal on my Hrady Heron .....

thnx again :guitar: :lolflag:

---

### Post by better2berich on 2008-07-11
Hi,
Thanks for your help, but I'm still having the same problem.
I'm coming from 6.06 LTS
I tried both your ideas. I still get the following message (I included the last 'good line' of output for reference point)
:
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Done downloading

Error during update

A problem occurre during the update. This is usually some sort of network problem, please check your network connections and retry.

W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)
Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Restoring original system state

Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done


I also created the /etc/apt/apt.conf file, but when I run apt-get update, I get the following error:

E: Syntax error /etc/apt/apt.conf:5: Extra junk after value

I've looked and the text looks identical.

Any help is appreciated. Another link made some reference to /etc/hosts and /etc/hostname contents needing to be identical, but I don't see how this can be the issue?

Thanks in advance
Ken

---

### Post by Aearenda on 2008-07-11
In my experience, the 'extra junk' message usually means there is a semi-colon missing in the apt.conf file.

There should be an entry in /etc/hosts for the name given in /etc/hostname, but the files have different purposes and should certainly not be identical!

So if your computer is named 'fred' then /etc/hostname should contain just ```
fred
```and your /etc/hosts file should contain at least```
127.0.0.1       localhost
127.0.1.1       fred
```
But I don't think this will be the cause of your problem. It is possible that you caught the servers in the middle of an update - have you tried again? 

If you are still having trouble can you please post the contents of /etc/apt/apt.conf and /etc/apt/sources.list.

---

### Post by waapwoop1 on 2008-07-13
same problem. Fix did not help

---

### Post by waapwoop1 on 2008-07-13
mine works now... hmmm

---

### Post by lightenup on 2008-10-28
Aearenda's post worked for me! Thanks!

---

### Post by george703 on 2009-03-24
> **Aearenda said:**
> I have just had to work around a similar issue. It seems that some ISPs transparently cache the files, so that we receive out of date or mismatched control data for the updates. Waiting for the cache to expire is one way to fix it, and Bug 24061 ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)) contains a workaround:
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and if that does not work:
```
sudo apt-get update -o Acquire::BrokenProxy=true
```

For me, the first one works. You can make this permanent by creating /etc/apt/apt.conf with the following contents (or adding the relevant bit if your apt.conf was already created):
```

APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}

```
Hello Aearenda;
i have 32 bit, with no capability to update. i get hash sum mis match. and failed to fetch errors, in the header of the error window it mentions checking my internet connection, so i am wondering if the above fix will work for me. unfortunetly i know enough to totaly trash my machine, so do you think this will work. if you can help and need more info i will gladly furnish it.
              thanks for any help,george

---

### Post by Aearenda on 2009-03-24
Well, it's hard to be sure since I know nothing about your setup, but I don't think trying the two command-line options will make things any worse.

I've seen this happen because of a bad wireless connection too, but in that case it fixes itself on the next attempt.

There are other suggestions in the bug report I linked to.

---

### Post by george703 on 2009-03-24
Aearenda; 
   you are the best! the fix worked so far. i cant thank you enough.!!!!!!!!!!!!!!!!!!!!
   
   I am new to linux, and i am not the sharpest knife in the drawer either, so, i hope you would not mind me calling on you in the future for more help?

   i would also like to know if and when you have the time telling me, in regard to the multiline session; do i enter all the info and than hit enter, and the apt terminal, how do i get to it.
               thank you so much for your time.
              PS. your help is helping me convert my wife, she loves Microsoft.:KS:popcorn::KS:popcorn::p

---

### Post by Aearenda on 2009-03-25
I'm glad it worked - it doesn't always, for me. And all I did was relay something Michael Vogt posted in the [linked bug report]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061") - no credit to me.

Anyway, here is how to make it permanent:
1. Press <ALT> and <F2> to bring up the "run application" box (this is like pressing <WINDOWS> and R on XP).

2. Type or paste this into the box:```
gksudo gedit /etc/apt/apt.conf
```... and then press <ENTER>. In this command, 'gksudo' does the same job as 'runas' for Windows - but it assumes you want the 'root' user, which is also called the 'superuser' at times, so you don't need to tell it anything apart from the command to be run which is 'gedit', the notepad equivalent. The last part is the name of the file we are creating.

3. It will probably ask for your password - so type it and press <ENTER>.

4. Copy the text in the box below and paste it into the editor window (which ought to be blank):```
APT 
{
// Options for the downloading routines
  Acquire
  {
    BrokenProxy "true";
    http
    {
      No-Cache "true";
    };
  };
}
```

UPDATE: I now think the apt.conf file above isn't right. The APT section is spurious. In practice, it's probably easier to maintain if specified like this, since you can just add lines without worrying about the layout:
```
Acquire::http::Proxy "http://your-proxy-server1:port-number/";
// Above line will be present if you specified a proxy server at installation time, not needed otherwise
Acquire::http::No-Cache true;
Acquire::BrokenProxy true;

```

5. Modify the contents of the file, depending on which of the workarounds worked for you - if the command that worked was the 'no-cache' one, delete (or comment out) the line containing 'BrokenProxy'; alternatively, if the one that worked was the 'BrokenProxy' one, comment out the 'no-cache' entry.

6. Now save the file, and it's done!

---

### Post by george703 on 2009-03-25
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
  Sub-process bzip2 returned an error code (2)

hello all i believe i celebrated too soon the above is the error i get now.
is the bzip to blame? anyway i need help anyone?Aearenda, if you can help or direct me where to look i would appreciate it.
  or if any one out there has found a solution to this, let me know.
is it my isp or is it repos. or this bzip?
     anyway take care and hope to here from you all soon.
                 george:confused::KS

---

### Post by Aearenda on 2009-03-26
That can happen for a number of reasons.
1. If you are connected by wireless, try a wired connection (I know it shouldn't happen, but it does).
2. You tried to update as the repository you are using was being updated. Waiting a few hours and trying again should fix that.
3. The repository is corrupt, or the ISP cache still interferes - you can try setting a different country in System->Administration->Software Sources to fix that.

---

### Post by itnet7 on 2009-05-06
> **Aearenda said:**
> I have just had to work around a similar issue. It seems that some ISPs transparently cache the files, so that we receive out of date or mismatched control data for the updates. Waiting for the cache to expire is one way to fix it, and Bug 24061 ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)) contains a workaround:
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and if that does not work:
```
sudo apt-get update -o Acquire::BrokenProxy=true
```

For me, the first one works. You can make this permanent by creating /etc/apt/apt.conf with the following contents (or adding the relevant bit if your apt.conf was already created):
```

APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}

```



I was receiving the following error:
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Just wanted to report back that 

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

Worked for me as well, Thanks Aearenda!!

Chris C. 
itnet7

---

### Post by Aeonsies on 2009-05-19
Here is how I fixed my problem with this, hopefully if the above does not work for others this might help.

In the /etc/apt folder is your source.list file, this contains the list of mirrors you query against to get your updates.

I moved my sources list to sources.list.backup then ran apt-get update.  No websites will be queried because it can't find the sources file.

Then next few parts I'm not sure helped but it's what I did.

Ran apt-get check, autoclean, and update again (second time).

Change the sources.list.backup back to sources.list and re-run apt-get update.

The query took a bit longer then normal, but it actually completed and I am now able to get my updates again.

This is on 8.04.

---

### Post by derekbuc on 2009-09-17
Nice one! That last one worked! I've had problems with this on and off since Intrepid. Thanks!

---

### Post by lazy_hoor on 2009-11-10
> **Aearenda said:**
> I have just had to work around a similar issue. It seems that some ISPs transparently cache the files, so that we receive out of date or mismatched control data for the updates. Waiting for the cache to expire is one way to fix it, and Bug 24061 ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)) contains a workaround:
```
sudo apt-get update -o Acquire::http::No-Cache=True
```
and if that does not work:
```
sudo apt-get update -o Acquire::BrokenProxy=true
```

For me, the first one works. You can make this permanent by creating /etc/apt/apt.conf with the following contents (or adding the relevant bit if your apt.conf was already created):
```

APT 
{
// Options for the downloading routines
  Acquire
  {
    http
    {
      No-Cache "true";
    };
  };
}

```

Sorry, how do I create this? With notes or save via the terminal?

---

### Post by Aearenda on 2009-11-10
I'm glad you've drawn my attention to this, since my post you quoted has an error in the apt.conf file! I've updated the original.

How you create the file doesn't really matter - it's the file's content that matters. You can do it with nano in a terminal, or with OpenOffice, but here's how to do it with Gedit:

1. Press Alt and F2 to bring up the 'run program' box.

2. Type this:
```
gksudo gedit /etc/apt/apt.conf
```Then press <enter> or click the 'Run' button. Gksudo elevates the command to have admin privilege, and will ask for your password if it has not been entered recently.

3. You may find some content already there if you specified a proxy server at installation time. Just add the lines that you need at the end, like this:
```
Acquire::http::Proxy "http://your-proxy-server1:port-number/";
// Above line will be present if you specified a proxy server at installation time, not needed otherwise
Acquire::http::No-Cache true;
// Acquire::BrokenProxy true;

```
Note that '//' marks a comment line - so the broken proxy line here is commented out. Also, if you didn't specify a proxy server earlier, the first line that I have here will be missing - that's fine.

4. Save the file - it takes effect as soon as the next package management task is run, either by you doing something or by the regular update checking done by the system.

---

### Post by lazy_hoor on 2009-11-11
Thanks for that, i haven't got it working but I was tinkering with it first thing this morning and I think I did something stupid.  I'll have another go tomorrow. I just wanted to say thanks for replying though, I posted elsewhere and didn't get any help! :D

EDIT - have finally discovered that the problem was with my internet connection. Coincidentally it went down the same day I downloaded the new Ubuntu so I blamed all my woes on Ubuntu without checking if there was a problem with the internet. I had a latency problem and it was messing  with the ubuntu repositories!

---

