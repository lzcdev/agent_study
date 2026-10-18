# 高级 Agent 工程师｜完整逐周学习计划

> **总周期**：27 周（不含前置准备 2 周）
> **阶段划分**：5 大阶段 + 压轴 Capstone 项目
> **适配背景**：Vue + Java 后端 + 全栈基础，Python 有基础，重点补异步、Pydantic、工程化
> **目标**：从应用开发 → 框架原理 → 多智能体架构 → 生产级平台 → Agent 算法优化，达到高级 Agent 工程师 / 智能体架构师标准

---

## 📋 总体路线图

| 阶段 | 主题 | 周期 | 产出项目 |
|---|---|---|---|
| 前置 | 基础补齐与环境搭建 | 2 周 | 环境 + SSE 接口 |
| 阶段 1 | 单 Agent 基础 | 4 周 | 项目 1、2、3 |
| 阶段 2 | 多 Agent 协作 | 6 周 | 项目 4、5、6、7 |
| 阶段 3 | Agent 工程化与生产落地 | 8 周 | 项目 8、9、10 |
| 阶段 4 | Agent 架构进阶 & 自研能力 | 7 周 | 项目 11、12、13 |
| 阶段 5 | Agent 算法优化 & 前沿研究 | 6 周 | 项目 14、15 |
| Capstone | 企业级分布式多 Agent 中台 | 贯穿阶段 4、5 | 综合项目 |

---

## 🔧 使用规范（必读）

### 仓库组织

统一一个 GitHub 仓库，命名为 `agent-study`，内部按阶段分文件夹：

```
agent-study/
├── phase1/01-native-react-agent
├── phase1/02-langgraph-basics
├── phase1/03-business-single-agent
├── phase1/04-rag-agent
├── phase2/05-code-multi-agent
├── phase2/06-customer-support-agent
├── phase2/07-contract-review-agent
├── phase2/08-multi-agent-optimization
├── phase3/09-agent-async-task
├── phase3/10-long-running-business-agent
├── phase3/11-agent-fault-tolerance
├── phase3/12-agent-tool-gateway
├── phase3/13-agent-cost-optimize
├── phase3/14-agent-observability
├── phase3/15-agent-eval-basic
├── phase3/16-agent-eval-platform
├── phase4/17-langgraph-source-study
├── phase4/18-custom-agent-runtime
├── phase4/19-event-driven-agent-base
├── phase4/20-distributed-event-agent
├── phase4/21-browser-rpa-agent
├── phase4/22-memory-architecture
├── phase4/23-mcp-multimodal-agent
├── phase5/24-tot-agent
├── phase5/25-self-learning-agent
└── capstone/enterprise-agent-platform
```

### 统一环境

- **编排**：Docker Compose 一键启动 PostgreSQL、Redis、向量库
- **本地模型**：Ollama（Llama3 / Qwen）
- **可观测**：LangSmith 账号
- **每周产出**：可运行代码 + README + 截图 / 演示视频 + 关键指标记录（任务成功率、Token 消耗）

### 学习投入建议

- 每周固定投入 **15～20 小时**；时间紧张可压缩到 10 小时，整体周期相应拉长到约 40 周
- 所有代码必须写单元测试，不要只跑 Demo
- 每个项目 README 必须包含：**业务场景、架构图、核心指标、运行截图、演示视频链接**
- 所有量化指标（成功率、幻觉率、Token 消耗）是简历核心亮点，不要省略

---

# 阶段 0｜前置准备（2 周）

**目标**：补齐基础，搭建环境

## 知识点

1. Python 进阶：`asyncio`、Pydantic v2、异常处理、类型注解、装饰器
2. FastAPI 基础、SSE 流式输出
3. Docker + Docker Compose、Git 规范
4. Ollama 本地部署模型（Llama3 / Qwen）
5. 向量库基础：PGVector 安装

## 参考仓库

- FastAPI 官方示例：`https://github.com/tiangolo/fastapi`
- Pydantic v2 示例
- Ollama：`https://github.com/ollama/ollama`

## 作业

1. 搭建基础环境，docker-compose 启动 PostgreSQL + Redis + PGVector
2. 写一个 FastAPI SSE 接口，Vue 前端对接流式输出（复用 Vue 能力）
3. 调用 Ollama 本地模型，实现基础对话接口

---

# 阶段 1｜单 Agent 基础（4 周，项目 1、2、3）

