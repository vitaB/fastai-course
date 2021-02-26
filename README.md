# fastai-course
exercises from https://course.fast.ai/


## branch for heroku
`git subtree push --prefix web heroku master`


## emptying GPU memory
```
import torch
import gc;
gc.collect()
torch.cuda.empty_cache()
torch.cuda.memory_allocated()
```

```
!pip install GPUtil
import torch
from GPUtil import showUtilization as gpu_usage

print("Initial GPU Usage")
gpu_usage()                             

tensorList = []
for x in range(10):
  tensorList.append(torch.randn(10000000,10).cuda())   # reduce the size of tensor if you are getting OOM
  
  

print("GPU Usage after allcoating a bunch of Tensors")
gpu_usage()

del tensorList

print("GPU Usage after deleting the Tensors")
gpu_usage()  

print("GPU Usage after emptying the cache")
torch.cuda.empty_cache()
gpu_usage()
```
