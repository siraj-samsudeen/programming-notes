# Jupyter Notebook

## Linux Command Line

### How to pass a python variable as an argument to a bash program?

I tried to do this and it did not work. 

```bash
folder1 = 'Dec&Nov_19_20_RCN_RRPL/RCN/'
%ls folder1 
```

{% embed url="https://stackoverflow.com/questions/35497069/passing-ipython-variables-as-arguments-to-bash-commands/35497161" %}

There are 2 options:

1. Use a $ prefix. 
2. Use {} syntax - this works well if you want to concatenate 2 strings to form the file path whereas $ would NOT work. So, this is better 

When I tried both the options, I still got an error. As suggested

```bash
folder1 = 'Dec&Nov_19_20_RCN_RRPL/RCN'
%ls -lh $folder1

/bin/sh: Nov_19_20_RCN_RRPL/RCN: No such file or directory

%ls -lh "$folder1"
%ls -lh "{folder1}"
```

This means that the & symbol is interpreted in some way cutting off the part of the folder-name before that. So, If I use double-quotes, it works. So, use double-quotes if there are spaces or any other special characters that can break the command line arguments. 

### When to use a raw string format when passing arguments to shell commands?

{% embed url="https://stackoverflow.com/questions/61606054/passing-ipython-variables-as-string-arguments-to-shell-command" %}
