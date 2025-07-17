# Swap Gnome's "KGX" terminal emulator to KDE's "konsole" terminal emulator
A bash script that should (In theory) let you replace kgx (gnome-console) with konsole

To install, replace "/usr/bin/kgx" with a bash file with the same name ("kgx")
Then, paste the following into that bash file:

```
#!/bin/bash
input_str=$1

input_str2="${input_str:0:9}"
argument="${input_str:10}"

echo "$input_str2"

if [ "$input_str2" = "--command" ]
then
	arguments="${input_str:10}"  && konsole -e $SHELL -c \"$arguments\"
else
	konsole --hold -e $SHELL -c "echo 'If an application was meant to launch here, I fucked up -currlyfries'; exec bash"
fi

```

This should mean that if an app or process runs `kgx --command="(command)"` it will be replaced by `konsole -e $SHELL -c "(command)"`



I only wrote this today so I have no clue what problems it will cause in the future, but for right now launching .desktop files with `terminal=true` does not work

This can be circumvented by setting `Exec=konsole -e "(exacutable link)"` and `terminal=false`


If anyone knows how the fuck desktop files actually launch the terminal please let me know so I can try to fix this
