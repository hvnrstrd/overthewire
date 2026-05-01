# Bandit Level 5

## What I needed to do

Find a file in `inhere` directory that is human-readable, 1033 bytes in size, and not executable.

## How I solved it

```bash
cd inhere
find . -size 1033c
cat ./maybehere07/.file2
```

`-size 1033c` means exactly 1033 bytes (`c` = bytes in find).

## Notes

- `find -size Nc` searches by exact byte size
- `find -size +Nc` means more than N bytes, `-Nc` means less
- Other useful find flags:
  - `-type f` only regular files
  - `! -executable` not executable
  - `-readable` human-readable
- Full solution with all conditions from the task:

```bash
find . -type f -size 1033c ! -executable
```

## Thoughts

`find` is one of the most powerful tools for security work. Attackers use it to locate sensitive files fast.

```bash
find / -name "*.env" 2>/dev/null
find / -name "id_rsa" 2>/dev/null
find / -perm -4000 2>/dev/null
```

Last one finds SUID binaries, a classic privilege escalation vector.