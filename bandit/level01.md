# Bandit Level 1 → Level 2

To solve this level first I sshed into the level and listed the files in the home directory using the `ls` command and found a file named `-` what a wierd way to name a file right? Since the file name starts with a dash , typing `cat -` won’t work because the terminal interprets it as an option. So I specified the full path to the file as `cat ./-` and boom the password fo the next level is desplayed.
