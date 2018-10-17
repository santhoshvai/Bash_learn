# Reusing History

## Bang Operator ( ! )
Use the bang operator ( ! ) to repeat a command from your
history that begins with the characters following it.

### Example

```
hussam@orjwan:∼$ pdflatex lecture3.tex
hussam@orjwan:∼$ !p
hussam@orjwan:∼$ !pdf
```

`!p` and `!pdf` will recall `pdflatex lecture3.tex`

Using `!` can save you many keystrokes when repeating tasks.

## Search

You can search through your command history using the shortcut
`Ctrl + R`:

* Press `Ctrl + R` and type a search string. Matching history
entries will be shown.

* Press `Ctrl + R` again to see other matches.

* If you like an entry, press `ENTER` to re-execute it.

* Press `ESC` to copy the entry to the prompt without executing.

* Press `Ctrl + G` to exit search and go back to an empty
prompt.

### Example

```
(reverse-i-search)‘pd’: pdsh -w node[0-9] -R ssh hostname -i
```

You will not be able to type if there are no matches.