# 数据说明

## 来源

| 项目 | 内容 |
| --- | --- |
| 数据集名称 | E-Commerce Orders Dataset 2026 |
| 发布平台 | Kaggle（公开数据集） |
| 页面地址 | https://www.kaggle.com/datasets/mmumairkhattak/e-commerce-orders-dataset-2026-scra |
| 文件 | `ecommerce_orders_dataset.csv` |
| 规模 | 30,000 行 × 41 列 |
| 数据性质 | 公开的模拟/合成电商订单数据，不含真实用户个人信息 |

## 为什么不把数据放进仓库

- 原始 CSV 约 7.4 MB、清洗后 CSV 约 9.6 MB，属于可再生的派生产物；
- 数据版权归 Kaggle 数据集发布方，重新分发需遵守其页面上的原始条款。

因此仓库只保留**字段字典**（`data_dictionary.csv`）与**清洗日志**（`cleaning_log.csv`），
数据文件本身请在本地自行下载。

## 本地数据准备（二选一）

### 方案 A：从 Kaggle 下载（推荐）

1. 打开上表中的 Kaggle 数据集页面，下载 `ecommerce_orders_dataset.csv`；
2. 放到本仓库的 `data/` 目录下：

```text
data/
├── ecommerce_orders_dataset.csv    # 原始数据（需自行下载，已被 .gitignore 忽略）
├── ecommerce_orders_cleaned.csv    # 清洗产物（由 01 号 notebook 生成）
├── data_dictionary.csv
└── cleaning_log.csv
```

### 方案 B：直接运行清洗脚本

若已按方案 A 放好原始数据，直接执行 `notebooks/01_data_cleaning.ipynb`，
会重新生成 `ecommerce_orders_cleaned.csv` 与 `cleaning_log.csv`。

> 注意：01 号 notebook 中"未来日期"以运行当天为截止日，
> 因此不同日期运行得到的行数会有差异（原始分析在 2026-11 运行，产出 28,953 行）。

## 字段字典

`data_dictionary.csv` 记录 41 个原始字段的英文名与含义。
清洗后新增 20 个字段（异常标记、截尾值、衍生特征），命名规则见 `notebooks/01_data_cleaning.ipynb` 第 21 节。

## 使用声明

- 本仓库的代码与文档未附加开源许可证，默认保留所有权利，转载或复用前请联系作者；
- 数据集版权归原始发布方，使用时请遵循其 Kaggle 页面声明的许可条款；
- 分析结论基于该数据集的生成方式，不代表真实电商业务规律（其局限已在 EDA 报告第 25 章说明）。
