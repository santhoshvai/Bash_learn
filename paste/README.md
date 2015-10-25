## cut
`paste [options] [file1 ...]`

## Options
- `-d`: specify a delimiter to separates fields (instead of tab)
- `-s`: concatenates serialy instead of side-by-side

## Examples
- `paste names.txt phones.txt`
```
Alice 607-233-2464
Bob 607-257-2884
Charlie 605-987-7886
```
- `paste -d : names.txt phones.txt`
```
Alice:607-233-2464
Bob:607-257-2884
Charlie:605-987-7886
```
- `paste -s names.txt phones.txt`
```
Alice Bob Charlie
607-233-2464 607-257-2884 605-987-7886
```