# RSI / 自进化相关综述精简报告：26 篇综述的介绍与对比

> 整理自 `RSI_literature_landscape.md` §1.2–1.4（2026-10-28）。21 篇精读（引言、分类法、记忆章节、评测、开放问题），5 篇只看摘要/标题。`*` 表示发表信息来自 PDF 或检索页，未核对论文集；Preprints.org 上的 4 篇均未经同行评审。

---

## 0. 一页总览

- **数量与时间**：2026 年 7–10 月集中出现 6 篇 RSI 专题综述；更早的 self-evolving / self-improvement / memory 综述共 15 篇做了支撑。
- **一条主线**：综述对 RSI 的定义在**收紧**——从"模型用自己的经验变好"（2024，Tao）到"改进机制本身被改，并且这个改动影响下一次改进如何发生"（2026，Liu / AI4AI / Wu / Niu / Zhou）。
- **一个共同结论**：按严格定义，**目前没有系统达到开放式 RSI**（Liu：187 个工作 0 个 L5；AI4AI：35 个系统无一能自己设定目标或反馈）。
- **对记忆的态度**：全部 21 篇把记忆当作 **被改进的对象**（harness / context / asset 的一个组件），没有一篇把记忆当作递归本身的载体；只有 Wu、Ren 留出了"记忆可以是改进者状态"的入口，Hu、Du、Huang 提出了相应愿景。

---

## 1. 五组综述分别讲了什么

### A. RSI 专题综述（6 篇，2026-07 ~ 10）

| 综述 | 出处 · 规模 | 一句话介绍 | 独有贡献 |
|---|---|---|---|
| **Chen, Wang, Qu（UCR）** *RSI in AI: From Bounded Self-Refinement to Autonomous Research Loops* | 2607.07663 · 1,250 篇（74% 发于 2026） | 规模最大的 RSI 文献统计；按"改什么"×"闭环程度（human-in/on/closed）"组织 | **验证层级**：形式化验证 > 可执行可比较 > 自评估，改进强度随之递减；Foundations 仅 60/1,250 是最大空白 |
| **Zhou, Yu 等（PKU/ZJU/NYU）** *Two Perspectives on RSI* | 2610.14625 · 46 页 · ~106 方法 | 4 组 9 维描述框架（更新目标 / 组织方式 / 时机范围 / 反馈与接受准则）+ 深度学习类比视角（Adam→SkillAdam，RL→MemRL，元学习→SEAL） | 指出**接受准则**问题：只看即时分数会拒绝那些只在后续轮次才产生回报的修改 |
| **Liu, Lin, …, Ye（阿里\*）** *The Path to Recursive Self-Improving Agents* | Preprints 202608.0051 · 375 篇参考文献 · 187 个工作分级 | 系统 = (M, H, D, T, Imp)，**RSI 指 Imp 本身可被更新**；仿 SAE J3016 定 L1–L5 | 分级结果：172 个 L3、15 个 L4、**0 个 L5**；所有记忆系统评为 L3 |
| **Wu Kai 等** *AI4AI Survey: From Long-Horizon Agents to RSI* | Preprints 202608.2108 · 369 条记录 · 审计 35 个系统 | D1–D5 五维审计（目标 / 自指 / 各阶段由谁负责 / 信号锚定 / 证据） | **composition gap**；"记忆容量不衡量存下的状态是否有用"；结论 "No current evidence meets all of these conditions" |
| **Wu Hao, …, Wang Kun（P. S. Yu、Q. Yang 参与）** *RSI in AI: A Survey* | Preprints 202609.2680 · 404 篇参考文献 | 三层定义：广义自我改进 / **结构性 RSI** / **经验性 RSI**；状态拆成 solver S 与 improver I；4 种保留模式 | 提出配对探针 Γ_t 衡量改进者质量；逐条质疑 DGM、Hyperagents、STOP 的证据强度 |
| **Wang, Hou, …, Fan** *Diving into Reliable Self-Evolving Agents* | Preprints 202609.0913 · 只读摘要 | L0 输出 / L1 模型 / L2 脚手架 / L3 改进者 / L4 准则 + 可靠性阶梯 | — |

### B. 自进化智能体综述（4 篇）

