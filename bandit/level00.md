# Bandit Level 0 → Level 1

For this level all we got to do is login into the overthewire device from our device using ssh. The credentials(username, password, the host and also the port is not the default 22, it is also provided) are provided. We just need to ssh our way into the remote device and get on.

![SSH login success](../images/Screenshot0.png)

After logging in we can see we are in the bandit level 0 environment. To find where the next level's password is let us first list the files using 'ls' command. I found a file named readme, so to find the file's content use the 'cat' command. Wala! we found the password and this is it for this level. We will use this password for the next level.

![ls and cat screenshot](../images/Screenshot1.png)
