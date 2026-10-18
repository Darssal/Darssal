<p align="center">
  <img src="assets/profile-banner.svg" alt="Darssal — Multimodal AI, Agent Memory, Python Engineering" width="100%">
</p>

<p align="center">
  <a href="https://github.com/Darssal/FracLogGPT-Lite">多模态项目</a> ·
  <a href="https://github.com/Darssal/Research-Code-Collection/tree/main/projects/memlab">Agent 记忆</a> ·
  <a href="https://github.com/Darssal/Research-Code-Collection/blob/main/docs/ENGINEERING_NOTES.md">工程笔记</a>
</p>

**多模态模型适配 · Agent 记忆 · Python 实验工程**

关注模型与系统之间的工程问题：训练阶段如何衔接、推理中断如何恢复、多会话记忆如何组装，以及实验结果如何核查。下面三个项目提供源码、运行说明和测试入口。

## 代表项目

### 01 / [FracLogGPT-Lite](https://github.com/Darssal/FracLogGPT-Lite)

**成像测井裂缝解释的多模态实验框架。** 基于 Qwen 模型，组织领域语料处理、LoRA-SFT、DPO / SimPO 与 Frac-VCD 解码实验。

- **阶段衔接与恢复**：配置驱动命令生成，解析 checkpoint 接续下游；按稳定样本键恢复预测，并对输出去重、加锁。
- **视觉对比解码**：同步原图与扰动图分支，融合下一 token 的 logits，维护 KV cache 与多模态字段。

`Python` `PyTorch` `Transformers` `PEFT / LoRA` `ms-swift`

[项目文档](https://github.com/Darssal/FracLogGPT-Lite) · [解码实现](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/vcd.py) · [恢复机制](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/predictions.py) · [无 GPU 验证](https://github.com/Darssal/FracLogGPT-Lite/blob/main/docs/QUICKSTART.md)

---

### 02 / [MemLab](https://github.com/Darssal/Research-Code-Collection/tree/main/projects/memlab)

**面向并行 Agent 会话的多层记忆与实验控制。** 将近期上下文、热缓存、元数据、向量检索和可选大对象存储组织为统一记忆接口。

- **记忆与上下文策略**：按重要度和对象大小分层放置；检索结果去重、预算控制，已有直接工具证据时绕过检索。
- **会话与实验记录**：用 ContextVar 保留异步会话归属，追踪降级路径；按有效性条件筛选运行记录，并为失效阶段生成重跑计划。

`Python 3.12` `asyncio` `Redis` `PostgreSQL` `Qdrant`

[架构说明](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/memlab/docs/ARCHITECTURE.md) · [记忆策略](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/memlab/memlab/memory_manager/manager.py) · [实验控制](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/memlab/memlab/pipeline/control_plane.py) · [离线测试](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/memlab/docs/TESTING.md)

---

### 03 / [招聘文本三分类](https://github.com/Darssal/Research-Code-Collection/tree/main/projects/job-text-classification)

**中文文本分类基线与服务批处理。** 提供字符 TF-IDF + 随机森林、可选 BERT 路径，以及统一的 CSV / JSONL 数据接口。

- **评测一致性**：先划分文本，再拟合训练词表；拒绝重复文本，按实际类别顺序对齐概率与指标。
- **可靠批处理**：外部服务请求设置超时和有界重试，并发结果保持输入顺序；失败记录错误类型，预测输出默认不带原文。

`Python` `scikit-learn` `TF-IDF` `Random Forest` `ThreadPoolExecutor`

[合成示例与运行](https://github.com/Darssal/Research-Code-Collection/tree/main/projects/job-text-classification#快速运行) · [分类流程](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/job-text-classification/src/job_text_classification/baseline.py) · [服务适配](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/job-text-classification/src/job_text_classification/http_adapter.py) · [回归测试](https://github.com/Darssal/Research-Code-Collection/blob/main/projects/job-text-classification/tests/test_regressions.py)

## 设计与取舍

[工程笔记](https://github.com/Darssal/Research-Code-Collection/blob/main/docs/ENGINEERING_NOTES.md)记录三个具体问题：预测输出如何支持恢复、共享记忆管理器如何区分异步会话、文本分类如何避免词表泄漏。每节对应实现、小例子和测试。

[![Research code checks](https://github.com/Darssal/Research-Code-Collection/actions/workflows/checks.yml/badge.svg)](https://github.com/Darssal/Research-Code-Collection/actions/workflows/checks.yml)

<details>
<summary>验证记录与项目来源</summary>

2026-10-18 的代码验证记录：FracLogGPT-Lite 59 项公共单元测试、MemLab 53 项离线测试、文本分类 16 项回归测试。测试覆盖相应代码行为；模型效果与外部服务实验的状态见各项目说明。

训练调用 ms-swift，模型加载基于 Transformers / PEFT；MemLab 保留 DeerFlow 适配来源。公开内容包含源码、配置、测试与合成示例，真实数据、权重和实验结果保留在本地。详见[来源与依赖](https://github.com/Darssal/Research-Code-Collection/blob/main/THIRD_PARTY.md)及[公开范围](https://github.com/Darssal/Research-Code-Collection/blob/main/docs/PUBLICATION_SCOPE.md)。

</details>
