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
#### test_argparse.py
```python
import argparse

##################  output  #####################

# PS E:\python3> python test_argparse.py --help
# test start
# usage: test_argparse.py [-h] [--dir1 DIR1] [--dir2 DIR2] [--a A] [--b B]

# parser test

# optional arguments:
#   -h, --help   show this help message and exit
#   --dir1 DIR1  help for --dir1
#   --dir2 DIR2
#   --a A
#   --b B
##################################################
def parser_args():
    parser = argparse.ArgumentParser(description='parser test')
    parser.add_argument('--dir1', type=str, default='./data', help='help for --dir1')
    parser.add_argument('--dir2', type=str, default='helloworld')
    parser.add_argument('--a', type=int, default=0)
    parser.add_argument('--b', type=int, default=0)


    return parser.parse_args()

def ab(a, b):
    return a*b


if __name__=='__main__':
    print('test start')
    args = parser_args()
    print(args.dir1)
    print(args.dir2)
    print(ab(args.a, args.b))
```

#### training scripts
I want to do 2 4-hours experiments in a row when I sleep.  
I try to use subprocess to do this. If there is any other method, I will update when I found them.  

