# find

**Searching for files/directories by name or attributes**

- used to locate files or directories
- search any set of directories for files that match a criteria
- search by name, owner, group, type, permissions, last modification date, and other criteria
- search is recursive (will search all subdirectories too)

## Syntax

```
find [where to look] criteria [what to do]
```

## Examples
- display pathnames of all files in current directory and subdirectories
```
find . -print
find -print
find .
```
(all equivalent)
- search for a file by name
```
find . -name my_awesome_file.txt
```
- Find all files accessed at most 10 minutes ago
```
find . -amin -10
```
- Find all files accessed at least 10 minutes ago
```
find . -amin +10
```
- Display all the contents of files accessed in the last 10 minutes
```
find . -amin -10 -exec cat ‘{}’ +
```

## Options
- `-name` : name of file or directory to look for
- `-maxdepth num` : descend at most num levels of directories while searching
- `-mindepth num` : descend at least num levels of directories while searching
- `-amin n` : file last access was n minutes ago
- `-atime n` : file last access was n days ago
- `-group name` : file belongs to group name
- `-path pattern` : file name matches shell pattern pattern
- `-perm mode` : file permission bits are set to mode

## More on find
- normally all modifiers for find are evaluated in conjunction (i.e. AND). We can find files matching a pattern OR another by using the -o flag.
- executes a command on found files by using the -exec command ‘{}’ + flag.
- executes a command on found files by using the -exec command ‘{}’ \; flag.
- The difference between \; and + is that with \; a single grep command for each file is executed whereas with + as many files as possible are given as parameters to grep at once.