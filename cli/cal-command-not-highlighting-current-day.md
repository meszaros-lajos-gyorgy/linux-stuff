# cal command not highlighting current day on Debian based systems

https://unix.stackexchange.com/a/668030/506762

Add this to `~/.bashrc`

```sh
# fix cal not highlighting current day on debian based systems
# source: https://unix.stackexchange.com/a/668030/506762
alias cal="if [ -t 1 ] ; then ncal -b ; else /usr/bin/cal ; fi"
```
