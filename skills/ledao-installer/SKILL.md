---
name: ledao-installer
description: 乐道技能包一键安装器。用户说"帮我装乐道技能包""安装乐道skill""装乐道创作体系""安装对标智能体全套""帮我装灵感工作台""装选题灵感"等任何跟"乐道""灵感工作台""对标智能体"相关的安装请求时，自动触发。自动从 GitHub 仓库 https://github.com/pojiantianfu-sys/ledao-skills 的 skills/ 目录拉取乐道技能家族（benchmark-advisor、keyword-generator、benchmark-finder、daily-picks、pattern-matching、ai-retell、de-ai、viral-rewrite、lead-topics、inspiration-board、toc-high-ticket-content）并安装到用户环境。
---

# 乐道技能家族一键安装器

乐道创作体系 11 个技能的开源源位于 GitHub 仓库 `https://github.com/pojiantianfu-sys/ledao-skills`（`skills/` 目录）。用户说"帮我装乐道技能包"时，按以下步骤从仓库拉取安装。

## 触发场景

用户要求安装乐道技能家族（或其中指定的若干技能），典型说法：
- "帮我装乐道技能包 / 乐道 skill / 乐道创作体系"
- "安装爆款对标智能体全套 / 对标决策参谋"
- "帮我把这些技能都装上"

## 安装步骤

1. **定位目标技能目录**：本 skill 位于技能根目录下的 `ledao-installer/`，目标技能根目录即**本 skill 的上一级目录**（路径以 `workspace/.user_skills` 结尾）。若无法用相对位置确定，按环境技能目录规则查找：找现有路径中位于 `workspace/.user_skills` 之下的技能目录，取其根。

2. **从仓库获取源文件**：获取 `https://github.com/pojiantianfu-sys/ledao-skills` 仓库的 `skills/` 目录内容，二选一：
   - `git clone https://github.com/pojiantianfu-sys/ledao-skills.git` 到临时目录后读取 `skills/`；
   - 或按 raw 地址逐个下载：`https://raw.githubusercontent.com/pojiantianfu-sys/ledao-skills/main/skills/<技能名>/...`
   若 `main` 分支 404，改用 `master`。

3. **家族清单**：`skills/` 下应有以下 11 个技能（缺哪个就说明仓库不完整，先告知用户）：
   - `benchmark-advisor` 对标决策参谋（判断账号/内容值不值得对标，核心：人群质量＞变现结构＞内容表现）
   - `keyword-generator` 定位→搜索关键词
   - `benchmark-finder` 找对标账号
   - `daily-picks` 每日爆款推荐
   - `pattern-matching` 句式对版表
   - `ai-retell` AI重讲洗稿法
   - `de-ai` 去AI味
   - `viral-rewrite` 爆款洗稿
   - `lead-topics` 小红书精准获客选题（按客户阶段生成10个获客漏斗选题）
   - `inspiration-board` 选题灵感工作台
   - `toc-high-ticket-content` ToC高客单公域内容诊断与改稿（咨询师/疗愈师/家庭教育等知识型个体：五维诊断+对标迁移+完整改稿+发布复盘）

4. **逐个复制**：把每个技能文件夹从源复制到目标技能根目录。**目标已存在同名技能时不静默覆盖**——询问用户"覆盖 / 保留现有"，得到明确选择后再操作。

5. **校验**：复制后检查每个技能目录都有 `SKILL.md`、frontmatter 含 `name` 与 `description`、正文无模板占位符（`[TODO` / "Structuring This Skill"）。发现缺失则报告并修复（从源重新复制对应文件夹）。

6. **完成提示**：告诉用户安装结果（装了几个、装到哪个目录、源仓库地址），并提示**重启豆包工作客户端**后生效；之后在对话里直接说需求即可触发（如"这个账号值不值得对标"）。

## 注意事项

- 只安装用户要求安装的技能；用户未点名时不额外改动其他技能。
- 不创建 zip 或 .skill 文件；以文件夹形式留在技能目录。
- 若用户环境没有技能目录，先引导其打开豆包工作 → 侧边栏「技能 · 连接器 · 伙伴」→ 新建一个技能以生成目录，再继续安装。