**目标**：手写原生 Agent + LangGraph 单 Agent + RAG+Agent；掌握 Agent 基础闭环

## 第 1 周｜原生 ReAct，无框架（项目 1）

### 知识点
1. Agent 基础闭环：感知 → 思考 → 动作 → 观察 → 反思
2. ReAct 原理、CoT 基础、Function Calling 思想
3. JSON 解析、异常捕获、LLM 输出格式修复、循环终止条件
4. 纯 Python while 循环实现 Agent 推理循环，**不使用任何 Agent 框架**

### 参考仓库
- `https://github.com/facebookresearch/ReAct`
- `https://github.com/huggingface/smolagents`（极简原生 Agent 参考）

### 作业：项目 1 原生 ReAct 计算器 Agent
1. 手写 ReAct 循环，工具：加法、减法、乘法、除法
2. 自动修复 LLM 输出非法 JSON，增加重试
3. 设置最大循环次数，防止无限循环
4. 写 README，附带测试用例，记录任务成功率
5. 提交到 `phase1/01-native-react-agent`

---

## 第 2 周｜LangGraph 基础：状态机、State、节点、边、条件分支

### 知识点
1. LangGraph 核心概念：StateGraph、自定义 State、节点、边、条件边
2. 基础消息存储、对话记忆
3. LangSmith 接入、链路追踪
4. 自定义工具编写（LangGraph Tool）

### 参考仓库
- LangGraph 官方教程：`https://github.com/langchain-ai/langgraph`
- LangGraph Academy

### 作业
1. 跑通官方基础 chatbot 示例
2. 改造示例：增加自定义工具「获取当前时间」
3. 接入 LangSmith，查看每一步 trace
4. 代码目录：`phase1/02-langgraph-basics`

---

## 第 3 周｜LangGraph 持久化、断点、HITL（项目 2：企业业务单 Agent）

### 知识点
1. LangGraph Checkpointer（Postgres 存储状态、断点续跑）
2. HITL 人机介入：人工暂停、修改状态、继续执行
3. 自定义工具开发：MySQL 查询、Excel 导出、HTTP 调用
4. 异常捕获、超时重试、参数校验

### 参考仓库
- langgraph-postgres-checkpointer 示例
- langgraph-human-in-the-loop

### 作业：项目 2 带记忆+工具调用企业内部数据查询 Agent
1. Agent 工具：MySQL 查询销售数据、导出 Excel
2. 对话短期记忆 + 向量长期用户记忆
3. 接入 FastAPI，SSE 流式输出
4. 对接 Vue 前端对话页面（强项）
5. 支持任务暂停，人工干预修改参数后继续执行
6. 目录：`phase1/03-business-single-agent`

---

## 第 4 周｜RAG + Agent 融合（项目 3：文档智能助手）

### 知识点
1. RAG 完整链路：文档解析、分块、Embedding、PGVector 检索、Rerank 重排
2. Agent 决策逻辑：什么时候检索知识库、什么时候调用搜索、什么时候直接回答
3. 混合检索策略、上下文压缩

### 参考仓库
- LlamaIndex RAG 示例
- langgraph RAG agent 示例

### 作业：项目 3 RAG+Agent 文档助手
1. 上传 PDF 合同文档，自动解析入库
2. Agent 自主判断：是否需要检索知识库
3. 评估 RAG 效果，记录召回率、问答准确率
4. 目录：`phase1/04-rag-agent`

> ✅ **阶段 1 验收**：3 个项目全部可运行；能手写 ReAct；熟练 LangGraph 状态机、checkpoint、HITL

---

# 阶段 2｜多 Agent 协作（6 周，项目 4、5、6、7）

**目标**：4 种主流多 Agent 架构；Supervisor、Handoff、Map-Reduce、Critic 反思

## 第 5 周｜多 Agent 基础：角色分工，CrewAI + LangGraph（项目 4）

### 知识点
1. 多 Agent 基本概念：角色、目标、工具、通信
2. CrewAI 角色编排原理
3. LangGraph 子图 Subgraph 封装、模块化 Agent

### 参考仓库
- `https://github.com/crewAIInc/crewAI`
- langgraph subgraph examples

### 作业：项目 4 科研写作多 Agent（调研+数据分析+撰稿+审核）
1. 4 个角色 Agent，子图封装
2. 并行执行调研任务，最后汇总
3. 目录：`phase2/04-multi-agent-research-writer`

