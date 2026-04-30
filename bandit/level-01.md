// Bandit Level 1

// What i needed to do

Read a file called `-` (just a dash) in the home directory.

// How I solved it

​```bash
cat ./-
​```

The `./` tells `cat` "this is a path to a file in the current directory", not a flag. The dash is now treated as a filename, not stdin.

// Notes

- `-` as an argument often means stdin in Unix tools
- `./filename` is the safe way to read files with weird names (starting with `-`, special chars, etc.)
- Other ways to do the same thing:
  - `cat < -` (redirect stdin from file)
  - `cat "$(pwd)/-"` (full path)
  - `cat -- -` (some tools accept `--` as "end of flags")