| 综述 | 出处 · 规模 | 一句话介绍 | 独有贡献 |
|---|---|---|---|
| **Gao 等（清华/普林斯顿）** *A Survey of Self-Evolving Agents* | 2507.21046 · TMLR 2026 · 77 页 | What / When / How / Where 四问框架；三条纳入标准（依赖经验、持久改变策略、自主探索） | **"Retention 是最欠缺的评测维度"**：多数 benchmark 在 episode 间重置状态 |
| **Fang 等（Glasgow）** *Comprehensive Survey of Self-Evolving AI Agents* | 2508.07407 · 55 页 | 三定律 Endure / Excel / Evolve；MOP→MOA→MAO→MASE 发展路径；优化器 = 搜索空间 + 算法 | 优化出的 prompt 和拓扑换骨干模型就失效（注：框架命名前后不一致） |
| **Ren, …, Zhuge, Schmidhuber** *Self-Improvements in Modern Agentic Systems* | 2607.13104 · 97 页 · ~490 篇参考文献 | A_t=(θ_t, Σ_t)，Σ=(prompt, 记忆, 工具, 控制逻辑)；按信号来源 / 按组件两套分类 | meta-level skill 序列化进记忆后"**算子成了自己操作数的一部分**"；critic 必须与生成器解耦 |
| **Wei 等（UIUC/Meta/GDM）** *Agentic Reasoning for LLMs* | 2601.12538 · TMLR\* · 135 页 · 797 篇参考文献 | 基础能力 / 自进化 / 协作三层；自进化 = 反馈 + 记忆 | ⚠️ arXiv 标题含 "Recursively Self-Improving"，正文却无 RSI 讨论，未引 DGM/ADAS/STOP |

### C. LLM 自我改进 / 测试时智能 / 终身学习（5 篇）

| 综述 | 出处 · 规模 | 一句话介绍 | 独有贡献 |
|---|---|---|---|
| **Yang 等（Stony Brook）** *Self-Improvement of LLMs: Technical Overview* | 2603.25681 · TMLR 2026\* · 135 页 | 闭环生命周期：数据获取 → 选择 → 模型优化 → 推理精炼 + 自主评估层 | 自进化优化"最不成熟"；增益上限受**验证器保真度**约束；多数投票自奖励会 reward hacking |
| **Niu 等（华南理工/NTU）** *Self-Improving Test-Time Intelligence* | 2609.01679 · 76 页 · 512 篇参考文献 | Update × Compute；TTL 四维（反馈 / 更新目标 / 时间范围 / 目标范围） | 最简洁的 RSI 判据："**一次保留下来的修改，是否改变了下一次改进是如何产生的**" |
| **Tao 等（北大/阿里）** *Survey on Self-Evolution of LLMs* | 2404.14387 · 2024 | 最早的框架：经验获取 → 精炼 → 更新 → 评估；自主性低/中/高 | 方法"超过三轮就很难再提升"，可能因自我评判者没跟着进化 |
| **Zheng 等（华南理工）** *Lifelong Learning of LLM Agents* | 2501.07278 · 360 篇参考文献 | 感知 / 记忆 / 行动；记忆是"脊梁" | 列出记忆架构专门化、动态管理、神经启发巩固等方向 |
| **Deng 等（UTD）** *Self-Improvement in MLLMs* | 2510.02665 | 只算参数更新，**脚注明确排除记忆** | 种子模型越强增益越小；同一 judge 既筛数据又评测会虚高 |

### D. 记忆综述（3 篇）

| 综述 | 出处 · 规模 | 分类维度 | 对"自我演化的记忆"的态度 |
|---|---|---|---|
| **Hu 等（NUS）** *Memory in the Age of AI Agents* | 2512.13564 · 107 页 · ~470 篇参考文献 | Forms × Functions × Dynamics | 演化多停留在内容层且人工设计；架构演化只一句话提 MemEvolve；§7.3 路线图终点是 "**self-designing memory architecture**" |
| **Huang 等（UIC，P. S. Yu）** *Agent Memory in the Second Half* | 2602.06052 · TMLR 2026\* · 分析 218 篇 | 载体 × 认知机制 × 主体 + 操作策略 | 未引 MemEvolve/ALMA；prompt 驱动法"缺少显式信用分配"；记忆演化与推理行为的耦合"理解得很差"，有"不受控漂移"风险 |
| **Du（HKRITA）** *Memory for Autonomous LLM Agents* | 2603.07670 · 15 页 | 时间范围 × 表示载体 × 控制策略 | 控制策略"最关键也最少被讨论"；§9.9 设想 "task-agnostic memory controller"；"Nobody evaluates forgetting well"（LoCoMo 近满分 → MemoryArena 仅 40–60%） |