---

## 第 6 周｜Supervisor 主管委派 + 反思 Critic Agent（项目 7）

### 知识点
1. Supervisor 架构：总管 Agent 拆分任务、分发子 Agent、汇总结果
2. Critic 评审 Agent：执行结果校验、幻觉检测、自动纠错
3. 双 Agent 自检闭环

### 参考仓库
- langgraph supervisor example
- Self-Reflection 论文示例

### 作业：项目 7 代码开发多 Agent（主管+编码+评审 Critic）
1. Supervisor 拆分需求，编码 Agent 生成代码
2. Critic 自动评审代码，找出 bug
3. 代码沙箱执行代码，验证运行结果
4. 目录：`phase2/05-code-multi-agent`

---

## 第 7 周｜Handoff 自动转交模式（项目 5：工单客服 Agent）

### 知识点
1. Agent Handoff 自动转交机制
2. 条件路由：根据意图自动切换 Agent
3. 多 Agent 之间消息传递、上下文精简

### 参考仓库
- langgraph handoff examples

### 作业：项目 5 电商售后工单多 Agent
1. 咨询 Agent → 订单查询 Agent → 退款 Agent，自动转交
2. 复杂问题触发 HITL 人工断点
3. 目录：`phase2/06-customer-support-agent`

---

## 第 8 周｜Map-Reduce 并行多 Agent（项目 6：批量合同审阅 Agent）

### 知识点
1. Map-Reduce 架构：任务拆分、子 Agent 并行执行、结果聚合
2. 并发控制、限流、Token 成本控制
3. 批量任务上下文压缩

### 参考仓库
- langgraph map-reduce examples

### 作业：项目 6 批量合同风险抽取 Agent
1. 主 Agent 把多份文档分片，派发给并行子 Agent 抽取风险条款
2. Reduce 阶段合并结果，生成汇总报告
3. 控制并发数量，防止模型 API 超限
4. 目录：`phase2/07-contract-review-agent`

---

## 第 9 周｜多 Agent 痛点专项：上下文治理、死循环、消息冲突

### 知识点
1. Token 爆炸问题：消息摘要、上下文裁剪
2. 多 Agent 死循环检测、循环终止策略
3. 消息标准化，避免消息错乱
4. MCP（Model Context Protocol）基础概念

### 参考仓库
- MCP 官方示例 `https://github.com/modelcontextprotocol`

### 作业
1. 在上面任意多 Agent 项目增加上下文摘要节点
2. 增加死循环检测：统计历史调用次数，重复动作直接终止
3. 把一个工具封装为 MCP 服务，Agent 调用 MCP 工具
4. 目录：`phase2/08-multi-agent-optimization`

---

## 第 10 周｜阶段 2 复盘：多 Agent 项目迭代 + 评测基础

### 知识点
1. LLM-as-Judge 基础评估思路
2. 多 Agent 指标：任务完成率、转交错误率、无效调用次数
3. 整理 4 种多 Agent 架构适用场景对比文档

### 作业
1. 给 4 个多 Agent 项目增加简单自动化评估脚本
2. 写一篇技术文档：4 种多 Agent 架构选型对比
3. 优化所有项目 README，增加演示截图

> ✅ **阶段 2 验收**：4 种多 Agent 架构全部实现；能解决多 Agent 上下文膨胀、死循环；具备 Critic 自检闭环

---

# 阶段 3｜Agent 工程化与生产落地（8 周，项目 8、9、10）

> 高级工程师分水岭：长任务、异步队列、安全、可观测、自动化评测

## 第 11 周｜长任务 + 异步任务队列 Celery+Redis（项目 8 前置）

### 知识点
1. Celery+Redis 任务队列原理、异步后台任务
2. 任务状态持久化、任务幂等性
3. 长任务进度保存、状态快照

### 参考仓库
- Celery 官方示例
- langgraph + celery 集成案例

### 作业
1. 搭建 Celery+Redis 环境，封装异步任务
2. 改造 LangGraph，将 Agent 任务提交到 Celery 后台执行
3. 实现任务状态查询接口
4. 目录：`phase3/09-agent-async-task`

---

## 第 12 周｜项目 8：企业级长周期业务 Agent（断点续跑）

### 知识点
1. LangGraph Postgres Checkpointer 深度使用
2. 任务分片、失败回滚、状态快照回溯
3. 全链路结构化日志

### 参考仓库
- langgraph checkpointer postgres example

