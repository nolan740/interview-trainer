# interview-trainer ⚡️ 职场面试场景化脱稿训练器

> **拒绝机械长文死背，在真实业务撕扯与场景中建立瞬时英文神经反射。**
>
> 专为面向涉外/外企求职的高阶职场人（B2B / AI PM、技术负责人、业务分析师、跨境运营等）打造的轻量场景化脱稿口语与词块训练器。

[![GitHub Pages](https://img.shields.io/badge/deployment-GitHub%20Pages-brightgreen)](https://nolan740.github.io/interview-trainer/)
[![Version](https://img.shields.io/badge/version-v1.1.1-blue.svg)](CHANGELOG.md)
[![Pure Frontend](https://img.shields.io/badge/architecture-Single%20File%20Vue%203-orange.svg)](#-技术架构与离线隐私)
[![Privacy First](https://img.shields.io/badge/privacy-100%25%20Local%20Storage-success.svg)](#-技术架构与离线隐私)

---

## 📱 在线体验与添加到手机

### 1. 在线直接体验
在手机或电脑浏览器中直接打开：  
👉 **[https://nolan740.github.io/interview-trainer/](https://nolan740.github.io/interview-trainer/)**

### 2. 添加到手机主屏幕（获得原生 App 触感）
- **iOS (Safari)**：点击屏幕底部中间的 **“分享”** 按钮（带向上箭头的方框）➔ 滑动选择 **“添加到主屏幕”**。
- **Android (Chrome)**：点击右上角菜单（三个点）➔ 选择 **“添加到主屏幕”** 或 **“安装应用”**。

---

## 🎯 解决的核心痛点与训练闭环

很多资深职场人在准备英文面试时面临的瓶颈不是单纯的词汇量，而是：
1. **真实深水区场景缺乏针对性训练**：通用口语 100 问解决不了跨部门需求冲突、系统重构取舍、自动化核销边界与上线延期应对等复杂表达。
2. **母语阻滞与大脑瞬间卡壳**：中文业务逻辑尚未理顺，导致英文输出瞬间停滞。
3. **时态与语法暗礁反复发作**：讲述过去经历频繁丢掉过去完成时（如混淆 `has launched` 与 `had been live for`），或固定搭配口误（如 `fill in` 误用为 `fill up`）。

**interview-trainer** 通过四大环节实现科学记忆闭环：
```
[ 1. 理解问题与中文思维链 ] 
            ⬇️
[ 2. 渐进式词块拼装 (Chunk Builder) ]  <-- 严格语序核验 + 避坑干扰项解析
            ⬇️
[ 3. 终局独立回忆 (No-Hint Recall) ]   <-- 初始全盲回忆 + 防作弊评级
            ⬇️
[ 4. 艾宾浩斯跨日巩固与排期调度 ]     <-- 红(D+1) / 橙(D+2) / 绿(D+7)
```

---

## 📖 自定义题库与增量更新体系 (V1.1.1 数据契约)

本应用支持用户在外部 AI（ChatGPT、Claude、DeepSeek 等）中使用提示词基于个人简历和目标岗位 JD 生成个性化题库，并支持**多次增量导入、内容热更新与学习进度无缝继承**。

### 1. 题库使用与更新流程
```
[ 官方通用题库 ] (开箱即用 10 场景)
       │
       ├─► 复制专属 AI 提示词 (附带个人简历 + 目标岗位 JD)
       │         │
       │         ▼
       ├─► 外部 AI 生成专属题库 JSON
       │         │
       │         ▼
       ├─► 本地文件导入 / 粘贴导入
       │         │
       │         ▼
       └─► 增量合并 (默认) ──► 自动追加新题、比对内容、继承已有学习排期与统计
```

---

### 2. 核心身份与元数据规范

| 字段 | 类型 | 必要性 | 规范与作用 |
|---|---|---|---|
| `schemaVersion` | string | 推荐 | 数据结构协议版本，当前为 `"1.1"` 或 `"1.1.0"`。不可与 `version` 混淆。 |
| `bankId` | string | **核心必填** | 题库的全局唯一稳定身份标识（如 `"custom-b2b-pm-v1"`）。系统根据 `bankId` 进行多题库数据隔离，**后续更新同一题库必须保持 `bankId` 不变**。 |
| `version` | string | 选填 | 题库内容版本号（如 `"1.0.0"`、`"1.1.0"`），仅用于版本展示，不能替代 `bankId` 决定题库身份。 |
| `updated_at` | string | 选填 | 题库维护日期（格式 `YYYY-MM-DD`）。 |
| `scenarios` | array | 选填* | 场景题库数组（增量更新时若只更新词汇可缺省）。 |
| `spelling_bank` | array | 选填* | 核心词汇数组（增量更新时若只更新场景可缺省）。 |

> \*注：全量题库导入时 `scenarios` 为必填非空数组；增量更新文件需至少包含非空的 `scenarios` 或 `spelling_bank` 之一。

---

### 3. 场景对象字段规范 (`scenarios[]`)

| 字段 | 类型 | 说明与规范要求 |
|---|---|---|
| `id` | string | **知识点唯一稳定 ID**（如 `"SCENE-01"`）。后续修改该题时必须保持 ID 不变；严禁因调整列表顺序而重命名 ID。 |
| `title` | string | 场景中英文标题（如 `"处理需求冲突 (Handling Conflicting Requirements)"`）。 |
| `interviewer_q` | string | 面试官的核心英文提问（用于终局回忆屏展示）。 |
| `foundation_text`| string | 约 80-100 词的基础版地道回答（脱稿推荐背诵版本）。 |
| `advanced_text` | string | 约 100-120 词的进阶版表达（选用替换）。 |
| `zh_scaffold_full`| string | 中文脱稿思考链（以 `→` 连接的 3~4 个核心逻辑节点，防止大脑卡壳）。 |
| `watch_outs` | array | 字符串数组，列出高频语法陷阱或口误提醒。 |
| `steps` | array | **微步骤拆解数组**（建议每题 2~3 个步骤，非空）。 |

#### 微步骤对象字段规范 (`steps[]`)
| 字段 | 类型 | 说明 |
|---|---|---|
| `step_zh` | string | 本微步骤的中文核心逻辑说明。 |
| `hint_text` | string | 语法、时态或动宾搭配提示（点击“查看避坑提示”后展示）。 |
| `target_sentence` | string | 本微步骤的标准地道英文整句。 |
| `correct_chunks` | array | 正确词块数组（非空）。每个对象含 `id` (string) 与 `text` (string)。系统以此为依据进行严格语序匹配。 |
| `distractors` | array | 干扰项数组（选填）。每个对象含 `id` (string)、`text` (string) 及 `trap_reason` (string，错误原因解析)。 |

---

### 4. 词汇对象字段规范 (`spelling_bank[]`)

| 字段 | 类型 | 说明 |
|---|---|---|
| `id` | string | 词汇唯一稳定标识（选填；若缺失，系统自动以标准化的 `target_word` 作为稳定身份）。 |
| `target_word` | string | 盲打目标英文单词（如 `"prioritize"`）。 |
| `zh` | string | 中文释义。 |
| `pos` | string | 词性（如 `"v."`、`"n."`、`"adj."`）。 |
| `topic` | string | 适用业务场景标签。 |
| `context_tip` | string | 语境提示与使用场景说明。 |
| `sentence_before`| string | 挖空题前半句。 |
| `sentence_after` | string | 挖空题后半句。 |
| `trap_note` | string | 易错警报（词性混淆或形近字提醒）。 |
| `full_sentence` | string | 完整示范全句。 |

---

### 5. 增量合并与内容变更重新验证机制 (INC-02 & INC-03)

当导入具有相同 `bankId` 的新 JSON 文件时，系统默认启用 **「增量合并（推荐）」** 管道：

```
                新导入知识点 (匹配已有 ID)
                            │
               ┌────────────┴────────────┐
               ▼                         ▼
         [ 核心训练内容不变 ]        [ 核心训练内容已变更 ]
         (仅修改标题/中文提示)    (修改提问/目标英文句/正确词块)
               │                         │
               ▼                         ▼
      保留当前掌握状态与排期       保留历史 Attempts & 完成轮次
    (如仍保持 "自评已巩固", D+7)    重置巩固等级为 "需重新验证" (D+1/D+2)
```

1. **新增 ID**：作为新知识点追加至当前题库末尾，初始状态标记为“未验证”。
2. **未包含的已有 ID**：**默认完整保留**，已有练习进度与复习排期完全不受影响，杜绝全库清空。
3. **内容变动精细判定**：
   - **非核心变动**（仅微调标题、说明文案）：原样继承复习排期和掌握程度。
   - **核心训练变动**（修改 `interviewer_q`、微步骤数量、`target_sentence` 或正确词块内容/顺序）：保留所有历史练习次数与首答统计，但将当前巩固状态重置为“需重新验证”，驱动用户按最新标准重新练习。
4. **两阶段预览与确认 (INC-04)**：
   - 导入前弹出 Diff 摘要卡片（展示目标题库、新增数、更新数、不变数、需重新验证数）。
   - 默认选中「增量合并」；若用户主动勾选「全量替换」，必须二次确认，且系统在写入前自动创建可恢复的安全备份。

---

## 📄 标准 JSON 题库示例

### 示例 1：完整标准题库示例 (`full_bank_sample.json`)
可直接保存为 `.json` 文件并导入本应用测试验证：

```json
{
  "schemaVersion": "1.1",
  "bankId": "custom-b2b-pm-v1",
  "version": "1.0.0",
  "updated_at": "2026-11-06",
  "scenarios": [
    {
      "id": "SCENE-01",
      "title": "处理需求冲突 (Handling Conflicting Requirements)",
      "interviewer_q": "How do you handle conflicting requirements from different stakeholders?",
      "foundation_text": "When stakeholders have conflicting requirements, I first listen to each group to understand their underlying objectives. Then, I bring data to light, including process impact and technical complexity. I propose phased solutions—delivering core needs first while deferring niche requests. Finally, I document the agreed scope in the PRD.",
      "advanced_text": "My methodology for navigating stakeholder misalignment centers on objective discovery. I initiate individual deep-dives to discern fundamental business drivers. By facilitating consensus workshops, I propose phased compromises, decoupling mandatory fields from progressive data entry.",
      "zh_scaffold_full": "深入调研各方底层诉求 → 客观数据呈现影响面 → 提出分期交付折中方案 → 固化决策入 PRD",
      "watch_outs": [
        "underlying objectives (底层真实诉求)",
        "document the agreed scope in the PRD (将达成一致的范围固化到 PRD)"
      ],
      "steps": [
        {
          "step_zh": "① 调研对齐：深入了解各方底层诉求，而非仅停留在表层争执",
          "hint_text": "倾听底层目标: understand their underlying objectives",
          "target_sentence": "I first listen to each group to understand their underlying objectives rather than surface-level demands.",
          "correct_chunks": [
            {
              "id": "s1_c1",
              "text": "I first listen to each group to understand"
            },
            {
              "id": "s1_c2",
              "text": "their underlying objectives rather than surface-level demands."
            }
          ],
          "distractors": [
            {
              "id": "s1_d1",
              "text": "their underly objective rather than demands",
              "trap_reason": "underlying 为形容词修饰复数 objectives"
            }
          ]
        },
        {
          "step_zh": "② 方案落地：提出分期交付折中方案，并将达成一致的决策记录入 PRD",
          "hint_text": "折中方案 phased compromises；记录变更 document agreed changes in PRD",
          "target_sentence": "I proposed phased compromises and documented the agreed scope in the PRD.",
          "correct_chunks": [
            {
              "id": "s1_c3",
              "text": "I proposed phased compromises"
            },
            {
              "id": "s1_c4",
              "text": "and documented the agreed scope in the PRD."
            }
          ],
          "distractors": [
            {
              "id": "s1_d2",
              "text": "agreement scope into PRD",
              "trap_reason": "动宾搭配是 document the agreed scope in the PRD"
            }
          ]
        }
      ]
    }
  ],
  "spelling_bank": [
    {
      "id": "word_01",
      "target_word": "prioritize",
      "zh": "按优先级排序",
      "pos": "v.",
      "topic": "需求排期与权衡",
      "context_tip": "根据商业价值和技术可行性确定先后顺序",
      "sentence_before": "As a product manager, I need to",
      "sentence_after": "the backlog based on technical feasibility.",
      "trap_note": "注意是动词 prioritize，不要误用为名词 priority",
      "full_sentence": "As a product manager, I need to prioritize the backlog based on technical feasibility."
    }
  ]
}
```

---

### 示例 2：增量追加与知识点修改示例 (`incremental_patch_sample.json`)
保持相同的 `bankId`，仅提供需要修改或新增的场景：

```json
{
  "schemaVersion": "1.1",
  "bankId": "custom-b2b-pm-v1",
  "version": "1.1.0",
  "updated_at": "2026-11-07",
  "scenarios": [
    {
      "id": "SCENE-01",
      "title": "处理需求冲突 (Handling Conflicting Requirements - 修订版)",
      "interviewer_q": "How do you handle conflicting requirements from different stakeholders?",
      "foundation_text": "When stakeholders have conflicting requirements, I first listen to each group to understand their underlying objectives. Then, I bring data to light, including process impact and technical complexity. I propose phased solutions—delivering core needs first while deferring niche requests. Finally, I document the agreed scope in the PRD.",
      "advanced_text": "My methodology for navigating stakeholder misalignment centers on objective discovery. I initiate individual deep-dives to discern fundamental business drivers. By facilitating consensus workshops, I propose phased compromises, decoupling mandatory fields from progressive data entry.",
      "zh_scaffold_full": "深入调研各方底层诉求 → 客观数据呈现影响面 → 提出分期交付折中方案 → 固化决策入 PRD",
      "watch_outs": [
        "underlying objectives (底层真实诉求)",
        "document the agreed scope in the PRD"
      ],
      "steps": [
        {
          "step_zh": "① 调研对齐：深入了解各方底层诉求，而非仅停留在表层争执",
          "hint_text": "倾听底层目标: understand their underlying objectives",
          "target_sentence": "I first listen to each group to understand their underlying objectives rather than surface-level demands.",
          "correct_chunks": [
            {
              "id": "s1_c1",
              "text": "I first listen to each group to understand"
            },
            {
              "id": "s1_c2",
              "text": "their underlying objectives rather than surface-level demands."
            }
          ],
          "distractors": [
            {
              "id": "s1_d1",
              "text": "their underly objective rather than demands",
              "trap_reason": "underlying 为形容词修饰复数 objectives"
            }
          ]
        },
        {
          "step_zh": "② 方案落地：提出分期交付折中方案，并将达成一致的决策记录入 PRD",
          "hint_text": "折中方案 phased compromises；记录变更 document agreed changes in PRD",
          "target_sentence": "I proposed phased compromises and documented the agreed scope in the PRD.",
          "correct_chunks": [
            {
              "id": "s1_c3",
              "text": "I proposed phased compromises"
            },
            {
              "id": "s1_c4",
              "text": "and documented the agreed scope in the PRD."
            }
          ],
          "distractors": [
            {
              "id": "s1_d2",
              "text": "agreement scope into PRD",
              "trap_reason": "动宾搭配是 document the agreed scope in the PRD"
            }
          ]
        }
      ]
    },
    {
      "id": "SCENE-02",
      "title": "项目上线突发延期应对 (Handling Launch Delays)",
      "interviewer_q": "How would you handle a sudden delay right before product launch?",
      "foundation_text": "I would first assess the root cause and impact on the critical path. Then, I would coordinate with technical leads to identify workarounds. Finally, I would brief stakeholders with a revised timeline.",
      "advanced_text": "My immediate priority would be isolating the blocker and re-evaluating critical path dependencies. I would collaborate with technical teams to construct a mitigation roadmap while keeping leadership aligned on scope adjustments.",
      "zh_scaffold_full": "定位根因与关键路径影响 → 协同技术制定变通方案 → 向上透明同步调整后排期",
      "watch_outs": [
        "assess the root cause (评估根因)",
        "critical path (关键路径)"
      ],
      "steps": [
        {
          "step_zh": "① 快速止损：评估根因以及对关键交付路径的影响",
          "hint_text": "评估影响: assess the impact on the critical path",
          "target_sentence": "I would first assess the root cause and its impact on the critical path.",
          "correct_chunks": [
            {
              "id": "s2_c1",
              "text": "I would first assess the root cause"
            },
            {
              "id": "s2_c2",
              "text": "and its impact on the critical path."
            }
          ],
          "distractors": [
            {
              "id": "s2_d1",
              "text": "assess root cause quick with no data",
              "trap_reason": "修饰动词应用副词 quickly"
            }
          ]
        }
      ]
    }
  ]
}
```

---

## 🤖 专属题库生成 AI 提示词（与代码 100% 同构）

复制下方完整 Prompt，发给 ChatGPT、Claude 或 DeepSeek，替换末尾的**简历内容**与**目标岗位 JD** 即可：

```text
你是一位资深外企/出海大厂的面试官与专业英语辅导专家。请根据我提供的【个人简历/项目经历】和【目标应聘岗位/JD信息】，为我量身定制一套专属于「interview-trainer」的结构化 JSON 题库。

【生成核心原则】
1. 真实业务溯源：题目与回答必须严格基于我的简历事实（如主导架构、数据指标、跨部门冲突、技术方案选型），杜绝脱离实际的空洞套话。
2. 防卡顿思维链 (zh_scaffold_full)：每道题前必须提供 3~4 个极简中文逻辑节点（用 → 连接，如：痛点阐述 → 方案折中 → 落地动作 → 复盘反思），防止英文卡顿前思维紊乱。
3. 渐进式拼装微步骤 (steps)：将每个场景的回答拆解为 2~3 个微步骤。每个步骤包含 2 个地道的核心动宾词块 (correct_chunks)，以及 1~2 个中国候选人常犯的时态飘移、中式搭配或易错介词干扰项 (distractors)，并注明针对性的避坑解析 (trap_reason)。每个词块必须包含稳定 id。
4. 核心词汇盲打提取 (spelling_bank)：提炼 4~6 个该岗位面试中至关重要的业务专有名词与高阶动词（附带词性、挖空例句及混淆警示）。
5. 身份稳定规范：为该题库分配一个英文字符构成的稳定 bankId（如 "custom-ai-pm-v1"），每个场景配唯一且有语义的 id（如 "SCENE-01"）。
6. 输出规范：必须输出严格合法的纯 JSON 文本，无 Markdown 标记外挂。

【标准 JSON 数据格式契约】
{
  "schemaVersion": "1.1",
  "bankId": "custom-my-role-v1",
  "version": "1.0.0",
  "updated_at": "2026-11-06",
  "scenarios": [
    {
      "id": "SCENE-01",
      "title": "场景名称 (如：处理需求冲突 / 复杂项目架构陈述)",
      "interviewer_q": "面试官针对该岗位的具体提问 (英文)",
      "foundation_text": "基础版英文示范 (约80-100词，适合脱稿先背这版)",
      "advanced_text": "进阶版英文示范 (约100-120词，适合理解与高阶替换)",
      "zh_scaffold_full": "中文脱稿思考链：步骤1 → 步骤2 → 步骤3",
      "watch_outs": [
        "易错语法点或避坑提醒 1",
        "避坑提醒 2"
      ],
      "steps": [
        {
          "step_zh": "① 步骤一中文思路",
          "hint_text": "语法、时态或动宾搭配提示",
          "target_sentence": "本微步骤的标准英文整句",
          "correct_chunks": [
            { "id": "s1_c1", "text": "正确词块前半句" },
            { "id": "s1_c2", "text": "正确词块后半句" }
          ],
          "distractors": [
            { "id": "s1_d1", "text": "易错口误或时态干扰项", "trap_reason": "错误原因深度解析" }
          ]
        }
      ]
    }
  ],
  "spelling_bank": [
    {
      "id": "word_01",
      "target_word": "prioritize",
      "zh": "按优先级排序",
      "pos": "v.",
      "topic": "岗位高频核心动词",
      "context_tip": "需求排期与跨团队沟通时使用",
      "sentence_before": "I had to coordinate with stakeholders and",
      "sentence_after": "the backlog based on technical feasibility.",
      "trap_note": "注意是动词 prioritize，不要误用为名词 priority",
      "full_sentence": "I had to coordinate with stakeholders and prioritize the backlog based on technical feasibility."
    }
  ]
}

---
【我的个人简历经历】：
[请在此粘贴你的简历项目经历、工作背景、核心成果]

【目标岗位招聘要求 / JD】：
[请在此粘贴目标岗位职责、任职要求与常见追问点]
```

---

## 🔒 技术架构与离线隐私

- **纯前端单文件架构 (Single-File Architecture)**：全部交互、拼装校验与状态机均内聚在单文件 `index.html` 中，无需后端服务器或数据库支撑。
- **100% 本地隐私防护 (Zero Data Leakage)**：导入的全部自定义题库、个人项目复盘话术、做题记录与排期进度完全保存在本地浏览器的 `localStorage` 中，绝不上报任何外部服务器。
- **离线与数据持久性注意**：
  - 页面初次加载依赖外部标准 CDN（Vue 3、Tailwind CSS、Font Awesome），弱网或首次无网络访问时请保持联网以加载资源。
  - 由于数据保存在浏览器本地，清除浏览器数据或更换设备会导致本地记录不可见。强烈建议定期在 **「设置」➔「导出完整备份」** 下载本地 JSON 备份文件。

---

## 📄 开源许可证

本项目基于 [MIT License](LICENSE) 开源。欢迎 Star、Fork 并根据个人求职方向自主定制！
