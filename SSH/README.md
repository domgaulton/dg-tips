# SSH

## Overview
https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html#SetupanSSHkey-ssh2

### Creating a key
* run `ssh-keygen` in terminal
* enter x2 to keep default and passcode can be blank
* see keys `ls ~/.ssh` in terminal which show as - `id_rsa id_rsa.pub` .pub is public and id_rsa is private DO NOT SHARE!

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