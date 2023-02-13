---
title: "the password thing"
date: 2022-11-25T15:15:20+01:00
draft: false
tags:
- dev
languages:
- English
---

# Why i wanted password protection?

I want to share personal stuff also with pictures therefore i want to limit who can access this site.

# The implementation

For now at least the implementation is kinda poor. You can just bypass it by disabling JavaScript in your browser.  
Then having a look in the SourceCode and setting the password cookie by yourself. (credit to TimstOrm)  
The problem is that no client side authentication is rly secure but because of the static nature of this site Authentication via OAuth (which would be the standard way) is not easy to implement.  
The security guru suggested to hash the password in the SourceCode  or to use the servers Pwd Auth capabilities.  
We'll see in the coming weeks.  
Here the bonobo implementation: xD


```
<script type="text/javascript">
    let password = "please";
    console.log(document.cookie.includes('loggedIn=true'));
    //checks for cookie
    if (document.cookie.includes('loggedIn=true') == false) {
        //puts up promtpt if cookie not existing
        let x = prompt("Enter in the password ", " ");
        if (x.toLowerCase() == password) {
            //set cookie
            let timespemp = new Date(Date.UTC(2022, 12, 23));
            document.cookie = "loggedIn=true; ${timespemp.toUTCString()}";
            //alertttt
            alert("Come right in \n \n You've entered in the right password");
            window.location = "index.html";
        } else {
            window.location = "bad.htm";
        }
    }
</script>
```