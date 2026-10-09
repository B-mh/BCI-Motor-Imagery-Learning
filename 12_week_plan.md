# 12 周详细学习计划 — 运动想象（MI）+ 低成本脑机接口（BCI）

本计划面向“零预算/低预算”学习者，目标是在 12 周内从基础理论出发，最终完成一个可展示的 MI-BCI 最小可行原型（伪实时或模拟设备控制）。每天建议学习时间：45–120 分钟（可根据个人时间调整）。

目录
- 总览与目标
- 周节奏与产出
- 逐周详细任务（Day1..Day7）
- 评估指标与零预算建议
- 快速上手命令与资源

---

## 总览与目标
目标能力：
- 理解运动想象的神经基础与 EEG 表征（ERD/ERS、MRCP）
- 掌握 EEG 信号预处理、特征提取（CSP、band power）、经典 ML 与简单深度学习方法
- 能在公开数据集上实现离线 MI 分类（2 类/3 类）并做离线评估
- 能实现伪实时/实时解码 demo，并将分类结果映射为控制命令（模拟或真实设备）

分阶段：
- 周1–3：理论与环境搭建
- 周4–6：信号处理与特征工程
- 周7–9：离线模型训练与评估
- 周10–11：实时/仿真解码与控制
- 周12：收尾、报告与后续路线

---

## 每周详细任务

### 第 1 周 — 框架与大脑/EEG 基础
目标：熟悉领域与搭建 Python 环境
- Day1：读一篇入门综述，写 200 字理解
- Day2：学习运动皮层与相关脑区，画草图
- Day3：学习 EEG 基本概念（通道、采样、常见频段）
- Day4：安装 Python、Jupyter、MNE 等（pip install mne numpy scipy scikit-learn matplotlib pandas jupyterlab）并初始化仓库
- Day5：完成 Python 基础练习 notebook（数组、绘图）并提交
- Day6：整理术语表（20–30 个词）并上传
- Day7：复盘与周报

产出：术语表、环境说明、基础 notebook

---

### 第 2 周 — MI 机制与数据资源
目标：理解 ERD/ERS、MRCP、收集数据源
- Day1：学习 ERD/ERS（写 300 字笔记）
- Day2：学习 MRCP 与任务时序（准备/想象/休息）
- Day3：整理公开数据集清单（Graz、PhysioNet、BCI Comp）
- Day4：在仓库建立 resources/ 数据集索引
- Day5：学习 EDF/MAT 文件格式，使用 MNE 读取示例
- Day6：在 Colab 上读取并绘图（通道时序）
- Day7：复盘

产出：资源清单、MNE 读取示例 notebook

---

### 第 3 周 — 信号处理基础
目标：掌握滤波与时频分析
- Day1：学习带通/陷波滤波理论与代码
- Day2：在合成信号上测试不同滤波器
- Day3：学习傅里叶变换与 Welch PSD
- Day4：在 EEG 示例上绘制 PSD，定位 μ/β 带
- Day5：实现短时傅里叶或小波时频图
- Day6：写周报，总结滤波参数与注意点
- Day7：休整

产出：信号处理 notebook（滤波、PSD、时频图）

---

### 第 4 周 — EEG 预处理与伪迹去除
目标：掌握 ICA、伪迹识别与处理
- Day1：了解常见伪迹（眼电 EOG、肌电 EMG、运动伪迹）
- Day2：用 MNE 实现带通 + 陷波过滤
- Day3：学习并实践 ICA 去伪迹（标注与移除分量）
- Day4：比较手动与 ICA 效果
- Day5：将预处理步骤封装为 preprocessing.py
- Day6：写周报并更新 README
- Day7：休整

产出：预处理脚本与清洗流程文档

---

### 第 5 周 — 特征工程基础
目标：实现 band power、时域特征、滑动窗口特征
- Day1：实现频带功率（band power）函数
- Day2：实现滑动窗口特征提取
- Day3：实现时域特征（方差、RMS、AR 系数）
- Day4：比较不同特征的区分能力
- Day5：封装 features.py
- Day6：写周报
- Day7：休整

产出：特征提取模块与对比分析

---

### 第 6 周 — CSP 与经典机器学习
目标：实现 CSP + LDA/SVM，完成离线小实验
- Day1：学习 CSP 原理
- Day2：用 MNE/sklearn 实现 CSP（选择 n_components=4）
- Day3：训练 LDA/SVM 并在公开数据集上运行 2 类实验
- Day4：交叉验证、混淆矩阵、可视化
- Day5：撰写实验报告（accuracy、混淆矩阵、参数）
- Day6：把代码加入仓库
- Day7：休整

产出：CSP+LDA/SVM 实验 notebook 与报告

---

