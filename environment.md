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



### Python 库安装
```SHELL
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple
```
