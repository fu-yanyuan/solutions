rclone to sync files from diff. cloud storage
----

### problem  
I have some data on server. But use ssh to download them are quit slow, about 20kb/s. 
So I want a way to save them on my Google drive from server and download from Google drive would be faster.  

### [rclone](https://rclone.org/)  

>  Rclone is a command line program to sync files and directories to and from
> 
> Google Drive
> Amazon S3
> Openstack Swift / Rackspace cloud files / Memset Memstore
> Dropbox
> Google Cloud Storage
> The local filesystem


#### install  
In short: `sudo apt install rclone -y`  
check: `rclone --version`  
[Install](https://rclone.org/install/)  

#### configuration  
run `rclone config` to create a new remote location for google drive  
follow this [Youtube video](https://www.youtube.com/watch?v=f8K-V3HHDA0)  
or refer to [here](https://medium.com/@houlahop/rclone-how-to-copy-files-from-a-servers-filesystem-to-google-drive-aaf21c615c5d)  
or [here](https://rclone.org/drive/)

#### some basic operations  
```
rclone ls Gdrive:
rclone mkdir Gdrive:/backup
rclone copy ./all_results.zip Gdrive:/backup
```  
from commands above, I check my google drive on server, and make a filefolder /backup, and upload my results to that folder.  
then, I download my results quickly 

find more in [how to use rclone](https://snapshooter.com/learn/linux/install-and-use-rclone#how-to-use-rclone)  




