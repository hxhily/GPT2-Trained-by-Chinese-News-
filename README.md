# GPT2 中文新闻语料训练与生成

本项目基于 **GPT-2**，使用中文新闻语料进行训练与文本生成实验。通过对大规模中文新闻数据进行预训练和微调，模型能够生成相对连贯的新闻短段落。

---

项目特点

- 使用 **中文新闻语料**（约 279MB），覆盖多领域新闻文本。  
- 基于 **GPT-2 小模型配置**，在单卡型号为GTX4060TI 16G的GPU上训练。  
- 已实现从 **数据预处理 → 模型训练 → 文本生成** 的完整流程。  
- 训练耗时约 **33 小时**。  

---

模型配置

训练使用的 GPT2 配置如下：（轻量化模型训练配置）

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
```


---

执行命令

训练命令：

```shell
python train.py --device 0 --model_config config/model_config_small.json --tokenizer_path cache/vocab_small.txt --raw_data_path data/train.json --tokenized_data_path data/tokenized/ --raw --epochs 1 --batch_size 8 --lr 1.5e-4 --warmup_steps 2000 --log_step 10 --stride 768 --gradient_accumulation 1 --num_pieces 20 --min_length 128 --output_dir model/ --writer_dir tensorboard_summary/
```

生成命令：

```shell
python generate.py --device 0 --length 1000 --batch_size 1 --nsamples 5 --temperature 0.8 --topk 50 --topp 0.9 --model_config config/model_config_small.json --tokenizer_path cache/vocab_small.txt --model_path model/final_model --prefix 2025年9月22日， --save_samples --save_samples_path samples/ --repetition_penalty 1.2
```

生成结果样例：




