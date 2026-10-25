# Brand Trend Fit · 品牌与趋势适配

把“热门”变成“对这个产品有用”。一个面向 AI agent 的可复用 skill，源于产品趋势推荐实践，公开版不依赖 GoTrend 的服务器或私有源码。

**产品画像 → 对标品牌／品类／场景种子词 → 获取并核实真实趋势 → 产品关联过滤 → 可解释的场景延伸 → 推荐优先级与偏好加权。**

## 它解决什么问题

| 能力 | 具体行为 |
|---|---|
| 画像与种子词 | 从明确的产品功能生成有依据的种子；不继承对标品牌的能力 |
| 真实来源核实 | 区分地区总榜、筛选榜、帖子搜索与补充证据，保留原名次和范围 |
| 三态过滤 | 相关／待确认／不相关；只有相关且证据合格的词进入榜单推荐 |
| 自然场景延伸 | 解释“用户需求 → 产品用途 → 已保存功能依据”，不只看字面重合 |
| 突发热点流程 | 区分首次发现与事件时间，核实城市/球队等实体、来源和旧闻，依赖宿主提供及时数据源 |
| 透明排序 | 先过滤，再按适配度、可比较热度或时效排序；推荐顺序不是官方排名 |
| 偏好约束 | 有授权的记忆仅给已符合产品需求的相似词加权，不放行无关词 |
| 验收与成本 | 多行业正反例、地区与时效、排名不变、调用数、费用和缓存检查 |

## 关联示例

- 美甲产品＋万圣节 OOTD → 搭配节日穿搭的美甲；必须有美甲产品能力。
- AI 宣传 agent＋万圣节 OOTD → 缺少自然产品用途，不能因“能写文案”就放行。
- 烘焙蛋糕＋生日聚会创意 → 聚会蛋糕和甜点；不代表蛋糕适合装饰专用查询。
- 宠物出行包＋带狗自驾 → 外出携行；仅销售宠物食品不足以通过。
- 桌面收纳产品＋书桌布置 → 整理桌面物品；不能只凭“居家”匹配其他家居产品。

## 服务定价

公开skill指令免费；拟议独立托管服务为Starter **$19/月**、Pro **$49/月**。**尚未开放付款或承诺实时监控交付**，范围和上线条件见[PRICING.md](PRICING.md)。

## 使用

把本仓库文件夹以 `brand-trend-fit` 名称放入 agent 的 skills 目录，确保 `SKILL.md` 位于该文件夹根目录。对于 Codex，目录通常为 `~/.codex/skills/brand-trend-fit/`。如果环境已有 GitHub skill 安装器，也可提供本仓库 URL 安装。

示例请求：

> 使用 $brand-trend-fit。我的产品是给小团队做内容选题、本地化初稿和人工审核的工具，目标地区西班牙。请先核实我提供的趋势数据来源，过滤与产品无关的词，保留每个原词、平台、地区、榜单类型、筛选条件和原始名次，并解释产品切入点。不要用帖子排序冒充热搜。

提供真实产品事实及趋势数据，或在 agent 环境中连接经过授权的数据源。协议见 [references/contract.md](references/contract.md)，边界示例见 [references/examples.md](references/examples.md)。

## 突发热点与更新速度

若需要捕捉“巴塞罗那”等突发事件，可按 [event-discovery.md](references/event-discovery.md) 配置宿主的及时来源、增量检查、去重和证据核实。先分清城市、球队或其他同名实体，再检查具体事件与产品是否自然相关。

建议先试验共享来源每3–5分钟检查、发现候选后再补证据；实际发现延迟必须测量，不能承诺秒级或不漏报。新闻/搜索发现单列为事件信号，没有官方榜单证据时原始名次为null。沿用产品相关性底线，不因事件突然爆红就放宽。

这些是配置与验收建议，本仓库不包含已运行的监控服务，不会自动开启收费调用。采集费用取决于宿主选择的数据源和频率；代码仓库不设置服务售价。

## 不包含什么

本仓库是**skill 指令与参考协议**，不是可直接运行的 GoTrend 后端，也不是通用语义模型、爬虫、浏览器登录工具或热搜 API。不内置平台凭据、私有账号、生产服务器配置、持久化记忆库、评分引擎或付费抓取器。Apify、官方 API 等可作为宿主环境的数据源；来源、预算和可用性仍须单独验证。

不承诺零误判、100%匹配率、零 token 或免费采集。应用上线需要单独实现、测试和部署；安装 skill 不会自动改变应用。来源不够或关联不清楚时，应返回缺口或待确认，不能凑数。

## English

Brand Trend Fit is an agent skill for matching verified trends to supported product needs. It plans grounded seeds, separates chart ranks from search evidence, filters relevance before ranking, explains natural product-use bridges, and constrains optional preference memory. It preserves original-language terms and source-specific ranks. It ships instructions and reference contracts, not a scraper, credentials, a scoring engine or a deployed application.
