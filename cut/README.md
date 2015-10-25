# Cut
`cut [-b] [-c] [-d delim] [-f list] [-s] [file]`
  - `delim` is a delimiter that separates fields
  - `list` consists of one of N, N-M, N-

## Options
- `-b`: extracts using range of bytes
- `-c`: extracts using range of characters
- `-d`: especifies a delimiter (tab by default)
- `-f`: especifies a range of fields separated by a delimiter
- `-s`: supressses line if delimiter is not found

## Examples

- `cut -d : -f 1 -s employee.txt`: Prints the names
- `cut -d : -f 3,4 -s employee.txt`: Prints the address and the zip code
- `cut -d : -f 2 employee.txt`: Prints phone numbers plus the last line
- `cut -d : -c 1 employee.txt`: Prints their first initial plus the first character of the last line
