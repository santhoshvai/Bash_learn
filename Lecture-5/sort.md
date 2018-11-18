# sort

- Sorts the lines of a text file alphabetically.

`sort -ru file`

- sorts the file in reverse order and deletes duplicate lines.

`sort -n -k 2 -t : file`

- sorts the file numerically by using the second column, separated by a colon

## Example

Consider a file (numbers.txt) with the numbers 1, 5, 8, 11, 62 each on a separate line, then:

```
$ sort numbers.txt
1
11
5
62
8
```

```
$ sort numbers.txt -n
1
5
8
11
62
```