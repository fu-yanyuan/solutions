pytorch runtimeerror
---

```
RuntimeError: one of the variables needed for gradient computation has been modified by an inplace operation: 
[torch.cuda.FloatTensor [4, 512, 16, 16]], which is output 0 of ConstantPadNdBackward, is at version 1; expected version 0 instead. 
Hint: enable anomaly detection to find the operation that failed to compute its gradient, with torch.autograd.set_detect_anomaly(True). 
```  

to be done  
https://github.com/NVlabs/FUNIT/issues/23  
https://discuss.pytorch.org/t/how-to-debug-gradient-computation-has-been-modified-by-an-inplace-operation-errors/107362  
https://zhuanlan.zhihu.com/p/38475183  
https://www.cnblogs.com/js2hou/p/13923089.html
