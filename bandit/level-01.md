# Bandit Level 1

## What I needed to do

After logging in as bandit0, find the password for bandit1. The level page said it's stored in a file called `readme` in the home directory.

## How I solved it

Once connected via SSH, I just listed the files and read it:

​```bash
ls
cat readme
​```

That was it, the password was sitting there in plaintext.

## Notes

- `ls` shows files in the current directory
- `cat filename` prints the file content to terminal
- The home directory after SSH login is usually `/home/username`, you start there automatically
- `pwd` (print working directory) is useful to confirm where you are

## Thoughts

Plaintext passwords in files = how 99% of credential leaks start.

A classic real-world example: developers accidentally committing `.env` files with API keys to public GitHub repos. Bots scan GitHub for new commits within seconds and grab any exposed credentials. By the time you realize and rotate the key, it's already been used.

```bash
# Bad: secrets in code
DB_PASSWORD="super_secret_123"

# Better: load from env at runtime
DB_PASSWORD="$DB_PASSWORD"

# Best: fetch from a secret manager
DB_PASSWORD=$(vault kv get -field=password secret/db)
```