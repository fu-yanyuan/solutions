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
when i clicked the [download link](http://www.vision.caltech.edu/Image_Datasets/Caltech101/101_ObjectCategories.tar.gz on the website), 
it turned to a [google drive](https://drive.google.com/file/d/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp/view)  
so i want to [download google drive files using wget](https://medium.com/@acpanjan/download-google-drive-files-using-wget-3c2c025a8b99)  

1. find the **FILEID** in the link: `https://drive.google.com/file/d/`**137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp**`/view`  
2. find the **FILENAME** : **101_ObjectCategories.tar.gz**  
3. command  
    + for small file(less than 100MB) run following command on your terminal:  
    `wget --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O FILENAME`  
    + for lagre file run the following command:  
    ```wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=FILEID" -O FILENAME && rm -rf /tmp/cookies.txt```   
    (this works well on Ubuntu, but not windows powershell)  
### result  
```
$ wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp" -O 101_ObjectCategories.tar.gz && rm -rf /tmp/cookies.txt--2021-06-03 22:50:51--  https://docs.google.com/uc?export=download&confirm=xdIv&id=137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp
docs.google.com (docs.google.com) をDNSに問いあわせています... 142.250.196.142, 2404:6800:4004:822::200e
docs.google.com (docs.google.com)|142.250.196.142|:443 に接続しています... 接続しました。
HTTP による接続要求を送信しました、応答を待っています... 302 Moved Temporarily
場所: https://doc-0k-7c-docs.googleusercontent.com/docs/securesc/vnid2rufopp0t4os83q6p369v2m1t0ce/36ptrneil3j5v1pb0c2hrvcov6f8mrd8/1622728200000/15424859768005087218/03482403324059924682Z/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp?e=download [続く]
--2021-06-03 22:50:51--  https://doc-0k-7c-docs.googleusercontent.com/docs/securesc/vnid2rufopp0t4os83q6p369v2m1t0ce/36ptrneil3j5v1pb0c2hrvcov6f8mrd8/1622728200000/15424859768005087218/03482403324059924682Z/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp?e=download
doc-0k-7c-docs.googleusercontent.com (doc-0k-7c-docs.googleusercontent.com) をDNSに問いあわせています... 172.217.25.65, 2404:6800:4004:818::2001
doc-0k-7c-docs.googleusercontent.com (doc-0k-7c-docs.googleusercontent.com)|172.217.25.65|:443 に接続しています... 接続しました。
HTTP による接続要求を送信しました、応答を待っています... 302 Found
場所: https://docs.google.com/nonceSigner?nonce=gstcmj3vq93m6&continue=https://doc-0k-7c-docs.googleusercontent.com/docs/securesc/vnid2rufopp0t4os83q6p369v2m1t0ce/36ptrneil3j5v1pb0c2hrvcov6f8mrd8/1622728200000/15424859768005087218/03482403324059924682Z/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp?e%3Ddownload&hash=u4ajl4u2o8pubbb7sf6an0bi9ts26eak [続く]
--2021-06-03 22:50:53--  https://docs.google.com/nonceSigner?nonce=gstcmj3vq93m6&continue=https://doc-0k-7c-docs.googleusercontent.com/docs/securesc/vnid2rufopp0t4os83q6p369v2m1t0ce/36ptrneil3j5v1pb0c2hrvcov6f8mrd8/1622728200000/15424859768005087218/03482403324059924682Z/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp?e%3Ddownload&hash=u4ajl4u2o8pubbb7sf6an0bi9ts26eak
docs.google.com (docs.google.com)|142.250.196.142|:443 に接続しています... 接続しました。
HTTP による接続要求を送信しました、応答を待っています... 302 Found
場所: https://doc-0k-7c-docs.googleusercontent.com/docs/securesc/vnid2rufopp0t4os83q6p369v2m1t0ce/36ptrneil3j5v1pb0c2hrvcov6f8mrd8/1622728200000/15424859768005087218/03482403324059924682Z/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp?e=download&nonce=gstcmj3vq93m6&user=03482403324059924682Z&hash=jecn1pd4odraa3ebhuh5ijjfjigti32u [続く]
--2021-06-03 22:50:53--  https://doc-0k-7c-docs.googleusercontent.com/docs/securesc/vnid2rufopp0t4os83q6p369v2m1t0ce/36ptrneil3j5v1pb0c2hrvcov6f8mrd8/1622728200000/15424859768005087218/03482403324059924682Z/137RyRjvTBkBiIfeYBNZBtViDHQ6_Ewsp?e=download&nonce=gstcmj3vq93m6&user=03482403324059924682Z&hash=jecn1pd4odraa3ebhuh5ijjfjigti32u
doc-0k-7c-docs.googleusercontent.com (doc-0k-7c-docs.googleusercontent.com)|172.217.25.65|:443 に接続しています... 接続しました。
HTTP による接続要求を送信しました、応答を待っています... 200 OK
長さ: 特定できません [application/x-gzip]
`101_ObjectCategories.tar.gz' に保存中

101_ObjectCategories.tar.gz     [           <=>                           ] 125.64M  42.1MB/s    in 3.0s    

2021-06-03 22:50:57 (42.1 MB/s) - `101_ObjectCategories.tar.gz' へ保存終了 [131740031]
```  

## Downloading Tools  
[5 Linux Command Line Based Tools for Downloading Files and Browsing Websites](https://www.tecmint.com/linux-command-line-tools-for-downloading-files/)  
[2 种从 Linux 终端下载文件的方法 | Linux 中国](https://zhuanlan.zhihu.com/p/268529000)  

## [unzip a .tar.gz file](https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file)  
`tar xf 101_ObjectCategories.tar.gz`  
`tar xf 101_ObjectCategories.tar.gz -C directory_you_want`  



