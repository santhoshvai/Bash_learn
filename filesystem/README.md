# Filesystem

![unix filesystem](http://i.imgur.com/wtOjv51.png)

## Whats where?

- `/dev`: Hardware devices can be accessed here - usually you dont mess with this stuff
- `/lib`: Stores libraries, along with `/usr/lib`, `/usr/local/lib`, etc.
- `/mnt`: Frequently used to mount disk drives
- `/usr`: Mostly user-installed programs and their related files
- `/etc`: System-wide settings

### Whats where: Programs edition

Programs are usually installed in one of the "binaries" directories:
- `/bin`: System programs
- `/usr/bin`: Most user programs
- `/usr/local/bin`: A few other user programs

### Home sweet home

```
/home/username
``` 

- Can be accessed using `~`

## pwd

**print working directory**

```
pwd
```

- prints the full path of directory
- Handy when you get lost
- Important variable for scripts

## ls

```
ls [flags] [file]
```

- Lists directory contents (including subdirectories)
- Works like the dir command from DOS
- Options
  - `-l` : lists detailed file/directory information 
  - `-a` : lists hidden files

## cd

**change directory**

```
cd [directory name]
```

- changes directory to [directory name]
- If not given a destination defaults to the user’s home directory
- takes both absolute (cd /home/user1/cs2043) and relative (cd cs2043) paths.

- Absolute path
  - location of a file or folder starting at /
- Relative Path
  - location of a file or folder beginning at the current directory

**Shortcuts:**
- `∼` - current user’s home directory
- `.` - the current directory (is useful I promise!)
- `..` - the parent directory of the current directory

## touch

The easiest way to create an empty file is touch

```
touch [flags] <file>
```

- Adjusts the timestamp of the specified file
- With no flags uses the current date/time
- If the file does not exist, touch creates it

> File extensions (.exe, .txt, etc) often don’t matter in UNIX. Using touch to create a file results in a blank plain-text file (so you don’t need to add .txt to it).

## mkdir

**Creating a new directory**

```
mkdir [flags] <directory>
```

- Makes a new directory with the specified names
- Can use relative/absolute paths to make directories outside the current directory

## rm

**file deletion**

```
rm [flags] <filename>
```

- Removes the file called `<filename>`
- Using wildcards you can remove multiple files
  - `rm *` - removes every file in the current directory
  - `rm *.jpg` - removes every .jpg file in the current directory
- `rm -i filename` - prompt before deletion

## rmdir

**Remove Directory**

```
rmdir [flags] <directory>
```
- removes a **empty** directory
- Throws an error if the directory is not empty

**To delete a directory and all its subdirectories we pass rm the flag -r (for recursive)**

```
rm -r /home/user1/oldstuff
```

## cp

```
cp [flags] <file> <destination>
```

- Copies a file from one location to another
- To copy multiple files you can use wildcards (such as *)
- To copy a complete directory use cp -r <src> <dest>
- `cp *.mp3 /Music/` - copies all .mp3 files from the current directory to /home/<username>/Music/

## mv

- Unlike cp, the move command automatically recurses for directories

```
mv [flags] <source> <destination>
```

- Moves a file or directory from one place to another
- Also used for **renaming**, just move from <oldname> to <newname>

## About flags

Most commands take flags (also called options). These usually come before any targets and begin with a -.

- One Option
```
ls -l
```
- Two Options
```
ls -l -a
```
- Two Options
```
ls -la
```
- Applies options left to right
  - rm -fi file ⇒ prompts
  - rm -if file ⇒ does not prompt

## Reading files

Often we only want to see what is in a file without opening it for editing.

**Print a file to the screen**

```
cat <filename>
```

- Prints the contents of the file to the terminal window

```
cat <filename1> <filename2>
```

- Prints the first file then the second which is what it is really for

**More**

```
more <filename>
```

- allows you to scroll through the file 1 page at a time

**Less**

```
less <filename>
```

- Lets you scroll up and down by pages or lines

### Beginning and End
Sometimes you only want to see the beginning of a file (maybe read a header) or the end of a file (see the last few lines of a log).

**Head and Tail**

```
head -[numlines] <filename>
tail -[numlines] <filename>
```

  - Prints the first/last numlines of the file
  - Default is 10 lines

**Example**

```
tail /var/log/Xorg.0.log
```

  - Prints the last ten lines of the log file.

## Note - printing to the terminal

```
echo <text_string>
```

- Prints the input string to the standard output (the terminal)
  - echo This is a string
  - echo ’This is a string’
  - echo "This is a string"
**all print the same thing**

## Link Files
we can create links to files and directories.
- There are two types of links, hard links and symbolic links.

```
ln [options] <target file> [link_name]
```

- Creates a link to <target file> at [link_name], defaulting to the current directory
- The link points to the same file on the system i.e. the link is indistinguishable from the original file
- In other words both the original file and the link both point to the same underlying object

### Symbolic link

```
ln -s <target_file> [link_name]
```

- Creates a symbolic link to the target file or directory
- The link file contains a string that is the pathname of the original file or directory
- In other words the symbolic link points to the other file
