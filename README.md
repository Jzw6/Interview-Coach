# 🎯 Interview Coach

> 基于 [OpenClaw](https://github.com/openclaw/openclaw) 的面试准备 Skill，支持**面试题生成**和**简历针对性优化**两种模式。

[![ClawHub](https://img.shields.io/badge/ClawHub-interview--coach-blue)](https://clawhub.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 功能

**模式一：面试题生成**

输入简历 + 岗位 JD，自动分析考点，生成 14–18 道针对性面试题，每题附带答题要点、参考答案和红线提示。覆盖技术硬技能、项目经历（STAR）、行为面试、情景假设、动机匹配五个维度。

**模式二：简历优化**

对照 JD 逐条修改简历，给出原文 → 建议改为 → 改动原因，说明每处修改为什么这么改、关联到 JD 的哪个具体要求。遵循"只增强，不捏造"原则。

---

## 安装

### 通过 ClawHub（推荐）

```bash
npm i -g clawhub
clawhub install interview-coach
```

### 手动安装

下载或克隆本仓库，将 `interview-coach/` 文件夹放到 OpenClaw 工作区的 `skills/` 目录下：

```bash
git clone https://github.com/你的用户名/interview-coach.git
cp -r interview-coach /path/to/openclaw-workspace/skills/
```

重启 OpenClaw 会话后生效。

---

## 使用

直接用自然语言触发，无需记命令：

```
帮我准备面试，简历和JD在附件
根据这个JD帮我出面试题
帮我针对这个岗位改一下简历
```

支持的文件格式：

| 格式 | 是否需要配置 |
|------|------------|
| 文本版 PDF（可复制文字） | ❌ 直接用 |
| Word 文档（.docx / .doc） | ❌ 直接用 |
| TXT 纯文本 | ❌ 直接用 |
| 直接粘贴文字 | ❌ 直接用 |
| 图片（JPG / PNG / WEBP） | ✅ 需要配置 Token |
| 扫描版 PDF（无法复制文字） | ✅ 需要配置 Token |

---

## 配置（可选）

仅上传**图片或扫描版 PDF** 时才需要配置，文本文件跳过此步骤。

1. 访问 [https://aistudio.baidu.com/paddleocr](https://aistudio.baidu.com/paddleocr) 获取 Access Token
2. 复制 `.env.example` 为 `.env`，填入 token：

```bash
cp .env.example .env
# 编辑 .env，填入你的 token
PADDLEOCR_TOKEN=你的token
```

---

## 依赖说明

Python 依赖按需自动安装，**无需提前手动安装任何包**：

| 场景 | 自动安装的包 |
|------|------------|
| 解析文本 PDF | `pdfplumber` |
| 解析 Word 文档 | `python-docx` |
| 图片 / 扫描 PDF OCR | `requests` |
| TXT / 粘贴文字 | 无 |

首次使用某个格式时会有几秒钟的安装过程，之后不会再出现。

---

## 文件结构

```
interview-coach/
├── SKILL.md                        # Skill 主配置，OpenClaw 读取的入口
├── .env.example                    # 环境变量配置模板
├── scripts/
│   └── parse_input.py              # 文件解析脚本（PDF / Word / 图片 / TXT）
└── references/
    ├── question-types.md           # 各题型出题技巧（供 Claude 内部参考）
    └── resume-optimization.md      # 简历修改技巧（供 Claude 内部参考）
```

---

## 系统要求

- [OpenClaw](https://github.com/openclaw/openclaw) 已安装
- Python 3.8+
- uv（推荐）或 pip

---

## License

MIT