### 作业：项目 8 财务对账长任务 Agent
1. 长任务：多步骤财务对账，耗时几十分钟
2. 任务中断后可恢复，不用从头跑
3. FastAPI + Celery + LangGraph + Postgres
4. Vue 前端实时 SSE 展示任务进度
5. 目录：`phase3/10-long-running-business-agent`

---

## 第 13 周｜稳定性、容错、熔断、重试、防注入

### 知识点
1. 多级重试策略、熔断降级、API 限流
2. 提示注入检测、输入过滤、敏感信息脱敏
3. 工具白名单、参数校验

### 参考仓库
- Guardrails AI
- langchain prompt injection defense

### 作业
1. 给项目 8 增加熔断、重试、输入过滤
2. 增加提示注入测试用例，测试防护效果
3. 目录：`phase3/11-agent-fault-tolerance`

---

## 第 14 周｜安全网关、工具调度（项目 9：Agent 工具网关平台）

### 知识点
1. Agent 工具网关架构：统一入口、鉴权、限流、参数校验
2. MCP 工具服务化、工具权限隔离
3. 沙箱安全：代码执行沙箱隔离

### 参考仓库
- MCP tool server examples
- fastapi gateway sample

### 作业：项目 9 Agent 安全网关+工具调度平台
1. 统一网关管理所有 Agent 工具
2. 工具鉴权、白名单、调用频率限制
3. 拦截越权调用、恶意输入
4. 目录：`phase3/12-agent-tool-gateway`

---

## 第 15 周｜性能与成本优化：Token 优化、缓存、模型路由

### 知识点
1. Token 开销优化：上下文摘要、结果缓存
2. 多模型路由：简单任务小模型、复杂推理大模型
3. 流式性能优化、批量请求

### 作业
1. 在项目 8 中增加缓存层，缓存高频工具返回结果
2. 实现模型路由，根据任务复杂度自动选择模型
3. 对比优化前后 token 消耗，记录量化数据
4. 目录：`phase3/13-agent-cost-optimize`

---

## 第 16 周｜可观测体系：LangSmith/LangFuse、监控指标

### 知识点
1. 全链路追踪，每一步 Agent 思考、工具调用记录
2. 核心指标定义：任务成功率、工具错误率、Token 消耗、耗时
3. 指标上报、简单告警

### 作业
1. 把 Agent 链路接入 LangSmith/LangFuse
2. 编写指标采集脚本，导出任务指标
3. 搭建简易监控面板，展示 Agent 运行指标
4. 目录：`phase3/14-agent-observability`

---

## 第 17 周｜Agent 自动化评测体系，DeepEval 基础

### 知识点
1. 评测指标：任务完成率、幻觉率、工具调用准确率
2. DeepEval 使用、LLM-as-Judge 打分
3. 评测数据集构建

### 参考仓库
- `https://github.com/confident-ai/deepeval`

### 作业
1. 构建测试用例集，至少 20 条测试案例
2. 使用 DeepEval 自动评估 Agent 输出，自动打分
3. 目录：`phase3/15-agent-eval-basic`

---

## 第 18 周｜项目 10：Agent 自动化评测平台

### 知识点
1. 批量执行评测任务、自动生成评测报告
2. 版本基线对比、回归测试：迭代后自动跑评测集，检测退化

### 作业：项目 10 Agent 自动化评测平台
1. Web 页面管理评测用例，批量启动评测任务
2. 自动生成报告：成功率、幻觉率、Token 消耗
3. 版本基线对比，保存历史评测结果
4. 目录：`phase3/16-agent-eval-platform`

> ✅ **阶段 3 验收**：3 个生产级项目；长任务断点续跑；安全网关；完整可观测 + 自动化评测平台

---

# 阶段 4｜Agent 架构进阶 & 自研能力（7 周，项目 11、12、13）

## 第 19 周｜LangGraph 源码阅读，理解状态机底层原理

### 知识点
1. 阅读 LangGraph 核心源码：状态流转、图执行引擎、持久化实现
2. 对比：LangGraph / CrewAI / AutoGen / smolagents 优缺点
3. 自定义节点、自定义调度逻辑改造

### 参考仓库
- langgraph 源码仓库

### 作业
1. 阅读 graph、state、checkpointer 核心源码，写源码阅读笔记
2. 给 LangGraph 做一个小插件：自定义日志中间件
3. 目录：`phase4/17-langgraph-source-study`

