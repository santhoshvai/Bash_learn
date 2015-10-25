# Redirection

Applications in UNIX are associated with Input/Output (I/O)

Streams:
- #0 : Standard input stream; STDIN (usually keyboard)
- #1 : Standard output stream; STDOUT (usually terminal console)
- #2 : Standard error stream; STDERR (depends on system setting, but usually terminal console)

**UNIX Philosophy**

> In UNIX you will find many tools that specialize in one or a few things, and they do them really well! To get more complex functionality combine one ore more tools by piping or I/O redirection

**To redirect input/Output streams, use one of > >> < Input/Output Streams**

- to redirect standard input, use the < operator

`command < file`

- to redirect standard output, use the > operator

`command > file`

- to redirect standard error, use the > operator and specify the stream by number (2)

`command 2> file`

## Merging streams
- You can combine two streams together by using `2>&1`
- This says: send standard error to where standard output is going.
- Useful for debugging/catching error messages.

## Examples

- Bash processes I/O redirection from left to right, allowing us to do fun things like this:
Let’s delete everything but the numbers from test1.txt, then store them in test2.txt

```
tr -cd ’0-9’ < test1.txt > test2.txt
```

- echo * prints everything in the directory, separated by spaces. Let’s separate them by newlines instead:
```
echo * | tr ’ ’ ’\n’ – replaces all spaces with newlines
```

- Let’s print a file in all uppercase:

`tr ’a-z’ ’A-Z’ < test.txt` - prints the contents of text.txt in all caps

## /dev/null - the black hole

/dev/null is a special file which has the following properties:
- Any user can write to it.
- Anything written to it goes nowhere
- it always reports a successful write.

It works like a black hole for data - you can output to it all day and it will never fill up. Anything you redirect to /dev/null just disappears.

## Dealing with excess output

Many programs output continuously as they run. For example
- ping and play both clutter up the terminal with output even when they are backgrounded.
- The solution is to use output redirection

- `ping google.com > testping.log &`
When you care about a program’s output, redirect it to a log file.

- `play somesong.mp3 > /dev/null &`
If the text output doesn’t matter, redirect it to /dev/null.