# 棉花粉虱检测

棉花粉虱检测模型，在 [YOLOv8s](https://github.com/ultralytics/ultralytics/) 单分类模型的基础上增加了 [Swin-Transformer](https://github.com/microsoft/Swin-Transformer) 和 p2-head

A model for detecing whiteflies on cotton, with [YOLOv8s](https://github.com/ultralytics/ultralytics/) as the base model and [Swin-Transformer](https://github.com/microsoft/Swin-Transformer) and p2-head as the additional components.

## 依赖

* Python 3.9
* [YOLOv8](https://github.com/ultralytics/ultralytics)
* [Swin-Transformer](https://github.com/microsoft/Swin-Transformer)

## 目录结构

* customed
    * `SwinTransformer.py`
    * `yolov8s-customed.yaml`
* `data.yaml`
* `dataset.gz`
* `eval.ipynb`
* `split.ipynb`
* `train.ipynb`

## 应用修改方式

1. 准备 `SwinTransformer.py` 文件
2. 写 `.yaml` 文件
3. 改 `task.py`

### 1. 准备 `SwinTransformer.py` 文件

文件放在 `ultralytics.nn.modules`

### 2. 写 `.yaml` 配置文件

模型的配置文件，随便放哪里，最好是 `.cfg.models.v8` 下

### 3. 修改 `task.py`

导入模块

```Python
from ultralytics.nn.modules (
    AIFI,
    C1,
    ...
    SwinTransformer,
)
```

在 `def parse_model()` 中加入

```Python
if m in (
    Classify,
    Conv,
    ...
    RepC3,
    SwinTransformer,
)
```

最好在 `__init__.py` 中也改一下

