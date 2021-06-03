download dataset via wget 
-------------------------

# download google drive file using wget on linux server

## situation  
[a similar case](https://stackoverflow.com/questions/61917838/wget-returns-statuscode-200-but-cant-find-the-file)  
when i try to download [caltech101 dataset](http://www.vision.caltech.edu/Image_Datasets/Caltech101/) on the server, i typed 

`wget http://www.vision.caltech.edu/Image_Datasets/Caltech101/101_ObjectCategories.tar.gz`

it seems just downloaded a website, although there do has a file named **101_ObjectCategories.tar.gz**  
i can not unzip this **.tar.gz** by the way, original file should be 100+M while this one is just 66KB  
```
@:~/VRtraining/PyRetri/data$ ls  
101_ObjectCategories.tar.gz  caltech101  
@:~/VRtraining/PyRetri/data$ tar xf 101_ObjectCategories.tar.gz

gzip: stdin: not in gzip format  
tar: Child returned status 1  
tar: Error is not recoverable: exiting now
```

what happend is, the same as [Souvik's answer](https://stackoverflow.com/questions/39643013/gzip-stdin-not-in-gzip-format-tar-child-returned-status-1-tar-error-is-not-r)  
> This means the file isn't really a gzipped tar file -- or any kind of gzipped file -- in spite of being named like one.  
> 
> When you download a file with wget, check for indications like Length: unspecified [text/html] 
> which shows it is plain text (text) and that it is intended to be interpreted as  
> html. Check the wget output below -
> ...  

## solution  
when i clicked the [download link](http://www.vision.caltech.edu/Image_Datasets/Caltech101/101_ObjectCategories.tar.gz on the website, 
it turned to a [google drive](https://drive.google.com/file/d/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp/view)  
so i want to [download google drive files using wget](https://medium.com/@acpanjan/download-google-drive-files-using-wget-3c2c025a8b99)  

1. find the **FILEID** in the link: https://drive.google.com/file/d/**137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp**/view  
2. find the **FILENAME** : **101_ObjectCategories.tar.gz**  
3. command  
    + for small file(less than 100MB) run following command on your terminal:  
    `wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O FILENAME`  
    + for lagre file run the following command:  
    `wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=FILEID" -O FILENAME && rm -rf /tmp/cookies.txt`
    (this works well on Ubuntu, but not windows powershell)  

## Downloading Tools  
[5 Linux Command Line Based Tools for Downloading Files and Browsing Websites](https://www.tecmint.com/linux-command-line-tools-for-downloading-files/)  
[2 种从 Linux 终端下载文件的方法 | Linux 中国](https://zhuanlan.zhihu.com/p/268529000)  

## [unzip a .tar.gz file](https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file)  
`tar xf 101_ObjectCategories.tar.gz`
`tar xf 101_ObjectCategories.tar.gz -C directory_you_want`  



