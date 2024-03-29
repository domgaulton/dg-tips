# Terminal

## Create folder

- `mkdir {folder-name}` - make directory

## Create file

- `touch {filename.type}` - create file

## Change directoy

- `cd {folder}` or `cd ..` - move into another child directory || move up one directory

## Move file(s)

- `mv [file] [directory]` - move file into another directory relative to your own e.g. move file to parent `mv README.md ../`

## Copy file

- `cp example.env .env` - copy `example.env` to same directory and rename as `.env`
- `cp README.md ../TEST/README.md` - copy `README.md` (this file) to same `TEST` directory with the (same) name `README.md`

## Open folder from terminal

- `open .` to open current file in terminal

## Curl

- Used to transfer data from or to a server `curl -F "hello.html=@local.html" "https://USER:PASS@neocities.org/api/upload"`

## VIM

- Quit VIM editor press `esc` then colon `:wq` - Write your file by entering :w and quit by entering :q . You can combine these to save and exit by entering `:wq`

## Hostsfile

- https://www.tekrevue.com/tip/edit-hosts-file-mac-os-x/
- `sudo nano /private/etc/hosts` and enter password
- Where it says `^G` Get Help | `^O` WriteOut| `^R` Read File use `ctrl + G` etc -

## Edit with NANO

- `EDITOR=nano {filename}`
- If this doesn't work you need to install Nano using `apt-get update && apt-get install nano`