### E. 相邻综述（4 篇）

| 综述 | 出处 · 规模 | 与本课题相关的点 |
|---|---|---|
| **Zhou 等（南京理工）** *Self-Evolving Coding Agents* | 2608.03392 · 108 个方法（75 个来自 2026） | 2026 年 75 篇中 **69 篇改资产或架构，仅 6 篇改权重**；每条记忆 = (知识, 证据, 适用条件)；区分行为变化 δ_t 与增益 ΔJ_t；EvoMap 150 万共享资产 98% 从未复用 |
| **Guo 等（城大）** *Agent System and Harness Design* | 2606.20683 · 262 篇参考文献 | harness 六元组；Terminal-Bench 2.0 同一模型换 harness 中位差 13.6%；受约束自进化 VerifyRetain |
| **Chen 等（浙大）** *Safety in Self-Evolving Agents* | 2610.00093 · 编码 683 篇 | SAVER 框架；记忆投毒、**权限坍塌**（整合时丢失使用范围约束）、EvoBreak；"遗忘 = 撤回影响，而不只是删记录" |
| **Chen 等** *The Horizon Gap* | 2608.06663 · 1,547 篇 | 区分长程（任务属性）/ 长上下文（模型属性）/ 长期记忆（系统属性）；"跨任务持久"这一列最稀疏 |

**只看标题/摘要的 4 篇**：*Externalization in LLM Agents*（2604.08224）、*Self-Evolving Agents as Dynamic Graph Transformation*（2608.18104）、*The Last AI Built by Humans*（2609.11873，RSI 路线图）、*Towards Long-Horizon Agents*（Preprints 202607.1328）。

---

## 2. 横向对比

### 2.1 RSI 定义的宽严谱

| 宽 | 中 | 严 |
|---|---|---|
| **Gao、Fang、Chen-UCR、Tao**：输出精炼、任务内 ICL 也算自我改进 | **Ren**：full scaffolding 才最接近 RSI；**Yang、Niu**：强调自主性 + 连续性 | **Liu**（Imp 可被更新）、**AI4AI**（自指 + 生产过程可编辑 + 证据四检）、**Wu**（结构性 vs 经验性）、**Niu**（保留的修改改变下一次改进）、**Zhou**（修改 → 保留 → 再修改） |

趋势：2024 → 2026，重心从"模型变好"转向"改进机制本身是否可变"，并开始要求**证据**（Wu 的 Γ_t、AI4AI 的 D5）而非仅结构。

### 2.2 组织方式对比

| 维度 | 代表综述 | 做法 |
|---|---|---|
| **单一分级** | Liu（L1–L5）、Wang（L0–L4） | 一条自主性 / 递归深度轴，便于给工作打标签 |
| **多维描述** | Zhou（9 维）、AI4AI（D1–D5）、Wu（目标 × 对象 × 保留模式） | 明确反对把改进压缩成一个分数 |
| **按改进对象** | Gao（What）、Ren（组件）、Fang（单/多智能体）、Zhou-Coding（资产/架构/模型） | 适合写 related work 的"改什么"段 |
| **按流程阶段** | Yang、Tao（获取 → 精炼 → 更新 → 评估）、Liu（Diagnose → Propose → Evaluate → Integrate） | 适合定位自己方法处在哪一步 |
| **按风险** | Chen-Safety（SAVER） | 载体 × 操作 → 违规 → 暴露 → 响应 |

### 2.3 记忆被放在哪里

| 位置 | 综述 |
|---|---|
| harness / scaffolding 组件 | Chen-UCR、Liu、AI4AI、Guo、Ren |
| context 下与 prompt 并列 | Gao（"多数情况下可互换"）、Fang |
| 非参数 artifact 之一 | Zhou-RSI（5 种之一）、Zhou-Coding（资产） |
| 一等可写状态 | Niu、Hu、Huang、Du、Zheng |
| 推理精炼下的次级模块 | Yang |
| **明确排除** | Deng |
| **可以属于改进者**（入口） | **Wu**（指导诊断 / 更新选择即属 improver）、**Ren**（算子成为操作数） |

