# Split

`split [options] [file1] [prefix]`

## Options
- `-l`: how many lines in each file
- `-b`: how many bytes in each file
- prefix: name prefix of each file produced

## Examples
- In this simple example, assume myfile is 3,000 lines long:
```
split myfile
```
This will output three 1000-line files: xaa, xab, and xac.

- Working on the same file, this next example is more complex:
```
split -l 500 myfile segment
```
This will output six 500-line files: segmentaa, segmentab, segmentac, segmentad, segmentae, and segmentaf.

- Finally, assume myfile is a 160KB file:
```
split -b 40k myfile segment
```
This will output four 40KB files: segmentaa, segmentab, segmentac, and segmentad.
