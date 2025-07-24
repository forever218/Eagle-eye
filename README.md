
# 🦅 鹰眼：智慧畜牧巡检系统  
> 基于无人机载多模态融合增强与文心大模型的智能化解决方案

[![License](https://img.shields.io/github/license/forever218/Eagle-eye?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/forever218/Eagle-eye?style=flat-square)](https://github.com/forever218/Eagle-eye/stargazers)
[![Issues](https://img.shields.io/github/issues/forever218/Eagle-eye?style=flat-square)](https://github.com/forever218/Eagle-eye/issues)



## 📌 项目简介

**“鹰眼”**是一套集成了**无人机巡检系统**、**多模态感知技术**与**大语言模型智能分析**的智慧畜牧解决方案。该系统可实现对牧场环境和牲畜状态的**高效监控**与**自动化分析**，显著提升畜牧业管理的智能化与自动化水平。

> 🧠 本项目融合了计算机视觉、遥感图像处理、LLM 智能问答、多模态数据融合、语义分析、目标检测等前沿技术。

| 功能点/创新点               | 技术应用                                      | 进展     |
|----------------------------|-----------------------------------------------|----------|
| 图像去雾增强               | DCP、CLAHE、Wavelet                           | 已部署   |
| 强度-偏振双模协同          | Stokes Vectors、Laplacian Pyramid             | 已部署   |
| 多相机同步触发与并行采集   | DDS 信号发生器                               | 已部署   |
| 三模态的图像配准           | Lightblue、Superpoint、Rasanc                 | 训练完毕 |
| 偏振-RGB-红外三模态融合    | Swin Transformer                              | 训练中   |



## ✨ 核心功能

- 🚁 **无人机自主巡检**：基于 GPS 路径规划的自动飞行，覆盖牧场全区域。
- 👁 **多模态感知增强**：集成 RGB、热红外、语音、环境传感器等多种传感器。
- 🧮 **智能识别分析**：结合 YOLO 系列模型与文心大模型，实现牲畜计数、行为识别、健康监测等。
- 🌐 **图文语义问答**：通过自然语言与文心对话，支持巡检总结、数据查询等功能。
- 📊 **可视化平台**：提供 Web 可视化面板，实时显示巡检轨迹、识别结果和异常告警。



## 🧠 技术架构

| 模块 | 技术栈 |
|------|--------|
| 无人机平台 | DJI SDK / 自主平台 + ROS |
| 感知算法 | YOLOv8 / 多模态融合 / OpenCV / PaddlePaddle |
| 大语言模型 | 文心大模型（ERNIE-Bot）|
| 后端服务 | Python / FastAPI / Flask |
| 前端展示 | Vue / Echarts / Cesium |
| 数据平台 | MongoDB / InfluxDB / Redis |

---

## 💡 创新点
### 强度-偏振-红外三模态融合的“超视觉”去雾增强
> 本项目突破传统单一模态（如RGB或红外）的去雾增强局限，首次将强度、偏振与红外三种异构信息进行像素级**实时融合**。这不仅解决了恶劣天气下的视觉穿透问题，更创造性地生成了包含多维度物理信息的“超视觉”图像，为后续AI识别提供了前所未有的丰富特征。
 <p align="center">
  <img src="https://github.com/user-attachments/assets/421a513d-b1ab-4c7f-8aa6-6d19282b5f62" alt="image" width="396" height="154" />
</p>
 <p align="center">
<img width="271" height="202" alt="image" src="https://github.com/user-attachments/assets/0f3990c7-4725-47b5-b62e-5c4ca12b8ec0" />
</p>


### 结合国产大模型的领域专用AI认知与决策引擎
> 作品的核心技术创新在于构建了一套结合国产大模型的领域专用AI认知与决策引擎。系统将百度飞桨文心大模型作为技术底座，利用其强大的跨模态理解能力，并结合畜牧业的专业标注数据进行深度领域适配和微调，由此打造的专用认知模型对牲畜的特定行为与生理状态识别精度远超通用方案。
 <p align="center">
 <img width="284" height="183" alt="image" src="https://github.com/user-attachments/assets/3d4627ec-1d67-47c3-a3a2-4c917950d7a5" />
</p>

## ⚒️ 技术实现
> 工业相机拍摄的视频或图片通过软触发和配准之后，将强度、偏振、红外三个变量输入多模态特征融合图像去雾模型，最终输出去雾后的图像。紧接着去雾后的图像输入到系统的认知认知决策引擎——文心一言大模型，通过对大模型进行的一系列训练，最终实现牲畜分类、牲畜标号、牲畜状态监测、牲畜行为预测等一系列功能。
 <p align="center">
<img width="426" height="132" alt="image" src="https://github.com/user-attachments/assets/4b46e818-6273-4297-9f7b-4adf23d7dd5c" />
</p>

### 图像去雾增强算法
> 在暗通道先验（DCP）去雾基础上，通过引入**天空分割算法**优化大气光值估计，并结合**引导滤波细化透射率**以消除伪轮廓；同时融合**CLAHE协同**增强图像对比度，最终采用**小波融合整合**两种算法以保留最多细节。如图所示，（a）有雾原图，（b）为DCP方法去雾效果图，（c）为CLAHE方法去雾效果图，（d）为由我们提出的结合小波融合的去雾算法的去雾效果图。主观观察与客观评价参数均证实，结合小波融合的去雾算法的H和σ2值明显优于其他几种方法，有着最优的去雾效果。
 <p align="center">
<img width="307" height="207" alt="image" src="https://github.com/user-attachments/assets/1599b686-9c76-431a-9097-dab472a5153f" />
</p>

| 方法                         | H    | σ²    | NIQE  |
|------------------------------|------|-------|-------|
| 原始图像                      | 6.90 | 2850  | 5.03  |
| DCP                          | 6.29 | 873   | 4.24  |
| CLAHE                        | 7.24 | 3087  | 4.30  |
| 基于小波域-多尺度的去雾算法    | 7.54 | 4411  | 3.58  |

### 强度-偏振双模协同

> 系统首先通过**多模态相机**获取四个方向（0°、45°、90°、135°）的偏振图像，并计算斯托克斯矢量得到强度分量（S0、S1、S2）和线偏振度（DoLP）图像。DoLP图像揭示了表面材料的偏振特性，系统据此生成偏振细节掩码，用于提取在普通图像中难以察觉的细节信息。随后，通过拉普拉斯金字塔融合算法，将偏振掩码与初步去雾的强度图像进行多尺度融合，得到兼具清晰结构和丰富纹理的双模态融合图像。

<img width="141" height="110" alt="image" src="https://github.com/user-attachments/assets/46a58e98-9eaa-41d4-b330-631dcb12cce3" />

### 三模态的特征提取、特征匹配与配准

> 由于强度是从偏振信息中计算出的，强度和偏振两种模态已经对齐，近红外相机因光学系统设计差异存在空间错位，近红外的视场角更小，若直接融合或分析，会因空间坐标不对应导致特征关联错误。因此需通过配准将强度模态映射至近红外模态的空间坐标系，确保两者在像素级层面的空间一致性。计算流程如下图所示

<img width="366" height="31" alt="image" src="https://github.com/user-attachments/assets/62d4cd43-58a1-4295-b10d-c55e1ed0ad0f" />

### 特征匹配

> 基于 Lightglue 的 Transformer 架构，先通过局部特征距离初步筛选匹配对，再借助自注意力机制建模全局上下文关系，并通过双向校验修正模态差异导致的匹配歧义。匹配结果经可视化保存为匹配效果图，直观呈现跨模态匹配效果。

<img width="215" height="90" alt="image" src="https://github.com/user-attachments/assets/2cb3bf9d-564f-4942-b50d-0259a452fd21" />

## 🔛 快速开始（目标检测）

> 本示例是基于PaddleDetection3.1.0版本实现的ppyoloe网络，在coco数据集进行了训练

### 环境
- PaddleDetection3.1.0
- OS 64位操作系统
- Python 3(3.5.1+/3.6/3.7/3.8/3.9)，64位版本
- pip/pip3(9.0.1+)，64位版本
- CUDA >= 10.1
- cuDNN >= 7.6
- 飞浆AI STUDIO

### 安装（飞浆AI STUDIO）
首先在[AI STUDIO](https://aistudio.baidu.com)新建一个**PaddleDetection3.1.0**框架的项目，启动环境，进入终端：
安装**PaddlePaddle**：
```bash
# CUDA10.2
python -m pip install paddlepaddle-gpu==2.3.2 -i https://pypi.tuna.tsinghua.edu.cn/simple

# CPU
python -m pip install paddlepaddle==2.3.2 -i https://pypi.tuna.tsinghua.edu.cn/simple
```
随后安装**PaddleDetection**：
```
# 克隆PaddleDetection仓库
cd work  # 选择你的工作文件夹，这里我以/work为例
git clone https://github.com/PaddlePaddle/PaddleDetection.git

# 安装其他依赖
cd PaddleDetection
pip install -r requirements.txt

# 编译安装paddledet
python setup.py install
```
***请注意，如果安装PaddleDetection过程由于网络原因报错（大概率遇到），请使用以下命令代替：***
```
cd work
# 替换克隆地址为gitee
git clone https://gitee.com/paddlepaddle/PaddleDetection.git

cd PaddleDetection
# 替换pip install源为清华镜像
pip install lapx -i https://pypi.tuna.tsinghua.edu.cn/simple

# 先行安装motmetrics
pip install motmetrics -i https://pypi.org/simple

# 编译安装paddledet
python setup.py install
```
安装完成后执行测试代码：
```bash
python ppdet/modeling/tests/test_architectures.py
```
若输出以下信息则测试通过：
```
.......
----------------------------------------------------------------------
Ran 7 tests in 12.816s
OK
```
### 数据集准备
数据集来源有很多，可以选择到[roboflow](https://universe.roboflow.com/)上下载对应的格式（例如COCO）数据集，本例使用的数据集为https://universe.roboflow.com/part-iv-project/cow-dataset
下载之后上传至[AI STUDIO](https://aistudio.baidu.com)的文件夹`/home/aistudio/work/PaddleDetection/dataset/coco`下并解压（如果选择COCO数据集的话）

<img width="476" height="562" alt="image" src="https://github.com/user-attachments/assets/185f5f62-9921-4912-a6d8-f5ce3e8ce595" />

当然，也可以选择将数据集先挂载在[AI STUDIO](https://aistudio.baidu.com)的`我的数据集`里，然后在项目中进行引用。


### 训练
修改`/home/aistudio/work/PaddleDetection/configs/datasets/coco_detection.yml`文件为以下内容：
```
metric: COCO
num_classes: 80

TrainDataset:
  name: COCODataSet
  image_dir: train
  anno_path: train/_annotations.coco.json
  dataset_dir: dataset/coco
  data_fields: ['image', 'gt_bbox', 'gt_class', 'is_crowd']

EvalDataset:
  name: COCODataSet
  image_dir: valid
  anno_path: valid/_annotations.coco.json
  dataset_dir: dataset/coco
  allow_empty: true

TestDataset:
  name: ImageFolder
  anno_path: test/_annotations.coco.json # also support txt (like VOC's label_list.txt)
  dataset_dir: dataset/coco # if set, anno_path will be 'dataset_dir/anno_path'
```
修改`/home/aistudio/work/PaddleDetection/configs/ppyoloe/ppyoloe_plus_crn_s_80e_coco.yml`为以下内容：
```
_BASE_: [
  '../datasets/coco_detection.yml',
  '../runtime.yml',
  './_base_/optimizer_80e.yml',
  './_base_/ppyoloe_plus_crn.yml',
  './_base_/ppyoloe_plus_reader.yml',
]

log_iter: 100
snapshot_epoch: 5
weights: output/best_model

pretrain_weights: https://bj.bcebos.com/v1/paddledet/models/pretrained/ppyoloe_crn_s_obj365_pretrained.pdparams
depth_mult: 0.33
width_mult: 0.50
```
执行命令以启动训练(单卡)：
```
export CUDA_VISIBLE_DEVICES=0
python -m paddle.distributed.launch --gpus 0 tools/train.py -c configs/ppyoloe/ppyoloe_plus_crn_s_80e_coco.yml --eval
```
训练完成后结果输出在`output`文件夹：
```
output/
 └── [你的配置名]/
     ├── model.pdparams         <-- 模型参数
     ├── model.pdopt            <-- 优化器状态（可选）
     ├── model.pdmodel          <-- 模型结构（可选）
     └── best_model/            <-- 如果有保存最佳模型
         ├── model.pdparams     <-- 最优模型参数

```
<img width="466" height="217" alt="image" src="https://github.com/user-attachments/assets/9381489e-b9c3-4418-aaec-888ff978e406" />

### 快速推理
使用刚刚训练的模型进行推理：
```
# 在GPU上预测一张图片
export CUDA_VISIBLE_DEVICES=0
# --infer_img=demo/0.jpg只是个例子，它可以是任何正确的图片文件地址，请自行修改
python tools/infer.py -c configs/ppyoloe/ppyoloe_plus_crn_s_80e_coco.yml -o use_gpu=true weights=output/best_model/model.pdparams --infer_img=demo/0.jpg
```
输出的推理结果仍在`output`文件夹，里面的同名文件`0.jpg`便是推理结果。


## 📸 硬件设计

<img width="421" height="130" alt="image" src="https://github.com/user-attachments/assets/e2d89419-8350-4636-941c-15f507b2ac41" />
<img width="190" height="142" alt="image" src="https://github.com/user-attachments/assets/d65bc96b-66af-43c0-93b6-920858676a4c" />

## 软件功能

| 功能模块       | 具体功能点                                               |
|----------------|----------------------------------------------------------|
| 数据获取       | 同步触发、软触发、多线程                                 |
| 图像预处理     | 强度图像去雾、偏振度图像掩码、近红外对比度增强           |
| 模态对齐       | 特征提取、特征匹配、变换估计与配准                       |
| 多模态融合     | 自注意力域内特征提取，跨域注意力域间融合                 |
| 检测模块       | 基于文心大模型实现牲畜的分类、标号、状态检测、行为检测等 |



## 🙌 贡献者 Contributors

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/forever218">
        <img src="https://avatars.githubusercontent.com/forever218" width="80px;" alt="forever218"/>
        <br /><sub><b>forever218</b></sub>
      </a>
      <br />💻 🧠 💡
    </td>
    <td align="center">
      <a href="https://github.com/Albertsaam">
        <img src="https://avatars.githubusercontent.com/Albertsaam" width="80px;" alt="Albertsaam"/>
        <br /><sub><b>Albertsaam</b></sub>
      </a>
      <br />🔍 🛠️ 🎨
    </td>
       <td align="center">
      <a href="https://github.com/Setiawan271">
        <img src="https://avatars.githubusercontent.com/Setiawan271" width="80px;" alt="Albertsaam"/>
        <br /><sub><b>Setiawan271</b></sub>
      </a>
      <br />🔍 🔗 📷
    </td>
  </tr>
</table>

## 🔗 参考链接
[🧃 superpoint提取器](https://github.com/magicleap/SuperPointPretrainedNetwork)  
[🔍 特征匹配器](https://github.com/cvg/LightGlue)  
[🤺 PaddleDetection](https://github.com/PaddlePaddle/PaddleDetection)  
[📚 roboflow数据集](https://universe.roboflow.com/)  
[📕 DeTone D, Malisiewicz T, Rabinovich A. SuperPoint: Self-Supervised Interest Point Detection and Description [EB/OL]. arXiv preprint, 2017-12-20 [2025-07-24].](https://arxiv.org/abs/1712.07629)   
[📕 Lindenberger P, Sarlin P-E, Pollefeys M. LightGlue: Local Feature Matching at Light Speed [EB/OL]. arXiv preprint, 2023-06-23 [2025-07-24].](https://arxiv.org/abs/2306.13643)   
[📕 He K, Sun J, Tang X. Single image haze removal using dark channel prior [C]//2009 IEEE Conference on Computer Vision and Pattern Recognition. Miami, FL, USA: IEEE, 2009.](https://ieeexplore.ieee.org/document/5206515)   
[📕 He K, Sun J, Tang X. Guided Image Filtering [J]. IEEE Transactions on Pattern Analysis and Machine Intelligence, 2013, 35(6): 1397-1409.](https://ieeexplore.ieee.org/document/6319316)   
[📕 Ma J, Tang L, Fan F, et al. SwinFusion: Cross-domain Long-range Learning for General Image Fusion via Swin Transformer [J]. IEEE/CAA Journal of Automatica Sinica, 2022, 9(7): 1200-1217.](https://ieeexplore.ieee.org/document/9812535)   










