# threads-yunwei

**Threads 全AI驱动自动账号运营 Skill**

基于 [OpenClaw](https://openclaw.ai) / Claude Code 运行，适用于任意 Threads 运营账号。Claude 作为决策大脑贯穿全程——不是规则引擎，不是关键词匹配，每一个节点都由 AI 做判断。

---

## 能做什么

- **每日海量抓取**：首页 Feed + 关键词搜索 + 对标账号，≈ 600 条原始数据
- **三维热度评分**：互动量 × 40% + 跨源验证 × 35% + 时效 × 25%，筛出当日最值得互动的内容
- **AI 精准评论**：两阶段筛选（关键词排除 → AI 语境判断），每日 20-30 条有效引流评论
- **智能发帖**：AI 分析热点后灵活决定是否发帖、发什么，不固定模板
- **效果闭环**：24-72 小时后回溯评论互动，数据驱动策略自迭代
- **账号成长监控**：每日记录粉丝/互动趋势，检测账号健康度
- **三层记忆进化**：daily → weekly → longterm，置信度驱动升级，策略越用越准
- **自动预热保护**：按账号开户天数动态限制操作频率，降低风险

---

## 依赖

| 依赖 | 说明 |
|------|------|
| [threads-skill](https://github.com/openclaw/threads-skills) | Threads CLI 工具，基于 Chrome CDP 控制浏览器 |
| Claude（claude-sonnet-4-6+） | 决策引擎，内容生成，数据分析 |
| Python 3.8+ | threads-skill 运行环境 |
| Chrome | 已启动调试模式 |

---

## 快速开始

### 1. 安装 threads-skill

按照 [threads-skill 文档](https://github.com/openclaw/threads-skills) 完成安装，确保能正常运行：

```bash
cd /path/to/threads-skills
. .venv/bin/activate
python scripts/cli.py --help
```

### 2. 安装本 Skill

通过 OpenClaw 安装：

```bash
openclaw skill install https://github.com/gaojiongwenv587-beep/threads-yunwei-skill
```

或手动使用：将 `SKILL.md` 放入 Claude Code 的 skills 目录，或直接作为 prompt 上下文加载。

### 3. 首次运行 — 安装向导

首次运行时，会自动触发 5 步安装向导：

```
Step 1/5  确认 threads-skill 路径
Step 2/5  AI 配置（Claude 默认 / 自定义 API）
Step 3/5  选择运营账号（从已配置账号中选择）
Step 4/5  配置知识库（产品文档 / 服务介绍，.md 格式）
Step 5/5  配置对标账号文档
```

向导完成后，每次触发 skill 直接进入运营流程，无需重复配置。

### 4. 日常运营

触发方式（自然语言）：

```
执行今日运营
帮我运营一下 Threads
```

每次执行完整流程约 15-30 分钟，含抓取 → 分析 → 发帖 → 评论 → 记忆更新。

---

## 运营流程

```
Phase 0    启动检查 + 断点续传 + Chrome 验证
Phase 0.5  效果回溯（检查 24-72h 前评论的实际互动）
Phase 1    三源抓取（Feed 50 + 关键词 20×20 + 对标账号×15 ≈ 600 条）
Phase 2    热度评分 + AI 筛选 + 策略更新
Phase 3    灵活发帖（AI 决定是否发、发什么）
Phase 4    精准评论（AI 两阶段筛选，20-30 条/日）
Phase 5    账号成长监控 + 日志
Phase 6    三层记忆更新（daily / weekly / longterm）
```

---

## 知识库接入

知识库文件（.md 格式）在安装向导中配置，skill 运行时只读取，不修改。适合放入：

- 产品/服务介绍
- 常见问答
- 内容禁区清单
- 品牌语气指南

多个文件用逗号分隔配置，AI 在生成评论和帖文时自动参考。

---

## 记忆文件

运行后自动生成以下记忆文件（默认位于 `~/.threads/yunwei/`）：

| 文件 | 内容 |
|------|------|
| `daily.md` | 每日洞察，3 天内评估是否升级 |
| `weekly.md` | 经 ≥3 天验证的规律 |
| `longterm.md` | C3/C4 置信度才写入的方法论 |
| `content-assets.md` | 爆款帖文结构模板（可复用）|
| `platform-changes.md` | Threads 算法/规则变化追踪 |
| `benchmarks.md` | 对标账号长期情报 |
| `skill-proposals.md` | SKILL 自更新提案记录 |

---

## 适用场景

- 品牌账号日常运营（医疗、美妆、餐饮、教育等垂直领域）
- 海外华人社区推广
- KOL 账号冷启动增粉
- 任何需要在 Threads 持续输出、精准互动的场景

---

## 注意事项

- 本 skill 不内置任何账号信息，所有账号通过 threads-skill 管理
- 知识库文件仅本地读取，不上传至任何服务
- 遵守 Threads 平台频率限制，预热期自动降频保护账号
- AI 生成的内容经过语境判断，但最终发布前建议定期人工抽查

---

## License

MIT
