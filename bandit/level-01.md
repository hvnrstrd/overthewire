# Bandit Level 1

## What I needed to do

Find the password for bandit1. Level page said it's in a file called `readme` in the home directory.

## How I solved it

```bash
ls
cat readme
```

Password was just sitting there in a plain text file. That's it.

## Notes

- `ls` lists files in current directory
- `cat filename` prints file content to terminal
- After SSH login you always start in `/home/username`
- `pwd` shows where you are if you get lost

## Thoughts

Plaintext passwords in files = how most credential leaks start.

Real example: dev commits `.env` file with API keys to a public GitHub repo. Bots watch GitHub 24/7 and grab new secrets within seconds. By the time you notice and rotate the key, its already gone.

```bash
# bad
DB_PASSWORD="super_secret_123"

# better
DB_PASSWORD="$DB_PASSWORD"

# best
DB_PASSWORD=$(vault kv get -field=password secret/db)
```