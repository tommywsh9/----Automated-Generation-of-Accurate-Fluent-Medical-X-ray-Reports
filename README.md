# Automated-Generation-of-Accurate-Fluent-Medical-X-ray-Reports with FFAIR datasets
---

## 代码使用说明
---
- 在使用代码前，请从[百度网盘](https://pan.baidu.com/s/1UquGdAqBjIYl_wyZfZ5ZDw)中下载
```
ffair_annotation_new_labels.json
```
将其放在对应项目目录下/data/FFAIR文件夹中,本项目所有云盘提取码均为2106
### 依赖的环境与python库
---
- py3.7 + pytorch 1.13.1 + CUDA 1.16
- tensorboardX, tqdm, spacy, sklearn, pandas, numpy, matplotlib
- 建議使用anaconda進行項目管理

### 用代码与已经训练好的模型生成报告-part1
---
- Step0:从[百度网盘](https://pan.baidu.com/s/1UquGdAqBjIYl_wyZfZ5ZDw)中下载
```
FFAIR_VisualTransformer_ResNet50_MaxView2_NumLabel113_NoHistory.pt
```
将其放在对应项目目录下/checkpoints文件夹中.这个是已经用ffair眼底数据集训练好的模型
- Step1:将train_full.py中PHASE设置为"INFER"
- Step2:将datasets.py中_getitem_方法img_file的路径设置为自己的输入图片路径
- Step3:运行train_full.py,生成的报告结果在项目文件夹下/outputs文件夹中


### 自己重新训练模型并进行验证-part2
---
- Step0:将train_full.py中PHASE设置为"TRAIN"
- Step1:使用datasets_ffair.py替代datasets.py,并将将datasets.py中_getitem_方法img_file的原本路径
```
img_file = 'X:/BaiduNetdiskDownload/ffa-ir-towards-an-explainable-and-reliable-medical-report-generation-benchmark-1.0.0/ffa-ir-towards-an-explainable-and-reliable-medical-report-generation-benchmark-1.0.0/FFAIR/' + img_files[i]
```
​	中X盘路径改为自己的路径
- Step2:
  - 第一次训练时将train_full.py中RELOAD设置为"FALSE"
  - 后续训练时将train_full.py中RELOAD设置为"TRUE"
- Step3:使用[百度网盘](https://pan.baidu.com/s/1TirpTEbn4SwZ5hkXHUkgVQ)中的数据集进行训练
  - 将下载的数据集文件进行解压
  - 对照Step1路径进行datasets.py的路径更改
- Step4:运行train_full.py,在checkpoints目录下生成模型文件
- Step5:生成报告方法同part2



### 参考文献:
---

1.[[Automated Generation of Accurate & Fluent Medical X-ray Reports - ACL Anthology](https://aclanthology.org/2021.emnlp-main.288/)](https://github.com/ginobilinie/xray_report_generation)