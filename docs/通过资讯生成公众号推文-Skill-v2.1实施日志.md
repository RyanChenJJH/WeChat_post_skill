# wechat-news-digest Skill v2.1 撰写阶段 · 实施日志

| 项 | 内容 |
|---|---|
| 日期 | 2026-06-20 |
| 阶段 | 方案撰写阶段（把 skill 实体从 v2.0 升级到 v2.1，落地 D8–D11） |
| 依据 | `通过资讯生成公众号推文-Skill开发方案-v2.0.md`（内容为 v2.1）第十五章实施清单 |
| 计划 | `通过资讯生成公众号推文-Skill-v2.1撰写阶段任务计划.md` |
| 范围 | **只写 skill 文件，未跑 eval**（测试阶段另计） |

---

## 一、做了什么

按"任务计划"逐项执行了第十五章实施清单：**新建 3 个 reference + 修改 6 个文件 + 1 个不动**，
并完成跨文件术语一致性自检。`wechat-news-digest/` 现已对齐 v2.1。

执行顺序遵循依赖关系：先建被依赖的底层文件（画像、选题、排版）→ 改定义术语的 copyright（S/A/B/C、AI 标识）
→ 改引用术语的 fact-risk → 改内容模板类 → 最后改总纲 SKILL/workflow → 自检。

## 二、文件清单与改动摘要

### 新建（3）

| 文件 | 内容 | 对应方案 |
|---|---|---|
| `references/account-profile.md` | 账号画像：定位/读者/偏好雷区/栏目名/语气/排版主色/互动句式库/AI 声明文案 + 默认值 | 6.4 / 11.4 / 9.5 |
| `references/topic-selection.md` | 三道门槛(G1/G2/G3 一票否决) + 三维评分(相关度0.4/话题度0.3/增量0.3×时效) + 6/9 锚点示例 + 组稿规则 + Step2 输出格式 | 第八章 |
| `references/wechat-formatting.md` | 排版稿生成方式(模型只产md) + 微信编辑器三约束 + 样式 token 表 + 粘贴自查3点 | 11.5 / 5.3 |

### 修改（6）

| 文件 | 改动 |
|---|---|
| `references/copyright-guardrails.md` | 增 9.2 来源分级表 S/A/B/C（并入微信雷区）、9.3 量化回查 Q1–Q4、9.4 独家内容规则、9.5 AI 内容标识 |
| `references/fact-risk-control.md` | 增"可信度与来源分级对应"表，术语对齐 S/A/B/C 并指向 9.2 |
| `references/digest-templates.md` | 模板 A 重写为分层节奏版（速览/头条/标准/简讯/结尾五区）；"仍需注意"改条件字段；增名词卡/背景卡写法；示例按新模板重走 |
| `references/titles-and-style.md` | 增"合集主标题策略（围绕封面条目）"，速览式标题可带「｜本期 N 条」 |
| `references/prepublish-checklist.md` | 版权组并入量化回查 Q1–Q4(❌硬项)；增合规标识组(AI声明/平台勾选/未打原创，❌硬项)、来源呈现、可读性、排版稿；更新输出格式块 |
| `SKILL.md` | 铁律二条→三条(加铁律三·标识与诚实)；Step2 改"选题评分+组稿"；默认配置指向画像；输出形态补排版稿；reference 索引补 3 行；description 增"选题评分/排版/多条资讯选哪条"触发词 |
| `references/workflow.md` | Step2 重写(废弃 ⭐️，引 topic-selection)；Step5 双交付物 L1+L2；事实卡片【来源类型】改 S/A/B/C；最终输出结构 7→8 块；Step6 标注量化回查/AI 声明为 ❌ 触发 |

> 注：上表"修改"含 SKILL.md，共 7 个修改文件；清单口径与方案第十五章一致（high/medium 优先级项全部落地）。

### 不动（1）

`references/monetization.md` —— 方案明确无需改。

## 三、关键决策落地点（D8–D11 可追溯）

| 决策 | 落地文件 |
|---|---|
| D8 选题双门槛+读者价值评分，废弃 ⭐️ | topic-selection.md（全章）、workflow.md Step2、SKILL.md Step2 |
| D9 微信排版稿 HTML（确定性转换） | wechat-formatting.md、workflow.md Step5、SKILL.md 输出形态、checklist 排版组 |
| D10 分层节奏正文 | digest-templates.md 模板 A、SKILL.md 输出形态 |
| D11 AI 内容标识（文末+平台） | copyright-guardrails.md 9.5、account-profile.md、SKILL.md 铁律三、checklist 合规标识组 |
| 配套：来源分级 S/A/B/C | copyright-guardrails.md 9.2（定义）+ fact-risk / workflow / topic-selection（引用） |
| 配套：量化回查 Q1–Q4 | copyright-guardrails.md 9.3、checklist 版权量化组 |
| 配套：独家内容规则 | copyright-guardrails.md 9.4 |

## 四、自检结果

| 检查 | 方法 | 结果 |
|---|---|---|
| 残留旧术语（"两条铁律"/"沿用卡片评分") | 全仓 grep | ✅ 无残留 |
| ⭐️ 仅出现在"废弃/不沿用"语境 | 全仓 grep | ✅ 仅 topic-selection 说明 + SKILL/workflow"不沿用" |
| S/A/B/C 跨文件一致 | grep 5 个文件 | ✅ copyright 定义，fact-risk/workflow/topic-selection/SKILL 引用一致 |
| 输出结构 8 块 | grep workflow | ✅ 【1…【8 完整 |
| AI 声明文案逐字一致 | grep | ✅ copyright 9.5 与 account-profile 完全一致；templates 用指针引用 |
| 三条铁律 | grep SKILL | ✅ 标题与正文均为"三条" |
| 方案第十五章覆盖 | 逐项对照 | ✅ 11 项全部达成（10 改动 + 1 不动） |

## 五、遗留与下一步

本阶段产物为"待测稿"。下一步按方案第十六章推进：

1. **测试阶段**：用 `20260609_AI人工智能.md` 跑 TC1–TC7（含选题专项 TC5、排版稿 TC6、合规标识 TC7），
   按结果迭代对应 reference。
2. **打包**：skill-creator 流程打包 `.skill` 供 Claude/Codex 安装。
3. **Phase 2 依赖**：自建网页端需另实现两个应用层确定性组件——版权量化检查器（9.3 的 Q1–Q4）、
   md→微信 HTML 转换器（11.5）；联网读原文降级为"只吃事实卡片"。
4. **可选 L3**：封面图/配图 AI 生成、金句卡、多平台变体（本期未做，入路线图）。

> 风险提示：本阶段未做行为验证（未跑模型），术语与结构一致性已用 grep 静态核对通过；
> 真实产出质量须经测试阶段确认。
