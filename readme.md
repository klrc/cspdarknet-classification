# yolov8_cspdarknet-detection

## 数据集格式要求
该模型仅针对自行车/电瓶车误检，如有负样本建议在第一阶段训练时加入，不要在这个模型内处理
- mydataset
    - train
        - class1名字
        - class2名字
        - ...
    - val
        - class1名字
        - class2名字
        - ...


## 训练模型
```shell
python trainer.py --device_id cuda \
--batch_size 16 \
--max_epochs 300 \
--ema_enabled \
--wandb_enabled \
--early_stop \
--trainset_path /nfs/datasets/mydataset/train \
--valset_path /nfs/datasets/mydataset/val
```

## 导出模型
```shell
python export.py --weight my_weight.pt --input_shape 1 3 1280 1280 --input_names image --opset_version 13 --enable_onnxsim
```