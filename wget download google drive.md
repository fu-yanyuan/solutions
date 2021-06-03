download dataset via wget 
-------------------------

# download google drive file using wget on linux server

when i try to download [caltech101 dataset](http://www.vision.caltech.edu/Image_Datasets/Caltech101/) on the server, i typed 
`wget http://www.vision.caltech.edu/Image_Datasets/Caltech101/101_ObjectCategories.tar.gz`

it seems just downloaded a website, although there do has a file named **101_ObjectCategories.tar.gz**
i can not unzip this **.tar.gz** by the way, original file should be 100+M while this one is just 66KB

\```
@:~/VRtraining/PyRetri/data$ ls
101_ObjectCategories.tar.gz  caltech101
@:~/VRtraining/PyRetri/data$ tar xf 101_ObjectCategories.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now
\```

what happend is   
