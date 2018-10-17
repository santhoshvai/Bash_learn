# Alias

```
alias name=command
```

* The alias allows you to rename or type something simple instead of typing a long command
* You can set an alias for your current session at the command prompt
* To set an alias more permanently add it to your `.bashrc` or `.bash_profile` file in your home directory.

### Examples

```
alias ls=‘ls --color=auto’
alias dc=cd
alias ll="ls -l"
```

* Quotes are necessary if the string being aliased is more than one word
* To see what aliases are active simply type `alias`
* Note: If you are poking around in `.bashrc` you should know that any line that starts with # is commented out.