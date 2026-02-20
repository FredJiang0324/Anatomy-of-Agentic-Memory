<h1 align="center">Anatomy of Agentic Memory: Taxonomy and Empirical Analysis of Evaluation and System Limitations</h1>

<div align="center">
  <a href=""><img src="https://img.shields.io/badge/arXiv-coming%20soon-b31b1b.svg?logo=arxiv" alt="arXiv"></a>
  <a href=""><img src="https://img.shields.io/badge/Hugging%20Face-Paper-ffcc4d.svg?logo=huggingface" alt="Hugging Face"></a>
  <a href="https://github.com/FredJiang0324/Anatomy-of-Agentic-Memory/pulls"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" alt="Contributions Welcome"></a>
  <a href="https://github.com/FredJiang0324/Anatomy-of-Agentic-Memory"><img src="https://img.shields.io/github/stars/FredJiang0324/Anatomy-of-Agentic-Memory.svg?style=social&label=Star" alt="GitHub Stars"></a>
</div>

> **Authors**: Dongming Jiang, Yi Li, Songtao Wei, Jinxin Yang, Ayushi Kishore, Alysa Zhao, Dingyi Kang, Xu Hu, Feng Chen, Qiannan Li, and Bingzhe Li†
>
> **Affiliations**: University of Texas at Dallas &nbsp;·&nbsp; University of California, Davis &nbsp;·&nbsp; Texas A&M University

## 🔥 News

