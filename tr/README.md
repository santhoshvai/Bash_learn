# tr - Translate command

**character manipulation**

```
tr [options] <char_list1> [char_list2]
```

- Translate or delete characters
- char_lists are strings of characters
- By default, searches for characters in char_list1 and replaces them with the ones that occupy the same position in char_list2

## Examples
- `tr ’AEIOU’ ’aeiou’` - changes all capital vowels to lower case vowels
- Let’s delete everything but the numbers from test1.txt, then store them in test2.txt
```
tr -cd ’0-9’ < test1.txt > test2.txt
```
- `echo *` prints everything in the directory, separated by spaces. Let’s separate them by newlines instead:

`echo * | tr ’ ’ ’\n’` – replaces all spaces with newlines

- Let’s print a file in all uppercase:

`tr ’a-z’ ’A-Z’ < test.txt` - prints the contents of text.txt in all caps

## Putting all together
We can put some of these together commands together now to do interesting things.
```
tr ’A-Z ’ ’a-z\n’ < file.txt | sort | uniq -c | sort -rn | head -n 10
```
Read file.txt, convert all letters to lower case, replace spaces with new lines, sort the result, count repeating words, and then sort again in reverse order (printing the most common words first), then display the top 10 entries. This effectively computes the most frequent words in file.txt (without handling punctuation, we’ll deal with that later)

## tr and sets

If the two sets passed to tr are the same length then the first character in the first set is replaced by the first in the second and so on. If the second is shorter than the first, then they are matched and all extra are changed to the last character. If the first is shorter, then only those corresponding characters in the second matter

```
echo "abcdefghijklmnopqrstuvwxyz" | tr ’a-z’ ’a’
aaaaaaaaaaaaaaaaaaaaaaaaaa

echo "abcdefghjiklmnopqrstuvwxyz" | tr ’a-z’ ’wxyz’
wxyzzzzzzzzzzzzzzzzzzzzzzz
```

## Options

- `tr -d <set>` - delete all characters that are in the set
- `tr -c <set1> [set2]` - complements set1 before replacing it with set2


## tr understands POSIX character sets

- [:alnum:] - alphanumeric character sets
- [:alpha:] - alphabetic characters
- [:digit:] - digits
- [:punct:] - punctuation characters
- [:lower:] - lowercase letter
- [:upper:] - uppercase letters
- [:space:] - whitespace characters

### Example
- Lets print a file with all non-letters removed:

`tr -cd ’a-zA-Z’ < somefile` - removes non-letters from somefile

## Substitution cypher
We can use tr to do a simple substitution cypher. Create a text file called ”cypher” with some reordering of the alphabet. Then to encode we would just do

```
tr ’a-z’ ‘cat cypher‘ < file > encodedfile
```

and to decode we would do

```
tr ‘cat cypher‘ ’a-z’ < encodedfile > decodedfile
```

### Note - backticks

Backticks around a command: the shell expands this command and replaces the expression within the backticks (including the backticks) with the expression’s output.

- The command whoami prints the name of the user

```
echo ‘whoami‘
ssh ‘whoami‘@csug01.csuglab.cornell.edu
```