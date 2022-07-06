zsh: command not found: pip
===

I want to check all the installed packages via `pip list`.  
but get `zsh: command not found: pip`.   

refer to [link](https://stackoverflow.com/questions/42870537/zsh-command-cannot-found-pip),  
> Maybe you have installed both python2 and python3. python3 may have been installed later.  
> use `pip3` instead of `pip`

```shell
fu@FUs-MacBook-Air datasets % pip3 -V
pip 22.1.2 from /Users/fu/Library/Python/3.8/lib/python/site-packages/pip (python 3.8)
```
