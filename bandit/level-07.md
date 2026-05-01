# Bandit Level 6 -> 7

## What I needed to do

Find a file somewhere on the server that is owned by user `bandit7`, group `bandit6`, and is 33 bytes in size.

## How I solved it

```bash
find / -size 33c -user bandit7 -group bandit6 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

## Notes

- `-user username` filters by file owner
- `-group groupname` filters by group
- `2>/dev/null` redirects stderr to nowhere, hides "Permission denied" noise
- searching from `/` means entire filesystem, not just home directory

## Thoughts

`2>/dev/null` is useful but dangerous habit in security scripts. It hides real errors too.

```bash
find / -name "secret" 2>/dev/null
# looks clean, but maybe find itself crashed?

find / -name "secret" 2>errors.log
# better: save errors separately, check later
```