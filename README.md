# 精简版NEZHA模型权重

原版NEZHA模型权重保存了Adam优化器的缓存参数，使得体积为默认情况下的3倍。多数情况下，多出来的2倍参数是没有用的，可以去掉。

所以这里提供去掉后的模型权重下载。仅做了删除冗余参数操作，没有对权重数值进行修改，用户可以自行对比结果。

**注：这个精简仅仅是删除开源权重中不必要的优化器参数，并非是蒸馏、剪枝等压缩技术。精简后的模型只是下载体积变小，其余与原模型没有区别。**

## 关于NEZHA

NEZHA是华为开源的中文预训练语言模型，跟BERT的区别是使用了相对位置编码。

https://github.com/huawei-noah/Pretrained-Language-Model/tree/master/NEZHA-TensorFlow

## 下载地址

链接: https://pan.baidu.com/s/1G4GAxoaJ1e9oWPCGN7591Q 提取码: npxf

## 转换代码

基于bert4keras，可以很简单进行转换：
```python
from bert4keras.models import build_transformer_model

config_path = '/root/kg/bert/nezha_base/bert_config.json'
checkpoint_path = '/root/kg/bert/nezha_base/model.ckpt-900000'

bert = build_transformer_model(
    config_path,
    checkpoint_path,
    model='nezha',
    with_mlm=True,
    with_nsp=True,
    return_keras_model=False
)  # 建立模型，加载权重

bert.save_weights_as_checkpoint('nezha/nezha_base/model.ckpt-900000')
```

## 交流反馈

QQ交流群：808623966，微信群请加机器人微信号spaces_ac_cn
