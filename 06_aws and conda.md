aws problems  
---  
## let's start  
[labwiki/aws](https://github.com/mti-lab/wiki/wiki/aws)  
[labwiki/ec2](https://github.com/mti-lab/wiki/wiki/ec2)  
[labwiki/s3](https://github.com/mti-lab/wiki/wiki/s3)  
[labwike/policy](https://github.com/mti-lab/wiki/wiki/policy)

## how to get instance id

`$ ec2metadata --instance-id`  
refer to [how-to-get-the-instance-id-from-within-an-ec2-instance](https://stackoverflow.com/questions/625644/how-to-get-the-instance-id-from-within-an-ec2-instance)  

## unable to excute aws command
 
```
PS C:\Users\fredy> aws s3 ls

An HTTP Client raised an unhandled exception: check_hostname requires server_hostname
```  
close VPN proxy  

## scp to ec2 instance without password 

```  
PS C:\Users\f***y> scp ubuntu@ip-172-31-13-105:~/workspace/nerf-pytorch/logs/fern_test/fern_test_spiral_150000_rgb.mp4 E:\NeRF
ssh: Could not resolve hostname ip-172-31-13-105: \262\273\326\252\265\300\325\342\321\371\265\304\326\367\273\372\241\243
PS C:\Users\f***y> scp ubuntu@12.345.678.9:~/workspace/nerf-pytorch/logs/fern_test/fern_test_spiral_150000_rgb.mp4 E:\NeRF    
ubuntu@12.345.678.9: Permission denied (publickey).
PS C:\Users\f***y> scp -i .ssh/mtilab-fu.pem ubuntu@12.345.678.9:~/workspace/nerf-pytorch/logs/fern_test/fern_test_spiral_150000_rgb.mp4 E:\NeRF 
fern_test_spiral_150000_rgb.mp4                                                                                                                  100% 3165KB 283.3KB/s   00:11   
```  
`ubuntu@12.345.678.9` is obtained by  
`aws ec2 describe-instances --instance-ids INSTANCE_ID --query 'Reservations[0].Instances[0].PublicIpAddress'`  

## conda installation  

1. `wget https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh` 
    + find the download link corresponding to the system, python version [here](https://docs.conda.io/en/latest/miniconda.html)
2. `bash Miniconda3-latest-Linux-x86_64.sh` 
    + find the file name from the current directory 
 
#### referrences:  
[install anaconda youtube](https://www.youtube.com/watch?v=0EuDhKXq_aM)  
[installation/uninstallation](https://conda.io/projects/conda/en/latest/user-guide/install/linux.html)  
[AWS EC2: Install Anaconda on Linux Instance](https://medium.com/@GalarnykMichael/aws-ec2-part-3-installing-anaconda-on-ec2-linux-ubuntu-dbef0835818a)  

#### how to use conda  
[conda安装与使用](https://zhuanlan.zhihu.com/p/89356758)  
[conda command](https://blog.csdn.net/menc15/article/details/71477949/)  
[conda 使用](https://www.cnblogs.com/zhangxingcomeon/p/13801554.html)   

## update python2 or miniconda2  
to be done : [upgrade python](https://rajputankit22.medium.com/upgrade-python-2-7-to-3-6-and-3-7-in-ubuntu-97d2727bf911)  
if needed : [from miniconda2 to miniconda3](https://stackoverflow.com/questions/58673299/how-to-migrate-safely-from-miniconda2-to-miniconda3)  

## conda: command not found  
1. open `~/.bashrc`  
2. add ```export PATH=/Users/XXX/opt/anaconda3/bin:$PATH``` to the last line  
3. run `source ~/.bashrc`  
4. check `conda --version` 








