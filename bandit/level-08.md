# Bandit Level 7 -> 8

## What I needed to do

Find the password in `data.txt` next to the word "millionth".

## How I solved it

```bash
grep "millionth" data.txt
```

## Notes

- `grep "word" file` finds all lines containing the word
- `-i` flag for case-insensitive search
- `-n` shows line numbers
- `-P` enables Perl regex, not needed for simple words

## Thoughts

grep is the fastest way to find secrets in large files. In real security work:

```bash
grep -r "password" /etc/ 2>/dev/null
grep -r "api_key" /var/www/ 2>/dev/null
grep -rE "BEGIN (RSA|EC) PRIVATE KEY" / 2>/dev/null
```

Last one finds exposed private keys on the filesystem.