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
