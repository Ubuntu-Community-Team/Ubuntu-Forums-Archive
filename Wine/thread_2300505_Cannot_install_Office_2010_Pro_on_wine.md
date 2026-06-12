---
title: "Cannot install Office 2010 Pro on wine"
date: 2015-10-26
forum: Wine
---

### Post by lukebenes on 2015-10-26
I was having the exact same issue [as this thread. ]("http://ubuntuforums.org/showthread.php?t=1691257")
The error message is:
```
fixme:rpc:handle_bind_error unexpected status value 1765 err:rpc:RpcAssoc_BindConnection rejected bind for reason 0 
```

The solution is to
```
$ sudo apt-get install Winbind
```

It's sad that on the previous thread, there were 2 pages of attacks for his work requiring a MS product and no answers. What's going on with the Ubuntu community?

---

### Post by ian-weisser on 2015-10-26
Please report posts that are unhelpful attacks. Moderators want help-request threads to be helpful.

We get all kinds here, the patient and helpful (gurus), the impatient but helpful (snarks), the patient but unhelpful (kindlys), and the impatient and unhelpful (dopes). All four kinds were in the community a decade ago, all four kinds are in the community today.

---

### Post by mystics on 2015-10-26
So you've already found a solution? Good.

After that, the thread you linked ran from early to mid 2011 (i.e. right after Office 2010 came out, so likely before a definite solution was found), and I saw more OpenOffice bashing than bashing of the OP's work. I would say to just calm down about a four year old thread, but the lack of attacks on the OP's work makes me think you might have linked the wrong one.

---

### Post by recepserit on 2015-11-02
How interesting...
Maybe you can install Office 2010 with PlayOnLinux.

---

### Post by mJayk on 2015-11-03
> **recepserit said:**
> How interesting...
Maybe you can install Office 2010 with PlayOnLinux.


This has always been my go to method for office, always worked for me too.

---

