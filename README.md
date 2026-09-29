# 显卡选型参考 · GPU Selection Reference

中文 | [English](#english)

一份**自包含、可离线打开**的显卡选型参考。三个 HTML 页面，双击即用，不需要联网、不需要装任何东西。

---

## 这是什么

| 文件 | 内容 | 适合看什么 |
|---|---|---|
| [`gpu-ladder.html`](gpu-ladder.html) | 性能天梯图 | 91 款显卡的相对性能排行，一眼看出"哪张比哪张强多少" |
| [`gpu-database.html`](gpu-database.html) | 全型号品牌数据库 | 具体买哪张。91 款芯片 × 24 个品牌 = 1962 条在售 SKU 的参数、供电、风险 |
| [`gpu-overview.html`](gpu-overview.html) | 选型总览（上面两个的合并版） | 想在一页里来回对照时用。两个视图数据互通，点击可互相跳转 |

三个页面内容独立、各自可用。只想要一个的话，下 `gpu-database.html` 就够。

## 数据规模

| 项目 | 数量 |
|---|---|
| 显卡型号（芯片级） | 91 |
| 品牌 SKU（具体在售版本） | 1962 |
| AIB 品牌 | 24 |
| 世代分组 | 13（NVIDIA 6 / AMD 5 / Intel 2） |
| 对比维度 | 34 项 |

基准：**RTX 5070 = 100%**。数据截至 **2026 年 9 月**。

## 主要功能

**筛选与搜索**
- 按世代筛选：NVIDIA 50/40/30/20/16/10 系、AMD 9000/7000/6000/5000/500 系、Intel Arc B/A 系列。下拉框与可多选标签行两种入口，互相同步
- 厂商 / 品牌 / 显存 / 定位档位 / 数据置信度 / 矿卡风险 / 供电制式 多维筛选
- 关键词搜索，支持空格分词（"华硕 5070" 可同时限定品牌与型号）

**对比**
- 「＋ 新建对比」两阶段向导：先选基准卡 A，再勾选 1–5 张对比卡（最多 6 张）
- 独立全屏对比页，34 项逐条对照
- 差异口径可切换：**相对基准 A**（只标出与 A 不同的取值，一眼看出"这张和我要买的差在哪"）或 **任意差异**（各卡不全相同就标出）
- 一键复制为表格（制表符文本，可直接粘进 Excel 自动分列）
- 生成分享链接：`#cmp=…` 形式，发给别人打开就是同一组对比

**阅读辅助**
- 浅色 / 深色主题
- 纹理开关：为色觉障碍读者与黑白打印提供颜色以外的第二编码通道

## 怎么用

下载任意一个 `.html`，双击用浏览器打开即可。**没有任何外部依赖** —— 三个页面都是单文件自包含，所有数据、样式、脚本都内联在里面，断网也能正常用。

放到服务器上分享也可以，直接丢进 Web 目录就行，不需要 Node、Python 或任何运行时。

## 校验文件完整性

本仓库每个发布版本都附 `CHECKSUMS.txt`。想确认下载到的文件有没有被改过：

```bash
shasum -a 256 gpu-database.html
```

把输出和 `CHECKSUMS.txt` 里的对应行比对，一致说明文件未被改动。

## 数据来源与口径

**务必先读这一节再使用数据。** 这个项目的原则是：**能确定的才写，不确定的明确标注**，宁可留空也不编造。

| 数据 | 来源 / 口径 |
|---|---|
| 型号与天梯参数 | 用户提供的《显卡天梯图.csv》 |
| 品牌 × 系列覆盖关系 | 各品牌**官网产品线逐条核验**（25 个品牌、数千款），仍以电商实际在售为准 |
| 技嘉的尺寸/供电/建议电源 | 技嘉官网公开规格 API，588 款完整产品线，**逐条抓取** |
| **尺寸（长×高×厚）** | 按芯片功耗区间**推导的区间值**，不是实测。约 87% 落在 ±10mm 内。装机前请实测机箱限长 |
| **散热方案 / 用料** | 从各**系列描述解析**的结构化字段（方案 / 风扇数 / 均热板 / 背板 / 灯效），**不是逐卡实测** |
| **矿卡概率** | **型号级**评估，依据矿老板历史收购偏好与 2022-09-15 以太坊合并前的时间窗。**非逐卡检测** |
| **炼丹卡（AI 训练）概率** | **型号级**评估，依据近年的扫货事件。非逐卡检测 |
| 生产力度量（星级） | 按大模型推理 / 视频编解码 / 渲染计算三个维度分别评级 |
| **价格** | **本仓库不含价格**。价格波动剧烈，任何静态价格表都会迅速过时，请以电商实时信息为准 |

**数据置信度**分四级，页面上可据此筛选：

| 级别 | 含义 |
|---|---|
| ★ 已核验 | 该「芯片 × 系列」组合经官网完整产品线逐条确认存在 |
| 较高 | 料号格式经官网核实；该系列覆盖此芯片档位 |
| 中 | 已按该品牌官网产品线核验系列名与覆盖范围 |
| 较低 | 档位推定，未经官网证实 |

**已回避的来源**：TechPowerUp（其 `robots.txt` 明确禁止 ClaudeBot 抓取 `/gpu-specs/`）与 ZOL 厂商页（robots 禁止 `/manu_`），均已按要求回避。

## 免责声明

本项目为个人整理的选型参考，**不构成购买建议**。硬件市场、驱动、游戏兼容性与价格都在快速变化，下单前请以厂商官网与电商实时信息为准。

发现数据错误欢迎提 Issue，附上官方来源链接会处理得更快。

## 许可

本项目采用 **[CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)** 许可，详见 [`LICENSE`](LICENSE)。

简单说：

- **可以** 原样转载、收藏、分享链接、自己使用
- **不可以** 改动后发布（修改数据、删除署名、更换配色等）
- **不可以** 用于商业用途
- **必须** 保留署名与本许可声明

---

<a name="english"></a>

# English

A **self-contained, offline-capable** GPU selection reference. Three HTML pages — double-click and use. No internet, no installs.

## What's inside

| File | Contents | Use it for |
|---|---|---|
| [`gpu-ladder.html`](gpu-ladder.html) | Performance ladder | Relative performance ranking of 91 GPUs — see at a glance how much faster one card is than another |
| [`gpu-database.html`](gpu-database.html) | Full model & brand database | Deciding which exact card to buy. 91 chips × 24 brands = 1,962 retail SKUs with specs, power requirements, and risk ratings |
| [`gpu-overview.html`](gpu-overview.html) | Combined view | Both of the above in one page, with data linked between the two views |

Each page works standalone. If you only want one, `gpu-database.html` is the one.

## Scale

| Item | Count |
|---|---|
| GPU models (chip level) | 91 |
| Brand SKUs (specific retail versions) | 1,962 |
| AIB brands | 24 |
| Generation groups | 13 (NVIDIA 6 / AMD 5 / Intel 2) |
| Comparison dimensions | 34 |

Baseline: **RTX 5070 = 100%**. Data as of **September 2026**.

## Features

**Filtering & search**
- Filter by generation: NVIDIA 50/40/30/20/16/10-series, AMD RX 9000/7000/6000/5000/500, Intel Arc B/A. Available as both a dropdown and multi-select chips, kept in sync
- Multi-dimensional filters: vendor / brand / VRAM / positioning tier / data confidence / used-mining risk / power standard
- Keyword search with space-separated terms — `"ASUS 5070"` narrows by brand *and* model at once

**Comparison**
- A two-step wizard: pick a baseline card (A), then check 1–5 more (up to 6 total)
- Dedicated full-screen comparison page with 34 rows
- Switchable diff mode: **relative to baseline A** (highlight only what differs from A — instantly shows how each card differs from the one you're considering) or **any difference** (highlight rows that aren't identical across all cards)
- One-click copy as a table (tab-separated, pastes straight into Excel with columns intact)
- Shareable links — `#cmp=…` URLs reopen the same comparison

**Reading aids**
- Light / dark theme
- Texture toggle: adds a non-colour encoding channel for colour-blind readers and black-and-white printing

## Usage

Download any `.html` file and double-click it. **There are no external dependencies** — each page is a single self-contained file with all data, styles and scripts inlined. It works fully offline.

To publish it, just drop the file into any web directory. No Node, Python, or any runtime required.

## Verifying file integrity

Every release includes `CHECKSUMS.txt`. To confirm the file you downloaded hasn't been altered:

```bash
shasum -a 256 gpu-database.html
```

Compare the output against the matching line in `CHECKSUMS.txt`. A match means the file is unmodified.

## Data sources & methodology

**Please read this section before relying on the data.** The guiding principle is: **state only what can be verified, and label what cannot** — figures are left blank rather than invented.

| Data | Source / method |
|---|---|
| Models & ladder metrics | The user-supplied `显卡天梯图.csv` |
| Brand × series coverage | **Verified line by line** against each brand's official product lineup (25 brands, several thousand products). E-commerce availability still governs |
| Gigabyte dimensions / power / PSU | Gigabyte's public product-spec API, full 588-product lineup, **scraped per product** |
| **Dimensions (L×W×H)** | **Derived ranges**, not measurements. ~87% fall within ±10 mm. Always measure your case clearance before buying |
| **Cooler / build material** | Structured fields **parsed from series descriptions** (cooler type, fan count, vapour chamber, backplate, lighting) — **not measured per card** |
| **Used-mining probability** | **Model-level** assessment based on what miners historically bought, within the window ending at the 2022-09-15 Ethereum Merge. **Not per-card inspection** |
| **AI-training (farmed) probability** | **Model-level** assessment based on recent bulk-buying events. Not per-card inspection |
| Productivity ratings | Rated separately across LLM inference / video codec / rendering |
| **Prices** | **Not included in this repository.** Prices move too fast for any static table; check live retailer listings |

**Data confidence** has four levels, filterable in the UI:

| Level | Meaning |
|---|---|
| ★ Verified | The chip × series combination was confirmed against the brand's complete official lineup |
| High | Part-number format verified against the official site; the series covers this chip tier |
| Medium | Series name and coverage checked against the brand's official lineup |
| Low | Tier inferred, not confirmed against official sources |

**Sources deliberately avoided**: TechPowerUp (`robots.txt` explicitly disallows ClaudeBot from `/gpu-specs/`) and ZOL vendor pages (robots disallows `/manu_`). Both were skipped as required.

## Disclaimer

This is a personal reference project and **does not constitute purchasing advice**. Hardware markets, drivers, game compatibility and prices all change quickly — verify against official vendor sites and live retailer listings before buying.

Data corrections are welcome via Issues; linking an official source gets them resolved fastest.

## License

Licensed under **[CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)**. See [`LICENSE`](LICENSE).

In short:

- **You may** redistribute verbatim, save it, share links, use it yourself
- **You may not** publish modified versions (altered data, removed attribution, recoloured, etc.)
- **You may not** use it commercially
- **You must** keep the attribution and this license notice
