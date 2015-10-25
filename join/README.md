# join

```
join [options] file1 file2
```

## Options
- `-1 field`: join by the field-th field of file 1
- `-2 field`: join by the field-th field of file 2
- `-a file_number`: displays unpaired lines of file file_number

## Examples
- `join age.txt salaries.txt`
```
Bob 30 129,000
Charlie 23 75,000
```
- `join -a1 age.txt salaries.txt`
```
Alice 12
Bob 30 129,000
Charlie 23 75,000
```
