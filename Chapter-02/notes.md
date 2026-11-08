# Chapter-02：你的第一个量化实验

## 学习目标
按教材顺序认识 OHLCV 日线数据、价格图和 OHLC 示意图；理解简单日收益率公式并用 pandas.pct_change() 计算；用收益率曲线、直方图、累计收益率观察 AAPL；最后比较 AAPL、TSLA、NVDA 的日收益率标准差。

## 逐段代码解释

1. **环境准备（代码单元 4）**：导入 warnings、
umpy、pandas、matplotlib.pyplot、yfinance，设置忽略警告和中文绘图字体。Python 的 import 用于引入模块；cParams 是 Matplotlib 的全局绘图配置。
2. **下载 AAPL（单元 6）**：yf.download(..., period='1y') 从 Yahoo Finance 获取近一年日线；dropna() 去掉含缺失值行；shape、head() 和 columns 用于检查表格尺寸、样例和字段。数据字段含 Open、High、Low、Close、Volume。
3. **价格与成交量图（单元 7）**：subplots(2,1) 创建共享横轴的上下图，折线显示收盘价，柱形显示成交量。
4. **OHLC 示意图（单元 8）**：取最后八行，用 iterrows() 逐日取开高低收；竖线表示 Low 到 High，短横线标记 Open/Close；用颜色区分收涨和收跌。
5. **收益率例子（单元 10）**：用 100→110 演示 (今天-昨天)/昨天，格式说明符 :.2% 将小数显示为百分数。
6. **整列收益率（单元 12）**：复制 Close 列，pct_change() 计算相邻交易日百分比变化；首行会是 NaN；再用最后两行手算核对。
7. **收益率曲线与直方图（单元 14）**：删除 NaN 后绘制逐日收益率和分布，输出样本数、均值、标准差。标准差在本章用作波动大小的粗略比较指标。
8. **累计收益率（单元 15）**：(1+rets).cumprod()-1 连乘每日增长因子，形成区间累计涨跌曲线。
9. **三只股票波动对比（单元 17）**：循环下载 AAPL、TSLA、NVDA，计算 Close 日收益率并以 Series 标准差排序。
10. **对比图（单元 18）**：绘制三条收益率时间序列、标准差柱状图，并标出波动最大者。
11. **三只股票直方图（单元 19）**：分别查看日收益率分布和标准差，比较尾部及离散程度。

## 依赖和数据来源
- Python：原 Notebook 元数据记录 Python 3.13.5、Python 3 (ipykernel)；用户环境优先计划使用 Python 3.11，兼容性尚未实测。
- 第三方包：
umpy、pandas、matplotlib、yfinance、ipykernel；Jupyter Notebook/Lab 用于交互执行。warnings、matplotlib.lines.Line2D 属于 Python/Matplotlib 自带接口，不需要额外包。
- 网络数据：yfinance 访问 Yahoo Finance，下载 AAPL、TSLA、NVDA 的 period='1y' 日线。没有外部本地行情文件依赖。当前网络可用性尚未验证。

## 环境与运行记录
- 检查日期：2026-11-05。
- Windows 中未发现 Python：py -0p 返回 No installed Pythons found!，python、python3 不存在。
- winget、Chocolatey、Scoop 均不可用；当前执行环境无法自动安装 Python。
- 因缺少解释器，本地 Notebook 尚未执行；因此本地运行状态、依赖导入和行情 API 连通性均未验证。
- 教材原 Notebook 中已有保存的历史输出（这是教材记录，不是本地复现结果）：AAPL 251 行行情、250 个日收益率；样本平均日收益率 0.167%、标准差 1.428%、区间累计涨跌 48.07%；三股波动排序 TSLA 2.810%、NVDA 2.210%、AAPL 1.429%。实际数值随数据下载时点变化，须在本地重跑核对。

## 教材代码与适配差异
- 复现 Notebook 是从 materials/02_你的第一个量化实验.ipynb 原样复制，未改动源码；原件保留在 materials/。
- 尚未为本地运行做代码适配。环境准备后需先逐单元运行；如出现 API/版本兼容问题，先记录报错再做最小调整并保留原始逻辑。
