---
title: "OpenOffice.org 2.04-0ubuntu problem with execution of macros"
date: 2006-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by ulefr01 on 2006-11-16
OpenOffice 64-bit
A big Problem with openoffice occurs on ubuntu Edgy : 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux	
	
I get a Base runtime error 
An exception occured
Type com.sun.star.lang IndexOut of Bounds Exception Message 

Happens after execution of a macro on a calc document (spreadsheet) .
The macro contains :
	dim odoc as object, osheets as object
	dim osheet1 as object, osheet2 as object
	dim ocell1 as object, ocell2 as object
	dim teller as integer
	odoc=thiscomponent
	osheets=odoc.sheets()
	osheet1=osheets.getbyname("Verrichting")
	osheet2=osheets.getbyname("Verrichtingen")
	ocell2=osheet2.getcellrangebyname("B4")
	teller=ocell2.getvalue
	teller=teller-1
	ocell2.setvalue(teller)
	ocell1=osheet2.getcellbyposition(3,teller-1)
        ....

This is very strange : value of teller becomes -1 on this last instruction.
Cel B4 on sheet "Verrichtingen" contains 579  before i run the macro and is '-1' after the run.

Instruction "teller=ocell2.getvalue" results in a value of teller = 0 ! Nevertheless cell B4 contains the value 579 !

Changing the "ocell2=osheet2.getcellrangebyname("B4")" to "ocell2=osheet2.getcellbyposition(1,3)" does not help 
Removing OpenOffice and reinstall Openoffice did not helped me.

Changing the value of B4 to another not zero and positive value did not help .

On all previous versions of openoffice this macro was running fine.

---

### Post by ulefr01 on 2006-11-18
This is really a problem on the Edgy version !
I have removed openoffice.org version 2.0.4 and afterwards installed the dapper version of openoffice 64-bit version : 2.0.2-2ubuntu12-1.

This problem occurs NOT on this 2.0.2-2ubuntu12-1 version.

---

