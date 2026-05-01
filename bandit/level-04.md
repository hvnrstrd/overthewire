# Bandit Level 4

## What I needed to do

Find a hidden file in the `inhere` directory.

## How I solved it

```bash
cd inhere
ls -la
cat ...Hiding-From-You
```

Regular `ls` showed nothing. `-la` flags revealed a hidden file starting with dots.

## Notes

- Files starting with `.` are hidden in Linux
- `ls` skips them by default
- `-a` flag shows all files including hidden
- `-l` shows permissions, owner, size, date
- Tab autocomplete works on hidden files even when `ls` does not show them

## Thoughts

Hidden files are not security. Just because `ls` does not show something does not mean it is not there.

```bash
ls        # shows nothing
ls -la    # shows everything

# attackers always run ls -la first
```