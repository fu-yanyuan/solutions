 transfer files over ssh via scp  
 -------------------------------   
 
 ## download
 1. a single file: `scp username@servername:/remote_path/filename ~/local_destination`  
 2. a whole directory: `scp -r username@servername:/remote_path/remote_dir/ ~/local_destination`  
   
 ## upload  
 1. a single file: `scp ~/local_path/local_filename username@servername:/remote_path`  
 2. a whole file: `scp  -r ~/local_dir username@servername:/remote_path/remote_di`
 
