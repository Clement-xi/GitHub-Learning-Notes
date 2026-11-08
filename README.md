# GitHub Learning Notes

基于公开教材 [ThreshoLdnnis/Quant-for-babies](https://github.com/ThreshoLdnnis/Quant-for-babies) 的个人量化金融学习与代码复现项目。项目目标是通过逐章运行 Notebook，理解行情数据、收益率、趋势策略、风险指标和组合分析。教材原件仅在本地 `materials/` 中作学习参考，不随个人成果仓库发布。

## 学习进度

| 个人章节 | 主题 | 当前状态 |
|---|---|---|
| [Chapter-02](Chapter-02/) | 你的第一个量化实验 | 已完成 AkShare 数据适配并运行；需最终核验输出与补充笔记 |
| [Chapter-03](Chapter-03/) | 移动平均线策略 | 部分单元运行；完整执行与笔记待补 |
| [Chapter-04](Chapter-04/) | 策略回测 | Notebook 已完整执行；AkShare 真实行情，含兼容适配 |
| [Chapter-05](Chapter-05/) | 理解波动率 | 仍待完整运行与笔记 |
| [Chapter-06](Chapter-06/) | 夏普比率与 Beta | 仍待完整运行与笔记 |
| [Chapter-07](Chapter-07/) | 最大回撤与仓位管理 | 仍待完整运行与笔记 |
| [Chapter-08](Chapter-08/) | 多标的组合与相关性 | 仍待完整运行与笔记 |

> 本 README 记录的是当前真实进度，不将部分运行标记为完成。行情数据为 AkShare 新浪财经接口返回的真实历史数据；Yahoo Finance 曾触发限流。各章数据源、区间和复权差异需以对应笔记为准。

## 项目结构

```text
Chapter-02/…Chapter-08/  个人复现 Notebook 与学习笔记
 data/akshare_us/         从 AkShare 获取的真实行情 CSV 缓存（可重新下载）
 requirements.txt         项目 Python 依赖
 materials_download_report.md  原教材文件校验摘要
```

## 环境配置

建议使用 Python 3.11。Windows PowerShell：

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

VS Code 打开项目后选择 `.venv\Scripts\python.exe`，Notebook Kernel 选择 `Python 3.11 (GitHub Learning Notes)`。

## 运行 Notebook

从项目根目录启动 Jupyter：

```powershell
.\.venv\Scripts\Activate.ps1
jupyter lab
```

在浏览器或 VS Code 中打开 `Chapter-XX/code/` 下的个人 Notebook，按单元顺序运行。行情接口需要联网；已缓存的 CSV 位于 `data/akshare_us/`。数据接口可能限流或调整，缓存只代表获取时的历史数据快照，不保证未来数据更新。

## 依赖

见 [requirements.txt](requirements.txt)。本项目仅供学习，不构成投资建议；历史计算结果不代表未来表现。
