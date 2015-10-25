# grep

```
grep <string> [file]
```

- searches file for all lines containing <string>
- grep stands for global / regular expression / print

## Options
- `grep -i` - ignores case
- `grep -A 20 -B 10` - prints the 10 lines before and 20 lines after each match
- `grep -v` - inverts the match
- `grep -o` - shows only the matched substring
- `grep -n` - displays the line number

## Examples
- `grep password file`

prints all lines that contain the word password in the file file.

- What lines contain the word monster in Frankenstein?
```
grep ’monster’ Frankenstein.txt
```
- `grep "chromium" /var/log/dpkg.log`

Shows when I have updated chromium-browser
- `history | grep grep`

When have I used grep recently?

- `grep -v # bashscript`

Prints all noncommented lines