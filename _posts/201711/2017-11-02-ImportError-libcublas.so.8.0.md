---
layout: post

title: "ImportError: libcublas.so.8.0: cannot open shared object file: No such file or directory"
date: 2017-11-02 23:53:34 +0800

categories: post
tags: [python, 问题集]
---

>环境配置
```
ubuntu 17.04
Python 3.5.3
```

<mark>问题描述</mark>

已经安装了 `caffe-cuda`, `libcaffe-cuda-dev`, `libcudart8.0`, `nvidia-cuda-dev` 包,但是还是报错.

```bash
$ python3 /path/to/test.py
Traceback (most recent call last):
  File "/usr/local/lib/python3.5/dist-packages/tensorflow/python/pywrap_tensorflow.py", line 58, in <module>
    from tensorflow.python.pywrap_tensorflow_internal import *
  File "/usr/local/lib/python3.5/dist-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 28, in <module>
    _pywrap_tensorflow_internal = swig_import_helper()
  File "/usr/local/lib/python3.5/dist-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 24, in swig_import_helper
    _mod = imp.load_module('_pywrap_tensorflow_internal', fp, pathname, description)
  File "/usr/lib/python3.5/imp.py", line 242, in load_module
    return load_dynamic(name, filename, file)
  File "/usr/lib/python3.5/imp.py", line 342, in load_dynamic
    return _load(spec)
ImportError: libcublas.so.8.0: cannot open shared object file: No such file or directory

Failed to load the native TensorFlow runtime.

See https://www.tensorflow.org/install/install_sources#common_installation_problems

for some common reasons and solutions.  Include the entire stack trace
above this error message when asking for help.
```

也安装了 `python3-pycuda` , `python3-pycuda-dbg` 但是还是不可以.

<mark>解决方法</mark>

需要安装 `cuda` 和 `cudnn`.

下载`CUDA Toolkit`, 以及 `NVIDIA cuDNN` 并安装.

---

如果发生 `ImportError: libcudnn.so.6: cannot open shared object file: No such file or directory` 错误, 则需要 下载安装`cudnn` (需要**注册**)


---
### 更多阅读
- [CUDA Toolkit Download](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1704&target_type=debnetwork)
- [NVIDIA cuDNN](https://developer.nvidia.com/cudnn)
