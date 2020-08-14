# SSH

## Overview
https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html#SetupanSSHkey-ssh2

### SSH into another machine on network
* Ensure Remote Login is active - To do this System Preferences > Remote Login > tick yes
* Find IP of machine to log into by looking in network preferences e.g. `192.168.0.69.`
* From another machine type `ssh [user]@192.168.0.69.` into terminal where [user] is name of other machine
* To exit type `exit` from terminal

### Creating a key
* run `ssh-keygen` in terminal from `$~` route
* passcode can be blank (press enter twice)
* see keys `ls ~/.ssh` in terminal which show as - `id_rsa id_rsa.pub` .pub is public and id_rsa is private DO NOT SHARE!
* copy public key using `cat ~/.ssh/id_rsa.pub | pbcopy` or `pbcopy < ~/.ssh/id_rsa.pub`

### Add key to ssh-agent
* the following 'eval `ssh-agent`' - expected output Agent pid 9700
* `ssh-add -K ~/.ssh/<private_key_file>` e.g. `ssh-add -K ~/.ssh/id_rsa`
* add or edit config file (use vi if needed)
```
vi ~/.ssh/config
```
* add the following:
```
Host *
  UseKeychain yes
```

* Note: To quit VIM editor see [Terminal VIM](../TERMINAL/README.md#VIM)

### Add key to apps
* Copy and paste using - `pbcopy < ~/.ssh/id_rsa.pub` 