# Awesome-LLM-Agent-Harness [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
---

## Scope

This repository collects papers, systems, benchmarks, and related resources on the **LLM agent harness**: the external executable layer that turns a language model into an agent by organizing control flow, tools, memory, state, validation, repair, safety, and human oversight.

The list is organized through the **Human-Machine Task Contract**: how responsibility is assigned among the human, the LLM, the tool/environment, and the harness itself. We include work where the external system around the model materially changes agent behavior; we avoid generic agent demos, prompt-only methods, and broad product lists without reusable harness mechanisms.

---

## Human-Machine Task Contract Taxonomy

```
LLM Agent Harness
├── 1. Core Surveys and Position Papers
├── 2. Harness Foundations: Reasoning–Acting Loops
│   ├── ReAct / reflection / planning loops
│   └── Search, compiler-style control, and structured LM programs
├── 3. Execution and Orchestration Harnesses
│   ├── Agent runtimes and workflow graphs
│   └── Multi-agent orchestration and software-agent platforms
├── 4. Code-as-Harness and Program-Controlled Agents
│   ├── Code-first harness synthesis
│   └── Programmatic LM pipelines and controllers
├── 5. Tool Interface, Action Validity, and Sandboxing
│   ├── Tool-use interfaces and API agents
│   └── Action spaces, ACIs, function calling, and sandboxes
├── 6. Context, Memory, and State Management
├── 7. Verification, Failure Diagnosis, and Repair
├── 8. Human-in-the-Loop, Oversight, and Contract Governance
├── 9. Policy, Safety, and Constraint Enforcement
├── 10. Benchmarks and Evaluation Environments
└── 11. Domain-Specific Harnesses
```

---

## Contents

