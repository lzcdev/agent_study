# 🤖 agent_study — 高级 Agent 工程师学习仓库

> 从应用开发 → 框架原理 → 多智能体架构 → 生产级平台 → Agent 算法优化，系统进阶高级 Agent 工程师 / 智能体架构师。
> 总周期 **27 周**（+2 周前置准备），5 大阶段 + 压轴 Capstone 项目。

## 📈 学习路线总览

| 阶段 | 主题 | 周期 | 产出项目 |
|---|---|---|---|
| 前置 | 基础补齐与环境搭建 | 2 周 | 环境 + SSE 接口 |
| Phase 1 | 单 Agent 基础 | 4 周 | 项目 01～04 |
| Phase 2 | 多 Agent 协作 | 6 周 | 项目 05～08 |
| Phase 3 | Agent 工程化与生产落地 | 8 周 | 项目 09～16 |
| Phase 4 | Agent 架构进阶 & 自研能力 | 7 周 | 项目 17～23 |
| Phase 5 | Agent 算法优化 & 前沿研究 | 6 周 | 项目 24～25 |
| Capstone | 企业级分布式多 Agent 中台 | 贯穿 Phase 4、5 | 综合项目 |

## 📂 仓库结构

```
agent_study/
├── phase1/   # 单 Agent 基础（ReAct / LangGraph / RAG）
│   ├── 01-native-react-agent        # 原生 ReAct 计算器 Agent（第 1 周）
│   ├── 02-langgraph-basics          # LangGraph 状态机基础（第 2 周）
│   ├── 03-business-single-agent     # 企业数据查询单 Agent（第 3 周）
│   └── 04-rag-agent                 # RAG+Agent 文档助手（第 4 周）
├── phase2/   # 多 Agent 协作（Supervisor / Handoff / Map-Reduce / Critic）
│   ├── 05-code-multi-agent          # 代码开发多 Agent（第 6 周）
│   ├── 06-customer-support-agent    # 电商售后工单 Agent（第 7 周）
│   ├── 07-contract-review-agent     # 批量合同审阅 Agent（第 8 周）
│   └── 08-multi-agent-optimization  # 多 Agent 优化专项（第 9 周）
├── phase3/   # 工程化与生产落地（长任务 / 安全 / 可观测 / 评测）
│   ├── 09-agent-async-task          # Celery+Redis 异步任务（第 11 周）
│   ├── 10-long-running-business-agent  # 长周期业务 Agent（第 12 周）
│   ├── 11-agent-fault-tolerance     # 稳定性与容错（第 13 周）
│   ├── 12-agent-tool-gateway        # 安全网关+工具调度（第 14 周）
│   ├── 13-agent-cost-optimize       # 性能与成本优化（第 15 周）
│   ├── 14-agent-observability       # 可观测体系（第 16 周）
│   ├── 15-agent-eval-basic          # DeepEval 评测基础（第 17 周）
│   └── 16-agent-eval-platform       # 自动化评测平台（第 18 周）
├── phase4/   # 架构进阶 & 自研能力（源码 / 状态机 / 分布式 / RPA / 记忆）
│   ├── 17-langgraph-source-study    # LangGraph 源码阅读（第 19 周）
│   ├── 18-custom-agent-runtime      # 自研 Agent 状态执行引擎（第 20 周）
│   ├── 19-event-driven-agent-base   # Kafka 事件驱动基础（第 21 周）
│   ├── 20-distributed-event-agent   # 分布式事件驱动多 Agent（第 22 周）
│   ├── 21-browser-rpa-agent         # Browser 网页操作 Agent（第 23 周）
│   ├── 22-memory-architecture       # 三级记忆架构（第 24 周）
│   └── 23-mcp-multimodal-agent      # MCP+多模态 Agent（第 25 周）
├── phase5/   # 算法优化 & 前沿研究（ToT / 自学习）
│   ├── 24-tot-agent                 # ToT 深度研究 Agent（第 26 周）
│   └── 25-self-learning-agent       # 自学习经验记忆 Agent（第 27 周）
├── capstone/
│   └── enterprise-agent-platform    # 🏆 企业级多 Agent 智能业务中台
├── docs/
│   └── agent-learning-plan.md       # 📖 完整逐周学习计划
├── README.md
└── LICENSE
```

## 🚀 快速开始

### 环境要求

- Python 3.10+
- Docker + Docker Compose（PostgreSQL / Redis / 向量库）
- Ollama（本地模型：Llama3 / Qwen）
- LangSmith 账号（可观测）

### 使用方式

1. 克隆仓库：`git clone git@github.com:lzcdev/agent_study.git`
2. 完整学习计划见 [docs/agent-learning-plan.md](docs/agent-learning-plan.md)
3. 按周推进：每周进入对应目录，完成该周作业（代码 + README + 指标记录）
4. 每个项目目录自带 README，说明该周学习目标与验收要求

## 📋 每周学习规范

- 每周固定投入 **15～20 小时**
- 所有代码必须写单元测试，不要只跑 Demo
- 每个项目 README 必须包含：**业务场景、架构图、核心指标、运行截图、演示视频链接**
- 量化指标（成功率 / 幻觉率 / Token 消耗）是简历核心亮点，必须记录

## 📖 配套资源

- 官方课程：LangGraph Academy（状态机、持久化、HITL、子图）
- 观测工具：LangSmith、LangFuse
- 评测工具：DeepEval
- 开源参考：DeerFlow、smolagents、CrewAI、AutoGen
- 论文集：ReAct、ToT、Self-Reflection、Multi-Agent Handoff

## 📄 License

[MIT](LICENSE) © 2026 lzcdev
