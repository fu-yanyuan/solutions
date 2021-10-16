AssertionError: Torch not compiled with CUDA enabled
---  

### the problem 
```python
import torch
print(torch.__version__)
print(rorch.cuda.is_available()) # False
```  

### how to check CUDA version  
1. 
```
nvidia-smi

Sat Oct 16 13:24:38 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 450.119.03   Driver Version: 450.119.03   CUDA Version: 11.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Tesla V100-SXM2...  On   | 00000000:00:1E.0 Off |                    0 |
| N/A   34C    P0    24W / 300W |      0MiB / 16160MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```  
2.  
```
nvcc -v

nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2018 NVIDIA Corporation
Built on Sat_Aug_25_21:08:01_CDT_2018
Cuda compilation tools, release 10.0, V10.0.130
```  
3.  
```
cat /usr/local/cuda/version.txt

CUDA Version 10.0.130
```

we can see that method 1 shows a different CUDA version (11.0) with 2 and 3's CUDA version (10.0.130)  
that's the difference of driver API and runtime API. we should refer to the runtime API, which is the result of method 2 and method 3.  

### 
