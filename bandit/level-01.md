// Bandit Level 1

// What I needed to do

After logging in as bandit0, find the password for bandit1. The level page said it's stored in a file called `readme` in the home directory.

// How I solved it

Once connected via SSH, I just listed the files and read it:

```
ls
cat readme
```

// Notes

- `ls` shows files in the current directory
- `cat filename` prints the file content to terminal
- The home directory after SSH login is usually `/home/username` — you start there automatically
- `pwd` (print working directory) is useful to confirm where you are