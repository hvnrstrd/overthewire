# Bandit Level 5

## What I needed to do

Find the only human-readable file among many files in `inhere` directory.

## How I solved it

```bash
find ./ -type f | xargs file | grep text
cat ./"-file07"
```

`file` command checks what type each file actually is. `grep text` filters only ASCII/text files.

## Notes

- `file filename` shows real file type, not just extension
- `xargs` passes output of one command as arguments to another
- `find ./ -type f` lists all regular files recursively
- Combining them: find files, check types, filter results

## Thoughts

File extensions lie. A file named `photo.jpg` can actually be a shell script.

```bash
file photo.jpg
# photo.jpg: Bourne-Again shell script, ASCII text executable

# always check real type before executing anything
file suspicious_binary
```

This is why `file` command matters in security work.