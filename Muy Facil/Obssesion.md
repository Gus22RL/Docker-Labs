### Step 1
#### We are start doing an scanig map.

The fist thing that i see  is that we can use the user **anonymous** to login with ftp. Also The ports 22/ssh and 80/http are open.

![[Pasted image 20240720131700.png]]
### Step 2
#### Login ftp
Using anonymous like user we dont need put a password.
![[Pasted image 20240720132042.png]]
Enlist the files.
![[Pasted image 20240720132227.png]]
Get the files.
![[Pasted image 20240720132310.png]]
Let's see the files content .

**chat-goza.txt :**
![[Pasted image 20240721122745.png]]
**pendientes.txt :**
![[Pasted image 20240721122847.png]]

### Step 3
#### Get the ssh password
We have 2 different user to try, Russoski appears also in the web page. thougth let's try this with hydra.

We found the password!
![[Pasted image 20240721123416.png]]

### Step 4
#### Now let's escalate privileges.

Login ssh.
![[Pasted image 20240721123703.png]]
We see that we can exploit a bulenerabiliti an spawn a shell with root privileges usin vim.

```
vim -c ':!/bin/sh'
```
![[Pasted image 20240720130347.png]]