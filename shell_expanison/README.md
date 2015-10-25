The following are special characters:

```
$ * < > & ? { } [ ]
```

- The shell interprets them in a special way unless we escape (\$) or place them in quotes “$”.
- When we first invoke a command, the shell first translates it from a string of characters to a UNIX command that it understands.
- A shell’s ability to interpret and expand commands is one of the powers of shell scripting

`* ^ ? { } [ ]` Are all “wildcard” characters that the shell uses to match:
  - Any string
  - A single character
  - A phrase
  - A restricted set of characters

The shell’s ability to interpret and expand commands is one of the powers of shell scripting

## *

`*` matches any string, including the null string (i.e. 0 or more characters).

| Input       | Matched                       | Not matched  |
|-------------|-------------------------------|--------------|
| Lec*        | Lecture1.pdf Lec.avi          | ALecBaldwin/ |
| L\*ure*      | Lecture2.pdf Lectures/        | sure.txt     |
| *.tex  tex/ | Lecture1.tex Presentation.tex | tex/         |

## ?

`?` matches a single character

| Input         | Matched                   | Not matched   |
|---------------|---------------------------|---------------|
| Lecture?.pdf  | Lecture1.pdf Lecture2.pdf | Lecture11.pdf |
| ca?           | cat can cap               | ca cake       |

## [...]

- `[...]` matches any character inside the square brackets
  - Use a dash to indicate a range of characters
  - Can put commas between characters/ranges

| Input              | Matched           | Not matched    |
|--------------------|-------------------|----------------|
| [SL]ec*            | Lecture Section   | Vector.tex     |
| Day[1-4].pdf       | Day1.pdf Day2.pdf | Day5.pdf       |
| [A-Z,a-z][0-9].mp3 | A9.mp3 z4.mp3     | Bz2.mp3 9a.mp3 |

## [^...]

`[^...]` matches any character not inside the square brackets

| Input    | Matched                | Not Matched |
|----------|------------------------|-------------|
|[^A-P]ec* | Section.pdf            | Lecture.pdf |
|[^A-Za-z]*| 9Days.avi .bash_profile| vacation.jpg|

## {...,...}

Brace Expansion: {...,...} matches any phrase inside the comma-separated brackets


|Input| Matched|
|-----|--------|
|{Hello,Goodbye}\ World| Hello World Goodbye World|

**NOTE** : Brace expansion must have a list of patterns to choose from. (i.e. at least two options)

## use them together


| Input | Matched | Not Matched |
|-------|---------|-------------|
| \*i[a-z]e* |gift_ideas profile.doc | DriVer.exe
| [bf][ao][ro].mp?| bar.mp3 foo.mpg | foo.mpeg
