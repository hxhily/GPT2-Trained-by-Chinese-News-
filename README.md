# GPT2-Trained-by-Chinese-News-
A small-scale GPT-2 model trained by Chinese News
# GPT2 中文新闻语料训练与生成

本项目基于 **GPT-2**，使用中文新闻语料进行训练与文本生成实验。通过对大规模中文新闻数据进行预训练和微调，模型能够生成较为连贯的新闻段落。

---

## 📌 项目特点

- 使用 **中文新闻语料**（约 8GB），覆盖多领域新闻文本。  
- 基于 **GPT-2 小模型配置**，支持在单卡消费级 GPU 上训练。  
- 已实现从 **数据预处理 → 模型训练 → 文本生成** 的完整流程。  
- 在 **RTX 4060Ti 16GB** 上单个 epoch 训练耗时约 **33 小时**。  

---

## ⚙️ 模型配置

训练使用的 GPT2 配置如下：

```json
{
  "initializer_range": 0.02,
  "layer_norm_epsilon": 1e-05,
  "n_ctx": 1024,
  "n_embd": 768,
  "n_head": 12,
  "n_layer": 10,
  "n_positions": 1024,
  "vocab_size": 13317
}
