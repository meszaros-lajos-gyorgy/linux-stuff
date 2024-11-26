# Adding a / after symlink directories when tab completing

https://unix.stackexchange.com/a/291725/506762

**step 1**: Add this to `~/.bashrc`

```sh
# symlink directories not getting / on first try when tab completed
# source: https://unix.stackexchange.com/a/291725/506762
export INPUTRC=~/.inputrc
```

**step 2**: Create `~/.inputrc` with the following content

```sh
set mark-symlinked-directories on
```
