# Bandit Level 3

## What I needed to do

Read a file with spaces in the name: `--spaces in this filename--`

## How I solved it

```bash
cat ./"--spaces in this filename--"
```

Quotes keep the spaces as one argument. `./` handles the leading dashes so cat does not read them as flags.

## Notes

- Spaces in filenames split into separate arguments without quotes
- Single quotes work too: `cat './--spaces in this filename--'`
- Tab autocomplete handles this automatically, just type `cat ./--` and hit Tab
- `--` also works: `cat -- "--spaces in this filename--"`

## Thoughts

Unquoted variables in scripts break the same way.

```bash
file="my report.pdf"

cp $file /backup
# cp: cannot stat 'my': No such file or directory

cp "$file" /backup
# works
```

Always quote your variables. `shellcheck` will yell at you if you forget.