import subprocess
---  

### materials
(https://geekflare.com/learn-python-subprocess/)
[每周一个python module](https://github.com/yongxinz/tech-blog/blob/master/python-module/%E6%AF%8F%E5%91%A8%E4%B8%80%E4%B8%AA%20Python%20%E6%A8%A1%E5%9D%97%20%20subprocess.md)

#### test
```python
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

