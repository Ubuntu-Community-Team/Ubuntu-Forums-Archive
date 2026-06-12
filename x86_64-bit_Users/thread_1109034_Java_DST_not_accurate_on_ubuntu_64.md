---
title: "Java DST not accurate on ubuntu 64"
date: 2009-03-28
forum: x86 64-bit Users
---

### Post by pclark95 on 2009-03-28
I am having an issue with all of my java installations on ubuntu 64.  Here is my system info and date info:

pclark@bks:~$ uname -a
Linux bks 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
pclark@bks:~$ date
Sat Mar 28 10:42:43 CDT 2009
pclark@bks:~$ aptitude search java | grep ^i
i A ca-certificates-java            - Common CA certificates (JKS keystore)     
i A java-common                     - Base of all Java packages                 
i A libaccess-bridge-java           - Java Access Bridge for GNOME              
i   ooobasis3.0-javafilter          - Java filter module for OpenOffice.org 3.0 
i A sun-java5-bin                   - Sun Java(TM) Runtime Environment (JRE) 5.0
i A sun-java5-demo                  - Sun Java(TM) Development Kit (JDK) 5.0 dem
i   sun-java5-jdk                   - Sun Java(TM) Development Kit (JDK) 5.0    
i A sun-java5-jre                   - Sun Java(TM) Runtime Environment (JRE) 5.0
i A sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-jdk                   - Sun Java(TM) Development Kit (JDK) 6      
i A sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc
i A tzdata-java                     - time zone and daylight-saving time data fo


No matter which JDK I use the time is still in CST and not CDT.  Here is a simple program that I have created to demonstrate the issue:

import java.util.Calendar;
import java.util.Date;
import java.util.GregorianCalendar;

public class TimeTest {

    public static void main(String[] args) {
        Calendar calendar = new GregorianCalendar(106 + 1900, 6, 8);

        System.out.println("Time" + new Date());

        System.out.println("ZONE_OFFSET: " + (calendar.get(Calendar.ZONE_OFFSET)/(60*60*1000)));

        System.out.println("DST_OFFSET: " + (calendar.get(Calendar.DST_OFFSET)/(60*60*1000)));        
    }

}


Here is the output of the program:
pclark@bks:/usr/lib/jvm$ ./java-6-sun/bin/java -cp . TimeTest
TimeSat Mar 28 09:47:56 CST 2009
ZONE_OFFSET: -6
DST_OFFSET: 1

And the output of my system time:
pclark@bks:~$ date
Sat Mar 28 10:47:57 CDT 2009


I have also tried to update the tz data using the sun tool: [http://java.sun.com/javase/tzupdater_README.html](http://java.sun.com/javase/tzupdater_README.html)

This is only happening on my 64 bit ubuntu and not my 32 bit.  Does anyone know why this is happening?

Thanks,
Patrick

---

### Post by pclark95 on 2009-03-28
I finally found the problem for those who are interested.

The bug is located here:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6456628](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6456628)

I just added the following to my .profile
export TZ=`cat /etc/timezone`

---

