<p align="center">
  <img src="assets/profile-banner.svg" alt="Darssal — Multimodal AI, Python and reproducible experiments" width="100%">
</p>

<p align="center">
  <a href="https://github.com/Darssal/FracLogGPT-Lite">主打项目</a> ·
  <a href="https://github.com/Darssal/FracLogGPT-Lite/tree/main/src/fraclog">阅读核心代码</a> ·
  <a href="https://github.com/Darssal/FracLogGPT-Lite/tree/main/tests">查看测试</a>
</p>

## Hi, I'm Darssal

关注多模态模型在专业场景中的应用，以及从数据处理、模型适配到推理与评测的工程实现。目前的代表项目是 **FracLogGPT-Lite**：面向成像测井裂缝解释的多模态实验框架。

这里展示可以直接阅读和验证的代码、实验配置与测试。

## Featured project

### [FracLogGPT-Lite](https://github.com/Darssal/FracLogGPT-Lite)

**把成像测井裂缝解释任务组织为可检查、可编排、可评测的多模态实验流程。**

围绕 Qwen 模型，提供领域语料处理、LoRA-SFT、DPO / SimPO 实验配置、视觉对比解码与结构化评测工具。

| 工程重点 | 代码中可以看到的实现 |
| --- | --- |
| 数据处理 | SFT / 偏好数据转换、图像引用检查与数据集划分 |
| 实验编排 | 配置驱动的阶段调度、checkpoint 解析和运行状态记录 |
| 推理流程 | Transformers 推理入口、预测恢复与 Frac-VCD 双分支解码 |
| 评测工具 | 裂缝计数、文本位置 / 形态一致性、幻觉与过度计数指标 |
| 代码验证 | 数据、指标、推理与流程相关单元测试 |

**技术栈：** Python · PyTorch · Transformers · PEFT / LoRA · ms-swift

公开仓库提供实验代码和合成格式示例；真实测井资料、模型权重与实验结果未公开。实验配置用于比较不同路线，模型效果需由实际实验验证。

## Explore the implementation

- [数据与格式](https://github.com/Darssal/FracLogGPT-Lite/blob/main/docs/DATA_SCHEMA.md)：输入如何检查与转换。
- [实验编排](https://github.com/Darssal/FracLogGPT-Lite/blob/main/scripts/run_pipeline.py)：训练阶段如何通过 checkpoint 衔接。
- [推理与解码](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/vcd.py)：原图与扰动图的 logits 如何融合。
- [评测实现](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/metrics.py)：预测文本如何转化为可比较的指标。

<sub>Multimodal AI experiments, with readable Python implementations and explicit evaluation boundaries.</sub>
