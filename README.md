# P11_02：心脏病早期风险动态预测

基于 UCI Heart Disease（Cleveland）数据集的心脏病二分类教学项目。项目按照 `P11_01.pdf` 的分析方案完成数据清洗、探索性数据分析、模型训练与解释，并提供可动态输入新病例、现场显示预测概率和分类结果的 Jupyter Notebook。

> 本项目仅用于数据科学教学与研究，不构成医学诊断、治疗建议或临床决策依据。

## 项目功能

- 读取并清洗 Cleveland 数据集，将原始诊断结果转换为二分类目标；
- 通过统计表、分布图、类别患病比例和相关性热图进行探索性数据分析；
- 训练并比较逻辑回归、决策树和随机森林；
- 使用 Accuracy、Sensitivity、Specificity、Precision、F1、ROC-AUC 和 5 折交叉验证评估模型；
- 展示 ROC 曲线、混淆矩阵、置换重要性和逻辑回归标准化系数；
- 通过交互控件输入 13 项医学指标，切换模型及分类阈值，并自动更新预测结果。

## 项目文件

```text
P11_02/
├── P11_心脏病风险动态预测.ipynb  # 已执行的主 Notebook，包含完整结果和交互面板
├── P11_01.pdf                    # 项目分析文档
├── P11题目.png                   # 项目题目
├── heart+disease/                # UCI 原始数据及字段说明
└── README.md
```

## 运行方法

建议使用 Anaconda/Python 环境，所需依赖包括 `numpy`、`pandas`、`matplotlib`、`seaborn`、`scikit-learn`、`ipywidgets` 和 `notebook`。

```bash
python -m pip install numpy pandas matplotlib seaborn scikit-learn ipywidgets notebook
jupyter notebook "P11_心脏病风险动态预测.ipynb"
```

在 Jupyter 中选择 **Kernel → Restart & Run All**，然后滚动到“**6. 动态输入新数据并现场预测**”。修改任一输入后，预测概率和分类结果会自动更新。

请保持 Notebook 与 `heart+disease` 文件夹的相对位置不变。Notebook 已保存执行结果，未安装 Jupyter 时也可以直接在 GitHub 上查看主要分析内容；交互预测需要在本地 Jupyter 环境中运行。

## 数据来源

数据来自 **UCI Machine Learning Repository：Heart Disease**：

- 数据集主页：https://archive.ics.uci.edu/dataset/45/heart-disease
- 本项目使用目录：`heart+disease/`
- 建模文件：`heart+disease/processed.cleveland.data`
- 字段说明：`heart+disease/heart-disease.names`

原始 Cleveland 数据包含 303 条记录和 14 个常用字段。按照项目 PDF 的完整病例分析方案，将 `ca` 和 `thal` 中的 `?` 作为缺失值，并删除含缺失值的 6 条记录，最终使用 297 条记录建模。目标变量中，0 表示无心脏病，1～4 合并表示存在心脏病。

### 原始数据作者与署名

根据 UCI 数据集中的 `heart-disease.names`，原始数据作者及机构为：

- Hungarian Institute of Cardiology, Budapest：Andras Janosi, M.D.
- University Hospital, Zurich, Switzerland：William Steinbrunn, M.D.
- University Hospital, Basel, Switzerland：Matthias Pfisterer, M.D.
- V.A. Medical Center, Long Beach and Cleveland Clinic Foundation：Robert Detrano, M.D., Ph.D.
- 数据捐赠者：David W. Aha

使用或引用该数据集时，请同时保留 UCI 数据来源及上述原始作者署名。

## 模型结果

测试集采用 75%/25% 分层划分，随机种子为 42。主要结果如下：

| 模型 | Accuracy | Sensitivity | Specificity | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| 逻辑回归 | 0.853 | 0.829 | 0.875 | 0.841 | 0.947 |
| 决策树 | 0.693 | 0.657 | 0.725 | 0.667 | 0.736 |
| 随机森林 | 0.827 | 0.771 | 0.875 | 0.806 | 0.934 |

这些结果仅反映当前小型公开数据集上的教学实验表现，不代表模型在其他人群或临床环境中的表现。

## 版权声明

本项目代码、Notebook 分析内容及项目文档：

**Copyright © 2026 LuoTaiyu. All Rights Reserved.**

UCI Heart Disease 数据集、原始字段说明及相关资料的权益归原数据作者、捐赠者、相关机构及原权利人所有，不属于本项目作者。数据的使用、引用和再分发应遵守 UCI 数据集的原始条款与署名要求；本项目的版权声明不替代或限制原始数据的权利与许可条件。

未经相应权利人授权，不得将本项目内容用于违反法律法规、侵犯第三方权益或未经授权的商业用途。
