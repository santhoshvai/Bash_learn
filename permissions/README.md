# Permissions

Unix was designed to allow multiple people to use the same machine at once. This raises some security issues - How do we keep our coworkers from reading our email, browsing our documents and changing/deleting programs and files while I’m using them?

- Access to files depends on the users account
- All accounts are presided over by the Superuser, or ”root” account
- Each user has absolute control over any files he/she owns, which can only be superseded by root.

## Group Theory

- Files can also be assigned to groups of users, allowing reading, modifications and/or execution to be restricted to a subset of users

> If each member of a class had an account on the same server, it would be wise to their assignments private (user based). However, if we had a class wiki hosted on the server, it would be advantageous to allow everyone in the class to edit it, but no one outside of the class.

- Each file is assigned to a single user and a single group (usually written user:group).
- For example Alice’s files belong to `alice:users`, and roots files belong to `root:root`.
- Needs root privilege to change file ownership — a regular user can’t take ownership of someone else’s files and can’t pass ownership of their files to another user or a group they don’t belong to.
- To see what groups you belong to type groups or id.

## Discovering permissions

```
ls -l - lists files and directories in the long format
```

- Example

```
-rw-r--r-- 1 hussam users 3775 2009-08-17 15:52 index.html
```

## Cracking the format

![permissions](http://i.imgur.com/cLNMCxL.png)

- R = Read, W = Write, X = Execute
- Directory Permissions begin with a d instead of a -

**What permissions would -rw-rw-r-- mean?**

- User and group can read and write the file while everyone else can just read i

## changing permissions

```
chmod <mode> <file>
```

- Changes file/directory permissions based on <mode>
- The format of <mode> is a combination of 3 fields:
  - Who is affected - a combination of u, g, o, or a (all)
  - Whether adding or removing permissions - + or -
  - Which permissions are being added/removed -any combination of r, w, x.

**Examples**

- `chmod ug+rx myfile` : adds read and execute permissions for user and group.
- `chmod a-r myfile` : remove read access for everyone
- `chmod ugo-rwx myfile` : removes all permissions from myfile

**Convenience**

- Think of r, w, and x as binary variables:
  - 1 ON
  - 0 OFF

**Examples**
```
chmod 755 : rwxr-xr-x
chmod 600 : rw-------
chmod 777 : rwxrwxrwx
```

## Changing Ownership

If you want to change the group a file you have ownership of, you use the following

**Change Group**

`chgrp group <target>`

- Changes the group ownership of file <target>

If you have root access and you want to change who owns a file you use

**Change Ownership**

`chown user:group <target>`

- changes ownership of file <target>
- group is optional
- use the flag ”-R” to do a recursive change to a directory and the files within

**Recursion**

Most commands (for which it makes sense) have a recursive option.
This is used to act on every file in every subdirectory of the target
- Usually -r or -R option (check manpage)

```
chmod -R o-w ∼/Documents/
```
- removes write privileges for other uses for every file and every directory in `∼/Documents/`

## Default permission

This command affects the permission of all files you create (during this session).

```
umask mode
```
- Removes mode from the file’s permission.

Umask is the last-stage filter that strips away permissions as a file or directory is created where the bit is set to ”1”

- `umask 077` : full access to user, no access to everyone else
- `umask g+w` : alternative notation: enables the group to have write permission
- `umask -S` : displays mask in symbolic notation