- [Scope](#scope)
- [Human-Machine Task Contract Taxonomy](#humanmachinetask-contract-taxonomy)
- [Harness Papers and Systems](#harness-papers-and-systems)
  - [1. Core Surveys and Position Papers](#1-core-surveys-and-position-papers)
  - [2. Harness Foundations: Reasoning–Acting Loops](#2-harness-foundations-reasoning-acting-loops)
  - [3. Execution and Orchestration Harnesses](#3-execution-and-orchestration-harnesses)
  - [4. Code-as-Harness and Program-Controlled Agents](#4-code-as-harness-and-program-controlled-agents)
  - [5. Tool Interface, Action Validity, and Sandboxing](#5-tool-interface-action-validity-and-sandboxing)
  - [6. Context, Memory, and State Management](#6-context-memory-and-state-management)
  - [7. Verification, Failure Diagnosis, and Repair](#7-verification-failure-diagnosis-and-repair)
  - [8. Human-in-the-Loop, Oversight, and Contract Governance](#8-human-in-the-loop-oversight-and-contract-governance)
  - [9. Policy, Safety, and Constraint Enforcement](#9-policy-safety-and-constraint-enforcement)
  - [10. Benchmarks and Evaluation Environments](#10-benchmarks-and-evaluation-environments)
  - [11. Domain-Specific Harnesses](#11-domain-specific-harnesses)
- [Benchmarks](#benchmarks)
- [Related Repositories](#related-repositories)

---

## Harness Papers and Systems

Each entry is placed under its primary harness role. Some systems naturally span multiple roles; for readability, they are listed once in the section where their harness contribution is most central.

### 1. Core Surveys and Position Papers

Foundational surveys and position papers that define the harness space, its neighboring areas, and the evaluation vocabulary needed to distinguish harness design from generic agent capability.

<details>
<summary><b>Core Surveys and Position Papers</b></summary>

- [Agent Harness for Large Language Model Agents: A Survey](https://www.preprints.org/manuscript/202604.0428) (2026; Preprints.org survey) [Code](https://github.com/Gloriaameng/Awesome-Agent-Harness)
- [Agent Systems with Harness Engineering](https://openreview.net/pdf/8bb940ad082fed1f1e2c0a132c0c5b4aa4c9d21c.pdf) (2026; OpenReview preprint / survey) [Code](https://github.com/RUCAIBox/awesome-agent-harness)
- [From Static Templates to Dynamic Runtime Graphs: A Survey of Workflow Optimization for LLM Agents](https://arxiv.org/abs/2603.22386) (2026; arXiv preprint)
- [Tool Learning with Large Language Models: A Survey](https://arxiv.org/abs/2405.17935) (2024; arXiv preprint)
- [Understanding the planning of LLM agents: A survey](https://arxiv.org/abs/2402.02716) (2024; arXiv preprint)
- [What Are Tools Anyway? A Survey from the Language Model Perspective](https://arxiv.org/abs/2403.15452) (2024; COLM / arXiv)
- [A Survey on Evaluation of LLM-based Agents](https://arxiv.org/abs/2503.16416) (2025; arXiv preprint)
- [The Evolution of Tool Use in LLM Agents: From Single-Tool to Multi-Tool Usage](https://arxiv.org/abs/2603.22862) (2026; arXiv preprint)
- [LLM-Based Human-Agent Collaboration and Interaction Systems](https://arxiv.org/abs/2505.00753) (2025; arXiv preprint)
- [Memory for Autonomous LLM Agents: Mechanisms, Evaluation, and Emerging Frontiers](https://arxiv.org/abs/2603.07670) (2026; arXiv preprint)

</details>

---

### 2. Harness Foundations: Reasoning–Acting Loops

Early and foundational mechanisms that externalize reasoning, planning, search, reflection, or program control beyond a single model call. These works are included when the loop or controller is part of the method, not just a prompting trick.

<details>
<summary><b>Harness Foundations: Reasoning–Acting Loops</b></summary>

- [An LLM Compiler for Parallel Function Calling](https://arxiv.org/abs/2312.04511) (2023; arXiv preprint) [Code](https://github.com/SqueezeAILab/LLMCompiler)
- [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines](https://arxiv.org/abs/2310.03714) (2023; arXiv preprint) [Code](https://github.com/stanfordnlp/dspy) [Project](https://dspy.ai)
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://openreview.net/forum?id=WE_vluYUL-X) (2023; ICLR 2023) [Code](https://github.com/ysymyth/ReAct) [Project](https://research.google/blog/react-synergizing-reasoning-and-acting-in-language-models/)
- [MRKL Systems](https://arxiv.org/abs/2205.00445) (2022; arXiv preprint)
- [Prompting Is Programming: A Query Language for Large Language Models](https://arxiv.org/abs/2212.06094) (2022; arXiv preprint) [Code](https://github.com/eth-sri/lmql)
- [CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing](https://arxiv.org/abs/2305.11738) (2023; ICLR / arXiv)
- [ReWOO: Decoupling Reasoning from Observations for Efficient Augmented Language Models](https://arxiv.org/abs/2305.18323) (2023; arXiv preprint)
- [SGLang: Efficient Execution of Structured Language Model Programs](https://arxiv.org/abs/2312.07104) (2023; arXiv preprint) [Code](https://github.com/sgl-project/sglang) [Project](https://www.sglang.io)
- [Tree Search for Language Model Agents](https://arxiv.org/abs/2407.01476) (2024; arXiv preprint) [Project](https://jykoh.com/search-agents)
- [Self-Refine: Iterative Refinement with Self-Feedback](https://arxiv.org/abs/2303.17651) (2023; arXiv preprint)

</details>

---

### 3. Execution and Orchestration Harnesses

Systems that manage control flow, roles, task routing, execution state, multi-agent coordination, or long-running workflows. This is the main systems layer of the harness.

<details>
<summary><b>Execution and Orchestration Harnesses</b></summary>

- [AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation](https://arxiv.org/abs/2308.08155) (2023; arXiv preprint / OpenReview) [Code](https://github.com/microsoft/autogen) [Project](https://microsoft.github.io/autogen/stable//index.html)
- [TaskWeaver: A Code-First Agent Framework](https://arxiv.org/abs/2311.17541) (2023; arXiv preprint) [Code](https://github.com/microsoft/TaskWeaver) [Project](https://microsoft.github.io/TaskWeaver/)
- [LangGraph](https://docs.langchain.com/oss/python/langgraph/overview) (2024; Official docs / OSS runtime) [Code](https://github.com/langchain-ai/langgraph) [Project](https://www.langchain.com/langgraph)
- [OpenHands: An Open Platform for AI Software Developers as Generalist Agents](https://arxiv.org/abs/2407.16741) (2024; arXiv preprint) [Code](https://github.com/OpenHands/openhands) [Project](https://docs.openhands.dev/overview/introduction)
- [LLM-as-Code: Agentic Programming for Agent Harness](https://arxiv.org/html/2606.15874v1) (2026; KDD 2026 AgenticSE workshop per paper page)
- [Natural-Language Agent Harnesses](https://arxiv.org/abs/2603.25723) (2026; arXiv preprint) [Code](https://github.com/curated-skills/natural-language-agent-harnesses)
- [ChatDev: Communicative Agents for Software Development](https://arxiv.org/abs/2307.07924) (2023; arXiv preprint) [Code](https://github.com/OpenBMB/ChatDev) [Project](https://chatdev.ai/)
- [MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352) (2023; arXiv preprint) [Code](https://github.com/geekan/MetaGPT)
- [AgentScope: A Flexible yet Robust Multi-Agent Platform](https://arxiv.org/abs/2402.14034) (2024; arXiv preprint) [Code](https://github.com/agentscope-ai/agentscope)
- [AgentVerse: Facilitating Multi-Agent Collaboration and Exploring Emergent Behaviors](https://arxiv.org/abs/2308.10848) (2023; arXiv preprint) [Code](https://github.com/openbmb/agentverse)
- [CAMEL: Communicative Agents for Mind Exploration of Large Language Model Society](https://arxiv.org/abs/2303.17760) (2023; arXiv preprint) [Code](https://github.com/camel-ai/camel) [Project](https://www.camel-ai.org)
- [Solving AI Tasks with ChatGPT and its Friends in Hugging Face](https://arxiv.org/abs/2303.17580) (2023; arXiv preprint)
- [TaskMatrix.AI: Completing Tasks by Connecting Foundation Models with Millions of APIs](https://arxiv.org/abs/2303.16434) (2023; arXiv preprint)

</details>

---

### 4. Code-as-Harness and Program-Controlled Agents

Works where code, declarative programs, or runtime graphs become the primary substrate for harness logic. The key issue is whether the external program owns control, constraints, optimization, or execution structure.

<details>
<summary><b>Code-as-Harness and Program-Controlled Agents</b></summary>

- [AutoHarness: improving LLM agents by automatically synthesizing a code harness](https://arxiv.org/abs/2603.03329) (2026; arXiv preprint)
- [Code as Agent Harness](https://arxiv.org/abs/2605.18747) (2026; arXiv preprint)
- [HarnessBridge: Learnable Bidirectional Controller for LLM Agent Harness](https://arxiv.org/abs/2606.12882) (2026; arXiv preprint)
- [HarnessX: A Composable, Adaptive, and Evolvable Agent Harness Foundry](https://arxiv.org/abs/2606.14249) (2026; arXiv preprint)
- [Meta-Harness: End-to-End Optimization of Model Harnesses](https://arxiv.org/abs/2603.28052) (2026; arXiv preprint) [Code](https://github.com/stanford-iris-lab/meta-harness) [Project](https://arxiv.org/pdf/2603.28052)

</details>

---

### 5. Tool Interface, Action Validity, and Sandboxing

Papers and systems that define how agents see, select, validate, and execute actions through APIs, tools, browsers, terminals, operating systems, or function-calling interfaces.

<details>
<summary><b>Tool Interface, Action Validity, and Sandboxing</b></summary>

- [SWE-agent: Agent-Computer Interfaces Enable Automated Software Engineering](https://proceedings.neurips.cc/paper_files/paper/2024/file/5a7c947568c1b1328ccc5230172e1e7c-Paper-Conference.pdf) (2024; NeurIPS 2024) [Code](https://github.com/swe-agent/swe-agent) [Project](https://swe-agent.com/latest/)
- [Toolformer: Language Models Can Teach Themselves to Use Tools](https://papers.nips.cc/paper_files/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html) (2023; NeurIPS 2023)
- [API-Bank: A Comprehensive Benchmark for Tool-Augmented LLMs](https://arxiv.org/abs/2304.08244) (2023; arXiv preprint)
- [Gorilla: Large Language Model Connected with Massive APIs](https://arxiv.org/abs/2305.15334) (2023; arXiv preprint) [Code](https://github.com/ShishirPatil/gorilla) [Project](https://gorilla.cs.berkeley.edu)
- [ToolLLM: Facilitating Large Language Models to Master 16000+ Real-world APIs](https://arxiv.org/abs/2307.16789) (2023; ICLR / arXiv) [Code](https://github.com/openbmb/toolbench)
- [MINT: Evaluating LLMs in Multi-turn Interaction with Tools and Language Feedback](https://arxiv.org/abs/2309.10691) (2023; ICLR / arXiv)
- [MetaTool Benchmark for Large Language Models: Deciding Whether to Use Tools and Which to Use](https://arxiv.org/abs/2310.03128) (2023; arXiv preprint)
- [ToolTalk: Evaluating Tool-Usage in a Conversational Setting](https://arxiv.org/abs/2311.10775) (2023; arXiv preprint) [Code](https://github.com/microsoft/ToolTalk)
- [Berkeley Function Calling Leaderboard](https://gorilla.cs.berkeley.edu/blogs/8_berkeley_function_calling_leaderboard.html) (2024; official benchmark page) [Project](https://gorilla.cs.berkeley.edu/leaderboard.html)
- [StableToolBench: Towards Stable Large-Scale Benchmarking on Tool Learning of Large Language Models](https://arxiv.org/abs/2403.07714) (2024; arXiv preprint) [Code](https://github.com/THUNLP-MT/StableToolBench) [Project](https://huggingface.co/stabletoolbench)
- [MTU-Bench: A Multi-granularity Tool-Use Benchmark for Large Language Models](https://arxiv.org/abs/2410.11710) (2024; arXiv preprint)
- [ACEBench: Who Wins the Match Point in Tool Usage?](https://arxiv.org/abs/2501.12851) (2025; arXiv preprint)
- [ToolHop: A Query-Driven Benchmark for Evaluating Large Language Models in Multi-Hop Tool Use](https://arxiv.org/abs/2501.02506) (2025; arXiv preprint) [Dataset](https://huggingface.co/datasets/bytedance-research/ToolHop)
- [On the Robustness of Agentic Function Calling](https://arxiv.org/abs/2504.00914) (2025; arXiv preprint)

</details>

---

### 6. Context, Memory, and State Management

Work on persistent state, episodic memory, skill libraries, context selection, and agent memory policies. These entries are included when memory changes the execution trajectory or contract boundary, not merely when retrieval improves a static answer.

<details>
<summary><b>Context, Memory, and State Management</b></summary>

- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://openreview.net/forum?id=vAElhFcKW6) (2023; NeurIPS 2023) [Code](https://github.com/noahshinn/reflexion)
- [Cognitive Architectures for Language Agents](https://arxiv.org/abs/2309.02427) (2023; arXiv preprint)
- [ExpeL: LLM Agents Are Experiential Learners](https://arxiv.org/abs/2308.10144) (2023; AAAI / arXiv)
- [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442) (2023; arXiv preprint)
- [MemGPT: Towards LLMs as Operating Systems](https://arxiv.org/abs/2310.08560) (2023; arXiv preprint) [Code](https://github.com/letta-ai/letta) [Project](https://memgpt.ai)
- [Voyager](https://arxiv.org/abs/2305.16291) (2023; arXiv preprint) [Code](https://github.com/minedojo/voyager) [Project](https://voyager.minedojo.org/)
- [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://arxiv.org/abs/2305.10250) (2023; AAAI / arXiv)
- [A-Mem: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110) (2025; arXiv preprint)

</details>

---

### 7. Verification, Failure Diagnosis, and Repair

Methods that inspect traces, validate intermediate steps, diagnose execution failures, repair trajectories, or improve harnesses through observability. This section is intentionally strict because repair is central to accountable agent behavior.

<details>
<summary><b>Verification, Failure Diagnosis, and Repair</b></summary>

- [Debug like a Human: A Large Language Model Debugger via Verifying Runtime Execution Step-by-step](https://arxiv.org/abs/2402.16906) (2024; arXiv preprint)
- [RGD: Multi-LLM Based Agent Debugger via Refinement and Generation Distillation](https://arxiv.org/abs/2410.01242) (2024; arXiv preprint)
- [Advancing Mobile GUI Agents: A Verifier-Driven Approach to Practical Deployment](https://arxiv.org/abs/2503.15937) (2025; arXiv preprint)
- [Self-Challenging Language Model Agents](https://arxiv.org/abs/2506.01716) (2025; arXiv preprint)
- [CWM: Contrastive World Models for Action Feasibility in Language Agents](https://arxiv.org/abs/2602.22452) (2026; arXiv preprint)
- [Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses](https://arxiv.org/abs/2604.25850) (2026; arXiv preprint) [Code](https://github.com/china-qijizhifeng/agentic-harness-engineering)
- [From Failed Trajectories to Reliable LLM Agents: Diagnosing and Repairing Harness Flaws](https://arxiv.org/abs/2606.06324) (2026; arXiv preprint)
- [Self-Harness: Harnesses That Improve Themselves](https://arxiv.org/abs/2606.09498) (2026; arXiv preprint)
- [Harness-Bench: Measuring Harness Effects across Models in Realistic Agent Workflows](https://arxiv.org/abs/2605.27922) (2026; arXiv preprint)

</details>

---

### 8. Human-in-the-Loop, Oversight, and Contract Governance

Work on where humans specify goals, approve actions, correct failures, supervise agents, or participate in mixed-initiative workflows. This section covers the human side of the contract rather than generic human-AI interaction.

<details>
<summary><b>Human-in-the-Loop, Oversight, and Contract Governance</b></summary>

- [Human-In-the-Loop Software Development Agents](https://arxiv.org/abs/2411.12924) (2024; arXiv preprint)
- [An Interactive Gym Environment for User-Centric Agents](https://arxiv.org/abs/2507.22034) (2025; arXiv preprint)
- [Learning to Cooperate with Humans using Generative Agents](https://arxiv.org/abs/2411.13934) (2024; arXiv preprint)
- [RealUserSim: Bridging the Reality Gap in Agent Evaluation with Grounded User Simulation](https://arxiv.org/abs/2605.20204) (2026; arXiv preprint)
- [Structuring and Managing Context for Human-AI Knowledge Work](https://arxiv.org/abs/2604.07121) (2026; arXiv preprint)

</details>

---

### 9. Policy, Safety, and Constraint Enforcement

Research on guardrails, prompt-injection defenses, privacy, permissions, policy engines, containment, and sandboxing. The focus is operational enforcement across tool use and execution, not abstract safety discussion alone.

<details>
<summary><b>Policy, Safety, and Constraint Enforcement</b></summary>

- [ToolEmu: Identifying the Risks of LM Agents with an LM-Emulated Sandbox](https://arxiv.org/abs/2309.15817) (2024; arXiv preprint) [Code](https://github.com/ryoungj/toolemu)
- [AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents](https://github.com/ethz-spylab/agentdojo) (2024; NeurIPS 2024 D&B) [Code](https://github.com/ethz-spylab/agentdojo)
- [Agent Security Bench (ASB): Formalizing and Benchmarking Attacks and Defenses in LLM-based Agents](https://arxiv.org/abs/2410.02644) (2024; arXiv preprint) [Code](https://github.com/agiresearch/ASB)
- [Dissecting Adversarial Robustness of Multimodal LM Agents](https://arxiv.org/abs/2406.12814) (2024; arXiv preprint)
- [GuardAgent: Safeguard LLM Agents by a Guard Agent via Knowledge-Enabled Reasoning](https://arxiv.org/abs/2406.09187) (2024; arXiv preprint) [Code](https://github.com/guardagent/code)
- [ceLLMate: Sandboxing Browser AI Agents](https://arxiv.org/abs/2512.12594) (2025; arXiv preprint) [Project](https://cellmate-sandbox.github.io/)
- [AgentSCOPE: Evaluating Contextual Privacy Across Agentic Workflows](https://arxiv.org/abs/2603.04902) (2026; arXiv preprint)
- [Security Analysis of the Model Context Protocol](https://arxiv.org/abs/2601.17549) (2026; arXiv preprint)
- [ActPlane: Programmable OS-Level Policy Enforcement for Agent Harnesses](https://arxiv.org/html/2606.25189v1) (2026; arXiv preprint) [Project](https://eunomia.dev/actplane/)
- [From Assistant to Double Agent: Formalizing and Benchmarking Attacks on OpenClaw for Personalized Local AI Agent](https://arxiv.org/abs/2602.08412) (2026; arXiv preprint) [Code](https://github.com/AstorYH/PASB)

</details>

---

### 10. Benchmarks and Evaluation Environments

Benchmarks and environments where harness design is empirically visible: stateful tasks, tool-mediated execution, browser or OS actions, hidden environment state, multi-turn interaction, safety attacks, or long-horizon recovery.

<details>
<summary><b>Benchmarks and Evaluation Environments</b></summary>

- [AgentBench: Evaluating LLMs as Agents](https://openreview.net/forum?id=zAdUB0aCTQ) (2023; OpenReview / arXiv) [Code](https://github.com/THUDM/AgentBench)
- [AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents](https://github.com/ethz-spylab/agentdojo) (2024; NeurIPS 2024 D&B) [Code](https://github.com/ethz-spylab/agentdojo) [Project](https://github.com/ethz-spylab/agentdojo)
- [AppWorld: A Controllable World of Apps and People for Benchmarking Interactive Coding Agents](https://aclanthology.org/2024.acl-long.850/) (2024; ACL 2024) [Code](https://github.com/StonyBrookNLP/appworld) [Project](https://appworld.dev/)
- [GAIA: A Benchmark for General AI Assistants](https://proceedings.iclr.cc/paper_files/paper/2024/file/25ae35b5b1738d80f1f03a8713e405ec-Paper-Conference.pdf) (2024; ICLR 2024) [Code](https://huggingface.co/gaia-benchmark) [Project](https://hal.cs.princeton.edu/gaia)
- [OSWorld: Benchmarking Multimodal Agents for Open-Ended Tasks in Real Computer Environments](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5d413e48f84dc61244b6be550f1cd8f5-Abstract-Datasets_and_Benchmarks_Track.html) (2024; NeurIPS 2024 D&B) [Code](https://github.com/xlang-ai/osworld)
- [The BrowserGym Ecosystem for Web Agent Research](https://arxiv.org/abs/2412.05467) (2024; arXiv preprint) [Code](https://github.com/ServiceNow/BrowserGym)
- [ToolSandbox: A Stateful, Conversational, Interactive Evaluation Benchmark for LLM Tool Use Capabilities](https://arxiv.org/abs/2408.04682) (2024; arXiv preprint) [Code](https://github.com/apple/ToolSandbox) [Project](https://machinelearning.apple.com/research/toolsandbox-stateful-conversational-llm-benchmark)
- [WebArena: A Realistic Web Environment for Building Autonomous Agents](https://arxiv.org/abs/2307.13854) (2024; NeurIPS 2024 Oral per project site) [Code](https://github.com/web-arena-x/webarena) [Project](https://webarena.dev/)
- [WorkArena: How Capable are Web Agents at Solving Common Knowledge Work Tasks?](https://proceedings.mlr.press/v235/drouin24a.html) (2024; ICML 2024) [Code](https://github.com/ServiceNow/workarena) [Project](https://servicenow.github.io/WorkArena/)
- [tau-bench](https://huggingface.co/papers/2406.12045) (2024; arXiv preprint) [Code](https://github.com/sierra-research/tau-bench) [Project](https://github.com/sierra-research/tau2-bench)
- [Mind2Web: Towards a Generalist Agent for the Web](https://arxiv.org/abs/2306.06070) (2023; arXiv preprint) [Code](https://github.com/OSU-NLP-Group/Mind2Web) [Project](https://osu-nlp-group.github.io/Mind2Web/)
- [MiniWoB++](https://miniwob.farama.org/index.html) (2023 refresh of classic benchmark; Official environment / docs) [Code](https://github.com/Farama-Foundation/miniwob-plusplus)
- [AgentBoard: An Analytical Evaluation Board of Multi-turn LLM Agents](https://arxiv.org/abs/2401.13178) (2024; NeurIPS D&B / arXiv)
- [AndroidWorld: A Dynamic Benchmarking Environment for Autonomous Agents](https://arxiv.org/abs/2405.14573) (2024; arXiv preprint)
- [AssistantBench: Can Web Agents Solve Realistic and Time-Consuming Tasks?](https://arxiv.org/abs/2407.15711) (2024; arXiv preprint) [Code](https://github.com/oriyor/assistantbench)
- [BrowserGym Ecosystem for Web Agent Research](https://arxiv.org/abs/2412.05467) (2024; arXiv preprint) [Code](https://github.com/servicenow/browsergym)
- [SWE-bench](https://arxiv.org/abs/2310.06770) (2024; ICLR 2024) [Code](https://github.com/swe-bench/SWE-bench) [Project](https://www.swebench.com/)
- [VisualWebArena](https://aclanthology.org/2024.acl-long.50/) (2024; ACL 2024) [Code](https://github.com/web-arena-x/visualwebarena) [Project](https://jykoh.com/vwa)
- [WebLINX: Real-World Website Navigation with Multi-Turn Dialogue](https://arxiv.org/abs/2402.05930) (2024; arXiv preprint) [Project](https://mcgill-nlp.github.io/weblinx)
- [An Illusion of Progress? Assessing the Current State of Web Agents](https://arxiv.org/abs/2504.01382) (2025; arXiv preprint) [Code](https://github.com/OSU-NLP-Group/Online-Mind2Web)
- [Mind2Web 2: Evaluating Agentic Search with Agent-as-a-Judge](https://arxiv.org/abs/2506.21506) (2025; arXiv preprint) [Code](https://github.com/OSU-NLP-Group/Mind2Web-2)
- [SWE-Lancer: Can Frontier LLMs Earn $1 Million from Real-World Freelance Software Engineering?](https://arxiv.org/abs/2502.12115) (2025; arXiv preprint) [Code](https://github.com/openai/SWELancer-Benchmark)
- [Evaluating Coding Agents in Interactive User Sessions](https://arxiv.org/abs/2606.29957) (2026; arXiv preprint)
- [Harness-Bench: Measuring Harness Effects across Models in Realistic Agent Workflows](https://arxiv.org/abs/2605.27922) (2026; arXiv preprint)
- [ScienceWorld: Is your Agent Smarter than a 5th Grader?](https://arxiv.org/abs/2203.07540) (2022; arXiv preprint)
- [WebShop: Towards Scalable Real-World Web Interaction with Grounded Language Agents](https://arxiv.org/abs/2207.01206) (2022; NeurIPS / arXiv)
- [TaskBench: Benchmarking Large Language Models for Task Automation](https://arxiv.org/abs/2311.18760) (2023; NeurIPS / arXiv) [Code](https://github.com/microsoft/JARVIS/tree/main/taskbench)
- [AgentGym: Evolving Large Language Model-based Agents across Diverse Environments](https://arxiv.org/abs/2406.04151) (2024; arXiv preprint) [Code](https://github.com/WooooDyy/AgentGym)
- [ProjDevBench: Benchmarking AI Coding Agents on End-to-End Project Development](https://arxiv.org/abs/2602.01655) (2026; arXiv preprint)

</details>

---

### 11. Domain-Specific Harnesses

Domain examples where task constraints force concrete harness design choices, such as chemistry tools, scientific discovery workflows, coding agents, and research assistants.

<details>
<summary><b>Domain-Specific Harnesses</b></summary>

- [Autonomous chemical research with large language models](https://www.nature.com/articles/s41586-023-06792-0) (2023; Nature)
- [ChemCrow: Augmenting large-language models with chemistry tools](https://arxiv.org/abs/2304.05376) (2023; arXiv preprint)
- [The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://arxiv.org/abs/2408.06292) (2024; arXiv preprint) [Code](https://github.com/SakanaAI/AI-Scientist)
- [Agent Laboratory: Using LLM Agents as Research Assistants](https://arxiv.org/abs/2501.04227) (2025; EMNLP Findings / arXiv)
- [The AI Scientist-v2: Workshop-Level Automated Scientific Discovery via Agentic Tree Search](https://arxiv.org/abs/2504.08066) (2025; arXiv preprint) [Code](https://github.com/SakanaAI/AI-Scientist-v2)
- [Accelerating scientific discovery with Co-Scientist](https://www.nature.com/articles/s41586-026-10644-y) (2026; Nature)

</details>

---

## Benchmarks

Benchmarks are grouped by the harness component they make visible. The goal is not to list every agent benchmark, but to highlight environments where the execution stack, tool interface, state tracking, policy layer, or repair loop materially affects results.

### Software Engineering Agents

| Benchmark / Environment | Harness Signal | Link |
|---|---|---|
| AppWorld | Stateful app/API execution, hidden environment state, and programmatic task completion | [Link](https://aclanthology.org/2024.acl-long.850/) |
| SWE-bench | Repository-level coding tasks with tests as external verification | [Link](https://arxiv.org/abs/2310.06770) |
| SWE-Lancer | Real-world freelance software tasks with economic and end-to-end completion signals | [Link](https://arxiv.org/abs/2502.12115) |
| ProjDevBench | Project-level software development requiring long-horizon planning and execution | [Link](https://arxiv.org/abs/2602.01655) |
| SWE-Together | Interactive coding sessions where user interaction and agent workflow both matter | [Link](https://arxiv.org/abs/2606.29957) |

### Web and Browser Agents

| Benchmark / Environment | Harness Signal | Link |
|---|---|---|
| WebArena | Browser action space, website state, and realistic web task execution | [Link](https://arxiv.org/abs/2307.13854) |
| VisualWebArena | Multimodal browser state and visual grounding for web actions | [Link](https://aclanthology.org/2024.acl-long.50/) |
| WorkArena | Enterprise web workflows and realistic knowledge-work tasks | [Link](https://proceedings.mlr.press/v235/drouin24a.html) |
| Mind2Web | Web action grounding from task instructions and DOM observations | [Link](https://osu-nlp-group.github.io/Mind2Web/) |
| Online-Mind2Web | Online web-agent execution with live interaction and changing environment state | [Link](https://arxiv.org/abs/2504.01382) |
| Mind2Web 2 | Agentic search and judge-based evaluation for web tasks | [Link](https://arxiv.org/abs/2506.21506) |
| AssistantBench | Time-consuming web tasks that stress planning, persistence, and information gathering | [Link](https://arxiv.org/abs/2407.15711) |
| WebLINX | Multi-turn dialogue and real website navigation | [Link](https://mcgill-nlp.github.io/weblinx) |
| BrowserGym | Shared ecosystem for reproducible web-agent environments | [Link](https://arxiv.org/abs/2412.05467) |
| MiniWoB++ | Classic browser-control primitives and compact interactive tasks | [Link](https://miniwob.farama.org/index.html) |
| WebShop | Grounded shopping tasks with search, navigation, and choice constraints | [Link](https://arxiv.org/abs/2207.01206) |

### OS, GUI, and Computer-Use Agents

| Benchmark / Environment | Harness Signal | Link |
|---|---|---|
| OSWorld | Real computer environments, GUI actions, and open-ended task completion | [Link](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5d413e48f84dc61244b6be550f1cd8f5-Abstract-Datasets_and_Benchmarks_Track.html) |
| AndroidWorld | Dynamic mobile-device interaction and Android action validity | [Link](https://arxiv.org/abs/2405.14573) |

### API, App, and Tool-Use Agents

| Benchmark / Environment | Harness Signal | Link |
|---|---|---|
| ToolSandbox | Stateful conversational tool use with hidden state and tool-side effects | [Link](https://arxiv.org/abs/2408.04682) |
| tau-bench | User-agent-tool interaction with realistic API constraints | [Link](https://huggingface.co/papers/2406.12045) |
| TaskBench | Task automation through API/tool composition | [Link](https://arxiv.org/abs/2311.18760) |
| ToolTalk | Conversational tool use, user clarification, and multi-turn decision making | [Link](https://arxiv.org/abs/2311.10775) |
| MTU-Bench | Multi-granularity tool-use evaluation | [Link](https://arxiv.org/abs/2410.11710) |
| ToolHop | Multi-hop tool-use dependency chains | [Link](https://arxiv.org/abs/2501.02506) |
| Berkeley Function Calling Leaderboard | Function-call formatting, tool selection, and action-validity benchmarking | [Link](https://gorilla.cs.berkeley.edu/leaderboard.html) |

### Safety and Security

| Benchmark / Environment | Harness Signal | Link |
|---|---|---|
| AgentDojo | Prompt-injection attacks and defenses in tool-using agents | [Link](https://github.com/ethz-spylab/agentdojo) |
| Agent Security Bench | Agent attack/defense formalization and security evaluation | [Link](https://openreview.net/forum?id=V4y0CpX4hK) |
| ASB | Security benchmark for LLM-based agents | [Link](https://arxiv.org/abs/2410.02644) |
| AgentSCOPE | Contextual privacy across agentic workflows | [Link](https://arxiv.org/abs/2603.04902) |
| ToolEmu | LM-emulated sandbox for identifying tool-use risks | [Link](https://arxiv.org/abs/2309.15817) |

### General / Mixed Agent Benchmarks

| Benchmark / Environment | Harness Signal | Link |
|---|---|---|
| AgentBench | Multi-environment evaluation of LLM agents | [Link](https://openreview.net/forum?id=zAdUB0aCTQ) |
| GAIA | General assistant tasks requiring tool use, reasoning, and multi-step workflows | [Link](https://proceedings.iclr.cc/paper_files/paper/2024/file/25ae35b5b1738d80f1f03a8713e405ec-Paper-Conference.pdf) |
| AgentBoard | Analytical evaluation board for multi-turn LLM agents | [Link](https://arxiv.org/abs/2401.13178) |
| AgentGym | Training/evaluation across diverse agent environments | [Link](https://arxiv.org/abs/2406.04151) |
| ScienceWorld | Scientific text-world tasks with action constraints and environment state | [Link](https://arxiv.org/abs/2203.07540) |
| TheAgentCompany | Workplace-style digital-worker benchmark with enterprise task structure | [Link](https://arxiv.org/abs/2412.14161) |
| Terminal-Bench 2.0 | Terminal-based agent tasks where shell environment and execution traces matter | [Link](https://arxiv.org/abs/2601.11868) |

---

## Related Repositories

| Resource | Owner / Organization | Scope | Description |
|---|---|---|---|
| [Awesome-Agent-Harness](https://github.com/Gloriaameng/Awesome-Agent-Harness) | Gloriaameng | Harness survey and resource list | A direct neighboring resource that explicitly uses the agent-harness framing and collects harness papers and systems. This repository is the closest comparator; our list should remain distinct by indexing each work through responsibility allocation, state ownership, action validity, failure boundaries, repair, and human oversight. |
| [Agent Systems with Harness Engineering](https://github.com/RUCAIBox/awesome-agent-harness) | RUCAIBox | Harness engineering survey companion repo | A structured academic roadmap around harness engineering, including design, model adaptation, benchmarks, and future directions. It validates the field-level importance of harnesses; our repository complements it by using the Human-Machine Task Contract as the main organizing lens. |
| [Awesome-Code-as-Agent-Harness-Papers](https://github.com/YennNing/Awesome-Code-as-Agent-Harness-Papers) | YennNing | Code-as-harness papers | A focused resource on code as the operational substrate for agent harnesses. It is best treated as the primary related list for the code-as-harness subsection, while this repository covers a broader contract stack including tools, policy, memory, verification, benchmarks, and human oversight. |
| [awesome-harness-engineering](https://github.com/ai-boost/awesome-harness-engineering) | ai-boost | Practitioner-oriented harness engineering | A fast-moving engineering list covering patterns, tools, memory, MCP, permissions, observability, and orchestration. It is useful for ecosystem awareness; our repository should compete on scholarly curation, verified paper metadata, and contract-oriented taxonomy rather than practitioner breadth alone. |
| [awesome-agentic-workflow-optimization](https://github.com/IBM/awesome-agentic-workflow-optimization) | IBM | Agentic workflow optimization | A close adjacent resource for workflow graphs, runtime planning, and optimization. It is especially relevant to execution and orchestration harnesses; our repository should extend beyond workflow optimization into human boundaries, tool validity, policy enforcement, repair, and evaluation environments. |
| [Awesome-Human-Agent-Collaboration-Interaction-Systems](https://github.com/HenryPengZou/Awesome-Human-Agent-Collaboration-Interaction-Systems) | HenryPengZou | Human-agent collaboration | A useful complement for the human-in-the-loop and oversight side of the contract. It is broader than harness engineering and less focused on runtime/tool verification, so it should be cross-linked mainly from the governance and collaboration sections. |
| [awesome-tool-llm](https://github.com/zorazrw/awesome-tool-llm) | zorazrw | Tool learning and tool use for LLMs | A strong adjacent list for tool-use literature, including prompting, training, and tool learning. Our repository uses tool-use as one contract layer rather than the whole scope, connecting tool interfaces to action validity, sandboxing, verification, and task-environment constraints. |
| [Awesome-Agent-Security](https://github.com/ucsb-mlsec/Awesome-Agent-Security) | ucsb-mlsec | Agent security and safety | A security-focused resource useful for prompt injection, tool misuse, privacy, and policy-control literature. It should be linked from the policy/safety section, while our repository places security inside the broader execution contract. |
| [awesome-evals](https://github.com/benchflow-ai/awesome-evals) | BenchFlow | Evaluation resources | A broad evaluation-resource hub covering benchmarks, tools, and evaluation methods. It is useful for benchmark discovery; our repository should narrow evaluation to cases where harness design materially affects action validity, state tracking, safety, or long-horizon task success. |
| [ai-agent-benchmark-compendium](https://github.com/philschmid/ai-agent-benchmark-compendium) | philschmid | Agent benchmark compendium | A compact benchmark-oriented resource. It can help with benchmark coverage, but our benchmark section should additionally label which harness component each environment stresses, such as tool interface, browser control, OS action space, sandboxing, or human-agent interaction. |
| [LLMAgentPapers](https://github.com/zjunlp/LLMAgentPapers) | ZJUNLP | Broad LLM-agent paper collection | A broad must-read list for LLM-agent literature. It is valuable for discovery but too general for our scope; our repository should include only entries where the external execution layer is central to the paper's contribution. |
| [LLM-Agent-Survey](https://github.com/paitesanshi/llm-agent-survey) | paitesanshi | General LLM-agent survey resource | A broad agent-survey resource covering many agent topics. It should be cited as related background, but our repository should avoid becoming another general agent list by enforcing the harness inclusion rule. |
| [awesome-llm-agents](https://github.com/kaushikb11/awesome-llm-agents) | kaushikb11 | LLM-agent frameworks and papers | A framework-oriented LLM-agent resource. It overlaps with orchestration and agent frameworks, but this repository should differentiate by requiring harness role and contract role annotations. |
| [awesome-llm-powered-agent](https://github.com/hyp1231/awesome-llm-powered-agent) | hyp1231 | Broad LLM-powered agent resources | A useful broad background list for agents, tools, and applications. It should remain a related resource rather than a model for our structure, because our scope is the executable harness layer rather than all LLM-powered agents. |
| [awesome-ai-agents](https://github.com/e2b-dev/awesome-ai-agents) | e2b-dev | Autonomous-agent ecosystem list | A general ecosystem directory for autonomous agents and tools. It is helpful for awareness but not a scholarly taxonomy; our repository should not imitate a product-directory style. |
| [Awesome Agentic Engineering Resources](https://github.com/EthicalML/awesome-agentic-engineering-resources) | EthicalML | Agent engineering resources | A practitioner resource covering articles, playbooks, benchmarks, and engineering material. It can be linked as ecosystem context, while our repository remains a paper-first and benchmark-first scholarly map. |
| [Awesome Agentic System Design](https://github.com/gtzheng/Awesome-Agentic-System-Design) | gtzheng | Agentic system design, evaluation, and deployment | A system-design-oriented related list. It is close in spirit but broader and less contract-specific; our repository should distinguish itself through stable categories, verified metadata, and explicit human/model/tool/task boundary descriptions. |
| [Anthropic: Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) | Anthropic | Practical agent-building patterns | A high-signal industry reference for agent workflows and composable patterns. It is not a literature tracker, but it helps justify why harness structure—not only model capability—is central to practical agent performance. |
| [LangChain: The Anatomy of an Agent Harness](https://www.langchain.com/blog/the-anatomy-of-an-agent-harness) | LangChain | Agent-harness definition and practitioner framing | A clear practitioner explanation of model, framework, runtime, and harness boundaries. It is useful for sharpening terminology, but the repository taxonomy should remain literature-driven and contract-oriented rather than vendor-framework-centered. |

---