---

## 第 20 周｜项目 11：自研极简 Agent 状态执行引擎（脱离 LangGraph）

### 知识点
1. 手写轻量状态机：节点、条件分支、循环、状态持久化
2. 支持子图、并行任务、状态快照存储

### 作业：项目 11 自研极简 Agent 引擎
1. 纯 Python 手写状态机，不依赖 LangGraph
2. 实现：状态保存、条件分支、循环、断点恢复
3. 封装成内部 Python 包，可导入使用
4. 目录：`phase4/18-custom-agent-runtime`

---

## 第 21 周｜事件驱动多 Agent 架构，Kafka 消息队列（项目 12 前置）

### 知识点
1. 事件驱动 Agent：消息触发 Agent 任务
2. Kafka 基础、消息消费、幂等、分布式任务调度
3. 多实例 Agent 集群负载均衡

### 参考仓库
- kafka-python 示例

### 作业
1. 搭建 Kafka 本地环境，编写生产者消费者
2. 消息触发 Agent 启动执行任务
3. 目录：`phase4/19-event-driven-agent-base`

---

## 第 22 周｜项目 12：分布式事件驱动工单多 Agent 平台

### 知识点
1. 分布式多 Agent 集群、多实例消费消息
2. 任务幂等，防止重复执行
3. 分布式链路追踪

### 作业：项目 12 事件驱动工单处理平台
1. Kafka 接收工单事件，自动触发多 Agent 处理流程
2. 多实例并发消费，负载均衡
3. 任务幂等设计，避免重复执行
4. 目录：`phase4/20-distributed-event-agent`

---

## 第 23 周｜Browser Agent + Playwright RPA（项目 13）

### 知识点
1. Playwright 网页自动化、网页元素定位
2. Agent 自主规划网页操作步骤
3. 网页操作失败重试、页面自适应

### 参考仓库
- playwright python 示例
- langgraph browser agent

### 作业：项目 13 Browser 网页操作 Agent（RPA+Agent）
1. Agent 自主规划操作步骤，自动打开网页、填写表单、抓取数据
2. 操作失败自动重试，防止死循环
3. 目录：`phase4/21-browser-rpa-agent`

---

## 第 24 周｜记忆系统深度优化：三级记忆架构

### 知识点
1. 三级记忆：短期对话记忆、中期任务状态快照、长期向量经验记忆
2. 记忆检索、记忆压缩、记忆遗忘策略
3. 长上下文混合 RAG + 摘要记忆方案

### 作业
1. 在自研 Agent 引擎上实现完整三级记忆
2. 对比：有无长期记忆的任务完成率差异
3. 目录：`phase4/22-memory-architecture`

---

## 第 25 周｜MCP 深度实践、多模态 Agent 基础

### 知识点
1. MCP 完整协议，搭建 MCP 工具服务
2. 多模态 Agent：OCR、截图识别、图文理解
3. Guardrails 输出约束、强结构化输出

### 作业
1. 把多个工具封装为独立 MCP 服务，Agent 远程调用
2. 实现简单图片单据识别 Agent（OCR + LLM）
3. 目录：`phase4/23-mcp-multimodal-agent`

> ✅ **阶段 4 验收**：自研 Agent 状态机；分布式事件驱动多 Agent；Browser RPA Agent；三级记忆体系

---

# 阶段 5｜Agent 算法优化 + 前沿研究（6 周，项目 14、15）

## 第 26 周｜高级规划算法 ToT 思维树（项目 14）

### 知识点
1. Plan-and-Solve、ToT 思维树、蒙特卡洛树搜索 MCTS
2. 多分支并行搜索、路径剪枝、择优策略
3. ToT 对比 ReAct，量化指标对比

### 参考论文
- Tree of Thoughts
- Plan-and-Solve Prompting

### 作业：项目 14 ToT 深度研究 Agent
1. 实现 ToT 多分支搜索规划，替代线性 ReAct
2. 同一批测试用例，对比 ReAct vs ToT 的任务完成率、幻觉率
3. 目录：`phase5/24-tot-agent`

---

## 第 27 周｜自学习经验记忆多 Agent（项目 15）

### 知识点
1. 任务完成后自动复盘，提取经验存入向量库
2. 同类任务自动检索历史经验，优化规划策略
3. 少量 LoRA 微调基础（可选）

### 参考论文
- Self-Reflection
- Agent Memory Architectures

