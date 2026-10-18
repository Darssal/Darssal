<p align="center">
  <img src="assets/profile-banner.svg" alt="Darssal — Multimodal AI, Python and reproducible experiments" width="100%">
</p>

<p align="center">
  <a href="https://github.com/Darssal/FracLogGPT-Lite">项目介绍</a> ·
  <a href="https://github.com/Darssal/FracLogGPT-Lite/blob/main/docs/QUICKSTART.md">无 GPU 快速验证</a> ·
  <a href="https://github.com/Darssal/FracLogGPT-Lite/tree/main/tests">查看测试</a>
</p>

关注多模态模型适配与 Python 实验工程。当前公开项目是 **FracLogGPT-Lite**，围绕成像测井裂缝解释组织数据处理、模型适配、推理与评测。

## [FracLogGPT-Lite](https://github.com/Darssal/FracLogGPT-Lite)

以 Qwen 模型为基础，提供领域语料处理、LoRA-SFT、DPO / SimPO 实验配置与 Frac-VCD 视觉对比解码。训练调用 ms-swift，模型与 adapter 加载基于 Transformers / PEFT。

**技术栈：** Python · PyTorch · Transformers · PEFT / LoRA · ms-swift

### 从实现与测试了解项目

- **实验编排与阶段衔接**：从配置生成阶段命令、记录运行状态，解析 checkpoint 接续下游阶段。[编排实现](https://github.com/Darssal/FracLogGPT-Lite/blob/main/scripts/run_pipeline.py) · [checkpoint 解析](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/checkpoints.py) · [测试](https://github.com/Darssal/FracLogGPT-Lite/blob/main/tests/test_run_pipeline.py)
- **推理中断恢复**：用稳定样本键跳过已完成预测，对结果去重，并通过输出文件锁避免并发覆盖。[实现](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/predictions.py) · [测试](https://github.com/Darssal/FracLogGPT-Lite/blob/main/tests/test_predictions.py)
- **视觉对比解码**：同步处理原图与扰动图分支，融合下一 token 的 logits，提供同步解码与缓存路径。[实现](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/vcd.py) · [测试](https://github.com/Darssal/FracLogGPT-Lite/blob/main/tests/test_vcd.py)

[数据处理](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/data.py)负责 SFT / 偏好格式转换、图像引用检查和数据集划分；[评测模块](https://github.com/Darssal/FracLogGPT-Lite/blob/main/src/fraclog/metrics.py)解析参考与预测文本中的计数、位置和形态标签，计算文本标签一致性及过计数 / 欠计数等指标。

### 快速验证

公共代码测试与阶段命令预演无需 GPU、模型权重或私有测井资料，步骤见[使用指南](https://github.com/Darssal/FracLogGPT-Lite/blob/main/docs/QUICKSTART.md)。

公开仓库包含代码、实验配置、测试与合成格式示例；真实资料、权重和实验结果未公开，模型效果需由实际实验验证。
