### 查看当前使用的 Python 环境
```python
import sys
print(sys.executable)
```
### 查看显卡使用情况
```SHELL
watch -n 10 nvidia-smi 
```


### 使用的 PyTorch 版本及 GPU 情况
```PYTHON
import torch
print(torch.__version__)
print(torch.cuda.is_available())
print(torch.cuda.device_count())
print(torch.cuda.get_device_name(0))
print(torch.cuda.current_device())
```
### 使用的 Tensorflow 版本及 GPU 情况
```PYTHON
import tensorflow as tf 
tf.test.is_gpu_available()
tf.config.list_physical_devices('GPU') # TF2

model.summary()
```

- 指定运行设备并打印运行信息
```python
import sys
import numpy as np
import tensorflow as tf
from datetime import datetime

sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))

shape = (1500, 1500)

#device_name = "/gpu:0"
device_name = "/cpu:0"


with tf.device(device_name):
    random_matrix = tf.random_uniform(shape=shape,seed=2)
    dot_operation = tf.matmul(random_matrix, tf.transpose(random_matrix))
    sum_operation = tf.reduce_sum(dot_operation)


startTime = datetime.now()
with tf.Session(config=tf.ConfigProto(log_device_placement=True)) as session:
        result = session.run(sum_operation)
        print(result)

# It can be hard to see the results on the terminal with lots of output -- add some newlines to improve readability.
print("\n" * 5)
print("Shape:", shape, "Device:", device_name)
print("Time taken:", datetime.now() - startTime)

print("\n" * 5)
```

### 字体
https://www.jetbrains.com/lp/mono/
https://fengtalk.com/227.html
https://blog.csdn.net/qq_31061615/article/details/104751496
> 在VSCode首选项中找到文本编辑器/字体/。
在控制字体系列。下方的输入框中输入或粘贴'JetBrains Mono', 。
同时，可以点击配置字体连字。下方的在 Settings.json 中编辑来编辑settings.son文件。
 "editor.fontLigatures": true,

### Jupyter
```SHELL
conda activate heqin
jupyter notebook --no-browser
```

### GIT
[初次配置](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

```shell
git config --global user.name "HeQin_dell"
git config --global user.email Will.He@outlook.com
```


### Python 库安装
```SHELL
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple
```


### conda 环境管理
删除未使用的的包
```SHELL
conda clean -a
conda clean -p
```
创建一个新的环境
```SHELL
conda create -n heqin

conda activate heqin
conda update -n base -c defaults conda

conda install ipykernel
python -m ipykernel install --name heqin
```

通常自己安装的话需要安装的
```
conda install numpy
conda install scikit-learn
conda install tensorflow-gpu
conda install pytorch torchvision cudatoolkit=10.1 -c pytorch
pip install fastai
pip install xgboost
pip install shapely
pip install proplot
pip install salem
pip install netCDF4
pip install descartes
conda install -c conda-forge gdal
conda install -c conda-forge rioxarray
```

环境备份  
[导出环境/导入环境](https://blog.csdn.net/shunaoxi2313/article/details/92003710)
```shell
d:
conda activate heqin
conda env export > conda_heqin.yaml
conda env create -f conda_heqin.yaml

pip freeze > pip_heqin.txt
pip install -r pip_heqin.txt

conda create -n new_name --clone base
conda remove -n new_name --all
```


### gdal环境问题
> ERROR 4: Unable to open EPSG support file gcs.csv 问题

[快速解决方案](https://blog.csdn.net/csdn_xuebing/java/article/details/88421708)  
将`gata-data`文件夹拷贝到`D:\RDP\Anaconda3\envs\heqin\Lib\site-packages\GDAL-2.3.3-py3.7-win-amd64.egg-info`  
此外注意`import rioxarray`前`import gdal`,否则就得把gdal放入环境变量

### shapely环境问题
> OSError: Could not find lib geos_c.dll or load any of its variants ['D:\\RDP\\Anaconda3\\envs\\heqin\\Library\\lib\\geos_c.dll'].  

将`D:\RDP\Anaconda3\envs\heqin\Lib\site-packages\shapely\DLLs`下的文件拷贝到`D:\RDP\Anaconda3\envs\heqin\Library\lib` 