### 作业：项目 15 自学习多 Agent 系统
1. 每次任务结束自动复盘，保存成功/失败经验到长期向量记忆
2. 新任务自动检索历史经验，优化 prompt 与规划
3. 量化对比：开启经验记忆前后任务成功率
4. 目录：`phase5/25-self-learning-agent`

> ✅ **阶段 5 验收**：ToT 落地；Agent 自反思 + 经验记忆；能够阅读论文并工程化落地

---

# 🎯 压轴 Capstone 项目：企业级分布式多 Agent 智能业务中台

> 不是单独一周完成，**从第 19 周开始持续迭代，每周增加模块，第 27 周完成完整版本**，作为简历王牌项目。

## 模块迭代顺序

1. 基础 Agent 工作流
2. 多 Agent 三层架构（规划层 / 执行层 / 校验层）
3. MCP 工具网关 + 权限安全
4. 三级记忆系统
5. 异步任务 + 断点续跑
6. 可观测与自动化评测平台接入
7. ToT 规划优化、自学习经验记忆
8. Vue 前端 SSE 可视化界面、HITL 人工干预页面
9. Docker Compose 一键部署脚本，完整文档

**仓库目录**：`capstone/enterprise-agent-platform`

---

# 📚 完整技术栈汇总（高级 Agent 工程师标准）

## 1. 编程语言
Python（主力）、TypeScript（前端交互）、Go（可选，高性能运行时）

## 2. Agent 框架（主次分明）
- **主**：LangGraph（生产首选）
- **辅**：CrewAI、AutoGen、LlamaIndex
- **深入**：smolagents、PydanticAI
- **自研**：手写状态机引擎

## 3. 大模型能力
Prompt 工程（CoT/ReAct/ToT）、Function Calling、结构化输出、多模型路由、RAG 全链路、LoRA 微调（少量）

## 4. 存储 & 中间件
- 向量库：PGVector、Qdrant、Milvus
- 关系库：PostgreSQL（存储 Agent 状态）、MySQL
- 缓存 & 队列：Redis、Celery、RabbitMQ、Kafka（分布式事件驱动）

## 5. 工程化 & 运维
FastAPI、异步 IO、SSE 流式输出、Docker、容器编排、日志、链路追踪（LangSmith/LangFuse）、熔断限流、幂等设计

## 6. 安全 & 评测
提示注入防护、工具权限隔离、代码沙箱；DeepEval、LLM-as-Judge、自动化评测集、任务指标量化

## 7. 多 Agent 核心模式
Supervisor 主管委派、Handoff 自动转交、角色分工、Map-Reduce 并行、子图嵌套、事件驱动

---

# ⚠️ 学习优先级 & 避坑提醒

1. **先工程，后算法**：不要一上来啃论文，先把 10 个工程项目全部落地，再做算法优化
2. **深耕 LangGraph，不要浅尝辄止**：当前企业生产环境 90% 基于 LangGraph，吃透状态机、持久化、子图是求职核心
3. **优先补齐全链路工程能力**：绝大多数候选人只会调 Demo，断点续跑、异步长任务、安全管控、自动化评测才是拉开薪资差距的关键
4. **发挥全栈优势**：把 Vue 前端 + Agent 后端打通，做成端到端产品，市面上纯 Python Agent 工程师普遍缺乏前端能力，这是核心竞争力
5. **项目一定要附带量化指标**：每个项目都写明任务成功率提升多少、幻觉下降比例、Token 节省比例，不要只写「实现了 XX 功能」

---

# 📖 配套资源清单

1. **官方课程**：LangGraph Academy（状态机、持久化、HITL、子图）
2. **观测工具**：LangSmith、LangFuse
3. **评测工具**：DeepEval
4. **开源项目参考**：DeerFlow（字节长周期 Agent）、smolagents、CrewAI、AutoGen
5. **论文集**：ReAct、ToT、Self-Reflection、Multi-Agent Handoff 系列

---

## 附：核心参考论文清单

- ReAct: Synergizing Reasoning and Acting in Language Models
- Plan-and-Solve Prompting
- Tree of Thoughts (ToT)
- AutoGPT、GPTs、Multi-Agent Communication
- Self-RAG、Reflection LLM
- Agent Memory Architectures
- MCP Model Context Protocol
- CrewAI Supervisor Handoff 多智能体分工

---

*文档生成时间：2026-10-18*