### 第 7 周 — 模型稳健性与跨会话问题
目标：参数调优、会话内自适应、跨被试思考
- Day1：学习标准化、正则化与特征选择
- Day2：比较不同窗口长度与滤波参数
- Day3：实现简单的会话内自适应（滑动均值更新）
- Day4：在另一个被试数据上测试泛化性能
- Day5：记录性能陷阱与解决方案
- Day6：提交中期总结到仓库
- Day7：休整

产出：鲁棒性笔记与参数对比图

---

### 第 8 周 — 深度学习入门（EEGNet/CNN）
目标：理解并实现 EEGNet 或浅层 CNN
- Day1：阅读 EEGNet 论文或教程
- Day2：在 Colab 上实现或复用 EEGNet 实现
- Day3：训练小模型（注意过拟合）
- Day4：与传统方法（CSP+LDA）对比
- Day5：若有 GPU，用 Colab 加速并保存模型
- Day6：写周报
- Day7：休整

产出：EEGNet 实验 notebook 与模型（小）

---

### 第 9 周 — 离线完整项目整合
目标：完成一套可复现的离线 pipeline
- Day1：选择数据集并设计完整实验流程
- Day2：运行从预处理到评估的完整 pipeline
- Day3：绘制 ROC、混淆矩阵、学习曲线
- Day4：对比多种算法（LDA/SVM/EEGNet）
- Day5：撰写实验报告并生成 figures
- Day6：整理项目到仓库（含数据下载说明）
- Day7：复盘

产出：离线项目（pipeline + 报告）

---

### 第 10 周 — 伪实时/在线仿真准备
目标：实现伪实时数据流与解码框架
- Day1：设计实时处理流程（缓冲、滑动窗口、延迟预算）
- Day2：实现伪实时数据流（用离线数据模拟 stream）
- Day3：写实时解码脚本（socket/websocket 或本地管道）
- Day4：设计控制指令映射（左/右/前/后/停止）
- Day5：实现控制端（pygame 或简单 web 前端）显示指令
- Day6：测试并测量端到端延迟
- Day7：复盘

产出：伪实时 demo（脚本 + 演示）

---

### 第 11 周 — 实时控制与反馈优化
目标：实现交互式实时 demo 并优化稳定性
- Day1：在本地运行实时 pipeline（模拟设备或虚拟机器人）
- Day2：加入视觉/听觉反馈
- Day3：实现预测平滑/投票机制提升稳定性
- Day4：记录多次实验的稳定性数据
- Day5：整理 Demo 为可运行脚本并写使用说明
- Day6：制作演示 GIF 或短视频并上传
- Day7：复盘

产出：实时 demo、演示视频、延迟/准确率记录

---

### 第 12 周 — 项目收尾与后续规划
目标：整理项目、写最终报告与后续 3–6 个月计划
- Day1：整理 notebooks、代码与数据说明
- Day2：撰写最终 README（动机、方法、结果、如何复现）
- Day3：制定无预算硬件计划（如何借设备、二手、社区资源）
- Day4：列出未来 3–6 个月扩展路线（多模态、迁移学习等）
- Day5：自我评估并写改进清单
- Day6：在仓库创建 Release 并写总结博文草稿
- Day7：复盘并庆祝

产出：最终项目仓库、README、未来路线文档

---

## 评估指标
- 周度目标：每周完成并上传至少一个 notebook、脚本或报告
- 性能目标（离线）：
  - Week6: CSP+LDA 在所选数据集上准确率目标 ≈ 70%（视数据集与被试而定）
  - Week9: 完整项目达到基线或接近公开基线
- 实时延迟目标：Week10–11 端到端延迟 < 1s（伪实时可放宽至 1–3s）

---

## 零预算建议
- 优先使用公开数据集与开源软件，不急于购买硬件
- 计算资源：Google Colab（免费 GPU）
- 存储/协作：GitHub（仓库）、Google Drive（大数据临时存储）
- 借设备：联系高校/研究所/校内实验室或社区（OpenBCI 社区）

---

## 快速上手命令示例
环境安装（本地或 Colab）：
```
pip install mne numpy scipy scikit-learn matplotlib pandas jupyterlab
```
MNE 读取 EDF 示例：
```
import mne
raw = mne.io.read_raw_edf('file.edf', preload=True)
raw.filter(8, 30)
epochs = mne.make_fixed_length_epochs(raw, duration=2.0, overlap=0.5)
```
CSP + LDA 伪代码：
```
from mne.decoding import CSP
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis as LDA
from sklearn.pipeline import Pipeline
pipeline = Pipeline([('csp', CSP(n_components=4)), ('lda', LDA())])
pipeline.fit(X_train, y_train)
score = pipeline.score(X_test, y_test)
```

---

如果你同意，我可以：
1) 将本文件再另存为 README.md（覆盖或补充），
2) 创建一个带有模板 notebook 的 examples/ 目录（包含信号处理、CSP+LDA 示例），
3) 或按照你的偏好调整计划的强度（每天时间、目标准确率）。

祝学习顺利！如果需要，我可以继续把示例 notebook 推送到仓库里。
