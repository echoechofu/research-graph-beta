# 个人知识库 · Personal Research Graph

**基于 PubMed，结合 AI，建立你的个人定制研究知识库，快速了解一个领域近期都在研究什么。**

个人知识库（Personal Research Graph，也称 Personal Knowledge Builder）是一款面向科研阅读与知识积累的 macOS 应用。围绕你关心的主题、研究对象与时间范围，它结合 PubMed 文献发现和 AI 分析，自动化完成从查找论文、提取研究发现到组织研究方向的工作，帮助你更快看清近期研究在问什么、发现了什么、还有哪些局限。

你确认研究范围后，应用分批建立可检索、可追溯的 Claim（研究发现）知识库；需要时再检查新增文献，并把整理结果沉淀为可编辑、带参考文献的学习笔记。每个知识库围绕你的问题定制，而不是预设的一套通用研究摘要。

[English](README.en.md) · [下载最新 Beta](https://github.com/echoechofu/research-graph-beta/releases/latest) · [版本记录](https://github.com/echoechofu/research-graph-beta/releases) · [反馈问题](https://github.com/echoechofu/research-graph-beta/issues)

> 本仓库是公开 **Beta 分发仓库**，提供安装包、更新清单与版本说明；不包含应用源码、用户数据、API 密钥或 JCR 数据。公开分发不代表开源许可。

## 它能帮你做什么？

- **摸清一个研究领域正在研究什么。** 从主题和研究边界出发，生成可审阅的 PubMed 检索方案，再分批建立知识库。
- **找到具体研究发现。** 在已建知识库中以 Claim 为单位检索，直接查看发现、来源论文与 PMID。
- **看清不同研究方向。** 将结果先按人体、动物、细胞／离体研究分组，再按研究方向与研究问题组织，逐层展开查看。
- **把阅读变成自己的知识。** 将完成的整理保存为学习笔记，自由改写正文、补充个人理解，并保留独立的原始来源快照。
- **持续补充新文献。** 沿用已确认的研究范围检查新增论文，或扩展检索时间范围，复用已处理文献与任务检查点。

适合探索新课题、准备组会、梳理研究方向，以及长期维护个人研究知识。它以摘要为起点，帮助你决定接下来应该精读哪些原论文。

## 从论文到学习笔记

**描述主题 → 审阅研究边界与检索式 → 预览文献 → 分批构建 → 浏览／检索 Claim → 整理研究方向 → 按需保存与编辑笔记**

| 能力 | 当前实现与价值 |
| --- | --- |
| 研究范围可控 | AI 起草研究边界、PubMed 检索式和 Topic；用户审阅后构建，避免把研究范围交给自动扩展。 |
| Claim 级知识组织 | 从摘要提取研究发现，保留论文关联；可沿发现回到来源，而不只获得论文标题列表。 |
| 本地关键词检索 | 支持中英文关键词、引号短语、全部词／任一词匹配，以及 Topic、研究对象和年份筛选。已建知识库的检索不需要模型或向量服务。 |
| 研究方向整理 | “帮我整理”使用配置的 LLM，整理当前筛选范围内的 Claim；先分研究对象，再分研究方向与问题。默认折叠卡片，按需展开。 |
| 可编辑学习笔记 | 只有主动保存才产生笔记。正文可自由编辑，引用编号、原始 Claim、来源论文和 PMID 作为独立来源快照保留。 |
| 笔记与参考文献一起导出 | 单篇笔记可导出为 UTF-8 TXT，包含正文、编号参考文献、Claim 来源快照和 PubMed 链接；知识库 JSON 导出也包含笔记。 |
| 增量维护 | 按 PMID 去重，已完成分析与有效整理结果可复用；失败任务可显式重试，减少重复处理。更新文献由用户发起。 |
| 中英文工作流 | 界面语言与知识库内容语言可分别选择；论文原文保持来源语言，PubMed 检索式使用英文／MeSH。 |

### 让整理结果保持可核对

人体、动物和细胞研究分别呈现，便于先了解各方向的研究问题，再查看具体发现。整理不生成研究条件分析，也不把不同研究合成一个“统一结论”。

检索与整理是临时工作区：刷新返回初始页面，不自动生成学习笔记。保存后的笔记是一份独立文档；改写正文不会改变原始 Claim，后续知识库更新也不会自动改写笔记。来源后来被排除或移出当前地图时，保存时的快照仍保留，并展示当前来源状态。

### 用户保持对知识库的控制

研究边界可以审阅，Topic 可以调整，文献可以排除，人工调整会在后续维护中保留。期刊分区用于文献准入筛选，不是研究结论可信度评分。JCR 快照不随安装包分发，需用户提供有权使用的数据。

## 安装与开始使用

当前版本：**0.3.0-beta.3 · build 3003**。

| 项目 | 要求 |
| --- | --- |
| 平台 | Apple Silicon Mac（arm64） |
| macOS | 安装包声明 macOS 14+；已在 macOS 15.6.1 验证，macOS 14 实机验证尚待完成 |
| 文献来源 | PubMed；检索与文献更新需要网络 |
| AI 配置 | 用户提供 OpenAI 兼容服务地址、模型名称和 API Key；不内置模型或模型额度 |
| 本地数据 | `~/Library/Application Support/Personal Research Graph` |

1. 从 [最新发布页](https://github.com/echoechofu/research-graph-beta/releases/latest) 下载 `arm64.dmg`。
2. 打开 DMG，将应用拖入 **Applications／应用程序**，再从该目录启动。
3. 首次打开如被 macOS 拦截，按系统提示在“系统设置 → 隐私与安全性”中允许打开。应用使用 ad-hoc 签名，未使用 Developer ID 或 notarization；首次手动放行属于当前 Beta 安装流程。参见 [Apple 官方说明](https://support.apple.com/en-us/102445)。
4. 浏览器打开本地工作界面后，在设置中填写模型配置及所需的文献筛选配置。
5. 创建知识库，确认研究范围，预览并开始构建；完成后即可浏览与检索 Claim。

目前不提供 Intel Mac、Windows 或 Linux 安装包。r5 及更早版本需要手动安装一次带更新器的版本，之后可使用应用内更新。

## 本地数据与外部调用

应用在本机运行 API 和后台 worker，通过本地浏览器界面使用。文献记录、知识结构、学习笔记和设置保存在本地 SQLite／应用数据目录；这个发布仓库不保存你的知识库。

**本地存储不等于完全离线。** PubMed 请求访问 NCBI；生成方案、分析摘要与整理 Claim 时，相关内容会发送到你配置的模型服务。请按自己的需求选择提供商并查看其数据政策。在已有知识库内进行关键词检索，不额外调用 LLM。

## Beta 更新

设置页提供版本信息、“检查更新”和默认开启的启动检查；自动检查最多每 24 小时一次。发现新版本后由原生窗口展示说明，用户确认下载，再确认重启安装。

更新使用 Sparkle 2.10.0 与独立 Ed25519 签名验证。安装前等待正在执行的后台任务，暂停接收新任务，并通过 SQLite 备份接口保存更新前数据库；取消等待会恢复任务处理。更新替换应用包，继续使用原应用数据目录。重启前请保存正在编辑的笔记。

Beta 尚有兼容性与异常恢复测试待补齐。签名更新不消除 macOS 对未公证应用的系统提示。更新清单：[appcast.xml](https://echoechofu.github.io/research-graph-beta/appcast.xml)。

## 当前边界

- 当前是 **关键词检索**，尚未提供向量语义检索或开放式知识库问答助手。
- 当前文献入口为 PubMed，分析以摘要为主；它不能替代全文阅读、系统综述、证据分级或临床判断。
- AI 提取与分组可能出错，应通过原始 Claim、论文和 PMID 核对；没有自动科学真伪裁决或综合 EvidenceScore。
- 文献维护由用户触发，尚不提供无人值守的定时监测；笔记首版为普通文本，单篇导出为 TXT。

## 项目定位与检索关键词

**类别：** 个人定制研究知识库、近期研究进展梳理、AI 辅助科研阅读、个人研究知识管理、PubMed 文献发现、Claim 级检索、来源可追溯的学习笔记。

**English terms:** personalized research knowledge base, recent research landscape, AI-assisted literature analysis, PubMed literature discovery, claim-level retrieval, research direction clustering, evidence traceability, editable learning notes, local data storage, bilingual research workflow, macOS research app.

提供给检索系统的简明事实说明：[llms.txt](llms.txt)。问题反馈请使用 [GitHub Issues](https://github.com/echoechofu/research-graph-beta/issues)，附上应用版本、复现步骤与脱敏后的错误信息。
