# DolphinDB 分钟频量化全流程框架

基于 [DolphinDB](https://www.dolphindb.com/) 构建的分钟频量化研究全流程框架，覆盖从原始行情数据到因子回测的完整链路。

## 项目概览

- **数据层**：基于 TSDB 分区数据库（`cookedDB` / `FactorDB`），从快照（snapshot）数据合成分钟 K 线；
- **因子库**：实现 20 余个高频波动率因子，包括已实现波动率、波动率变化率、量价波动率（VWVOL）、上行/下行波动率及比值、振幅类因子、流动性因子（CVILLIQ），以及 Parkinson、Garman-Klass、Rogers-Satchell、Yang-Zhang、Cho-Free 等增强波动率估计；
- **因子处理**：截面去极值（1%–99% winsorize）+ Z-score 标准化，生成因子暴露表；
- **回测**：按分钟持仓（1–20 分钟）构建 5 分组多空组合，计算 IC / rankIC / IRIC、年化收益、年化波动、夏普比率、最大回撤、胜率等指标，并输出因子绩效表与净值曲线。

## 目录结构

- `DB&TABLE.dos` — 建库建表（分钟 K 线表、因子原始值表、因子暴露表、因子绩效表）
- `min_k_line.dos` — 由快照数据合成分钟 K 线
- `alphadef.dos` — 高频波动率因子定义（20 余个）
- `alphaload.dos` — 因子计算与入库
- `exposure.dos` — 因子去极值 + Z-score 标准化，生成因子暴露
- `backtest.dos` / `test.dos` / `test2.dos` — 单因子回测、IC 检验与绩效指标计算
- `报告/` — 项目报告（LaTeX / PDF / Word）、回测图表与绩效数据

## 说明

本项目为 DolphinDB 组织的量化实战项目（2025.09 – 2026.02）。
