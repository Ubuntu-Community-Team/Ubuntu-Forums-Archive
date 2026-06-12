---
title: "Numbers gone wrong (Lubuntu 14.10-Wine-Acess 2003"
date: 2014-05-14
forum: Wine
---

### Post by Gary_Calzavara on 2014-05-14
What I have:
  
[LIST]
[*]1 PC with windows XP (server) 
[*]1 PC with windows 7 (client 1) 
[*]1 PC with lubuntu 14.10 and wine-1.6.2 
[/LIST]
  
This is locale command output:

  LANG=es_VE.UTF-8
LANGUAGE=es_VE:en
LC_CTYPE="es_VE.UTF-8"
LC_NUMERIC=es_VE.UTF-8
LC_TIME=es_VE.UTF-8
LC_COLLATE="es_VE.UTF-8"
LC_MONETARY=es_VE.UTF-8
LC_MESSAGES="es_VE.UTF-8"
LC_PAPER=es_VE.UTF-8
LC_NAME=es_VE.UTF-8
LC_ADDRESS=es_VE.UTF-8
LC_TELEPHONE=es_VE.UTF-8
LC_MEASUREMENT=es_VE.UTF-8
LC_IDENTIFICATION=es_VE.UTF-8
LC_ALL=
  This is my regedit:
  [Control Panel\\International] 1399488839
"iCalendarType"="1"
"iCountry"="58"
"iCurrDigits"="2"
"iCurrency"="2"
"iDate"="1"
"iDigits"="2"
"iFirstDayOfWeek"="6"
"iFirstWeekOfYear"="0"
"iLDate"="0"
"iLZero"="1"
"iMeasure"="0"
"iNegCurr"="12"
"iNegNumber"="1"
"iPaperSize"="1"
"iTime"="0"
"iTimePrefix"="0"
"iTLZero"="1"
"LC_CTYPE"="0000200a"
"LC_MEASUREMENT"="0000200a"
"LC_MONETARY"="0000200a"
"LC_NUMERIC"="0000200a"
"LC_PAPER"="0000200a"
"LC_TELEPHONE"="0000200a"
"LC_TIME"="0000200a"
"Locale"="0000200a"
"Numshape"="1"
"s1159"="a.m."
"s2359"="p.m."
"sCountry"="Venezuela"
"sCurrency"="Bs"
"sDate"="/"
"sDecimal"=","
"sGrouping"="3;0"
"sLanguage"="ESV"
"sList"=","
"sLongDate"="dddd, dd' de 'MMMM' de 'yyyy"
"sMonDecimalSep"=","
"sMonGrouping"="3;0"
"sMonThousandSep"="."
"sNativeDigits"="0123456789"
"sNegativeSign"="-"
"sPositiveSign"=""
"sShortDate"="dd/MM/yyyy"
"sThousand"="."
"sTime"=":"
"sTimeFormat"="hh:mm:ss tt"
"sYearMonth"="MMMM' de 'yyyy"
  
The Problem:    I am using an administrative software made under MS  acess 2003 (sfp.exe) . whenever I run the software in my lubuntu PC,   all the prices are wrong. For example, I have a product called “escoba  arauca”. Each box cost 293.00. The system shows  -28.00, multiplied by 1  =  2,800.00. It should be 293 x 1 = 293.
  
t is obvious I am doing something wrong but I don’t know what else  to do. This is my 3erd week surfing the web searching for answers but no  luck for now.

  
Under Windows works fine. Here the screen shots under windows 7 (the rigth one) and under lubuntu (the one with the issue). 

[ATTACH=CONFIG]253161[/ATTACH][ATTACH=CONFIG]253160[/ATTACH]


Thank you very much for your help.  


PS: It is good to let you know that if I read an already made invoice created from any windows computer, the prices are Ok. So, reading the  tables don't cause any problem. This wrong numbers comes when I am  making the invoice from my lubuntu PC. I guess that the problem comes  when there are some calculations to do. In example: the prices is the  result of this math operation: Cost + Profit.


  I have another screen shot showing that the products prices are Ok,  but somehow they are multiplied by 100 instead of 1. I can't post it  neither, sorry. So, every time math is involved, results are wrong. I  use coma (,) for decimals and the dot (.) for thousands.


[ATTACH=CONFIG]253162[/ATTACH]

---

