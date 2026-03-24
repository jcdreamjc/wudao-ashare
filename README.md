# Wudao A Share Data · 悟道A股数据套件

A股全能数据套件，26 个实时 API 接口，专为 AI Agent 设计。

覆盖 K 线分时、涨停板梯队、资金流向、龙虎榜、竞价数据、板块轮动、研报热榜等，一个 Key 通用。

## 快速安装

**方式一：一句话安装（推荐）**

把下面这段话发给你的 AI Agent（Cursor / OpenClaw / Claude 等），它会自动完成安装：

```
Install WuDao A-share data skills following https://stock.quicktiny.cn/api/openclaw/skills/wudao-market/skill.md and https://stock.quicktiny.cn/api/openclaw/skills/wudao-limitup/skill.md and https://stock.quicktiny.cn/api/openclaw/skills/wudao-analysis/skill.md and https://stock.quicktiny.cn/api/openclaw/skills/wudao-intel/skill.md
```

**方式二：手动下载**

```bash
# 下载 4 个子技能包到你的 skills 目录
curl -sL -o ~/.openclaw/skills/wudao-market.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-market/skill.md"
curl -sL -o ~/.openclaw/skills/wudao-limitup.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-limitup/skill.md"
curl -sL -o ~/.openclaw/skills/wudao-analysis.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-analysis/skill.md"
curl -sL -o ~/.openclaw/skills/wudao-intel.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-intel/skill.md"
```

**方式三：Cursor 用户**

```bash
# 在项目根目录下
mkdir -p .cursor/skills
curl -sL -o .cursor/skills/wudao-market.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-market/skill.md"
curl -sL -o .cursor/skills/wudao-limitup.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-limitup/skill.md"
curl -sL -o .cursor/skills/wudao-analysis.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-analysis/skill.md"
curl -sL -o .cursor/skills/wudao-intel.md "https://stock.quicktiny.cn/api/openclaw/skills/wudao-intel/skill.md"
```

## 获取 API Key

1. 访问 [stock.quicktiny.cn](https://stock.quicktiny.cn) 注册并登录
2. 进入「开发者 API」页面（`/developer`）
3. 点击「创建密钥」，获取 `lb_` 开头的 API Key
4. 立即复制保存，密钥仅显示一次

```bash
export LB_API_KEY="lb_your_key_here"
export LB_API_BASE="https://stock.quicktiny.cn/api/openclaw"
```

## 4 个技能包 · 26 个接口

### 📈 wudao-market · A股行情数据（6 接口）

| 接口 | 说明 |
|------|------|
| 股票搜索 | 按名称、代码、行业、拼音搜索 |
| K 线数据 | 历史 + 实时合并 K 线 |
| 分时数据 | 分钟级分时行情 |
| 股票排行 | 多维度排行榜（涨幅/跌幅/换手/成交额等） |
| 市场概况 | 每日市场总览数据 |
| 交易日历 | 查询是否为交易日 |

### 🔥 wudao-limitup · A股涨停板（9 接口）

| 接口 | 说明 |
|------|------|
| 涨停梯队 | 连板梯队及每层个股详情 |
| 涨停筛选 | 多维度筛选历史涨停数据 |
| 涨停溢价 | 涨停股次日开盘溢价率分析 |
| 炸板池 | 盘中触及涨停但未封住的股票 |
| 跌停池 | 当前跌停股票列表 |
| 冲刺涨停 | 涨幅接近涨停的股票 |
| 涨跌停统计 | 封板数、炸板率等实时统计 |
| 最强风口 | 按涨停聚集度排名的板块 |
| 封板事件流 | 盘中实时封板/炸板事件，精确到秒 |

### 🔍 wudao-analysis · A股资金分析（6 接口）

| 接口 | 说明 |
|------|------|
| 异动检测 | 个股异常交易行为检测 |
| 资金流向 | 个股/板块/大盘/北向资金流向 |
| 板块轮动 | 板块动量与强度四象限分析 |
| 股票关联 | 基于概念共现的关联股票 |
| 概念排行 | 概念板块排名 |
| 概念成分股 | 概念板块成分股列表 |

### 📰 wudao-intel · A股市场情报（5 接口）

| 接口 | 说明 |
|------|------|
| 智能热榜 | 多平台聚合热点主题 |
| 研报数据 | 券商研报，含评级和目标价 |
| 竞价数据 | 个股集合竞价成交数据（单股/批量/历史） |
| 每日简报 | AI 生成的市场简报 |
| 龙虎榜 | 龙虎榜数据，含买卖营业部明细 |

## 示例

```bash
# 搜索股票
curl -s -H "Authorization: Bearer $LB_API_KEY" "$LB_API_BASE/search?query=茅台"

# 获取 K 线
curl -s -H "Authorization: Bearer $LB_API_KEY" "$LB_API_BASE/kline/600519?days=30"

# 查看涨停梯队
curl -s -H "Authorization: Bearer $LB_API_KEY" "$LB_API_BASE/ladder?date=2026-03-20"

# 查询龙虎榜
curl -s -H "Authorization: Bearer $LB_API_KEY" "$LB_API_BASE/dragon-tiger?date=2026-03-20"

# 查询个股竞价数据
curl -s -H "Authorization: Bearer $LB_API_KEY" "$LB_API_BASE/auction?code=600519"
```

## License

MIT
