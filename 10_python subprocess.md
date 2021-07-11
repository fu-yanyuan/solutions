import subprocess
---  

(https://geekflare.com/learn-python-subprocess/)  

#### test
```
import subprocess

print('test subprocess')

print('#################################')
command1 = ['python', 'test_argparse.py']
subprocess.run(command1)

print('#################################')
command2 = ['python', 'test_argparse.py', '--help']
subprocess.run(command2)

print('#################################')
command3 = ['python', 'test_argparse.py', '--a', '5', '--b', '1']
subprocess.run(command3)

print('#################################')
command4 = ['python', 'test_argparse.py', '--a=6', '--b=2']
subprocess.run(command4)

print('#################################')
command5 = ['python', 'test_argparse.py', '--dir1', 'data']
subprocess.run(command5)

print('#################################')
command6 = ['python', 'test_argparse.py', '--dir1=data']
subprocess.run(command6)
```

#### training scripts
I want to do 2 4-hours experiments in a row when I sleep.  
I try to use subprocess to do this. If there is any other method, I will update when I found them.  

