# Basic Calculator

```
bc
```

- Performs arithmetic and logical calculations

## Options
- -l field: increase the precision to 20 decimal places (default 0)

## Examples
- `echo "1/3" | bc`
```
0
```
- `echo "1/3" | bc -l`
```
0.33333333333333333333
```
- `echo "1>3" | bc -l`
```
0
```
- `echo "1<3" | bc -l`
```
1
```
