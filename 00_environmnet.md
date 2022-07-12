### tf  
find the corresponding tf version, python version and cudatoolkit version
https://www.tensorflow.org/install/source#gpu  
change the version below and run it.

```python
# To run: conda env create -f environment.yml
name: env_name
channels:
    - conda-forge
dependencies:
    - python=3.7
    - pip
    - cudatoolkit=10.0
    - tensorflow-gpu==1.15
    - numpy
    - matplotlib
```


#### export environment
BTW, if need to export current env as a .yml
```python
$ conda env export > myenv.yaml
```

### test env
```python
import torch
from torchvision import datasets
from torchvision.transforms import ToTensor

# test pytorch
print(torch.__version__) 

# test CUDA
print(torch.cuda.is_available())

# # test torchvision
# training_data2 = datasets.MNIST(
#     root='data',
#     train=True,
#     download=False,  
#     transform=ToTensor()
# )
```
