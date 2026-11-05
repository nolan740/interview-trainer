# ScenarioHQ ⚡️ 职场面试场景化脱稿训练器

> **脱离机械背诵，在真实业务撕扯与场景中建立瞬时英文神经反射。**  
> 专为资深产品经理 (B2B / AI PM)、外贸跟单、跨境电商等职场人打造的场景化脱稿口语与词块训练器。

[![GitHub Pages](https://img.shields.io/badge/Demo-Live%20on%20GitHub%20Pages-brightgreen)](https://nolan740.github.io/interview-trainer/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Zero-Backend](https://img.shields.io/badge/Architecture-Pure%20Client--Side-orange)](#)
[![Privacy-First](https://img.shields.io/badge/Privacy-100%25%20Local%20Storage-emerald)](#)

---

## 🎯 痛点与设计背景

很多职场人在进行涉外面试或业务交流时，面临的不是“缺乏英语词汇量”，而是**“缺乏真实场景上下文”**与**“瞬时提取速度慢”**：
1. **机械背单词毫无用处**：孤立背诵单词后，在描述复杂业务逻辑（如跨部门撕扯、上线延期应对、系统对账对账规则）时脑中依然一片空白。
2. **大脑卡顿与母语干扰**：常常因为中文逻辑还没理顺，导致英文输出卡壳。
3. **高频语法与时态暗礁**：叙述过去项目经验时频繁遗漏过去完成时（如混淆 `has launched` 与 `had been live for`），或者介词与固定搭配口误（如 `fill in` 误用为 `fill up`）。

**ScenarioHQ** 采用“思考链脚手架 + 多邻国式渐进拼装 + 核心生词键盘盲打”的闭环机制，让你在手机端的碎片化时间（排队、通勤）完成高强度神经提取训练。

---

## ✨ 核心功能亮点

### 1. 🧩 渐进式词块拼装 (Chunk Builder)
- **拒绝长句臃肿**：将一段 100 词的场景长句，按照“中文脱稿思路”拆分为 2~3 个微步骤。
- **高频易错暗礁排查**：候选项中混入中式口误与时态干扰项；答题时不预先剧透，提交后实时震动高亮，提供针对性的语法诊断。
- **“想不起提示”按钮**：提供脚手架提示，但系统自动记录使用痕迹，避免虚假自信。

### 2. ⌨️ 核心专业词汇盲打 (Spelling Sprint)
- **主动回忆提取**：针对易忘的专业硬词（如 `subsidiary`、`retrieval`、`prototype`、`reconciliation`）设计键盘盲打槽。
- **词性与拼写纠偏**：实时校验字符，并指出词性混淆陷阱（例如强调 `prioritize` 是动词，避免错用为名词 `priority`）。

### 3. 📖 中英双版本完整范文即时查阅
- 每个场景内置 **基础版（先背这版，约90词）** 与 **进阶版（选用替换，约110词）**。
- 提供中文脱稿骨架与核心避坑清单，无需退出答题流程即可随时对照查阅。

### 4. 🎨 三套视觉主题自由切换
- **多邻国趣味风 (Duolingo Style)**：活泼高对比、3D 拟物触控感厚底按钮（默认推荐）。
- **苹果极简风 (Apple Minimalist)**：磨砂毛玻璃透光、冷灰排版、克制专业。
- **北欧有机风 (Nordic Clean)**：低饱和度鼠尾草绿与暖沙色，适合长时间沉浸阅读。

### 5. 🔒 隐私先行与零服务器依赖 (Privacy-First)
- **公共仓库脱敏**：开源代码只包含通用无害演示模板，不包含任何个人简历与具体项目经历。
- **本地私有存储**：支持上传自己的专属题库 JSON，数据 100% 留存在你的手机本地浏览器中（`localStorage`），无需后端服务器，零隐私泄露风险。

---

## 📱 在线体验与手机安装指南

### 1. 在线访问
在手机或电脑浏览器中打开：  
👉 [https://nolan740.github.io/interview-trainer/](https://nolan740.github.io/interview-trainer/)

### 2. 添加到手机主屏幕（获得原生 App 体验）
- **iOS (Safari)**：点击屏幕底部中间的 **“分享”** 按钮（带向上箭头的方框）➔ 滑动选择 **“添加到主屏幕”**。
- **Android (Chrome / 浏览器)**：点击右上角菜单（三个点）➔ 选择 **“添加到主屏幕”** 或 **“安装应用”**。

添加后即可全屏运行，支持断网离线练习，随时随地开启碎片化复习。

---

## 📥 如何导入专属题库

1. 在手机上打开训练器页面，点击右上角的 **`📥 导入`** 按钮。
2. 点击 **`📁 选择本地 JSON 文件导入`**，直接选取你生成的题库文件（例如 `my_scenarios.json`）。
3. 也可以选择直接将 JSON 纯文本粘贴在下方的备用文本框中，点击载入。
4. 导入成功后，顶部会点亮 **`🔒 私有题库`** 标识，即刻开启专属场景训练！

---

## 🤖 专属题库生成 Prompt（支持任意行业与角色）

你可以将以下提示词完整复制，发送给 **ChatGPT / Claude / DeepSeek** 等大语言模型，并附带你自己的工作总结、沟通素材、外贸邮件或面试题，AI 将一键为你生成完全兼容的题库 JSON。

```text
你是一位资深的职场外语培训专家与场景化学习架构师。请根据我提供的【岗位角色、业务场景、常见沟通痛点或中英文对话素材】，帮我将其提炼并转化为专属于「ScenarioHQ 脱稿训练器」的标准 JSON 题库格式。

【生成规范】
1. 脱稿思考链 (zh_scaffold_full)：必须将回答逻辑拆解为极简的中文思维链条（用 → 连接），帮助我在英文卡顿前先理清母语表达逻辑。
2. 渐进拼句步骤 (steps)：将每个场景的核心回复拆解为 2~3 个微步骤。每个步骤提供 2 个地道的核心动宾词块（correct_chunks），以及 1~2 个该角色极易犯的中式口误/时态错误/介词混淆干扰项（distractors），并注明针对性的避坑解析（trap_reason）。
3. 高频盲打词汇 (spelling_bank)：提炼 4~8 个该岗位最核心、最容易拼错或词性混淆的专有名词与高频动词。
4. 输出要求：必须输出严格合法的纯 JSON 格式文本，不要包含任何额外的 Markdown 说明文字。

【标准 JSON 数据格式规范】
{
  "version": "1.0.0",
  "updated_at": "YYYY-MM-DD",
  "scenarios": [
    {
      "id": "01",
      "title": "场景名称 (例如：处理海外客户交期延误与索赔)",
      "interviewer_q": "对方的提问或邮件核心诉求（英文）",
      "foundation_text": "约80-100词的地道基础版表达",
      "advanced_text": "约100-120词的进阶地道表达",
      "zh_scaffold_full": "中文思维链条：致歉并说明客观原因 → 给出紧急替代方案 → 提出折扣补偿",
      "watch_outs": [
        "避坑提醒 1 (如：delay in delivery 而非 delay of)",
        "避坑提醒 2 (如：apologize for doing)"
      ],
      "mastery": 50,
      "status": "orange",
      "steps": [
        {
          "step_zh": "① 步骤一：说明交期延误客观原因并致歉",
          "hint_text": "注意表达致歉的固定介词搭配",
          "target_sentence": "We sincerely apologize for the delay in delivery due to port congestion.",
          "correct_chunks": [
            { "text": "We sincerely apologize for" },
            { "text": "the delay in delivery due to port congestion." }
          ],
          "distractors": [
            { "text": "apologize the delay of delivery", "trap_reason": "apologize 必须加 for；延误搭配用 in delivery" }
          ]
        }
      ]
    }
  ],
  "spelling_bank": [
    {
      "target_word": "consignment",
      "zh": "托运货物 / 寄售",
      "pos": "n.",
      "topic": "外贸跟单核心词",
      "context_tip": "海运提单与交货时常用术语",
      "sentence_before": "The entire",
      "sentence_after": "was held at customs for inspection.",
      "trap_note": "注意中间有 g 不发音，不要漏写 g",
      "full_sentence": "The entire consignment was held at customs for inspection."
    }
  ]
}

---
我的业务材料 / 岗位场景如下：
[请在此粘贴你的业务场景描述、日常邮件沟通案例或中英文痛点]
```

---

## 🛠 本地开发与二次开发

本项目为单文件静态架构（Single-file Application），无需安装 Node.js、npm 或任何打包工具。

```bash
# 1. 克隆本仓库
git clone https://github.com/nolan740/interview-trainer.git

# 2. 进入目录
cd interview-trainer

# 3. 使用任意本地静态服务或直接双击 index.html 运行
# 例如通过 Python 快速起服：
python3 -m http.server 8000
```

在浏览器打开 `http://localhost:8000` 即可实时预览修改。

---

## 📄 License

本项目采用 [MIT License](LICENSE) 开源许可，欢迎 Fork、Star 并基于此框架构建你自己的垂直行业脱稿训练库！