- **[2026/02/20]** Our survey *Anatomy of Agentic Memory* is released! See [paper](https://github.com/libingzheren/libingzheren.github.io/blob/master/file/2026_CoNLL_AgenticMemorySurvey__arxiv_.pdf) for details.
- **[2026/02/20]** We create this repo to maintain the papers we cover in the agentic memory area. More papers are coming — **welcome to contribute to the community!** Open an issue or submit a pull request to add papers, fix links, or improve categorization.

## ⚡ Introduction

This repo maintains a curated list of papers on **agentic memory for LLM-based agents**, organized around the taxonomy introduced in our survey. We cover Memory-Augmented Generation (MAG) systems across four structural paradigms and will keep the list updated as the field evolves.

If you have a new paper or find a work we missed, feel free to open an **issue** or submit a **pull request** — it helps us maintain this repo, update our manuscript, and contribute to the broader community. 🤝

## 🔍 What Makes This Survey Different

Most existing surveys on agentic memory operate at the **theoretical level** — cataloguing architectures, defining conceptual taxonomies, or drawing cognitive science analogies. We complement these efforts with **systematic empirical analysis** across representative MAG systems, surfacing four practical pain points that are frequently overlooked.

The table below compares our survey with closely related work. ✓ = systematically discussed, (✓) = partially covered, ✗ = not addressed.

<table>
  <thead>
    <tr>
      <th>Survey</th>
      <th>Taxonomy Focus</th>
      <th align="center">Memory Mgmt.<br>&amp; Policy</th>
      <th align="center">Benchmark<br>Saturation</th>
      <th align="center">Metric<br>Validity</th>
      <th align="center">Backbone<br>Sensitivity</th>
      <th align="center">System Cost<br>&amp; Latency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="https://arxiv.org/abs/2601.09113">The AI Hippocampus</a> (Jia et al., 2026)</td>
      <td>Brain-inspired: implicit, explicit, agentic</td>
      <td align="center">(✓)</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td>
    </tr>
    <tr>
      <td><a href="https://arxiv.org/abs/2512.13564">Memory in the Age of AI Agents</a> (Hu et al., 2025)</td>
      <td>Forms–functions–dynamics</td>
      <td align="center">(✓)</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td>
    </tr>
    <tr>
      <td><a href="https://arxiv.org/abs/2601.14192">Toward Efficient Agents</a> (Yang et al., 2026)</td>
      <td>Efficiency-focused: memory, tool learning, planning</td>
      <td align="center">✓</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td><td align="center">✓</td>
    </tr>
    <tr>
      <td><a href="https://arxiv.org/abs/2602.06052">Rethinking Memory Mechanisms</a> (Huang et al., 2026)</td>
      <td>Substrate–cognition–subject</td>
      <td align="center">✓</td><td align="center">(✓)</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td>
    </tr>
    <tr>
      <td>From Storage to Experience (Luo et al., 2026)</td>
      <td>Evolutionary: storage–reflection–experience</td>
      <td align="center">(✓)</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td>
    </tr>
    <tr>
      <td><a href="https://arxiv.org/abs/2602.05665">Graph-based Agent Memory</a> (Yang et al., 2026)</td>
      <td>Graph-oriented lifecycle</td>
      <td align="center">✓</td><td align="center">(✓)</td><td align="center">✗</td><td align="center">✗</td><td align="center">✗</td>
    </tr>
    <tr>
      <td><strong>Ours</strong></td>
      <td>Structural + Empirical analysis</td>
      <td align="center">✓</td><td align="center">✓</td><td align="center">✓</td><td align="center">✓</td><td align="center">✓</td>
    </tr>
  </tbody>
</table>

**1. Benchmark Saturation** — Many existing benchmarks fit within modern 128k+ context windows, making external memory structurally unnecessary. We propose the **Context Saturation Gap** (Δ = Score<sub>MAG</sub> − Score<sub>FullContext</sub>) to test whether a benchmark genuinely requires external memory.

**2. Metric Misalignment** — Lexical metrics (F1, BLEU) diverge from semantic correctness and can misrank systems. LLM-as-a-judge is more reliable but requires careful prompt calibration.

**3. Backbone Sensitivity** — Complex memory architectures (graph-based, episodic) rely on structured output generation during updates. Weaker backbones produce higher format error rates, silently corrupting long-term memory.

**4. System Cost** — Agentic memory introduces write–consolidate overhead absent in standard RAG. Trade-offs among latency, construction time, and token consumption are rarely reported but critical for deployment.

## 🗂️ Taxonomy

We organize agentic memory into four structural paradigms:

- **💡 Lightweight Semantic Memory** — Independent textual units retrieved via top-*k* similarity. Simple, cheap, and widely adopted.
- **🧑 Entity-Centric and Personalized Memory** — Information organized around explicit entities or user profiles via structured records.
- **🔄 Episodic and Reflective Memory** — Temporal abstraction via episodes with periodic consolidation through reflection.
- **🏗️ Structured and Hierarchical Memory** — Multi-tier or graph-based organization with explicit relational structure.

## 🧾 Paper List

<details open>
  <summary>📂 Table of Contents <em>(click to expand/collapse)</em></summary>
  <ul>
    <li><a href="#lightweight-semantic-memory">💡 Lightweight Semantic Memory</a>
      <ul>
        <li><a href="#rl-optimized-semantic-compression">RL-Optimized Semantic Compression</a></li>
        <li><a href="#context-window-management">Context Window Management</a></li>
        <li><a href="#heuristic--prompt-optimized">Heuristic / Prompt-Optimized</a></li>
        <li><a href="#token-level-semantic-memory">Token-Level Semantic Memory</a></li>
      </ul>
    </li>
    <li><a href="#entity-centric--personalized-memory">🧑 Entity-Centric & Personalized Memory</a>
      <ul>
        <li><a href="#entity-centric-memory">Entity-Centric Memory</a></li>
        <li><a href="#personalized-memory">Personalized Memory</a></li>
      </ul>
    </li>
    <li><a href="#episodic--reflective-memory">🔄 Episodic & Reflective Memory</a>
      <ul>
        <li><a href="#episodic-buffer-with-learned-control">Episodic Buffer with Learned Control</a></li>
        <li><a href="#episodic-reflection--consolidation">Episodic Reflection & Consolidation</a></li>
        <li><a href="#episodic-recall-for-exploration">Episodic Recall for Exploration</a></li>
        <li><a href="#episodic-utility-learning">Episodic Utility Learning</a></li>
      </ul>
    </li>
    <li><a href="#structured--hierarchical-memory">🏗️ Structured & Hierarchical Memory</a>
      <ul>
        <li><a href="#graph-structured-memory">Graph-Structured Memory</a></li>
        <li><a href="#os-inspired--hierarchical-memory">OS-Inspired & Hierarchical Memory</a></li>
        <li><a href="#policy-optimized-memory-management">Policy-Optimized Memory Management</a></li>
      </ul>
    </li>
  </ul>
</details>

---

<a name="lightweight-semantic-memory"></a>
### 💡 Lightweight Semantic Memory

<a name="rl-optimized-semantic-compression"></a>
#### RL-Optimized Semantic Compression

* [MemAgent: Reshaping Long-Context LLM with Multi-Conv RL-based Memory Agent](https://arxiv.org/abs/2507.02259) (Yu et al., 2025)
* [MemSearcher: Training LLMs to Reason, Search and Manage Memory via End-to-End Reinforcement Learning](https://arxiv.org/abs/2511.02805) (Yuan et al., 2025)
* [Mem-α: Learning Memory Construction via Reinforcement Learning](https://arxiv.org/abs/2509.25911) (Wang et al., 2025)
* [Memory-R1: Enhancing Large Language Model Agents to Manage and Utilize Memories via Reinforcement Learning](https://arxiv.org/abs/2508.19828) (Yan et al., 2025)

<a name="context-window-management"></a>
#### Context Window Management

* [AgentFold: Long-Horizon Web Agents with Proactive Context Management](https://arxiv.org/abs/2510.24699) (Ye et al., 2025)
* [Scaling Long-Horizon LLM Agent via Context-Folding](https://arxiv.org/abs/2510.11967) (Sun et al., 2025)
* [LLM-MemCluster: Empowering Large Language Models with Dynamic Memory for Text Clustering](https://arxiv.org/abs/2511.15424) (Zhu et al., 2025)
* [LightMem: Lightweight and Efficient Memory-Augmented Generation](https://arxiv.org/abs/2510.18866) (Fang et al., 2025)
* MemAgent-Cache: A Cache-Inspired Framework for Augmenting Conversational Web Agents with Task-Specific Information (Sakib et al., 2025)
* LM2 (Kang et al., 2025)
* RCR-Router (Liu et al., 2025)

<a name="heuristic--prompt-optimized"></a>
#### Heuristic / Prompt-Optimized

* [A Simple yet Strong Baseline for Long-Term Conversational Memory of LLM Agents](https://arxiv.org/abs/2511.17208) (Zhou & Han, 2025)
* ACON (Kang et al., 2025)
* Compressed Step Information Memory (CISM) (Liu et al., 2025)
* [AME: An Efficient Heterogeneous Agentic Memory Engine for Smartphones](https://arxiv.org/abs/2511.19192) (Zhao et al., 2025)
* [CogMem: A Cognitive Memory Architecture for Sustained Multi-Turn Reasoning in Large Language Models](https://arxiv.org/abs/2512.14118) (Zhang et al., 2025)
* [PISA: A Pragmatic Psych-Inspired Unified Memory System for Enhanced AI Agency](https://arxiv.org/abs/2510.15966) (Jia et al., 2025)
* [Memento: Fine-Tuning LLM Agents without Fine-Tuning LLMs](https://arxiv.org/abs/2508.16153) (Zhou et al., 2025)

<a name="token-level-semantic-memory"></a>
#### Token-Level Semantic Memory

* [TokMem: Tokenized Procedural Memory for Large Language Models](https://arxiv.org/abs/2510.00444) (Wu et al., 2025)
* [MemGen: Weaving Generative Latent Memory for Self-Evolving Agents](https://arxiv.org/abs/2509.24704) (Zhang et al., 2025)
* [Memory³: Language Modeling with Explicit Memory](https://arxiv.org/abs/2407.01178) (Yang et al., 2024)

---

<a name="entity-centric--personalized-memory"></a>
### 🧑 Entity-Centric & Personalized Memory

<a name="entity-centric-memory"></a>
#### Entity-Centric Memory

* [RET-LLM: Towards a General Read-Write Memory for Large Language Models](https://arxiv.org/abs/2305.14322) (Modarressi et al., 2023)
* [A-MEM: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110) (Xu et al., 2025)
* [Memory-R1: Enhancing Large Language Model Agents to Manage and Utilize Memories via Reinforcement Learning](https://arxiv.org/abs/2508.19828) (Yan et al., 2025)
* [Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory](https://arxiv.org/abs/2504.19413) (Chhikara et al., 2025)
* RMM: Reinforced Memory Management for Class-Incremental Learning (Liu et al., 2021) ![NeurIPS 2021](https://img.shields.io/badge/NeurIPS%202021-blue)
* WebCoach (Liu et al., 2025)
* [MEM1: Learning to Synergize Memory and Reasoning for Efficient Long-Horizon Agents](https://arxiv.org/abs/2506.15841) (Zhou et al., 2025)

<a name="personalized-memory"></a>
#### Personalized Memory

* [Preference-Aware Memory Update for Long-Term LLM Agents (PAMU)](https://arxiv.org/abs/2510.09720) (Sun et al., 2025)
* [EgoMem: Lifelong Memory Agent for Full-Duplex Omnimodal Models](https://arxiv.org/abs/2509.11914) (Yao et al., 2025)
* [MemOrb: A Plug-and-Play Verbal-Reinforcement Memory Layer for E-Commerce Customer Service](https://arxiv.org/abs/2509.18713) (Huang et al., 2025)
* WebCoach (Liu et al., 2025)
* [MemoryBank: Enhancing Large Language Models with Long-Term Memory](https://arxiv.org/abs/2305.10250) (Zhong et al., 2024) ![AAAI 2024](https://img.shields.io/badge/AAAI%202024-blue)
* [Hello Again! LLM-powered Personalized Agent for Long-term Dialogue](https://arxiv.org/abs/2406.05925) (Li et al., 2025) ![NAACL 2025](https://img.shields.io/badge/NAACL%202025-blue)
* Embodied Agents (Kwon et al., 2025)
* [Bi-Mem: Bidirectional Construction of Hierarchical Memory for Personalized LLMs](https://arxiv.org/abs/2601.06490) (Mao et al., 2026)
* [Beyond Dialogue Time: Temporal Semantic Memory for Personalized LLM Agents](https://arxiv.org/abs/2601.07468) (Su et al., 2026)

---

<a name="episodic--reflective-memory"></a>
### 🔄 Episodic & Reflective Memory

<a name="episodic-buffer-with-learned-control"></a>
#### Episodic Buffer with Learned Control

* [MemR³: Memory Retrieval via Reflective Reasoning for LLM Agents](https://arxiv.org/abs/2512.20237) (Du et al., 2025)
* [Memory as Action: Autonomous Context Curation for Long-Horizon Agentic Tasks (MemAct)](https://arxiv.org/abs/2510.12635) (Zhang et al., 2025)
* [The Act of Remembering: A Study in Partially Observable Reinforcement Learning](https://arxiv.org/abs/2010.01753) (Icarte et al., 2020)

<a name="episodic-reflection--consolidation"></a>
#### Episodic Reflection & Consolidation

* [In Prospect and Retrospect: Reflective Memory Management for Long-term Personalized Dialogue Agents](https://arxiv.org/abs/2503.08026) (Tan et al., 2025) ![ACL 2025](https://img.shields.io/badge/ACL%202025-blue)
* TiMem (Li et al., 2026)
* [MemP: Exploring Agent Procedural Memory](https://arxiv.org/abs/2508.06433) (Fang et al., 2025)
* Pre-Storage Reasoning (Kim et al., 2025)
* [Nemori: Self-Organizing Agent Memory Inspired by Cognitive Science](https://arxiv.org/abs/2508.03341) (Nan et al., 2025)
* [LEGOMem: Modular Procedural Memory for Multi-Agent LLM Systems for Workflow Automation](https://arxiv.org/abs/2510.04851) (Han et al., 2025)
* [ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory](https://arxiv.org/abs/2509.25140) (Ouyang et al., 2025)
* [A Human-Inspired Reading Agent with Gist Memory of Very Long Contexts (ReadAgent)](https://arxiv.org/abs/2402.09727) (Lee et al., 2024) ![ICML 2024](https://img.shields.io/badge/ICML%202024-blue)
* [ProMem: Beyond Static Summarization — Proactive Memory Extraction for LLM Agents](https://arxiv.org/abs/2601.04463) (Yang et al., 2026)
* Human-like Episodic Memory (Dong et al., 2025)

<a name="episodic-recall-for-exploration"></a>
#### Episodic Recall for Exploration

* [EMU: Efficient Episodic Memory Utilization of Cooperative Multi-Agent Reinforcement Learning](https://arxiv.org/abs/2403.01112) (Na et al., 2024)
* [SAM2RL: Towards Reinforcement Learning Memory Control in Segment Anything Model 2](https://arxiv.org/abs/2507.08548) (Adamyan et al., 2025)

<a name="episodic-utility-learning"></a>
#### Episodic Utility Learning

* [MemRL: Self-Evolving Agents via Runtime Reinforcement Learning on Episodic Memory](https://arxiv.org/abs/2601.03192) (Zhang et al., 2026)
* [Memory-T1: Reinforcement Learning for Temporal Reasoning in Multi-Session Agents](https://arxiv.org/abs/2512.20092) (Du et al., 2025)
* [Memento: Fine-Tuning LLM Agents without Fine-Tuning LLMs](https://arxiv.org/abs/2508.16153) (Zhou et al., 2025)
* [Remember Me, Refine Me: A Dynamic Procedural Memory Framework for Experience-Driven Agent Evolution](https://arxiv.org/abs/2512.10696) (Cao et al., 2025)

---

<a name="structured--hierarchical-memory"></a>
### 🏗️ Structured & Hierarchical Memory

<a name="graph-structured-memory"></a>
#### Graph-Structured Memory

* [MAGMA: A Multi-Graph based Agentic Memory Architecture for AI Agents](https://arxiv.org/abs/2601.03236) (Jiang et al., 2026)
* [Zep: A Temporal Knowledge Graph Architecture for Agent Memory](https://arxiv.org/abs/2501.13956) (Rasmussen et al., 2025)
* [SGMem: Sentence Graph Memory for Long-Term Conversational Agents](https://arxiv.org/abs/2509.21212) (Wu et al., 2025)
* [SYNAPSE: Empowering LLM Agents with Episodic-Semantic Memory via Spreading Activation](https://arxiv.org/abs/2601.02744) (Jiang et al., 2026)
* [LatentGraphMem: Implicit Graph, Explicit Retrieval — Towards Efficient and Interpretable Long-Horizon Memory](https://arxiv.org/abs/2601.03417) (Zhang et al., 2026)
* [LiCoMemory: Lightweight and Cognitive Agentic Memory for Efficient Long-Term Reasoning](https://arxiv.org/abs/2511.01448) (Huang et al., 2025)
* Hindsight (Latimer et al., 2025)
* [A Simple yet Strong Baseline for Long-Term Conversational Memory of LLM Agents](https://arxiv.org/abs/2511.17208) (Zhou & Han, 2025)
* [From Single to Multi-Granularity: Toward Long-Term Memory Association and Selection of Conversational Agents](https://arxiv.org/abs/2505.19549) (Xu et al., 2025)
* [StockMem: An Event-Reflection Memory Framework for Stock Forecasting](https://arxiv.org/abs/2512.02720) (Wang et al., 2025)
* [G-Memory: Tracing Hierarchical Memory for Multi-Agent Systems](https://arxiv.org/abs/2506.07398) (Zhang et al., 2025)
* [Membox: Weaving Topic Continuity into Long-Range Memory for LLM Agents](https://arxiv.org/abs/2601.03785) (Tao et al., 2026)
* [Memory Matters More: Event-Centric Memory as a Logic Map for Agent Searching and Reasoning](https://arxiv.org/abs/2601.04726) (Hu et al., 2026)
* [AssoMem: Scalable Memory QA with Multi-Signal Associative Retrieval](https://arxiv.org/abs/2510.10397) (Zhang et al., 2025)

<a name="os-inspired--hierarchical-memory"></a>
#### OS-Inspired & Hierarchical Memory

* [MemGPT: Towards LLMs as Operating Systems](https://arxiv.org/abs/2310.08560) (Packer et al., 2023)
* [Memory OS of AI Agent (MemoryOS)](https://arxiv.org/abs/2506.06326) (Kang et al., 2025)
* [EverMemOS: A Self-Organizing Memory Operating System for Structured Long-Horizon Reasoning](https://arxiv.org/abs/2601.02163) (Hu et al., 2026)
* [HiMem: Hierarchical Long-Term Memory for LLM Long-Horizon Agents](https://arxiv.org/abs/2601.06377) (Zhang et al., 2026)
* MeMAD (Ling et al., 2025)
* [MIRIX: Multi-Agent Memory System for LLM-Based Agents](https://arxiv.org/abs/2507.07957) (Wang & Chen, 2025)
* [A Scenario-Driven Cognitive Approach to Next-Generation AI Memory](https://arxiv.org/abs/2509.13235) (Cai et al., 2025)
* ReMe (Li Yu, 2025)
* [LightMem: Lightweight and Efficient Memory-Augmented Generation](https://arxiv.org/abs/2510.18866) (Fang et al., 2025)
* Conversational Agents: From RAG to LTM (Zhang et al., 2025) ![SIGIR-AP 2025](https://img.shields.io/badge/SIGIR--AP%202025-blue)
* [MemOS: A Memory OS for AI System](https://arxiv.org/abs/2507.03724) (Li et al., 2025)
* [EvoMem: Improving Multi-Agent Planning with Dual-Evolving Memory](https://arxiv.org/abs/2511.01912) (Fan et al., 2025)
* AGENT KB (Tang et al.)
* KARMA: Augmenting Embodied AI Agents with Long-and-Short Term Memory Systems (Wang et al., 2025) ![ICRA 2025](https://img.shields.io/badge/ICRA%202025-blue)
* MaaS (Li, 2025)
* [Can Memory-Augmented LLM Agents Aid Journalism in Interpreting and Framing News (MADES)](https://arxiv.org/abs/2507.21055) (Ouyang, 2025)
* TiMem (Li et al., 2026)
* [Memory Management and Contextual Consistency for Long-Running Low-Code Agents](https://arxiv.org/abs/2509.25250) (Xu, 2025)

<a name="policy-optimized-memory-management"></a>
#### Policy-Optimized Memory Management

* [MEM1: Learning to Synergize Memory and Reasoning for Efficient Long-Horizon Agents](https://arxiv.org/abs/2506.15841) (Zhou et al., 2025)
* [Mem-α: Learning Memory Construction via Reinforcement Learning](https://arxiv.org/abs/2509.25911) (Wang et al., 2025)
* [AtomMem: Learnable Dynamic Agentic Memory with Atomic Memory Operation](https://arxiv.org/abs/2601.08323) (Huo et al., 2026)
* [SEDM: Scalable Self-Evolving Distributed Memory for Agents](https://arxiv.org/abs/2509.09498) (Xu et al., 2025)
* [Memory-R1: Enhancing Large Language Model Agents to Manage and Utilize Memories via Reinforcement Learning](https://arxiv.org/abs/2508.19828) (Yan et al., 2025)
* [Memory-T1: Reinforcement Learning for Temporal Reasoning in Multi-Session Agents](https://arxiv.org/abs/2512.20092) (Du et al., 2025)
* [IterResearch: Rethinking Long-Horizon Agents via Markovian State Reconstruction](https://arxiv.org/abs/2511.07327) (Chen et al., 2025)
* RCR-Router (Liu et al., 2025)
* LM2 (Kang et al., 2025)

---

## 📌 Citation

If you find this survey useful, please cite:

```bibtex
@article{jiang2026anatomy,
  title     = {Anatomy of Agentic Memory: Taxonomy and Empirical Analysis of Evaluation and System Limitations},
  author    = {Dongming Jiang and Yi Li and Songtao Wei and Jinxin Yang and Ayushi Kishore and Alysa Zhao and Dingyi Kang and Xu Hu and Feng Chen and Qiannan Li and Bingzhe Li},
  year      = {2026},
}
```
