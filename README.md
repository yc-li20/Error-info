# Llama

error when setting 4bit or 8bit=True after pip install bitsandbytes:
```
AttributeError: 'NoneType' object has no attribute 'cquantize_blockwise_fp16_fp4'
```
solution:
```
1. pip install accelerate
2. conda install cudatoolkit -- make sure it is installed in the env you are using.
3. cd ....../site-packages/bitsandbytes -- where the bitsandbytes is installed
4. cp libbitsandbytes_cuda122.so libbitsandbytes_cpu.so -- replace the _cpu.so with the cuda.so of your current cuda version. Then delete all cuda.so files with higher version. e.g., if your cuda version is 12.2, then delete 12.3, 12.4, etc.
5. export LD_LIBRARY_PATH="/afs/inf.ed.ac.uk/user/s20/s2057508/miniconda3/envs/yuanchao/lib:$LD_LIBRARY_PATH" in ~/.bashrc -- modiy the path to your own env path.
6. pip uninstall torchvision torch
7. pip install torchvision torch
```
references:
```
https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g/discussions/11
https://blog.csdn.net/weixin_40959890/article/details/130064103
https://blog.csdn.net/GXG_boss6/article/details/138379394
https://github.com/TimDettmers/bitsandbytes/issues/156
https://github.com/pyg-team/pytorch_geometric/issues/2040
https://github.com/TimDettmers/bitsandbytes/issues/914
https://github.com/TimDettmers/bitsandbytes/issues/1093
https://stackoverflow.com/questions/13428910/how-to-set-the-environment-variable-ld-library-path-in-linux
https://www.reddit.com/r/StableDiffusion/comments/16tny9z/kohyass_error_latest_ubuntu/
```

# Transformer

error:
```
ERROR: cannot import name 'AdapterType'
```
solution:
```
pip install adapter-transformers
```


# Python

error:
```
ERROR: Could not build wheels for psutil, which is required to install pyproject.toml-based projects
when doing "pip3 install notebook"
```
solution:
```
First, pip3 install wheel
Then, pip3 install --upgrade setuptools
```

error:
```
内核版本不对
```
solution:
```
https://blog.csdn.net/gdkyxy2013/article/details/88539171
```

# GPU server

error:
```
pip install package, no permission
```
solution:
```
pip install --user package, to install on home directory
```

error:
```
/lib64/libm.so.6: version `GLIBC_2.27' not found```
```

solution:
```
使用新的libm.so.6文件，重定位。
然后export LD_LIBRARY_PATH=$HOME/Documents/libm:$LD_LIBRARY_PATH
```

# librosa

error:
```
pyin function generates nan in f0
```
solution:
```
改用yin function，因为pyin会对unvoiced部分pad nan
```

error:
```
Could not find a `llvm-config` binary
```
solution:
```
pip install --upgrade pip 升级pip
```


# decomposition.PCA

error:
```
Input contains NaN, infinity or a value too large for dtype('float64')
```
solution:
```
1. 检查序列中是否有NaN值: print(np.isnan(spt_A).any())
2. 多半由于对0进行了处理, 所以想办法去掉0
```

# Biosppy

error:
```
ufunc 'multiply' did not contain a loop with signature matching types (dtype('<U12'), dtype('<U12')) -> dtype('<U12')
```
solution:
```
U32是长度为32个字节的无符号整数类型，需要转换为float格式
```

# Wav2vec

# MSE Loss

error:
```
loss or tensor为nan
```
solution:
```
normalization的时候给std加一个非常小的余项。比如：std + 0.01，避免数据中出现0，导致除以0出现nan
```

# Matplot

error:
```
不显示图像
```
solution:
```
更换后端：
import matplotlib
matplotlib.use('TkAgg')
import matplotlib.pyplot as plt
```
error:
```
plt.show()报错：
Process finished with exit code 139 (interrupted by signal 11: SIGSEGV)
```
solution:
```
升级matplot
```

# T-SNE

error:
```
fit.transform时报错：TypeError: delayed() got an unexpected keyword argument 'check_pickle'
```
solution:
```
降级pip install joblib==0.17.0
https://github.com/scikit-learn-contrib/hdbscan/pull/438
```
