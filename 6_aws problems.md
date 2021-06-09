aws problems  
---  
## let's start  
[labwiki/aws](https://github.com/mti-lab/wiki/wiki/aws)  
[labwiki/ec2](https://github.com/mti-lab/wiki/wiki/ec2)  
[labwiki/s3](https://github.com/mti-lab/wiki/wiki/s3)

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
