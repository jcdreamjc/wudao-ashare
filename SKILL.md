---
name: wudao-ashare
version: "1.0.0"
description: "A股全能数据套件，26个实时API接口：K线分时、涨停板梯队、资金流向、龙虎榜、竞价数据、板块轮动、研报热榜等。安装后自动获取4个子技能包，一个Key通用。"
metadata:
  {
    "openclaw":
      {
        "emoji": "📊",
        "requires": { "bins": ["curl"] },
      },
  }
---

# 悟道 · A股全能数据套件

一键安装，获取 A 股短线交易所需的全部数据能力。本 Skill 是 4 个子技能包的**总入口**，共提供 **26 个数据接口**。

## Instructions for the hosting agent（AI 必读）

安装本 Skill 后，**必须立即执行以下步骤安装 4 个子技能包**，否则无法调用任何数据接口：

```bash
# 1. 下载 4 个子技能（请将路径替换为你实际存放 Skill 的目录）
curl -s -o SKILLS_DIR/wudao-market.md "$LB_API_BASE/skills/wudao-market/skill.md"
curl -s -o SKILLS_DIR/wudao-limitup.md "$LB_API_BASE/skills/wudao-limitup/skill.md"
curl -s -o SKILLS_DIR/wudao-analysis.md "$LB_API_BASE/skills/wudao-analysis/skill.md"
curl -s -o SKILLS_DIR/wudao-intel.md "$LB_API_BASE/skills/wudao-intel/skill.md"
```

将 `SKILLS_DIR` 替换为实际路径（如 `~/.openclaw/skills/` 或 `.cursor/skills/`）。

安装完成后，每个子技能文件内都有自己的 **Instructions for the hosting agent**（含版本检查和自动更新机制），请遵照执行。

## 4 个子技能包一览

| 技能包 | 接口数 | 覆盖领域 |
|--------|--------|----------|
| 📈 **wudao-market** · A股行情数据 | 6 | 股票搜索、K线、分时、排行榜、市场概况、交易日历 |
| 🔥 **wudao-limitup** · A股涨停板 | 9 | 涨停梯队、涨停筛选、涨停溢价、炸板池、跌停池、冲刺涨停、涨跌停统计、最强风口、封板事件流 |
| 🔍 **wudao-analysis** · A股资金分析 | 6 | 异动检测、资金流向、板块轮动、股票关联、概念排行、概念成分股 |
| 📰 **wudao-intel** · A股市场情报 | 5 | 智能热榜、研报数据、竞价数据、每日简报、龙虎榜 |

## Setup

### 获取 API Key

1. 访问 [https://stock.quicktiny.cn](https://stock.quicktiny.cn) 注册账号并登录
2. 进入「开发者 API」页面（路径：`/developer`）
3. 点击「创建密钥」，系统会生成一个以 `lb_` 开头的 API Key
4. **立即复制保存**，密钥仅显示一次

### 配置环境变量

```bash
export LB_API_KEY="lb_your_key_here"
export LB_API_BASE="https://stock.quicktiny.cn/api/openclaw"
```

4 个子技能共享同一个 API Key 和 Base URL。

## 版本检查

查询所有子技能的最新版本：

```bash
curl -s "$LB_API_BASE/skills/version"
```

查询单个子技能版本：

```bash
curl -s "$LB_API_BASE/skills/wudao-market/version"
```

## Notes

- 日期格式：同时支持 `YYYY-MM-DD` 和 `YYYYMMDD`
- 股票代码：6 位数字（`600519`）或完整代码（`600519.SH`）
- A 股交易时间：9:25-15:01（北京时间）
- 每个子技能的完整接口文档请参见对应的 Skill 文件
