# Hushuang Shen · 沈瑚双

[Academic Homepage](https://darssal.github.io/) · [Public CV](https://darssal.github.io/cv.html) · [Engineering Notes](https://github.com/Darssal/Research-Code-Collection/blob/main/docs/ENGINEERING_NOTES.md)

我是中国石油大学（北京）数据科学与大数据技术专业本科生，预计 **2027 年毕业**，专业成绩排名 **3/94（2026.09）**。

**2027 Postgraduate Destination · 保研去向：中国科学院大学（UCAS）／中国科学院计算技术研究所（ICT），计算机科学与技术，2027 级，尚未入学。**

研究兴趣包括多模态大模型、Agent 记忆与检索增强，近期工作围绕成像测井裂缝解释、长上下文记忆评测和招聘文本标注展开。以第一作者身份发表 **2 篇 SCI-E 论文**；另有 **1 篇 IEEE SMC 2026 录用论文（共同一作，作者首位）**。

## Research

### [Persistent Retrieval in Hierarchical Memory Systems for Long-Context Agents: A Controlled Evaluation](https://conf.papercept.net/conferences/conferences/SMC26/program/SMC26_ContentListWeb_3.html#tua16_05)

**Hushuang Shen\***, Yuan Wang\*<br>
**IEEE SMC 2026 · Accepted · 共同一作，作者首位**（\* Equal contribution）

固定模型、解码、提示与检索预算，在长上下文任务中比较记忆配置，分析证据充足与稀缺条件下持久检索的作用。

[Official Program](https://conf.papercept.net/conferences/conferences/SMC26/program/SMC26_ContentListWeb_3.html#tua16_05) · [MemLab](https://github.com/Darssal/MemLab)

### [Two-Stage Recruitment Text Labeling via Lexicon-Guided Routing and Retrieval-Augmented Large Language Models](https://doi.org/10.3791/70153)

**Hushuang Shen**, Yuan Wang<br>
**Journal of Visualized Experiments (JoVE), (231), e70153, 2026 · Published · 第一作者**

以词表分流处理常规文本，将歧义样本交给检索增强模型，研究招聘文本的两阶段标注流程。

[DOI](https://doi.org/10.3791/70153) · [PubMed](https://pubmed.ncbi.nlm.nih.gov/42184252/) · [Classification Baseline](https://github.com/Darssal/Recruitment-Text-Classification)

### [FracLogGPT: A Multimodal Large Language Model for Fracture Interpretation in Imaging Logging](https://doi.org/10.3390/electronics15010127)

**Hushuang Shen**, Ang Li, Liyan Zhang, Xiangxiang Liu<br>
**Electronics, 15(1), 127, 2026 · Published · 第一作者**

基于 Qwen2.5-VL-7B，研究领域适配、LoRA-SFT 与 DPO 对成像测井裂缝解释的作用，联合评价裂缝计数、空间一致性和文本描述。论文在线发表于 2025-12-26，正式引用卷年为 2026。

[DOI](https://doi.org/10.3390/electronics15010127) · [Publisher](https://www.mdpi.com/2079-9292/15/1/127) · [FracLogGPT-Lite](https://github.com/Darssal/FracLogGPT-Lite)

## Selected Projects

### [FracLogGPT-Lite](https://github.com/Darssal/FracLogGPT-Lite)

**Multimodal Experiment Framework** · `Python` `PyTorch` `Transformers` `PEFT / LoRA` `ms-swift`

组织成像测井实验的阶段衔接与可恢复推理：配置驱动训练命令，解析 checkpoint 接续下游，以稳定样本键恢复预测；视觉对比解码同步原图与扰动图分支，并维护 KV cache 和多模态字段。

[Decoding](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/vcd.py) · [Resumable Inference](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/predictions.py) · [Quickstart](https://github.com/Darssal/FracLogGPT-Lite/blob/main/docs/QUICKSTART.md)

### [MemLab](https://github.com/Darssal/MemLab)

**Agent Memory & Controlled Evaluation** · `Python 3.12` `asyncio` `Redis` `PostgreSQL` `Qdrant`

将近期上下文、热缓存、元数据与持久检索接入统一记忆接口；为检索结果去重、控制上下文预算，用 ContextVar 区分异步会话，并根据运行有效性检查生成重跑计划。

[Architecture](https://github.com/Darssal/MemLab/blob/main/docs/ARCHITECTURE.md) · [Memory Policy](https://github.com/Darssal/MemLab/blob/main/memlab/memory_manager/manager.py) · [Evaluation Control](https://github.com/Darssal/MemLab/blob/main/memlab/pipeline/control_plane.py) · [Offline Checks](https://github.com/Darssal/MemLab/blob/main/docs/TESTING.md)

### [Recruitment-Text-Classification](https://github.com/Darssal/Recruitment-Text-Classification)

**Text Classification Baselines & HTTP Batching** · `scikit-learn` `TF-IDF` `Random Forest` `ThreadPoolExecutor`

提供中文字符 TF-IDF／随机森林基线、可选 BERT 路径和统一 CSV／JSONL 接口。划分训练集后拟合词表，按实际类别顺序对齐概率；HTTP 批处理设置超时、有界重试和输入顺序恢复。

[Baseline](https://github.com/Darssal/Recruitment-Text-Classification/blob/main/src/job_text_classification/baseline.py) · [HTTP Adapter](https://github.com/Darssal/Recruitment-Text-Classification/blob/main/src/job_text_classification/http_adapter.py) · [Regression Checks](https://github.com/Darssal/Recruitment-Text-Classification/blob/main/tests/test_regressions.py)

## Research Experience

- **基于时序Transformer的跨井域泛化测井预测系统** · 在研，2026.06–2027.06（计划）。研究方向：时序 Transformer、跨井域泛化与测井预测。
- **国家级大学生创新训练项目** · 项目成员，2026.09 结题。项目为“基于联合时空注意力机制和多模态大模型的地层信息处理系统——油田数据预测和隐私安全研究”；参与 Web 平台开发、地质数据读取与可视化，以及裂缝识别的多模态任务验证。

## Selected Honors

- **2025** · 第十八届先进机器人及仿真技术大赛 · 国赛一等奖
- **2025** · 睿抗机器人开发者大赛（RAICOM），编程技能竞赛 · 全国总决赛三等奖
- **2025** · 全国高校计算机能力挑战赛，C++ 本科组 · 全国决赛三等奖
- **2026** · Interdisciplinary Contest In Modeling（ICM）· Honorable Mention

完整研究、荣誉与教育信息见 [Academic Homepage](https://darssal.github.io/) 与 [Public CV](https://darssal.github.io/cv.html)。

<details>
<summary>Code Scope & Attribution</summary>

三个独立仓库提供精选工程实现、合成示例与离线检查。FracLogGPT-Lite 的公开 4B 实验与原论文 7B 模型分开记录；MemLab 的离线检查未运行原论文完整评测；文本分类基线未实现 JoVE 论文的完整词表分流与 RAG 链路。论文结果与公开代码验证范围分别说明。

训练调用 ms-swift，模型与适配器使用 Transformers／PEFT。MemLab 的 DeerFlow 适配保留 [ByteDance / deer-flow](https://github.com/bytedance/deer-flow) 上游归属。各仓库保留来源、依赖与公开范围说明：[FracLogGPT-Lite](https://github.com/Darssal/FracLogGPT-Lite) · [MemLab](https://github.com/Darssal/MemLab/blob/main/THIRD_PARTY.md) · [Recruitment-Text-Classification](https://github.com/Darssal/Recruitment-Text-Classification/blob/main/THIRD_PARTY.md)。[Research-Code-Collection](https://github.com/Darssal/Research-Code-Collection) 保留项目索引与工程笔记。

</details>
