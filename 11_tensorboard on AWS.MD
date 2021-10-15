HOW TO RUN ACCESS TENSORBORAD ON AWS
---  
### on AWS
```python
writer_fake = SummaryWriter(f"logs/fake")
writer_real = SummaryWriter(f"logs/real")
``` 

the images are saved in ./logs  
so, after running train.py on tmux, back to the terminal on AWS and run  
`tensorboard --logdir=logs`  

### on local PC  
run  
`ssh -i .ssh/mtilab-fu.pem -NL 6006:localhost:6006 ubuntu@IP`  

after that we can browse to http://localhost:6006/  


refer to https://stackoverflow.com/questions/42277280/accessing-tensorboard-on-aws