### 2.4 共识（几乎所有综述都同意）

1. **验证信号质量决定改进上限**——Chen-UCR 验证层级、Yang 验证器保真度、Deng "可靠验证是前提"、Ren critic 抗利用性，说的是同一件事。
2. **没有系统达到开放式 RSI**——Liu 0 个 L5；AI4AI 无一闭环；Wu 质疑 DGM / Hyperagents / STOP 的证据。
3. **harness 与预算的影响大于多数方法增益**——Guo 13.6% 中位差、AI4AI 最多 28 点、Zhou-Coding "演化 harness 不稳定胜过测试时搜索"。必须同预算比较。
4. **纵向评测最缺**——Gao "retention 最欠缺"、Huang "benchmark 以重置为中心"、Du "没人评测好遗忘"、Horizon Gap "跨任务持久最稀疏"。
5. **记忆会先升后降 / 越长越没用**——Wu、AI4AI、Gao（经验回放阈值）、Niu（陈旧、污染、膨胀）、Zhou-Coding（98% 资产从未复用）。

### 2.5 分歧

| 议题 | 一方 | 另一方 |
|---|---|---|
| 分级 vs 多维 | Liu、Wang 用单一阶梯 | AI4AI、Wu、Zhou 明确反对单分数 |
| 输出精炼算不算自我改进 | Chen-UCR、Gao 算 | AI4AI、Wu 不算；Reflexion、MemGPT 只是固定 harness |
| 记忆是改进者还是对象 | 主流（Liu："固定决策规则下积累记忆 = L3"） | Wu、Ren 留出入口 |
| 记忆演化的终点 | Hu：自设计记忆架构（RL 驱动） | Du：任务无关记忆控制器；Huang：记忆与策略联合元学习 |
| RSI 的证据标准 | Chen-UCR 定性规律即可 | Wu 要求配对探针 Γ_t；AI4AI 要求增益 / 保持 / 与人类对比 / 迁移四检 |

---

## 3. 对 memory-RSI 论文的直接含义

1. **定位要先过严口径**：引用 Liu 的 L3 判定和 Niu 的判据，承认"在固定规则下演化记忆内容"不算 RSI，再说明你的工作改的是**记忆管理算法 / 改进者状态**（Wu 的 solver–improver 划分是现成的理论入口）。
2. **related work 可直接借用的框架**：Zhou-RSI 9 维（尤其"接受准则"）、Wu 的 4 种保留模式、Hu §7.3 路线图、Du 的四层指标体系。
3. **必须回应的综述级批评**：
   - 只报容量不报有用性（AI4AI）→ 报有用性 / 复用率；
   - 内容 vs 管理算法未消融（Wu）→ 冻结 admission / retrieval / consolidation / content 中一项、变化其余；
   - 无 retention 评测（Gao、Huang、Du）→ 跨 episode 不重置、报遗忘；
   - 权限坍塌 / 记忆投毒（Chen-Safety）→ 至少讨论；
   - 同预算比较（Guo、AI4AI、Zhou-Coding）。
4. **可引的愿景句**：Hu "self-designing memory architecture"、Du "task-agnostic memory controller"、Ren "算子成为自己操作数的一部分"、Huang "记忆与策略联合元学习"——都在"开放问题"节，说明空白被综述承认但尚无系统性工作。

---

## 4. 引用时的注意事项

- **Wei (2601.12538)**：标题含 RSI，正文无 RSI 内容，不要作为 RSI 定义来源引用。
- **Fang (2508.07407)**：§3 与结论对框架四组件的命名不一致，引用时核对版本。
- **Deng (2510.02665)**：脚注排除记忆，不适合作为记忆相关论断的出处。
- **Wang (202609.0913)**：只读了摘要，分级细节待核。
- **Liu、AI4AI、Wu、Wang、Towards Long-Horizon** 均在 Preprints.org，无同行评审；**Huang、Yang、Wei** 的 TMLR 信息带 `*`，未核对论文集。
- **Huang (2602.06052)** 未引 MemEvolve / ALMA，**Hu (2512.13564)** 仅一句提 MemEvolve——两篇记忆综述对"记忆架构演化"覆盖都很薄，这本身可作为空白的证据。
