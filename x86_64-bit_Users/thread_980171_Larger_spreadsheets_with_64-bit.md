---
title: "Larger spreadsheets with 64-bit?"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by Caps18 on 2008-11-12
In my 32-bit world, my spreadsheet program has 65536 rows maximum.  I'm wondering if this is a software limitation or memory limitation, and if using 64-bit OpenOffice on a 64-bit machine would allow me to have more rows of data?

Thanks

---

### Post by jespdj on 2008-11-12
It's a software limitation that doesn't have anything to do with memory limits and 32-bit or 64-bit.

What spreadsheet program are you using, OpenOffice 2.4? If I remember correctly, the maximum has been raised in OpenOffice 3.0.

---

### Post by felker2 on 2008-11-13
[http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Calc/Miscellaneous/What%27s_the_maximum_number_of_rows_and_cells_for_a_spreadsheet_file%3F](http://wiki.services.openoffice.org/wiki/Documentation/FAQ/Calc/Miscellaneous/What%27s_the_maximum_number_of_rows_and_cells_for_a_spreadsheet_file%3F) gives this information:


The limitations of the OpenOffice.org 2.x Calc versions are

    * maximum number of rows: 65,536
    * maximum number of columns: 256
    * maximum number of cells per sheet: 16,777,216
    * maximum number of sheets: 256
    * maximum number of cells per file: 4,294,967,296 



The limitations of the OpenOffice.org 3.x Calc versions are

    * maximum number of rows: 65,536
    * maximum number of columns: 1024
    * maximum number of cells per sheet: 67,108,864 




So: the 32 or 64 bitness is not mentioned, and thus does not matter.

---

### Post by gboniel on 2008-11-29
I have encountered this problem several times already. From Visual Foxpro, I export a table into a csv format. When I open the exported file in Open Office spreadsheet, the following message appears:
The maximum number of rows has been exceeded. Excess rows were not imported!

The spreadsheet file that is opened is indeed missing some rows, as only 154 records are imported. I am confused since there are only 207 lines/records exported from Visual Foxpro.

Please help.

Thanks in advance.

---

