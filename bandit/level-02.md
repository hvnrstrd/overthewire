# Bandit Level 2

## What I needed to do

Read a file called `-` (just a dash) in the home directory.

## How I solved it

```bash
cat ./-
```

`./` makes it a path, not a flag. Without it, `cat -` just waits for keyboard input forever.

## Notes

- `-` in most Unix tools means "read from stdin", not a file
- `./filename` is the safe way to handle files with weird names
- Other ways that work:
  - `cat < -` (redirect from file)
  - `cat "$(pwd)/-"` (full path)
  - `cat -- -` (double dash = end of flags)

## Thoughts

Weird filenames are a real attack vector. A file named `; rm -rf /` has killed plenty of scripts that didn't quote variables.

```bash
filename="my file.txt"

rm $filename
# rm: cannot remove 'my': No such file or directory
# rm: cannot remove 'file.txt': No such file or directory

rm "$filename"
# works
```