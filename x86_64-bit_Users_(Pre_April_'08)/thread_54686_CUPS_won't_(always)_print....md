---
title: "CUPS won't (always) print..."
date: 2005-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by manfo on 2005-08-05
I read around that this is a pretty common issue, but I hadn't it solved yet. The system correctly detects and installs my printer (the infamous HP DeskJet 720C  :) ) and I get no errors, but still every job sent on queue disappears in a second or two and nothing gets printed.

99% of the times, at least: I really don't know why, but I noticed that *sometimes* I was able to print something (a couple of text files and thegnome-cups-manager test page, for example). This means that both the printer and CUPS work fine, I guess, but why don't they *always* do the job?  :mad:  

Thanks & bye!
.m

---

### Post by Corbelius on 2005-08-05
Install the gs-gpl package and try again, if don't work post ur cups log. (found it in /var/cups/)

Edit: ho notato dopo che eri italiano lol, cmq installa quel pacchetto, anche a me faceva lo stesso scherzetto (canon s600), poi leggendo i log di cups sono arrivato al fatto che gli servivano degli interpreti postscript, ho installato gs-gpl e la stampa è andata una meraviglia :D

---

### Post by manfo on 2005-08-05
Ciao Corbelius, grazie per la risposta e per il consiglio!

Ho installato gs-gpl, ma ancora niente da fare  :-| 
Di seguito incollo l'ultima parte dell'error_log di CUPS, dal momento in cui gli dò da stampare una pagina di prova dall'interfaccia web.

(To non-Italian readers: installed gs-gpl, but it's still not working...)

```

D [06/Aug/2005:02:22:50 +0200] AcceptClient: 5 from localhost:631.
D [06/Aug/2005:02:22:50 +0200] ReadClient: 5 GET /printers/HP-DeskJet-720C?op=print-test-page HTTP/1.1
D [06/Aug/2005:02:22:50 +0200] CGI /usr/lib/cups/cgi-bin/printers.cgi started - PID = 30784
I [06/Aug/2005:02:22:50 +0200] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=30784)
D [06/Aug/2005:02:22:50 +0200] SendCommand: 5 file=7
D [06/Aug/2005:02:22:50 +0200] AcceptClient: 6 from localhost:631.
D [06/Aug/2005:02:22:50 +0200] ReadClient: 6 POST /printers/HP-DeskJet-720C HTTP/1.1
D [06/Aug/2005:02:22:50 +0200] print_job: request file type is application/postscript.
D [06/Aug/2005:02:22:50 +0200] check_quotas: requesting-user-name = 'manfo'
D [06/Aug/2005:02:22:50 +0200] print_job: requesting-user-name = 'manfo'
D [06/Aug/2005:02:22:50 +0200] Adding default job-sheets values "none,none"...
I [06/Aug/2005:02:22:50 +0200] Adding start banner page "none" to job 4.
I [06/Aug/2005:02:22:50 +0200] Adding end banner page "none" to job 4.
I [06/Aug/2005:02:22:50 +0200] Job 4 queued on 'HP-DeskJet-720C' by 'manfo'.
D [06/Aug/2005:02:22:50 +0200] Job 4 hold_until = 0
D [06/Aug/2005:02:22:50 +0200] StartJob(4, 0x54e520)
D [06/Aug/2005:02:22:50 +0200] StartJob() id = 4, file = 0/1
D [06/Aug/2005:02:22:50 +0200] job-sheets=none,none
D [06/Aug/2005:02:22:50 +0200] banner_page = 0
D [06/Aug/2005:02:22:50 +0200] StartJob: argv = "HP-DeskJet-720C","4","manfo","Test Page","1","","/var/spool/cups/d00004-001"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[2]="USER=root"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[3]="CHARSET=utf-8"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[4]="LANG=it"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[5]="TZ=Europe/Rome"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[6]="PPD=/etc/cups/ppd/HP-DeskJet-720C.ppd"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[11]="DEVICE_URI=parallel:/dev/lp0"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[12]="PRINTER=HP-DeskJet-720C"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[15]="CUPS_SERVER=localhost"
D [06/Aug/2005:02:22:50 +0200] StartJob: envp[16]="IPP_PORT=631"
D [06/Aug/2005:02:22:50 +0200] StartJob: statusfds = [ 8 9 ]
D [06/Aug/2005:02:22:50 +0200] StartJob: filterfds[1] = [ 10 -1 ]
D [06/Aug/2005:02:22:50 +0200] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [06/Aug/2005:02:22:50 +0200] StartJob: filterfds[0] = [ 11 12 ]
D [06/Aug/2005:02:22:50 +0200] start_process("/usr/lib/cups/filter/pstops", 0x7fbffefab0, 0x7fbffeec90, 10, 12, 9)
I [06/Aug/2005:02:22:50 +0200] Started filter /usr/lib/cups/filter/pstops (PID 30785) for job 4.
D [06/Aug/2005:02:22:50 +0200] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [06/Aug/2005:02:22:50 +0200] StartJob: filterfds[1] = [ 10 13 ]
D [06/Aug/2005:02:22:50 +0200] start_process("/usr/lib/cups/filter/foomatic-rip", 0x7fbffefab0, 0x7fbffeec90, 11, 13, 9)
I [06/Aug/2005:02:22:50 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 30786) for job 4.
D [06/Aug/2005:02:22:50 +0200] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [06/Aug/2005:02:22:50 +0200] StartJob: filterfds[0] = [ -1 11 ]
D [06/Aug/2005:02:22:50 +0200] start_process("/usr/lib/cups/backend/parallel", 0x7fbffefab0, 0x7fbffeec90, 10, 11, 9)
I [06/Aug/2005:02:22:50 +0200] Started backend /usr/lib/cups/backend/parallel (PID 30787) for job 4.
D [06/Aug/2005:02:22:50 +0200] ProcessIPPRequest: 6 status_code=0
D [06/Aug/2005:02:22:50 +0200] [Job 4] Page = 595x842; 0,0 to 595,842
D [06/Aug/2005:02:22:50 +0200] [Job 4] slowcollate=0, slowduplex=0, sloworder=0
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%BoundingBox: 0 0 612 792
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%Pages: 1
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%LanguageLevel: 1
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%DocumentData: Clean7Bit
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%DocumentSuppliedResources: procset testprint/1.1
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%DocumentNeededResources: font Helvetica Helvetica-Bold Times-Roman
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%Creator: Michael Sweet, Easy Software Products
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%CreationDate: May 11, 1999
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%Title: Test Page
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%EndComments
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%BeginProlog
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%BeginResource procset testprint 1.1 0
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%EndResource
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%EndProlog
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%Page: 1 1
D [06/Aug/2005:02:22:50 +0200] [Job 4] 0 %%Page: 1 1
D [06/Aug/2005:02:22:50 +0200] [Job 4] pw = 595.0, pl = 842.0
D [06/Aug/2005:02:22:50 +0200] [Job 4] PageLeft = 0.0, PageRight = 595.0
D [06/Aug/2005:02:22:50 +0200] [Job 4] PageTop = 842.0, PageBottom = 0.0
D [06/Aug/2005:02:22:50 +0200] [Job 4] PageWidth = 595.0, PageLength = 842.0
D [06/Aug/2005:02:22:50 +0200] [Job 4] perl: warning: Setting locale failed.
D [06/Aug/2005:02:22:50 +0200] [Job 4] perl: warning: Please check that your locale settings:
D [06/Aug/2005:02:22:50 +0200] [Job 4] LANGUAGE = (unset),
D [06/Aug/2005:02:22:50 +0200] [Job 4] LC_ALL = (unset),
D [06/Aug/2005:02:22:50 +0200] [Job 4] LANG = "it"
D [06/Aug/2005:02:22:50 +0200] [Job 4] are supported and installed on your system.
D [06/Aug/2005:02:22:50 +0200] [Job 4] perl: warning: Falling back to the standard locale ("C").
D [06/Aug/2005:02:22:50 +0200] CloseClient: 6
D [06/Aug/2005:02:22:50 +0200] [Job 4] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [06/Aug/2005:02:22:50 +0200] [Job 4] Parsing PPD file ...
D [06/Aug/2005:02:22:50 +0200] [Job 4] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option ColorSpace
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option Resolution
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option PageSize
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option PageRegion
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option ImageableArea
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option PaperDimension
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option EconoFast
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option ColorMode
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option Dither
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option Bidirectional
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option Blackness
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option BottomMargin
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option LeftMargin
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option RightMargin
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option TopMargin
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option XOffset
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option YOffset
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option Model
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option GammaFile
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option pnmFormat
D [06/Aug/2005:02:22:50 +0200] [Job 4] Added option Font
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4] Parameter Summary
D [06/Aug/2005:02:22:50 +0200] [Job 4] -----------------
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4] Spooler: cups
D [06/Aug/2005:02:22:50 +0200] [Job 4] Printer: HP-DeskJet-720C
D [06/Aug/2005:02:22:50 +0200] [Job 4] PPD file: /etc/cups/ppd/HP-DeskJet-720C.ppd
D [06/Aug/2005:02:22:50 +0200] [Job 4] Printer model: HP DeskJet 720C Foomatic/pnm2ppa (recommended)
D [06/Aug/2005:02:22:50 +0200] [Job 4] Job title: Test Page
D [06/Aug/2005:02:22:50 +0200] [Job 4] File(s) to be printed:
D [06/Aug/2005:02:22:50 +0200] [Job 4] <STDIN>
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4] ================================================
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4] File: <STDIN>
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4] ================================================
D [06/Aug/2005:02:22:50 +0200] [Job 4]
D [06/Aug/2005:02:22:50 +0200] [Job 4] Reading PostScript input ...
D [06/Aug/2005:02:22:51 +0200] [Job 4] --> This document is DSC-conforming!
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4] -----------
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginProlog
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%EndProlog
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4] -----------
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginSetup
D [06/Aug/2005:02:22:51 +0200] [Job 4] Inserting PostScript code for CUPS' page accounting
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *PageSize A4
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: PageSize=A4 --> Option will be set by PostScript interpreter
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *pnmFormat PixMap
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: pnmFormat=PixMap --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: pnmFormat=PixMap
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: pnmFormat=PixMap --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *ColorMode CMYK
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: ColorMode=CMYK --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: ColorMode=CMYK
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: ColorMode=CMYK --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *EconoFast Off
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: EconoFast=Off --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: EconoFast=Off
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: EconoFast=Off --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *Dither FloydSteinberg
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: Dither=FloydSteinberg --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: Dither=FloydSteinberg
D [06/Aug/2005:02:22:51 +0200] ReadClient: 5 GET /favicon.ico HTTP/1.1
D [06/Aug/2005:02:22:51 +0200] SendError: 5 code=404 (Not Found)
D [06/Aug/2005:02:22:51 +0200] CloseClient: 5
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: Dither=FloydSteinberg --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *GammaFile Default
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: GammaFile=Default --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: GammaFile=Default
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: GammaFile=Default --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *Bidirectional Default
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: Bidirectional=Default --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: Bidirectional=Default
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: Bidirectional=Default --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *Blackness 2
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: Blackness=2 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: Blackness=2
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: Blackness=2 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *TopMargin 10
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: TopMargin=10 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: TopMargin=10
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: TopMargin=10 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *BottomMargin 150
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: BottomMargin=150 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: BottomMargin=150
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: BottomMargin=150 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *LeftMargin 10
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: LeftMargin=10 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: LeftMargin=10
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: LeftMargin=10 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *RightMargin 10
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: RightMargin=10 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: RightMargin=10
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: RightMargin=10 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *XOffset 160
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: XOffset=160 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: XOffset=160
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: XOffset=160 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%BeginFeature: *YOffset 50
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: YOffset=50 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %% FoomaticRIPOptionSetting: YOffset=50
D [06/Aug/2005:02:22:51 +0200] [Job 4] Option: YOffset=50 --> Setting option
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found: %%EndSetup
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4] -----------
D [06/Aug/2005:02:22:51 +0200] [Job 4] New page:  1 1
D [06/Aug/2005:02:22:51 +0200] [Job 4] Inserting option code into "PageSetup" section.
D [06/Aug/2005:02:22:51 +0200] [Job 4] No page header or page header not DSC-conforming
D [06/Aug/2005:02:22:51 +0200] [Job 4] 0 %%EOF
D [06/Aug/2005:02:22:51 +0200] [Job 4] Saw EOF!
D [06/Aug/2005:02:22:51 +0200] [Job 4] Stopping search for page header options
D [06/Aug/2005:02:22:51 +0200] [Job 4] Found:
D [06/Aug/2005:02:22:51 +0200] [Job 4] pageHeight sub                   % Move down...
D [06/Aug/2005:02:22:51 +0200] [Job 4] --> Output goes directly to the renderer now.
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4] Starting renderer
D [06/Aug/2005:02:22:51 +0200] [Job 4] JCL: <job data>
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4] renderer PID kid4=30789
D [06/Aug/2005:02:22:51 +0200] [Job 4] renderer command: gs -q -dNOPAUSE -dPARANOIDSAFER -dBATCH -r600 -sDEVICE=ppmraw  -sOutputFile=- - | pnm2ppa -v 720  -B 2 -t 10 -b 150 -l 10 -r 10 -x 160 -y 50 -i - -o -
D [06/Aug/2005:02:22:51 +0200] [Job 4] perl: warning: Setting locale failed.
D [06/Aug/2005:02:22:51 +0200] [Job 4] perl: warning: Please check that your locale settings:
D [06/Aug/2005:02:22:51 +0200] [Job 4] LANGUAGE = (unset),
D [06/Aug/2005:02:22:51 +0200] [Job 4] LC_ALL = (unset),
D [06/Aug/2005:02:22:51 +0200] [Job 4] LANG = "it"
D [06/Aug/2005:02:22:51 +0200] [Job 4] are supported and installed on your system.
D [06/Aug/2005:02:22:51 +0200] [Job 4] perl: warning: Falling back to the standard locale ("C").
D [06/Aug/2005:02:22:51 +0200] [Job 4] foomatic-gswrapper: gs '-dNOPAUSE' '-dPARANOIDSAFER' '-dBATCH' '-r600' '-sDEVICE=ppmraw' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [06/Aug/2005:02:22:51 +0200] [Job 4] ESP Ghostscript 7.07 (2003-07-12)
D [06/Aug/2005:02:22:51 +0200] [Job 4] Copyright 2003 artofcode LLC and Easy Software Products, all rights reserved.
D [06/Aug/2005:02:22:51 +0200] [Job 4] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [06/Aug/2005:02:22:51 +0200] [Job 4] Loading NimbusSanL-Bold font from /var/lib/defoma/gs.d/dirs/fonts/n019004l.pfb... 2743528 1253970 1812136 498216 0 done.
D [06/Aug/2005:02:22:51 +0200] [Job 4] Loading NimbusSanL-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n019003l.pfb... 2857544 1367787 1812136 507238 0 done.
D [06/Aug/2005:02:22:51 +0200] [Job 4] Loading NimbusRomNo9L-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n021003l.pfb... 3040000 1479260 1771768 392101 0 done.
D [06/Aug/2005:02:22:51 +0200] [Job 4]
D [06/Aug/2005:02:22:51 +0200] [Job 4] Closing renderer
D [06/Aug/2005:02:22:51 +0200] [Job 4] Loading NimbusSanL-BoldItal font from /var/lib/defoma/gs.d/dirs/fonts/n019024l.pfb... 3174200 1610840 1791952 418386 0 done.
D [06/Aug/2005:02:22:53 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Aug/2005:02:22:53 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Aug/2005:02:22:53 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Aug/2005:02:22:53 +0200] ProcessIPPRequest: 4 status_code=1
D [06/Aug/2005:02:22:53 +0200] [Job 4] tail process done writing data to STDOUT
D [06/Aug/2005:02:22:53 +0200] [Job 4] KID4 finished
D [06/Aug/2005:02:22:53 +0200] [Job 4] KID3 finished
D [06/Aug/2005:02:22:53 +0200] [Job 4] KID4 exited with status 0
D [06/Aug/2005:02:22:53 +0200] [Job 4] KID3 exited with status 0
D [06/Aug/2005:02:22:53 +0200] [Job 4] Renderer exit stat: 0
D [06/Aug/2005:02:22:53 +0200] [Job 4] Renderer process finished
D [06/Aug/2005:02:22:53 +0200] [Job 4]
D [06/Aug/2005:02:22:53 +0200] [Job 4] Closing foomatic-rip.
D [06/Aug/2005:02:22:53 +0200] UpdateJob: job 4, file 0 is complete.
D [06/Aug/2005:02:22:53 +0200] CancelJob: id = 4
D [06/Aug/2005:02:22:53 +0200] StopJob: id = 4, force = 0
D [06/Aug/2005:02:22:53 +0200] StopJob: printer state is 3
D [06/Aug/2005:02:22:58 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Aug/2005:02:22:58 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Aug/2005:02:22:58 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Aug/2005:02:22:58 +0200] ProcessIPPRequest: 4 status_code=1

```

---

### Post by Corbelius on 2005-08-06
Credo sia un problema di linguaggio locale, hai installato i pacchetti della lingua italiano vero? se no fallo, se si invece prova a riconfigurare il linguaggio del sistema:

dpkg-reconfigure locales

Scegli tutto quello che c'è di italiano nella prima lista, alla seconda scegli it@euro, una volta fatto, riavvii gnome o direttamente il pc e riprova. Se non va nenche così allora installa "localeconf" e configuralo.

---

### Post by manfo on 2005-08-06
[QUOTE=Corbelius]Credo sia un problema di linguaggio locale, hai installato i pacchetti della lingua italiano vero? se no fallo, se si invece prova a riconfigurare il linguaggio del sistema:

dpkg-reconfigure locales

Scegli tutto quello che c'è di italiano nella prima lista, alla seconda scegli it@euro, una volta fatto, riavvii gnome o direttamente il pc e riprova. Se non va nenche così allora installa "localeconf" e configuralo.[/QUOTE]
...fatto, ma ancora non funziona... 

Se lancio "locale", mi dà:
```

LANG=it_IT@euro
LC_CTYPE="it_IT@euro"
LC_NUMERIC="it_IT@euro"
LC_TIME="it_IT@euro"
LC_COLLATE="it_IT@euro"
LC_MONETARY="it_IT@euro"
LC_MESSAGES="it_IT@euro"
LC_PAPER="it_IT@euro"
LC_NAME="it_IT@euro"
LC_ADDRESS="it_IT@euro"
LC_TELEPHONE="it_IT@euro"
LC_MEASUREMENT="it_IT@euro"
LC_IDENTIFICATION="it_IT@euro"
LC_ALL=

```
e il log di CUPS mi sembra uguale a quello dell'altra volta:
```

D [06/Aug/2005:20:12:01 +0200] ReadClient: 5 GET /printers/DeskJet-720C?op=print-test-page HTTP/1.1
D [06/Aug/2005:20:12:01 +0200] CGI /usr/lib/cups/cgi-bin/printers.cgi started - PID = 7206
I [06/Aug/2005:20:12:01 +0200] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7206)
D [06/Aug/2005:20:12:01 +0200] SendCommand: 5 file=7
D [06/Aug/2005:20:12:01 +0200] AcceptClient: 6 from localhost:631.
D [06/Aug/2005:20:12:01 +0200] ReadClient: 6 POST /printers/DeskJet-720C HTTP/1.1
D [06/Aug/2005:20:12:01 +0200] print_job: request file type is application/postscript.
D [06/Aug/2005:20:12:01 +0200] check_quotas: requesting-user-name = ''
D [06/Aug/2005:20:12:01 +0200] print_job: requesting-user-name = ''
D [06/Aug/2005:20:12:01 +0200] Adding default job-sheets values "none,none"...
I [06/Aug/2005:20:12:01 +0200] Adding start banner page "none" to job 18.
I [06/Aug/2005:20:12:01 +0200] Adding end banner page "none" to job 18.
I [06/Aug/2005:20:12:01 +0200] Job 18 queued on 'DeskJet-720C' by ''.
D [06/Aug/2005:20:12:01 +0200] Job 18 hold_until = 0
D [06/Aug/2005:20:12:01 +0200] StartJob(18, 0x7048d0)
D [06/Aug/2005:20:12:01 +0200] StartJob() id = 18, file = 0/1
D [06/Aug/2005:20:12:01 +0200] job-sheets=none,none
D [06/Aug/2005:20:12:01 +0200] banner_page = 0
D [06/Aug/2005:20:12:01 +0200] StartJob: argv = "DeskJet-720C","18","","Test Page","1","","/var/spool/cups/d00018-001"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[2]="USER=root"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[3]="CHARSET=iso-8859-15"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[4]="LANG=it"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[5]="TZ=Europe/Rome"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[6]="PPD=/etc/cups/ppd/DeskJet-720C.ppd"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[11]="DEVICE_URI=parallel:/dev/lp0"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[12]="PRINTER=DeskJet-720C"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[15]="CUPS_SERVER=localhost"
D [06/Aug/2005:20:12:01 +0200] StartJob: envp[16]="IPP_PORT=631"
D [06/Aug/2005:20:12:01 +0200] StartJob: statusfds = [ 8 9 ]
D [06/Aug/2005:20:12:01 +0200] StartJob: filterfds[1] = [ 10 -1 ]
D [06/Aug/2005:20:12:01 +0200] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [06/Aug/2005:20:12:01 +0200] StartJob: filterfds[0] = [ 11 12 ]
D [06/Aug/2005:20:12:01 +0200] start_process("/usr/lib/cups/filter/pstops", 0x7fbfff0060, 0x7fbffef240, 10, 12, 9)
I [06/Aug/2005:20:12:01 +0200] Started filter /usr/lib/cups/filter/pstops (PID 7207) for job 18.
D [06/Aug/2005:20:12:01 +0200] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [06/Aug/2005:20:12:01 +0200] StartJob: filterfds[1] = [ 10 13 ]
D [06/Aug/2005:20:12:01 +0200] start_process("/usr/lib/cups/filter/foomatic-rip", 0x7fbfff0060, 0x7fbffef240, 11, 13, 9)
I [06/Aug/2005:20:12:01 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7208) for job 18.
D [06/Aug/2005:20:12:01 +0200] StartJob: backend = "/usr/lib/cups/backend/parallel"
D [06/Aug/2005:20:12:01 +0200] StartJob: filterfds[0] = [ -1 11 ]
D [06/Aug/2005:20:12:01 +0200] start_process("/usr/lib/cups/backend/parallel", 0x7fbfff0060, 0x7fbffef240, 10, 11, 9)
I [06/Aug/2005:20:12:01 +0200] Started backend /usr/lib/cups/backend/parallel (PID 7209) for job 18.
D [06/Aug/2005:20:12:01 +0200] ProcessIPPRequest: 6 status_code=0
D [06/Aug/2005:20:12:01 +0200] [Job 18] Page = 595x842; 0,0 to 595,842
D [06/Aug/2005:20:12:01 +0200] [Job 18] slowcollate=0, slowduplex=0, sloworder=0
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%BoundingBox: 0 0 612 792
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%Pages: 1
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%LanguageLevel: 1
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%DocumentData: Clean7Bit
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%DocumentSuppliedResources: procset testprint/1.1
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%DocumentNeededResources: font Helvetica Helvetica-Bold Times-Roman
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%Creator: Michael Sweet, Easy Software Products
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%CreationDate: May 11, 1999
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%Title: Test Page
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%EndComments
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%BeginProlog
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%BeginResource procset testprint 1.1 0
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%EndResource
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%EndProlog
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%Page: 1 1
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%Page: 1 1
D [06/Aug/2005:20:12:01 +0200] [Job 18] pw = 595.0, pl = 842.0
D [06/Aug/2005:20:12:01 +0200] [Job 18] PageLeft = 0.0, PageRight = 595.0
D [06/Aug/2005:20:12:01 +0200] [Job 18] PageTop = 842.0, PageBottom = 0.0
D [06/Aug/2005:20:12:01 +0200] [Job 18] PageWidth = 595.0, PageLength = 842.0
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Setting locale failed.
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Please check that your locale settings:
D [06/Aug/2005:20:12:01 +0200] [Job 18] LANGUAGE = (unset),
D [06/Aug/2005:20:12:01 +0200] [Job 18] LC_ALL = (unset),
D [06/Aug/2005:20:12:01 +0200] [Job 18] LANG = "it"
D [06/Aug/2005:20:12:01 +0200] [Job 18] are supported and installed on your system.
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Falling back to the standard locale ("C").
D [06/Aug/2005:20:12:01 +0200] CloseClient: 6
D [06/Aug/2005:20:12:01 +0200] [Job 18] foomatic-rip version $Revision: 3.43.2.6 $ running...
D [06/Aug/2005:20:12:01 +0200] [Job 18] Parsing PPD file ...
D [06/Aug/2005:20:12:01 +0200] [Job 18] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option ColorSpace
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option Resolution
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option PageSize
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option PageRegion
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option ImageableArea
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option PaperDimension
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option EconoFast
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option ColorMode
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option Dither
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option Bidirectional
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option Blackness
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option BottomMargin
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option LeftMargin
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option RightMargin
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option TopMargin
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option XOffset
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option YOffset
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option Model
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option GammaFile
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option pnmFormat
D [06/Aug/2005:20:12:01 +0200] [Job 18] Added option Font
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] Parameter Summary
D [06/Aug/2005:20:12:01 +0200] [Job 18] -----------------
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] Spooler: cups
D [06/Aug/2005:20:12:01 +0200] [Job 18] Printer: DeskJet-720C
D [06/Aug/2005:20:12:01 +0200] [Job 18] PPD file: /etc/cups/ppd/DeskJet-720C.ppd
D [06/Aug/2005:20:12:01 +0200] [Job 18] Printer model: HP DeskJet 720C Foomatic/pnm2ppa (recommended)
D [06/Aug/2005:20:12:01 +0200] [Job 18] Job title: Test Page
D [06/Aug/2005:20:12:01 +0200] [Job 18] File(s) to be printed:
D [06/Aug/2005:20:12:01 +0200] [Job 18] <STDIN>
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] ================================================
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] File: <STDIN>
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] ================================================
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] Reading PostScript input ...
D [06/Aug/2005:20:12:01 +0200] [Job 18] --> This document is DSC-conforming!
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] -----------
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginProlog
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%EndProlog
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] -----------
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginSetup
D [06/Aug/2005:20:12:01 +0200] [Job 18] Inserting PostScript code for CUPS' page accounting
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *PageSize A4
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: PageSize=A4 --> Option will be set by PostScript interpreter
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *pnmFormat PixMap
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: pnmFormat=PixMap --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: pnmFormat=PixMap
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: pnmFormat=PixMap --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *ColorMode CMYK
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: ColorMode=CMYK --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: ColorMode=CMYK
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: ColorMode=CMYK --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *EconoFast Off
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: EconoFast=Off --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: EconoFast=Off
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: EconoFast=Off --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *Dither FloydSteinberg
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: Dither=FloydSteinberg --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: Dither=FloydSteinberg
D [06/Aug/2005:20:12:01 +0200] ReadClient: 5 GET /favicon.ico HTTP/1.1
D [06/Aug/2005:20:12:01 +0200] SendError: 5 code=404 (Not Found)
D [06/Aug/2005:20:12:01 +0200] CloseClient: 5
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: Dither=FloydSteinberg --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *GammaFile Default
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: GammaFile=Default --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: GammaFile=Default
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: GammaFile=Default --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *Bidirectional Default
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: Bidirectional=Default --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: Bidirectional=Default
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: Bidirectional=Default --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *Blackness 2
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: Blackness=2 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: Blackness=2
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: Blackness=2 --> Setting option


D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *TopMargin 10
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: TopMargin=10 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: TopMargin=10
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: TopMargin=10 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *BottomMargin 150
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: BottomMargin=150 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: BottomMargin=150
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: BottomMargin=150 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *LeftMargin 10
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: LeftMargin=10 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: LeftMargin=10
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: LeftMargin=10 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *RightMargin 10
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: RightMargin=10 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: RightMargin=10
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: RightMargin=10 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *XOffset 160
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: XOffset=160 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: XOffset=160
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: XOffset=160 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%BeginFeature: *YOffset 50
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: YOffset=50 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %% FoomaticRIPOptionSetting: YOffset=50
D [06/Aug/2005:20:12:01 +0200] [Job 18] Option: YOffset=50 --> Setting option
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found: %%EndSetup
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] -----------
D [06/Aug/2005:20:12:01 +0200] [Job 18] New page:  1 1
D [06/Aug/2005:20:12:01 +0200] [Job 18] Inserting option code into "PageSetup" section.
D [06/Aug/2005:20:12:01 +0200] [Job 18] No page header or page header not DSC-conforming
D [06/Aug/2005:20:12:01 +0200] [Job 18] 0 %%EOF
D [06/Aug/2005:20:12:01 +0200] [Job 18] Saw EOF!
D [06/Aug/2005:20:12:01 +0200] [Job 18] Stopping search for page header options
D [06/Aug/2005:20:12:01 +0200] [Job 18] Found:
D [06/Aug/2005:20:12:01 +0200] [Job 18] pageHeight sub                  % Move down...
D [06/Aug/2005:20:12:01 +0200] [Job 18] --> Output goes directly to the renderer now.
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] Starting renderer
D [06/Aug/2005:20:12:01 +0200] [Job 18] JCL: <job data>
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] renderer PID kid4=7211
D [06/Aug/2005:20:12:01 +0200] [Job 18] renderer command: gs -q -dNOPAUSE -dPARANOIDSAFER -dBATCH -r600 -sDEVICE=ppmraw  -sOutputFile=- - | pnm2ppa -v 720  -B 2 -t 10 -b 150 -l 10 -r 10 -x 160 -y 50 -i - -o -
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Setting locale failed.
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Please check that your locale settings:
D [06/Aug/2005:20:12:01 +0200] [Job 18] LANGUAGE = (unset),
D [06/Aug/2005:20:12:01 +0200] [Job 18] LC_ALL = (unset),
D [06/Aug/2005:20:12:01 +0200] [Job 18] LANG = "it"
D [06/Aug/2005:20:12:01 +0200] [Job 18] are supported and installed on your system.
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Falling back to the standard locale ("C").
D [06/Aug/2005:20:12:01 +0200] [Job 18] foomatic-gswrapper: gs '-dNOPAUSE' '-dPARANOIDSAFER' '-dBATCH' '-r600' '-sDEVICE=ppmraw' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [06/Aug/2005:20:12:01 +0200] [Job 18] ESP Ghostscript 7.07 (2003-07-12)
D [06/Aug/2005:20:12:01 +0200] [Job 18] Copyright 2003 artofcode LLC and Easy Software Products, all rights reserved.
D [06/Aug/2005:20:12:01 +0200] [Job 18] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [06/Aug/2005:20:12:01 +0200] [Job 18] Loading NimbusSanL-Bold font from /var/lib/defoma/gs.d/dirs/fonts/n019004l.pfb... 2743528 1253970 1812136 498216 0 done.
D [06/Aug/2005:20:12:01 +0200] [Job 18] Loading NimbusSanL-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n019003l.pfb... 2857544 1367787 1812136 507238 0 done.
D [06/Aug/2005:20:12:01 +0200] [Job 18] Loading NimbusRomNo9L-Regu font from /var/lib/defoma/gs.d/dirs/fonts/n021003l.pfb... 3040000 1479260 1771768 392101 0 done.
D [06/Aug/2005:20:12:01 +0200] [Job 18]
D [06/Aug/2005:20:12:01 +0200] [Job 18] Closing renderer
D [06/Aug/2005:20:12:01 +0200] [Job 18] Loading NimbusSanL-BoldItal font from /var/lib/defoma/gs.d/dirs/fonts/n019024l.pfb... 3174200 1610840 1791952 418386 0 done.
D [06/Aug/2005:20:12:04 +0200] [Job 18] KID3 exited with status 0
D [06/Aug/2005:20:12:04 +0200] [Job 18] tail process done writing data to STDOUT
D [06/Aug/2005:20:12:04 +0200] [Job 18] KID4 finished
D [06/Aug/2005:20:12:04 +0200] [Job 18] KID4 exited with status 0
D [06/Aug/2005:20:12:04 +0200] [Job 18] Renderer exit stat: 0
D [06/Aug/2005:20:12:04 +0200] [Job 18] KID3 finished
D [06/Aug/2005:20:12:04 +0200] [Job 18] Renderer process finished
D [06/Aug/2005:20:12:04 +0200] [Job 18]
D [06/Aug/2005:20:12:04 +0200] [Job 18] Closing foomatic-rip.
D [06/Aug/2005:20:12:04 +0200] UpdateJob: job 18, file 0 is complete.
D [06/Aug/2005:20:12:04 +0200] CancelJob: id = 18
D [06/Aug/2005:20:12:04 +0200] StopJob: id = 18, force = 0
D [06/Aug/2005:20:12:04 +0200] StopJob: printer state is 3
D [06/Aug/2005:20:12:04 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Aug/2005:20:12:04 +0200] ProcessIPPRequest: 4 status_code=0
D [06/Aug/2005:20:12:04 +0200] ReadClient: 4 POST / HTTP/1.1
D [06/Aug/2005:20:12:04 +0200] ProcessIPPRequest: 4 status_code=1

```
Boh! Grazie comunque per i consigli fino ad ora!  :-) 
.m

---

### Post by Corbelius on 2005-08-07
> LANG=it_IT@euro
LC_CTYPE="it_IT@euro"
LC_NUMERIC="it_IT@euro"
LC_TIME="it_IT@euro"
LC_COLLATE="it_IT@euro"
LC_MONETARY="it_IT@euro"
LC_MESSAGES="it_IT@euro"
LC_PAPER="it_IT@euro"
LC_NAME="it_IT@euro"
LC_ADDRESS="it_IT@euro"
LC_TELEPHONE="it_IT@euro"
LC_MEASUREMENT="it_IT@euro"
LC_IDENTIFICATION="it_IT@euro"
LC_ALL= 

> D [06/Aug/2005:20:12:01 +0200] [Job 18] renderer command: gs -q -dNOPAUSE -dPARANOIDSAFER -dBATCH -r600 -sDEVICE=ppmraw  -sOutputFile=- - | pnm2ppa -v 720  -B 2 -t 10 -b 150 -l 10 -r 10 -x 160 -y 50 -i - -o -
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Setting locale failed.
D [06/Aug/2005:20:12:01 +0200] [Job 18] perl: warning: Please check that your locale settings:
D [06/Aug/2005:20:12:01 +0200] [Job 18] LANGUAGE = (unset),
D [06/Aug/2005:20:12:01 +0200] [Job 18] LC_ALL = (unset),
D [06/Aug/2005:20:12:01 +0200] [Job 18] LANG = "it" 

Come vedi il problema è lì, riprova a configurare prima locales e poi installa e configura localeconf.

---

### Post by manfo on 2005-08-08
[QUOTE=Corbelius]Come vedi il problema è lì, riprova a configurare prima locales e poi installa e configura localeconf.[/QUOTE]

Fatto e rifatto, ma il problema rimane...
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = (unset),
LC_ALL = (unset),
LANG = "it"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

---

### Post by Tomàs M. on 2007-11-21
Solved deleting /etc/pnm2ppa.conf
HTH

---

