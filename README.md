# kgx_to_konsole
A bash script that should (In theory) let you replace kgx (gnome-console) with konsole


```
`#!/bin/bash
input_str=$1

arguments="${input_str:10}"

konsole -e $SHELL -c \"$arguments\"

```

this should mean that if an app or process runs `kgx --command=(command)` it will be replaced by `konsole -e $SHELL -c "command"`

I only wrote this today so I have no clue what problems it will cause in the future, but for right now launching .desktop files with `terminal=true` does not work

This can be circumvented by setting `Exec=konsole -e "(exacutable link)"` and `terminal=false`

If anyone knows how the fuck desktop files actually launch the terminal please let me know so I can try to fix this
