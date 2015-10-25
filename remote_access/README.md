# Remote Access

## ssh

- You can use “secure shell” (ssh) to connect to a remote machine.
```
ssh [username@]<remote machine name or IP address>
```

- If the username is omitted, local username will be used.
- Remote machine has to be configured to accept ssh connections:
  - `ssh daemon` (service) has to be running and listening on an open port (by default 22)

### Executing remote commands

- ssh can be used to execute commands on the remote machine

```
ssh ha232@csug01.csuglab.cornell.edu ls
```

- this will execute ls on csug01.csuglab.cornell.edu and output the result to the screen before ssh terminates the connection
  - the `-f` flag puts ssh into the background before executing the remote command
  - the `-Y` or `-X` (interactive) flags forward X11 (graphical user interface) to the local machine

**Run firefox on the remote machine**

```
ssh -Y ha232@csug01.csuglab.cornell.edu firefox
```

### Identity files

- An identity file authenticates with the remote machine instead of using your username/password.
- Allows you to authenticate yourself with a “pass phrase” (which could be empty).
- Consists typically of a pair of public/private keys used for asymmetric key cryptography (e.g., RSA).

- If you don’t want to type your password every time.

**create identity files**

```
ssh-keygen -t dsa
```

- Append the generated public key file (by default ~/.ssh/id_rsa.pub) to the ~/.ssh/authorized_keys file on the remote machine.
### ssh configuration file

- If you don’t want to set the corresponding flags every time, use the ssh config file `~/.ssh/config`.

**Sample config**

```
host office
hostname mishmish.cs.cornell.edu
host tiger
hostname tiger.cs.cornell.edu
user Alice
ForwardX11 yes
IdentityFile ~/.ssh/id_rsa
```

- Here, `ssh office` connects to `mishmish.cs.cornell.edu`
- `ssh tiger` connects to `tiger.cs.cornell.edu` with username Alice and identity ~/.ssh/id_rsa and enable X11 forwarding.

## scp - secure copy

- Copy files securely over a network using an encrypted ssh transport.

- copy file to remote machine
  - `scp file [username]@remote machine:`
- copy file from remote machine
  - `scp [username]@remote machine:file .`

- The ’:’ is necessary after the remote machine name. A path on the remote machine starting from the user’s home directory can be specified after the colon ’:’.

- copy directories using the -r flag
  - `scp -r pics/ remote machine:`

## wget

```
wget [OPTIONS] [URL...]
```

- Download a file from a remote location over HTTP. Popular options:
  - `-r` : recursive
  - `-l[number]` : how many levels to descend when following links
  - `-c` : continue a partial download

## curl

```
curl [OPTIONS] [URL...]
```

- Transfer data from/to web servers.