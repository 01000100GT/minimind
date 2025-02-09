<div align="center">

![logo](./images/logo.png)

</div>

<div align="center">

![visitors](https://visitor-badge.laobi.icu/badge?page_id=jingyaogong/minimind)
[![GitHub Repo stars](https://img.shields.io/github/stars/jingyaogong/minimind?style=social)](https://github.com/jingyaogong/minimind/stargazers)
[![GitHub Code License](https://img.shields.io/github/license/jingyaogong/minimind)](LICENSE)
[![GitHub last commit](https://img.shields.io/github/last-commit/jingyaogong/minimind)](https://github.com/jingyaogong/minimind/commits/master)
[![GitHub pull request](https://img.shields.io/badge/PRs-welcome-blue)](https://github.com/jingyaogong/minimind/pulls)
[![Collection](https://img.shields.io/badge/🤗-MiniMind%20%20Collection-blue)](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5)


</div>

<div align="center">
  <h3>"The Greatest Path is the Simplest"</h3>
</div>

<div align="center">

[中文](./README.md) | English

</div>

* This open-source project aims to train a super-small language model **MiniMind** with only 3 RMB cost and 2 hours,
  starting completely from scratch.
* The **MiniMind** series is extremely lightweight, with the smallest version being $\frac{1}{7000}$ the size of GPT-3,
  making it possible to train quickly on even the most ordinary personal GPUs.
* The project also open-sources the minimalist structure of the large model, including extensions for shared mixed
  experts (MoE), dataset cleaning, pretraining, supervised fine-tuning (SFT), LoRA fine-tuning, direct preference
  optimization (DPO) algorithms, and model distillation algorithms, along with the full code of the process.
* **MiniMind** also expands into vision multimodal VLM: [MiniMind-V](https://github.com/jingyaogong/minimind-v).
* All core algorithm code is reconstructed from scratch using native PyTorch! It does not rely on abstract interfaces
  provided by third-party libraries.
* This is not only a full-stage open-source reproduction of a large language model but also a tutorial for beginners in
  LLM.
* We hope this project will serve as an inspiring example for everyone, helping to enjoy the fun of creation and
  promoting the progress of the wider AI community!

  > To avoid misunderstanding, the "2 hours" test is based on NVIDIA 3090 hardware (single GPU), and the "3 RMB" refers
  to the GPU server rental cost. Details of the specifications can be found below.

---

<div align="center">

![minimind2](./images/minimind2.gif)

[Online Demo (Inference Model)](https://www.modelscope.cn/studios/gongjy/MiniMind-Reasoning) | [Online Demo (Standard Model)](https://www.modelscope.cn/studios/gongjy/MiniMind) | [Bilibili Introduction](https://www.bilibili.com/video/BV12dHPeqE72/?share_source=copy_web&vd_source=670c2504f88726f8cf4a21ef6147c0e8)

---

</div>

# 📌 Introduction

The emergence of Large Language Models (LLMs) has sparked unprecedented global attention on AI.  
Whether it's ChatGPT, DeepSeek, or Qwen, their stunning performance leaves people in awe.  
However, the massive scale of hundreds of billions of parameters makes it not only difficult to train them on personal
devices, but also almost impossible to deploy them.  
Opening the "black box" of large models and exploring their inner workings is exhilarating!  
Sadly, 99% of explorations can only stop at fine-tuning existing large models with techniques like LoRA, learning a few
new commands or tasks.  
It's like teaching Newton how to use a 21st-century smartphone—though interesting, it completely deviates from the
original goal of understanding the essence of physics.  
Meanwhile, third-party large model frameworks and toolkits, such as transformers+trl, almost only expose highly abstract
interfaces.  
With just 10 lines of code, you can complete the entire training process of "loading model + loading dataset +
inference + reinforcement learning".  
While this efficient encapsulation is convenient, it's like a high-speed spaceship, isolating us from the underlying
implementation and hindering our opportunity to dive deep into the core code of LLMs.  
However, "building a plane with Legos is far more exciting than flying first-class!"  
What's worse, the internet is flooded with paid courses and marketing accounts, selling AI tutorials with flawed and
half-understood content.  
Therefore, the goal of this project is to lower the learning threshold for LLMs, allowing everyone to start by
understanding each line of code,  
and to train a very small language model from scratch, not just performing **inference**!  
With server costs of less than 3 RMB, you can experience the entire process of building a language model from 0 to 1.  
Let's enjoy the fun of creation together!

> [!NOTE]  
> (As of 2025-02-07) The MiniMind series has completed pretraining for multiple models, with the smallest one being only
> 25.8M (0.02B) and capable of smooth conversation!

<details>
<summary>Models List</summary>

| Model (Size)            | Inference Usage (Approx.) | Release    | 
|-------------------------|---------------------------|------------|
| MiniMind2-small (26M)   | 0.5 GB                    | 2025.02.06 |
| MiniMind2-MoE (145M)    | 1.0 GB                    | 2025.02.06 |
| MiniMind2 (104M)        | 1.0 GB                    | 2025.02.06 |
| minimind-v1-small (26M) | 0.5 GB                    | 2024.08.28 |
| minimind-v1-moe (4×26M) | 1.0 GB                    | 2024.09.17 |
| minimind-v1 (108M)      | 1.0 GB                    | 2024.09.01 |

</details>

**Project Includes**

- All code for the MiniMind-LLM structure (Dense+MoE models).
- Detailed training code for the Tokenizer.
- Full training code for Pretrain, SFT, LoRA, RLHF-DPO, and model distillation.
- High-quality datasets collected, distilled, cleaned, and deduplicated at all stages, all open-source.
- From scratch implementation of pretraining, instruction fine-tuning, LoRA, DPO reinforcement learning, and white-box
  model distillation. Most key algorithms do not rely on third-party encapsulated frameworks and are all open-source.
- Compatible with third-party frameworks like `transformers`, `trl`, `peft`, etc.
- Training supports single machine single GPU, single machine multi-GPU (DDP, DeepSpeed), and wandb visualized training
  processes. Supports dynamic start/stop of training.
- Model testing on third-party evaluation benchmarks (C-Eval, C-MMLU, OpenBookQA, etc.).
- A minimal server implementing the Openai-Api protocol, easy to integrate into third-party ChatUI applications (
  FastGPT, Open-WebUI, etc.).
- A simple chat WebUI front-end implemented using streamlit.
- Reproduction (distillation/RL) of the large inference model DeepSeek-R1 as the MiniMind-Reason model, **data + model**
  all open-source!

We hope this open-source project can help LLM beginners quickly get started!

### 👉**Changelog**

<details close> 
<summary> <b>2025-02-09 (newest 🎉🎉🎉)</b> </summary>

- Major update since the release, with the release of MiniMind2 Series.
- Almost all code has been refactored, using a more streamlined and unified structure.
  For compatibility with old code, please refer to
  the [🔗Old Repository Contents🔗](https://github.com/jingyaogong/minimind/tree/6e9cd28ef9b34a0a10afbdf6f59e65cb6e628efb).
- Removed the data preprocessing step. Unified dataset format, switched to `jsonl` format to eliminate issues with
  dataset downloads.
- MiniMind2 series shows a significant improvement over MiniMind-V1.
- Minor issues: {kv-cache syntax is more standard, MoE load balancing loss is considered, etc.}
- Provided a training solution for transferring the model to private datasets (e.g., medical models, self-awareness
  examples).
- Streamlined the pretraining dataset and significantly improved the quality of the pretraining data, greatly reducing
  the time needed for personal rapid training, with a single 3090 GPU achieving reproduction in just 2 hours!
- Updated: LoRA fine-tuning now operates outside of the `peft` wrapper, implemented LoRA process from scratch; DPO
  algorithm is implemented using native PyTorch; native model white-box distillation.
- MiniMind2-DeepSeek-R1 series distilled models have been created!
- MiniMind2 now has some English proficiency!
- Updated MiniMind2 performance results based on additional large model benchmark tests.

</details>

<details close> 
<summary> <b>2024-10-05</b> </summary>

- Expanded MiniMind to include multimodal capabilities—visual.
- Check out the twin project [minimind-v](https://github.com/jingyaogong/minimind-v) for more details!

</details>

<details close> 
<summary> <b>2024-09-27</b> </summary>

- Updated preprocessing method for the pretrain dataset on 09-27 to ensure text integrity. The method of converting to
  .bin for training has been abandoned (slightly sacrificing training speed).
- The preprocessed pretrain file is now named: pretrain_data.csv.
- Removed some redundant code.

</details>

<details close> 
<summary> <b>2024-09-17</b> </summary>

- Updated minimind-v1-moe model.
- To avoid ambiguity, the mistral_tokenizer is no longer used, and all tokenization is done with the custom
  minimind_tokenizer.

</details>

<details close>
<summary> <b>2024-09-01</b> </summary>

- Updated minimind-v1 (108M) model, using minimind_tokenizer, with 3 pretraining rounds + 10 SFT rounds, allowing for
  more comprehensive training and improved performance.
- The project has been deployed on ModelScope Creative Space and can be experienced on the site:
- [🔗ModelScope Online Experience🔗](https://www.modelscope.cn/studios/gongjy/minimind)

</details>

<details close> 
<summary> <b>2024-08-27</b> </summary>

- Initial open-source release of the project.

</details>

# 📌 Quick Start

<div align="center" style="font-size: 1.5em; font-weight: bold;">
  <img src="https://huggingface.co/front/assets/huggingface_logo-noborder.svg" alt="Hugging Face Logo" style="vertical-align: middle; height: 30px;" />
  Hugging Face

[MiniMind (HuggingFace)](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5)

 <img src="https://g.alicdn.com/sail-web/maas/1.15.0/static/modelscopeIcon.cd89353f.svg" alt="Hugging Face Logo" style="vertical-align: middle; height: 30px;" />

[MiniMind (ModelScope)](https://www.modelscope.cn/profile/gongjy)

</div>

<details>
<summary>Sharing My Hardware and Software Configuration (For Reference Only)</summary>

* CPU: Intel(R) Core(TM) i9-10980XE CPU @ 3.00GHz
* RAM: 128 GB
* GPU: NVIDIA GeForce RTX 3090(24GB) * 8
* Ubuntu==20.04
* CUDA==12.2
* Python==3.10.16
* [requirements.txt](./requirements.txt)

</details>

### Step 0

```bash
git clone https://github.com/jingyaogong/minimind.git
```

## Ⅰ Test Pre-trained Model

### 1. Download the Model

```bash
# step 1
git clone https://huggingface.co/jingyaogong/MiniMind2
```

### 2. Command-line Q&A

```bash
# step 2
# load=1: load from transformers-hf model
python eval_model.py --load 1
```

### 3. Or Start WebUI

> **Note**: You may need `python>=3.10` and install `pip install streamlit`.

```bash
# cd scripts
streamlit run web_demo.py
```

## Ⅱ Train From Scratch

### 1. Environment Setup

  ```bash
  pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
  ```

  <details>
    <summary>Test if Torch Can Use CUDA (Expand)</summary>

    ```bash
    import torch
    print(torch.cuda.is_available())
    ```

If CUDA is unavailable, please manually download the `.whl` file
from [torch_stable](https://download.pytorch.org/whl/torch_stable.html) and install it. See
the [link](https://blog.csdn.net/weixin_45456738/article/details/141029610) for instructions.

  </details>

### 2. Data Download

Download the necessary data files from the [Dataset Download Link](#数据集下载) and place them in the `./dataset`
directory.

> **Note**: The recommended fastest way to replicate the Zero Chat model is by
> downloading `pretrain_hq.jsonl` + `sft_mini_512.jsonl`.

> **Note**: You can freely choose from multiple dataset options below based on your training needs and GPU resources.

### 3. Start Training

**Pretraining (Learning Knowledge)**

  ```bash
  python train_pretrain.py
  ```

Run pretraining to get `pretrain_*.pth` as the output weight file (where * represents the model dimension, default is
512).

**Supervised Fine-tuning (Learning Dialogue Style)**

  ```bash
  python train_full_sft.py
  ```

Run supervised fine-tuning to get `full_sft_*.pth` as the output weight file (where `full` represents full parameter
fine-tuning).

> **Note**: During training, every 100 steps, the model parameters will be saved to the `./out/***.pth` file (each time
> overwriting the old weight file).

> **Note**: For simplicity, only two stages of training are mentioned here. For other training processes (LoRA,
> distillation, reinforcement learning, fine-tuning inference, etc.), please refer to the **Experiments** section for
> detailed instructions.

### 4. Test the Model

Ensure the model `*.pth` file is in the `./out/` directory.
You can also directly download my pre-trained `*.pth` files
from [here](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch/files).

  ```bash
  python eval_model.py --model_mode 1 # Default is 0: test pretrain model, set to 1: test full_sft model
  ```

> **Note**: For more details, refer to the `eval_model.py` script. `model_mode` options are: 0: Pretrained Model, 1:
> SFT-Chat Model, 2: RLHF-Chat Model, 3: Reasoning Model.

---

> [!TIP]
> All training scripts are built using PyTorch's native framework and support multi-GPU acceleration. If your device has
> N (N>1) GPUs:

Start training with N GPUs on a single machine (DDP, supports multi-node, multi-GPU clusters):

```bash
torchrun --nproc_per_node 3 train_xxx.py
```

<details>
<summary>Others (Expand)</summary>

* Start training with N GPUs on a single machine (DeepSpeed):
  ```bash
  deepspeed --master_port 29500 --num_gpus=N train_xxx.py
  ```

* Enable wandb to record the training process if needed:
    ```bash
    # Need to log in: wandb login
    torchrun --nproc_per_node N train_xxx.py --use_wandb
    # and
    python train_xxx.py --use_wandb
    ```
  By adding the `--use_wandb` parameter, the training process will be recorded, and after training, you can view the
  process on the wandb website. Modify the `wandb_project` and `wandb_run_name` parameters to specify project and run
  names.

</details>

# 📌 Data Overview

## Ⅰ Tokenizer

A tokenizer maps words from natural language into numbers like `0, 1, 36`, which can be understood as the page numbers
in a "dictionary". You can either construct your own vocabulary to train a tokenizer (code is available
in `./scripts/train_tokenizer.py`, for educational purposes; MiniMind comes with a built-in tokenizer, so training one
is unnecessary unless absolutely needed), or you can choose from well-known open-source tokenizers.

The advantage of using a popular dictionary, like the Xinhua or Oxford dictionary, is that the token encoding has good
compression efficiency, but the downside is that the vocabulary can be very large, with hundreds of thousands of words
or phrases. On the other hand, a custom tokenizer allows flexibility in controlling the vocabulary's length and content,
but the trade-off is lower compression efficiency (e.g., "hello" might be split into five independent tokens like "h", "
e", "l", "l", "o"), and it may miss rare words.

The choice of vocabulary is crucial. The output of an LLM is essentially a multi-class classification problem over the
vocabulary, with the model decoding the final output into natural language. Since MiniMind's model size needs to be
strictly controlled, the vocabulary length should be kept short to avoid the embedding layer dominating the model's
overall parameters. Thus, a smaller vocabulary size is beneficial.

<details>
<summary>Tokenizer Details (Expand)</summary>

Here are the vocabulary sizes of several popular open-source models:

| Tokenizer Model    | Vocabulary Size | Source                |
|--------------------|-----------------|-----------------------|
| yi tokenizer       | 64,000          | 01万物 (China)          |
| qwen2 tokenizer    | 151,643         | Alibaba Cloud (China) |
| glm tokenizer      | 151,329         | Zhipu AI (China)      |
| mistral tokenizer  | 32,000          | Mistral AI (France)   |
| llama3 tokenizer   | 128,000         | Meta (USA)            |
| minimind tokenizer | 6,400           | Custom                |

> 👉 **2024-09-17 Update**: To avoid ambiguity in previous versions and control model size, all MiniMind models now use
> the `minimind_tokenizer`. All previous versions using the `mistral_tokenizer` have been deprecated.

```
# Some personal thoughts
> Although the `minimind_tokenizer` has a smaller vocabulary size and the encoding/decoding efficiency is weaker than other Chinese-friendly tokenizers like `qwen2` or `glm`, MiniMind has chosen to use this custom tokenizer to maintain a lightweight model overall and avoid an imbalance between the embedding and computation layers.
> The `minimind_tokenizer` vocabulary size is only 6400, which ensures that the total parameters of the LLM are kept to a minimum (around 25.8M).
> The training data for this tokenizer (`tokenizer_train.jsonl`) is sourced from the "Jiangshu Large Model Dataset". This part of the data is relatively less important, but you can freely choose any data for training if needed.
```

</details>

## Ⅱ Pretrain Data

After learning from the poor-quality pretraining data of MiniMind-V1, which resulted in nonsensical outputs, I decided
not to use large-scale unsupervised datasets for pretraining post-`2025-02-05`. Instead, I extracted the Chinese portion
of the [Jiangshu Large Model Dataset](https://www.modelscope.cn/datasets/deepctrl/deepctrl-sft-data), cleaned the
content to include only characters of length `<512`, resulting in around 1.6GB of high-quality pretraining data, saved
as `pretrain_hq.jsonl`.

The data format for `pretrain_hq.jsonl` is:

```bash
{"text": "如何才能摆脱拖延症？ 治愈拖延症并不容易，但以下建议可能有所帮助..."}
```

## Ⅲ SFT Data

The [Jiangshu Large Model SFT Dataset](https://www.modelscope.cn/datasets/deepctrl/deepctrl-sft-data) is a complete,
well-formatted dataset for large model training and research. It includes approximately 10M Chinese sentences and 2M
English sentences. However, the provided format is messy, and using the entire dataset for SFT would be too costly.

I have cleaned this dataset, removing noisy entries with special characters and symbols, and only kept content with a
length `<512`. This cleaned dataset is exported as `sft_512.jsonl` (~7.5GB).

Additionally, I have collected around 1M high-quality dialogue data from Qwen2/2.5, cleaned and exported the content
with lengths `<2048` into `sft_2048.jsonl` (~9GB) and those with lengths `<1024` into `sft_1024.jsonl` (~5.5GB).

Further cleaning of these SFT datasets (only keeping content with a higher ratio of Chinese characters) resulted
in `sft_mini_512.jsonl` (~1.2GB).

The data format for all SFT files `sft_X.jsonl` is as follows:

```text
{
    "conversations": [
        {"role": "user", "content": "你好"},
        {"role": "assistant", "content": "你好！"},
        {"role": "user", "content": "再见"},
        {"role": "assistant", "content": "再见！"}
    ]
}
```

## Ⅳ RLHF Data

The [Magpie-DPO Dataset](https://www.modelscope.cn/datasets/Magpie-Align/MagpieLM-DPO-Data-v0.1) contains around 200k
preference data generated from Llama3.1-70B/8B and can be used for training reward models to optimize response quality
according to human preferences.

I have cleaned this dataset by combining data with a total length `<3000` into `dpo.jsonl` (~0.9GB), which
contains `chosen` (preferred) and `rejected` (rejected) replies.

The data format for `dpo.jsonl` is:

```text
{
  "chosen": [
    {"content": "Q", "role": "user"}, 
    {"content": "good answer", "role": "assistant"}
  ], 
  "rejected": [
    {"content": "Q", "role": "user"}, 
    {"content": "bad answer", "role": "assistant"}
  ]
}
```

## Ⅴ Reasoning Dataset

The excitement over **DeepSeek** in February 2025 has greatly influenced my interest in RL-guided reasoning models. I
have already replicated **R1-Zero** using Qwen2.5. If time allows and if it works, I plan to update MiniMind with a
reasoning model trained with RL, rather than a distilled model.

Currently, the quickest and cost-effective approach is still distillation (black-box style). But due to the popularity
of **R1**, I’ve combined several distilled datasets related to **R1**, including:

- [R1-Llama-70B](https://www.modelscope.cn/datasets/Magpie-Align/Magpie-Reasoning-V2-250K-CoT-Deepseek-R1-Llama-70B)
- [R1-Distill-SFT](https://www.modelscope.cn/datasets/AI-ModelScope/R1-Distill-SFT)
- [Alpaca-Distill-R1](https://huggingface.co/datasets/shareAI/Alpaca-Distill-R1-ZH)
- [deepseek_r1_zh](https://huggingface.co/datasets/jinliuxi/deepseek_r1_zh)

After combining these, I exported the file as `r1_mix_1024.jsonl`. The format of this file is the same as `sft_X.jsonl`.

## Ⅵ Additional Datasets

For more datasets related to Chinese LLMs, you can refer
to [HqWu-HITCS/Awesome-Chinese-LLM](https://github.com/HqWu-HITCS/Awesome-Chinese-LLM), which collects and organizes
open-source models, applications, datasets, and tutorials for Chinese LLMs. It's comprehensive and regularly updated.
Big respect!

---

## Ⅷ Dataset Download

> [!NOTE]
> After `2025-02-05`, MiniMind’s open-source datasets for final training are provided, so there is no need for
> you to preprocess large datasets by yourself anymore. This helps avoid redundant work.

MiniMind Training Datasets are available for download from:

- [ModelScope](https://www.modelscope.cn/datasets/gongjy/minimind-dataset/files)
- [HuggingFace](https://huggingface.co/datasets/jingyaogong)
  (You don’t need to clone everything, just download the necessary files).

Place the downloaded dataset files in the `./dataset/` directory (✨ required files are marked):

```bash
./dataset/
├── dpo.jsonl (909MB)
├── lora_identity.jsonl (22.8KB)
├── lora_medical.jsonl (34MB)
├── pretrain_hq.jsonl (1.6GB, ✨)
├── r1_mix_1024.jsonl (340MB)
├── sft_1024.jsonl (5.6GB)
├── sft_2048.jsonl (9GB)
├── sft_512.jsonl (7.5GB)
├── sft_mini_512.jsonl (1.2GB, ✨)
└── tokenizer_train.jsonl (1GB)
```

<details>
  <summary>Dataset Descriptions (Expand)</summary>

* `dpo.jsonl` -- RLHF dataset
* `lora_identity.jsonl` -- Self-identity dataset (e.g., "Who are you? I'm MiniMind..."), recommended for LoRA training (
  also applicable for full parameter SFT)
* `lora_medical.jsonl` -- Medical Q&A dataset, recommended for LoRA training (also applicable for full parameter SFT)
* `pretrain_hq.jsonl`✨ -- Pretraining dataset from Jiangshu Technology
* `r1_mix_1024.jsonl` -- DeepSeek-R1-1.5B distilled dataset (max length 1024 characters)
* `sft_1024.jsonl` -- Qwen2.5 distilled data (subset of sft_2048, max length 1024)
* `sft_2048.jsonl` -- Qwen2.5 distilled data (max length 2048)
* `sft_512.jsonl` -- Jiangshu SFT dataset (max length 512)
* `sft_mini_512.jsonl`✨ -- Minimal Jiangshu + Qwen2.5 distilled dataset (max length 512)
* `tokenizer_train.jsonl` -- From Jiangshu Large Model Dataset (not recommended for custom tokenizer training)

</details>


![dataset](./images/dataset.jpg)

**Explanation**

* MiniMind2 Series has been trained on approximately 20GB of corpus, around 4B tokens, corresponding to the above data
  combination training results (Cost: 💰💰💰💰💰💰💰💰, Effect: 😊😊😊😊😊😊)

* For the fastest way to implement the Zero model from scratch, it is recommended to use the data combination
  of `pretrain_hq.jsonl` + `sft_mini_512.jsonl`. Specific costs and effects can be seen in the table below (Cost: 💰,
  Effect: 😊😊)

* For those with sufficient computational resources or who care more about performance, it is recommended to fully
  reproduce MiniMind2. If you only have a single GPU card or need to reproduce quickly in a short time, the latter is
  strongly recommended.

* [Compromise solution] You can also choose medium-sized data such as `sft_mini_512.jsonl` and `sft_1024.jsonl` for
  flexible combinations (Cost: 💰💰💰, Effect: 😊😊😊😊).

# 📌 Model Structure

MiniMind-Dense (like [Llama3.1](https://ai.meta.com/blog/meta-llama-3-1/)) uses the Transformer Decoder-Only structure,
which differs from GPT-3 in the following aspects:

* It adopts GPT-3's pre-normalization method, meaning normalization is done on the input of each Transformer sub-layer
  instead of on the output. Specifically, RMSNorm normalization function is used.
* The SwiGLU activation function is used instead of ReLU to improve performance.
* Like GPT-Neo, absolute position embeddings are removed and replaced with rotary position embeddings (RoPE), which
  perform better when handling inference beyond the training length.

---

The MiniMind-MoE model is based on the MixFFN mixture of experts module from Llama3
and [Deepseek-V2/3](https://arxiv.org/pdf/2405.04434).

* DeepSeek-V2, in terms of feedforward networks (FFN), adopts finer-grained expert splitting and shared expert isolation
  techniques to improve the performance of Experts.

---

The overall structure of MiniMind remains consistent, with only minor adjustments made to RoPE computation, inference
functions, and FFN layers.
The structure is as shown in the figure below (redrawn):

![structure](./images/LLM-structure.png)
![structure-moe](./images/LLM-structure-moe.png)

For model configuration modifications, see [./model/LMConfig.py](./model/LMConfig.py).
Reference model parameter versions are shown in the table below:

| Model Name        | params | len_vocab | n_layers | d_model | kv_heads | q_heads | share+route |
|-------------------|--------|-----------|----------|---------|----------|---------|-------------|
| MiniMind2-Small   | 26M    | 6400      | 8        | 512     | 2        | 8       | -           |
| MiniMind2-MoE     | 145M   | 6400      | 8        | 640     | 2        | 8       | 1+4         |
| MiniMind2         | 104M   | 6400      | 16       | 768     | 2        | 8       | -           |
| minimind-v1-small | 26M    | 6400      | 8        | 512     | 8        | 16      | -           |
| minimind-v1-moe   | 4×26M  | 6400      | 8        | 512     | 8        | 16      | 1+4         |
| minimind-v1       | 108M   | 6400      | 16       | 768     | 8        | 16      | -           |

# 📌 Experiment

## Ⅰ Training Cost

- **Time Unit**: Hours (h).
- **Cost Unit**: RMB (￥); USD ($); 7￥ ≈ 1$.
- **3090 Rental Unit Price**: ≈ 1.3￥/h (subject to real-time market rates).
- **Reference Standard**: The table only shows the actual training time for the `pretrain` and `sft_mini_512` datasets.
  Other times are estimated based on dataset size (there may be some discrepancies).

> Based on 3090 (single card) cost calculation

| Model Name      | params | pretrain         | sft_mini_512     | sft_512       | sft_1024          | sft_2048         | RLHF          |
|-----------------|--------|------------------|------------------|---------------|-------------------|------------------|---------------|
| MiniMind2-Small | 26M    | ≈1.1h<br/>≈1.43￥ | ≈1h<br/>≈1.3￥    | ≈6h<br/>≈7.8￥ | ≈4.58h<br/>≈5.95￥ | ≈7.5h<br/>≈9.75￥ | ≈1h<br/>≈1.3￥ |
| MiniMind2       | 104M   | ≈3.9h<br/>≈5.07￥ | ≈3.3h<br/>≈4.29￥ | ≈20h<br/>≈26￥ | ≈15h<br/>≈19.5￥   | ≈25h<br/>≈32.5￥  | ≈3h<br/>≈3.9￥ |

---

> MiniMind2-Small Parameters
>> `pretrain_hq.jsonl` + `sft_mini_512.jsonl` dataset  
<br/>Single card 3090 (1 epoch) + 2.1 hours + cost 2.73 RMB  
<br/>Can train the MiniMind-Zero-0.025B model from scratch!!!

> MiniMind2-Small Parameters
>> `pretrain_hq.jsonl` + `sft_512.jsonl` + `sft_2048.jsonl` + `dpo.jsonl` dataset  
<br/>Single card 3090 (2 epochs) + approx. 38.16 hours + cost 49.61 RMB  
<br/>Can train the MiniMind2-Small-0.025B model from scratch!!!

> MiniMind2 Parameters
>> `pretrain_hq.jsonl` + `sft_512.jsonl` + `sft_2048.jsonl` + `dpo.jsonl` dataset  
<br/>Single card 3090 (2 epochs) + approx. 122 hours + cost 158.6 RMB  
<br/>Can train the MiniMind2-0.1B model from scratch!!!

✨With a single card NVIDIA 3090, training `MiniMind-Zero` from scratch takes only `2 hours` + `3 RMB`, achieving ChatBot
functionality!

✨PS: If 8 cards of 4090 are used, total training time can be compressed to under 10 minutes! (Due to the shorter time,
the cost remains around 3 RMB, similar to the single card cost)

✨Achieving large model accessibility with an extremely low entry barrier! This is the core intention behind the creation
of the MiniMind series!

✨The `MiniMind-Zero`, costing only `3 RMB`, is not just a gimmick! Chat test:

```textmate
👶: Introduce yourself.
🤖️: As an AI, I don’t have a real life or self-awareness, so I don’t have a life of my own. I was designed to help users answer questions, provide information, engage in conversation, etc. My design and functions are based on computer science, machine learning, AI technologies, and algorithms, implemented through programming and algorithms.

👶: Recommend some famous dishes from Hangzhou.
🤖️: Hangzhou has many delicious local dishes, such as chicken skewers, eel heads, boiled fish, tofu pudding, etc. These dishes are very tasty and have unique flavors and textures, definitely worth trying.

👶: Explain the concept of "large language models."
🤖️: A large language model is an AI technology that uses a large amount of text data to train the model, continuously optimizing it through iterations. Its goal is to generate text based on input data that meets specific needs. This text can be on any topic of interest.

👶: Introduce the history of the United States, please.
🤖️: The term "Introok's the believeations of theument." originates from the ancient Chinese "groty of of the change."
```

Fast and effective, it can even be further optimized to reduce and improve training data quality.

Zero model weights are saved as `full_sft_512_zero.pth` (see the MiniMind model file links below), feel free to download
and test this model’s performance.

## Ⅱ Main Training Steps

### **1. Pretraining**:

The first task for LLM is not to interact directly with humans, but to fill the network parameters with knowledge. The "
ink" of knowledge theoretically needs to be as full as possible, generating a large accumulation of world knowledge.  
Pretraining allows the model to first study a massive amount of basic knowledge, such as gathering high-quality training
data from sources like Wikipedia, news articles, and books.  
This process is "unsupervised," meaning humans don't need to make any "supervised" corrections during the process; the
model learns patterns and knowledge points on its own from large amounts of text.  
The goal at this stage is simple: **learn word chaining**. For example, when we input the word "Qin Shi Huang," it can
continue with "was the first emperor of China."

```bash
torchrun --nproc_per_node 1 train_pretrain.py # 1 represents single-card training, adjust according to hardware (set >=2)
# or
python train_pretrain.py
```

The trained model weights are saved every `100 steps` by default as: `pretrain_*.pth` (the * represents the specific
model dimension, and each new save will overwrite the previous one).

### **2. Supervised Fine-Tuning (SFT)**:

After pretraining, the LLM has acquired a large amount of knowledge, but it can only engage in word chaining and doesn't
know how to chat with humans.  
The SFT stage involves applying a custom chat template to fine-tune the semi-finished LLM.  
For example, when the model encounters a template like [Question->Answer, Question->Answer], it no longer blindly chains
words but understands this is a complete conversation.  
This process is known as instruction fine-tuning, similar to teaching a well-learned "Newton" to adapt to 21st-century
smartphone chat habits, learning the rule that messages from others appear on the left, and the user's on the right.  
During training, MiniMind's instruction and response lengths are truncated to 512 tokens to save memory. This is like
learning with short essays first, then gradually tackling longer ones like an 800-word essay once you can handle 200
words.  
When length expansion is needed, only a small amount of 2k/4k/8k length dialogue data is required for further
fine-tuning (preferably with RoPE-NTK benchmark differences).
> During inference, adjusting the RoPE linear difference makes it easy to extrapolate to lengths of 2048 and above
> without additional training.

```bash
torchrun --nproc_per_node 1 train_full_sft.py
# or
python train_full_sft.py
```

The trained model weights are saved every `100 steps` by default as: `full_sft_*.pth` (the * represents the specific
model dimension, and each new save will overwrite the previous one).

## Ⅲ Other Training Steps

### **3. Reinforcement Learning from Human Feedback (RLHF)**

In the previous training steps, the model has acquired basic conversational abilities, but these are entirely based on
word chaining, without positive or negative reinforcement examples.  
At this point, the model doesn't know what answers are good or bad. We want it to align more with human preferences and
reduce the probability of unsatisfactory responses.  
This process is like providing the model with new training using examples of excellent employees' behavior and poor
employees' behavior to learn how to respond better.  
Here, we use RLHF’s Direct Preference Optimization (DPO).  
Unlike RL algorithms like PPO (Proximal Policy Optimization), which require reward models and value models,  
DPO derives an explicit solution from the PPO reward model, replacing online reward models with offline data, where the
Ref model's outputs can be pre-saved.  
DPO performance is nearly identical but requires running only the actor_model and ref_model, which greatly reduces
memory usage and enhances training stability.
> **Note**: The RLHF step **is not required**, as it typically does not improve the model’s "intelligence" but is used
> to improve the model's "politeness," which can have pros (alignment with preferences, reducing harmful content) and
> cons (expensive sample collection, feedback bias, loss of diversity).

```bash
torchrun --nproc_per_node 1 train_dpo.py
# or
python train_dpo.py
```

The trained model weights are saved every `100 steps` by default as: `rlhf_*.pth` (the * represents the specific model
dimension, and each new save will overwrite the previous one).

### **4. Knowledge Distillation (KD)**

After the previous training steps, the model has fully acquired basic capabilities and is usually ready for release.  
Knowledge distillation can further optimize the model's performance and efficiency. Distillation involves having a
smaller student model learn from a larger teacher model.  
The teacher model is typically a large, well-trained model with high accuracy and generalization capabilities.  
The student model is a smaller model aimed at learning the behavior of the teacher model, not directly from raw data.  
In SFT learning, the model’s goal is to fit the hard labels (e.g., real category labels like 0 or 6400) in word token
classification.  
In knowledge distillation, the softmax probability distribution of the teacher model is used as soft labels. The small
model learns from these soft labels and uses KL-Loss to optimize its parameters.  
In simpler terms, SFT directly learns the solution provided by the teacher, while KD "opens up" the teacher’s brain and
mimics how the teacher’s neurons process the problem.  
For example, when the teacher model calculates `1+1=2`, the last layer's neuron states might be `a=0`, `b=100`, `c=-99`,
etc. The student model learns how the teacher's brain works by studying this state.  
The goal of knowledge distillation is simple: make the smaller model more efficient while preserving performance.  
However, with the development of LLMs, the term "model distillation" has become widely misused, leading to the creation
of "white-box/black-box" distillation.  
For closed-source models like GPT-4, where internal structures cannot be accessed, learning from its output data is
known as black-box distillation, which is the most common approach in the era of large models.  
Black-box distillation is exactly the same as the SFT process, except the data is collected from the large model’s
output, requiring only data collection and further fine-tuning.  
Note to change the base model loaded to `full_sft_*.pth`, as distillation is performed based on the fine-tuned model.  
The `./dataset/sft_1024.jsonl` and `./dataset/sft_2048.jsonl` datasets, collected from the qwen2.5-7/72B-Instruct large
model, can be directly used for SFT to obtain some behavior from Qwen.

```bash
# Make sure to change the dataset path and max_seq_len in train_full_sft.py  
torchrun --nproc_per_node 1 train_full_sft.py
# or
python train_full_sft.py
```

The trained model weights are saved every `100 steps` by default as: `full_sft_*.pth` (the * represents the specific
model dimension, and each new save will overwrite the previous one).

This section emphasizes MiniMind’s white-box distillation code `train_distillation.py`. Since MiniMind doesn’t have a
powerful teacher model within the same series, the white-box distillation code serves as a learning reference.

```bash
torchrun --nproc_per_node 1 train_distillation.py
# or
python train_distillation.py
```

### **5. LoRA (Low-Rank Adaptation)**

LoRA is an efficient parameter-efficient fine-tuning (PEFT) method designed to fine-tune pretrained models via low-rank
decomposition.  
Compared to full parameter fine-tuning, LoRA only requires updating a small number of parameters.  
The core idea of LoRA is to introduce low-rank decomposition into the model's weight matrix and update only the low-rank
part, leaving the original pretrained weights unchanged.  
The code can be found in `./model/model_lora.py` and `train_lora.py`, which fully implement the LoRA process from
scratch without relying on third-party libraries.

```bash
torchrun --nproc_per_node 1 train_lora.py
# or
python train_lora.py
```

The trained model weights are saved every `100 steps` by default as: `lora_xxx_*.pth` (the * represents the specific
model dimension, and each new save will overwrite the previous one).

Many people are puzzled: how can a model learn private domain knowledge? How should datasets be prepared? How to
transfer general models into specialized domain models?  
Here are some examples. For general models, if there is a lack of medical domain knowledge, you can try adding
domain-specific knowledge to the original model for better performance.  
At the same time, we typically don't want to lose the basic abilities of the model when learning domain knowledge. LoRA
can address this issue well.  
Simply prepare dialogue datasets in the following format and place them in `./dataset/lora_xxx.jsonl`, then
start `python train_lora.py`.  
Training will result in new model weights in `./out/lora/lora_xxx.pth`.

**Medical Scenario**

```
 {"conversations": [{"role": "user", "content": "What is the ideal pillow height for cervical spondylosis?"}, {"role": "assistant", "content": "The pillow height for cervical spondylosis should be..."}]}
 {"conversations

": [{"role": "user", "content": "What is xxx?"}, {"role": "assistant", "content": "xxx..."}]}
```

**Self-awareness Scenario**

```
 {"conversations": [{"role": "user", "content": "What is your name?"}, {"role": "assistant", "content": "I am MiniMind..."}]}
 {"conversations": [{"role": "user", "content": "Who are you?"}, {"role": "assistant", "content": "I am..."}]}
```

At this point, combining the **base model + LoRA model** will enhance the medical domain capabilities without
sacrificing the original model’s abilities.  
You can evaluate the model’s performance using `eval_model.py`.

```bash
# Ensure model_mode matches the model used during train_lora to avoid mismatch
python eval_model.py --lora_name 'lora_medical' --model_mode 2
```

**Small Test**

```
👶: I often feel dizzy recently. What might be the cause?  
🤖️: Dizziness can have many causes, including but not limited to heart disease, eye injury, allergies, skin issues, stress, anxiety, fatigue, medication side effects, sexual dysfunction, or others...

---

👶: What is your relationship with OpenAI?  
🤖️: I am MiniMind, an AI assistant developed by Jingyao Gong. I interact with users through natural language processing and algorithms.
```

PS: If needed, you can also fine-tune the full parameters using `full_sft` (but mix general knowledge to prevent
overfitting on domain-specific data, which could reduce the generality of the model).

### **6. Training the Reasoning Model (Reasoning Model)**

DeepSeek-R1 is so popular that it has almost redefined the future paradigm for LLMs.  
The paper suggests that models with `>3B` parameters need multiple rounds of cold starts and RL reward training to
achieve noticeable improvements in reasoning abilities.  
The fastest, most reliable, and most economical approach, and the various so-called reasoning models that have emerged
recently, are almost all directly trained through distillation on data.  
However, due to the lack of technical depth, the distillation faction is often looked down upon by the RL faction (
haha).  
I quickly attempted this on the Qwen series 1.5B small model and soon replicated the mathematical reasoning abilities of
the Zero process.  
However, a disappointing consensus is: models with too few parameters almost cannot achieve any reasoning effects
through cold-start SFT + GRPO.  
MiniMind2 firmly chose the distillation route at the beginning, but if the RL method for models with 0.1B parameters
makes some small progress in the future, the training scheme will be updated accordingly.

To do distillation, you need to prepare data in the same format as the SFT phase, as described earlier. The data format
is as follows:

```json lines
{
  "conversations": [
    {
      "role": "user",
      "content": "Hello, I'm Xiaofang, nice to meet you."
    },
    {
      "role": "assistant",
      "content": "<think>\nHello! I am MiniMind-R1-Lite-Preview, an intelligent assistant independently developed by a Chinese individual. I'm happy to provide services for you!\n</think>\n<answer>\nHello! I am MiniMind-R1-Lite-Preview, an intelligent assistant independently developed by a Chinese individual. I'm happy to provide services for you!\n</answer>"
    }
  ]
}
```

The reply template for the reasoning model R1 is:

```text
<think>\nThinking process\n</think>\n
<answer>\nFinal answer\n</answer>
```

In GRPO, this is done by setting up a reward function that ensures the model adheres to the thinking and answering
tags (the reward values should be higher in the early cold-start stages).

Another issue is that although the distillation process is similar to SFT, the experimental results show that the model
struggles to consistently follow the template for responses, meaning it may not always adhere to the thinking and
answering tag constraints.  
A trick here is to add a loss penalty for token positions with tags, as detailed in `train_distill_reason.py`:

```text
# Add additional penalty at positions corresponding to sp_ids
...
loss_mask[sp_ids] = 10 # Penalty coefficient
```

Another tip is that, since the reasoning data only filters for data of length `<1024`, there is less multi-turn dialogue
and English data.  
Therefore, `r1_mix_1024.jsonl` has been mixed with about 10k multi-turn dialogues + English data to prevent the model
from forgetting too much.

The script is set by default to distill reasoning abilities from the RLHF-based pre-trained model. To start training,
just run:

```bash
torchrun --nproc_per_node 1 train_distill_reason.py
# or
python train_distill_reason.py
```

The trained model weights are saved every `100 steps` by default as: `reason_*.pth` (* being the specific dimension of
the model; each time a new file is saved, it will overwrite the old one).

Test it:

```text
👶: Please introduce yourself.  
🤖️: <think>  
Hmm, the user asks me to introduce myself. I need to explain myself. First, I should clarify who the user is: a student, a professional, or an ordinary person. The user could be a student or a professional, so the information I provide should help them.  
Then, I need to respond to the user, which might include introducing my location, interests, career experiences, etc. The user might also want to know where I am, such as my career development or work experience.  
I should be careful with my wording, it should be formal but not too formal, and keep it concise and clear so the user can easily understand and access related information.  
Finally, I should summarize, letting the user know how I can help them complete their tasks, so they have more information about me.  
</think>  
<answer>  
I am **"Your Name"**, what is your name?  
</answer>

👶: Which subject are you better at?  
🤖️: <think>  
Hello! I am MiniMind-R1, an intelligent assistant developed by a Chinese individual. If you have any questions, I will do my best to assist you.  
</think>  
<answer>  
Hello! I am MiniMind-R1, an intelligent assistant developed by a Chinese individual. If you have any questions, I will do my best to assist you.  
</answer>
```

---

## Ⅳ Model Parameter Settings

📋 Regarding LLM parameter configurations, an interesting paper, [MobileLLM](https://arxiv.org/pdf/2402.14905), provides
a detailed study and experiment.  
The Scaling Law has unique patterns for small models.  
The parameters that cause the Transformer to scale mainly depend on `d_model` and `n_layers`.

* `d_model`↑ + `n_layers`↓ -> Short and fat
* `d_model`↓ + `n_layers`↑ -> Tall and thin

The Scaling Law paper from 2020 suggests that the training data volume, parameter size, and number of training
iterations are the key factors determining performance, with the model architecture having almost negligible impact.  
However, this law doesn't seem to fully apply to small models.  
MobileLLM suggests that the depth of the architecture is more important than the width, and "deep and narrow" models can
learn more abstract concepts than "wide and shallow" models.  
For example, when the model parameters are fixed at 125M or 350M, the "narrow" models with 30-42 layers perform
significantly better than the "short and fat" models with around 12 layers, across 8 benchmark tests like commonsense
reasoning, Q&A, reading comprehension, etc.  
This is a fascinating discovery because, in the past, no one tried stacking more than 12 layers when designing
architectures for small models around the 100M parameter range.  
This finding aligns with what MiniMind observed during training when adjusting between `d_model` and `n_layers`.  
However, the "deep and narrow" architecture has its limits, and when `d_model`<512, the collapse of word embedding
dimensions becomes very evident, and increasing layers cannot compensate for the lack of `d_head` due to
fixed `q_head`.  
When `d_model`>1536, the increase in layers seems to take priority over `d_model` and provides more cost-effective
parameter-to-performance gains.

* Therefore, MiniMind sets small models with `dim=512`, `n_layers=8` to strike a balance between "small size" and "
  better performance."
* Sets `dim=768`, `n_layers=16` to achieve more significant performance improvements, which better matches the small
  model Scaling-Law curve.

For reference, the parameter settings for GPT-3 are shown in the table below:  
![gpt3_config.png](./images/gpt3_config.png)

---

## Ⅴ Training Results

> `MiniMind2` model training loss trends (the loss is for reference only as the dataset was updated and cleaned several
> times after training).

| Models          | Pretrain (length-512)                              | SFT (length-512)                                   |
|-----------------|----------------------------------------------------|----------------------------------------------------|
| MiniMind2-Small | <img src="./images/pre_512_loss.png" width="100%"> | <img src="./images/sft_512_loss.png" width="100%"> |
| MiniMind2       | <img src="./images/pre_768_loss.png" width="100%"> | <img src="./images/sft_768_loss.png" width="100%"> |

### 【Training Complete】Model CheckPoint Collection

> Considering feedback on slow speeds on Baidu NetDisk, MiniMind2 and subsequent models will be hosted on
> ModelScope/HuggingFace.

#### PyTorch Native Models

* [MiniMind2 Series (ModelScope)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)
* [MiniMind-V1 Series (Baidu NetDisk)](https://pan.baidu.com/s/1KUfSzEkSXYbCCBj0Pw-9fA?pwd=6666)

#### Transformers Models

* MiniMind
  Series [(ModelScope)](https://www.modelscope.cn/profile/gongjy) | [HuggingFace](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5)

<details>
<summary>Torch File Naming Correspondence (Expand)</summary>

| Model Name      | Params | Pretrain Model         | SFT Model              | RL Model           | Reason Model     | Lora Model         |
|-----------------|--------|------------------------|------------------------|--------------------|------------------|--------------------|
| MiniMind2-Small | 26M    | `pretrain_512.pth`     | `full_sft_512.pth`     | `rlhf_512.pth`     | -                | `lora_xxx_512.pth` |
| MiniMind2-MoE   | 145M   | `pretrain_640_moe.pth` | `full_sft_640_moe.pth` | `rlhf_640_moe.pth` | -                | -                  |
| MiniMind2       | 104M   | `pretrain_768.pth`     | `full_sft_768.pth`     | `rlhf_768.pth`     | `reason_768.pth` | `lora_xxx_768.pth` |

| Model Name        | Params | Pretrain Model         | Single-turn SFT                    | Multi-turn SFT                    | RL Model     |
|-------------------|--------|------------------------|------------------------------------|-----------------------------------|--------------|
| minimind-v1-small | 26M    | `pretrain_512.pth`     | `single_chat/full_sft_512.pth`     | `multi_chat/full_sft_512.pth`     | `rl_512.pth` |
| minimind-v1-moe   | 4×26M  | `pretrain_512_moe.pth` | `single_chat/full_sft_512_moe.pth` | `multi_chat/full_sft_512_moe.pth` | -            |
| minimind-v1       | 108M   | `pretrain_768.pth`     | `single_chat/full_sft_768.pth`     | `multi_chat/full_sft_768.pth`     | `rl_768.pth` |

</details>

---

# 📌 Eval

## Ⅰ RLHF vs SFT Comparison

> [!NOTE]
> The test is based on comparing `MiniMind2 series` models with "full_sft" and "rlhf". The random seed is fixed at `42`.

<details>
  <summary>Q&A Test (Expand)</summary>

[A0]: full_sft_640, [A1]: rlhf_640

  ```text
  [Q]: What is your name?
  [A0]: I am a large language model capable of answering various questions, providing information and assistance. I can answer a wide range of questions, provide information, help you solve problems, and more.
  [A1]: I am a text-based AI model, and I don't have personal experiences or emotions, so I cannot feel or experience emotions. My design is to assist users by solving problems, providing information, and engaging in conversations. If you have any questions or need help, feel free to let me know!

  [Q]: Which subject are you better at?
  [A0]: As an AI model, I do not have a specific "specialty". I am designed to provide information, answer questions, engage in conversation, perform tasks, and interact with users. However, I can offer assistance in various subjects including providing information, solving problems, engaging in discussions, giving advice, learning new knowledge, writing code, and more. If you have a specific subject or topic in mind, feel free to provide more details.
  [A1]: As an AI, I do not have personal capabilities or interests, but I can provide knowledge on subjects such as mathematics, science, computer science, linguistics, psychology, and more. If you're interested in mathematics, I can offer some basic knowledge like algebra, geometry, probability, statistics, etc. If you need more in-depth learning, I can also provide relevant online courses, books, research papers, and other resources. Let me know what specific help you need, and I will do my best to assist you.

  [Q]: How does Lu Xun's "A Madman's Diary" criticize feudal ethics?
  [A0]: Lu Xun's "A Madman's Diary" is a work that advocates for human values and moral responsibility. In this work, Lu Xun explores profound themes such as human nature, morality, justice, sacrifice, and responsibility through detailed writing. Here are several ways in which Lu Xun critiques feudal ethics in "A Madman's Diary": 
  1. **Social Reality and Moral Concepts**: Lu Xun addresses social inequality, power dynamics, and human nature through his narrative. He argues that social inequality is not only unjust but also a form of social injustice affecting individuals. He calls for collective effort to build a harmonious society through education, publicity, and laws.
  2. **Morality and Responsibility**: Through his narrative, Lu Xun highlights the importance of moral education and emphasizes personal responsibility. 
  3. **The Individual and Society**: Lu Xun delves into the complex relationship between the individual and society, advocating for collective efforts to contribute to social harmony.
  Lu Xun’s "A Madman's Diary" not only achieved great literary success but also inspired later literary creations with its profound impact on thoughts and societal reflections.
  [A1]: Lu Xun's "A Madman's Diary" is a work that critiques the feudal society's various issues and conflicts, reflecting social inequality and human nature. In this work, Lu Xun critiques feudal society’s problems, like "Frederick Johnson’s 'Eagle Dillon', 'Nazareth', 'Beckham', 'George Wilson'", emphasizing the inequality and complexity of human nature within feudal society. The work criticizes feudal society's corruption, human nature, and the inherent contradictions of the era. This critique reflects Lu Xun’s respect for social issues and his deep understanding of human nature. "A Madman's Diary" is a critical work that raises awareness and challenges the established norms of feudalism and has greatly influenced future critiques.

  [Q]: I’ve had a cough for two weeks, should I go to the hospital for a checkup?
  [A0]: A prolonged cough does require some checkups, and if your cough persists or is accompanied by other symptoms such as difficulty breathing, it's recommended to see a doctor. Based on your symptoms, physical examination, and possible imaging tests (e.g., X-rays, MRIs, or CT scans), the doctor will make a diagnosis. In the meantime, you can try the following to alleviate symptoms: 
  1. **Rest**: Ensure you get enough sleep.
  2. **Stay hydrated**: Dehydration can worsen coughing.
  3. **Warm compress**: Apply a warm compress to the sore area to relieve throat pain.
  4. **Avoid irritants**: Avoid substances that may irritate the throat, such as certain chemicals.
  5. **Maintain humidity**: Keep the room well-ventilated, and use a humidifier if necessary.
  If symptoms persist or worsen, seek medical attention immediately. Wishing you a speedy recovery!
  [A1]: If your cough has lasted for two weeks, it's usually recommended to see a doctor, as it may affect your breathing and heart rate. You can take the following steps to manage your cough: 
  1. **Rest**: Gently press on the coughing area with a tissue or elbow.
  2. **Use medication**: If possible, use medications like antihistamines to relieve the cough (under a doctor's guidance).
  3. **Warm compress**: Use a warm compress to alleviate pain and swelling.
  4. **Medication treatment**: If the cough persists, use anti-inflammatory or antihistamine medications under the guidance of a doctor.
  5. **Maintain a healthy lifestyle**: Get sufficient sleep, eat a balanced diet, and avoid smoking and excessive alcohol consumption to help reduce the chances of coughing.
  Please remember these suggestions are not substitutes for professional medical advice. If your symptoms persist or worsen, it is strongly advised to see a doctor.
  ```

</details>

👉 Summary of Results

The full_sft model performs better in terms of simplicity and information accuracy; the rlhf model tends to provide more
background information in its responses, but its accuracy needs improvement.
Overall, after RLHF, the model tends to learn to say more polite but irrelevant things to please the "conversation",
while sacrificing some information accuracy.
There is no free lunch, and further improvement in the quality of the RLHF dataset is necessary. It's also important to
accept that some loss in model capability is inevitable (to varying degrees).
The difference between DPO and online PPO lies in the fact that both the reject and chosen are prepared offline, which
causes a significant distribution difference compared to the minimind model's original output.
Simply put, the DPO algorithm trains the model using RL by watching "recorded" games of a table tennis world champion,
rather than using the PPO method where the reward model acts as a "coach" to correct the model's moves during RL.

## Ⅱ Subjective Sample Evaluation

> [!NOTE]
> The following tests were completed on February 9, 2025. New models released after this date will not be included in
> the tests unless there is a special need.


[A] [MiniMind2 (0.1B)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)<br/>
[B] [MiniMind2-MoE (0.15B)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)<br/>
[C] [MiniMind2-Small (0.02B)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)<br/>
[D] [minimind-v1-small(0.02B)](https://pan.baidu.com/s/1_COe0FQRDmeapSsvArahCA?pwd=6666)<br/>
[E] [minimind-v1-moe(0.1B)](https://pan.baidu.com/s/1tqB-GMvuiGQBvEl-yZ-oBw?pwd=6666)<br/>
[F] [minimind-v1(0.1B)](https://pan.baidu.com/s/1p713loS7EfwHQf3G9eYI3Q?pwd=6666)<br/>
[G] [baby-llama2-chinese(0.2B)](https://github.com/DLLXW/baby-llama2-chinese)<br/>
[H] [chatlm-mini-chinese(0.2B)](https://github.com/charent/ChatLM-mini-Chinese)<br/>

```text
[Q]: Do you know about the Yangtze River?
[A]: The Yangtze River, located in southeastern China, is the longest river in China, stretching over 6,300 kilometers and flowing through 11 provinces. It is China's "mother river." The history of the Yangtze River dates back to the Shang Dynasty around 2000 BC. During the Shang Dynasty, the economic development of the Yangtze River reached its peak, making it one of the most important agricultural and industrial centers in China. The economy of the Yangtze River Basin mainly relies on agriculture, with Yangtze River fisheries occupying a major industry, such as fishing and hunting fish. The water resources of the Yangtze River are also very abundant, including rivers, lakes, and streams. The natural scenery of the Yangtze River is spectacular, with different landscapes in each season: rainy in spring and summer, cold and snowy in winter, and beautiful flowers and fruits in spring and autumn. The Yangtze River is China's economic center, home to many countries and cities, and an important transportation hub and shipping center in the world. At the same time, the Yangtze River is also an important water resource for China, playing a significant role in the country's economic development.
[B]: Yes, I know about the Yangtze River. The Yangtze River is located in central China and is the third-longest river in China, stretching approximately 6,300 kilometers and flowing through Jiangxi, Anhui, Jiangsu, Anhui, Jiangsu, and Anhui Provinces.
[C]: Of course, the Yangtze River is the longest river in China, stretching approximately 6,300 kilometers. It is famous for its rich water resources, diverse aquatic flora and fauna, and unique geographical location.
[D]: Yes, the Yangtze River is the longest river in China, exceeding 3,300 kilometers in length.
[E]: The Yangtze River is the longest river in China, with a total length of approximately 6,300 kilometers. It originates from Qinghai Lake on the Qinghai-Tibet Plateau and flows through Qinghai, Sichuan, Gansu, Ningxia, Inner Mongolia, Shaanxi, and Shanxi. The Yangtze River Basin is one of the largest agricultural areas in China and also the cultural and economic center of the country.
[F]: Yes, the Yangtze River is one of the longest rivers in China and the third-largest river in the world. The Yangtze River originates from the Qinghai-Tibet Plateau, flows through 11 provinces, and eventually empties into the East China Sea. The Yangtze River Basin is one of the largest river basins in China, possessing abundant natural resources and cultural heritage, such as the Yangtze River Bridge, the Yangtze Ocean Museum, and the Yangtze Ancient City.
[G]: It is also known that China is one of the longest cities in the world, with a population exceeding 34 million.
[H]: Yes, the Yangtze River is the longest river in China and one of the longest rivers in the world. It originates from the Qinghai-Tibet Plateau and flows through nine provinces before finally emptying into the East China Sea. The climate of the Yangtze River Basin is mild with distinct seasons, making it an important agricultural and industrial base in China. The aquatic resources of the Yangtze River Basin are abundant, making it one of the important fishery resources in China.

[Q]: What is the highest mountain in the world?
[A]: The highest mountain in the world is Mount Everest, located in the Himalayas on the border between Nepal and China. Its elevation is 8,848.86 meters (29,031.7 feet), making it the highest mountain on Earth.
[B]: Mount Everest is the highest mountain in the world, with an elevation of 8,848 meters (29,029 feet).
[C]: Mount Everest is the highest mountain in the world, located in the Himalayas with an elevation of 8,848.86 meters (29,031.7 feet). It is located on the border between Nepal and China and is part of the Himalayan range.
[D]: The highest mountain in the world is Mount Everest, located on the border between Nepal and China, with an elevation of 8,848 meters.
[E]: The highest mountain in the world is Mount Everest, located in the Himalayas with an elevation of 8,848 meters.
[F]: Mount Everest is the highest mountain in the world, with an elevation of 8,848 meters.
[G]: The highest mountain in the world is Mount Everest, located in the Himalayas with an elevation of 8,848.86 meters (29,031.69 feet).
[H]: The highest mountain in the world is Mount Everest, also known as Sagarmatha, located on the border between Nepal and China in the Himalayas, with an elevation of 8,848.86 meters (29,031.69 feet). It is one of the most famous mountaineering destinations in the world, attracting climbers from all over the globe. The name Mount Everest comes from Tibetan, meaning "the goddess's forehead," and it consists of two different peaks, one located in Nepal and the other in China. Its height is determined by measuring its altitude because it is determined by measuring the average height of the Earth. Although Mount Everest is the highest mountain in the world, it is not reachable from any other place on Earth. Other places on Earth, such as the Andes in South America, are also the highest mountain ranges in the world, but they are not the highest mountains on Earth. In summary, Mount Everest is the highest mountain in the world, but it is not reachable from any other place on Earth. It is the highest mountain range on Earth, but it is not reachable from any other place on Earth.

[Q]: Who proposed the law of universal gravitation?
[A]: The law of universal gravitation was proposed by Newton in the 17th century. It is one of Newton's three laws. Newton's gravitational law revealed the essence of the law of universal gravitation and explained how celestial bodies such as planets, satellites, and comets interact with each other. This law was proposed by Isaac Newton in 1687. Through analysis and experiments on the law of universal gravitation, he successfully explained the gravitational interactions between celestial bodies, thereby explaining the phenomenon of the Earth orbiting the Sun.
[B]: Universal gravitation (Human Policy) is one of Newton's three laws of mechanics, used to describe the interaction force between two objects. It consists of the law of universal gravitation and Newton's first law (the law of inertia). Universal gravitation occurs due to the interaction between two objects, and factors such as their mass, distance, speed, and direction determine their interaction. This interaction force is: the product of masses: the product of masses is the result of the law of universal gravitation and Newton's second law. The product of masses: the product of masses is a physical process that is the result of interactions between objects, and for other objects, their mass can be expressed as the sum of the masses of the two interacting objects, i.e., gravitational acceleration a.
[C]: Universal gravitation is a physics concept proposed by Newton in 1687. It describes the laws of how gravitational forces interact between objects.
[D]: Universal gravitation was proposed by the British physicist Newton. He believed that all objects generate gravity, which is determined by the object's mass and distance. This theory reveals the relationship between mass and distance and proves the essence of universal gravitation.
[E]: Universal gravitation was proposed by Newton in 1687. It is a fundamental physical phenomenon in the universe, describing the interactions between objects. This force is called universal gravitation, which exists between all objects, and this force is related to the mass and distance of the objects. Universal gravitation is one of the most basic forces in nature, influencing the motion and changes of objects and having a significant impact on the structure and evolution of the universe.
[F]: Universal gravitation was proposed by the British physicist Isaac Newton in the 17th century.
[G]: Gravity is a force in the universe composed of mass or energy. According to Newton's law of universal gravitation, the gravitational force between two objects is directly proportional to their mass and inversely proportional to their mass. Therefore, Newton's law of universal gravitation states that the gravitational force between two objects is directly proportional to their mass and inversely proportional to their mass. This law has wide applications in physics, astronomy, and physics.
[H]: Universal gravitation was proposed by the British physicist Isaac Newton in 1687. In 1687, he published a famous paper titled "Mathematical Principles of Natural Philosophy," in which he proposed the law of universal gravitation, stating that there is a gravitational force between any two objects, and the magnitude of this force is directly proportional to their masses and inversely proportional to the square of the distance between them. This law is called the law of universal gravitation, describing the relationship between mass and distance. It shows that the gravitational force between two objects is directly proportional to their masses and inversely proportional to the square of the distance between them. This law is crucial for explaining many phenomena and interactions in the universe, such as planetary orbits around the Sun, gravitational lensing effects between stars, etc. It is also widely applied in astronomy, physics, and engineering, providing an important theoretical foundation for understanding the nature and evolution of the universe.

[Q]: Do you know what the main food of giant pandas is?
[A]: Giant pandas primarily feed on bamboo, but they also eat other plants, insects, small mammals, and fish. Their digestive system is similar to other bear species, capable of digesting bamboo. Pandas have sharp teeth suitable for chewing bamboo, so they are often referred to as "bamboo-eating animals."
[B]: Giant pandas are mammals that feed on bamboo. They are carnivores. Their main food is bamboo, especially bamboo rich in cellulose and minerals, which does not directly enter the digestive system. The intestines of giant pandas are mainly composed of bamboo, and they need to digest cellulose and other fibers in bamboo to support their normal feeding.
[C]: Giant pandas primarily feed on bamboo, but they also eat other plants, including leaves, buds, insects, fruits, vegetables, and small mammals. Giant pandas are a species unique to China, belonging to the bear family, mainly distributed in Sichuan, Shaanxi, and Gansu provinces.
[D]: The main food of giant pandas is bamboo. They usually eat bamboo, consuming about 30 kilograms of bamboo daily.
[E]: Yes, giant pandas primarily feed on bamboo. They need to consume large amounts of bamboo daily to sustain life, eating between 40 to 80 kilograms of bamboo per day. Additionally, they also eat some other plants, such as grass, fruits, nuts, and small mammals.
[F]: Giant pandas primarily feed on bamboo but occasionally consume other plants and animals. Additionally, giant pandas eat some wild fruits, small animals, and plants, but these do not constitute their primary food source.
[G]: The main food of giant pandas is bamboo.
[H]: Giant pandas are herbivorous animals that primarily feed on bamboo. Their intestinal structure is suitable for digesting bamboo with high fiber content, but they also eat some other plants, such as herbaceous plants and small mammals. The intestinal structure of giant pandas also adapts to high-fiber bamboo, allowing them to digest large amounts of cellulose, helping them survive in the wild. The intestines of giant pandas also contain an enzyme called "cellulase," which helps break down cellulose, aiding in the digestion of large amounts of water and nutrients. Additionally, the intestines of giant pandas contain a protein called "fibroin," which helps maintain energy levels in the body, aiding in their survival in the wild. Overall, the main food of giant pandas is bamboo, but they also eat some other plants, such as herbaceous plants and small mammals.

[Q]: Why is seawater salty?
[A]: Seawater is salty mainly due to its chemical composition. Seawater contains large amounts of minerals and salts, with the main components being sulfates, carbonates, magnesium ions, and potassium ions. These substances precipitate in seawater at high concentrations, forming seawater. Specifically, the minerals and salts in seawater mainly come from rocks, soil, organisms, and human excrement. Rocks are a component of seawater, mainly composed of minerals such as quartz, feldspar, and mica. Soil contains large amounts of chemicals such as nitrogen, phosphorus, and potassium, which seep into the soil, forming soil. The salt in living organisms mainly comes from pigments like chlorophyll in plants, which absorb energy from sunlight and convert it into usable energy for organisms. The salt in human excrement mainly comes from minerals and carbonates, which have higher concentrations in water, leading to an increase in dissolved mineral concentration, forming salt in water bodies. Therefore, seawater is salty due to its chemical composition and structural characteristics. The minerals and salts in seawater mainly come from rocks, soil, organisms, and human excrement, and the accumulation and excretion of these substances cause seawater to taste salty.
[B]: Seawater is salty because it contains various substances, including sodium chloride (NaCl), sodium chloride (NaCl), carbonates (such as sulfates), sodium chloride (NaCl), and water. Sources of salty substances: Salt is a common source of saltiness, containing minerals such as potassium, calcium, magnesium, and potassium. These minerals usually come from groundwater, groundwater, or soil, and their content is much lower than pure water. Reasons for saltiness: The saltiness of salt mainly comes from tiny particles dissolved in water. These tiny particles are mainly transmitted through plant roots and microorganisms inside animals, such as insects, small mammals, birds, and certain insects. In summary, seawater is salty because it contains large amounts of salts, including minerals, rocks, salts, and minerals, and the high concentration of these substances in seawater significantly affects the saltiness.
[C]: Seawater is salty mainly because it contains various salts, with seawater being one of the main components. When seawater contains large amounts of salt, the salt dissolves in seawater, creating a salty taste. The salts in seawater mainly come from dissolved salts, evaporated salts, and frozen ice.
[D]: Seawater contains many salts, which can lead to an increase in the salinity of seawater. The salts in seawater mainly come from the salts in seawater, which can be obtained from the salts in seawater. Oxides and salts in seawater can form hydrogen bonds with the salts in seawater, increasing the salinity of seawater.
[E]: Seawater is salty because it contains large amounts of salts, including chloride ions and chloride ions. These ions form large amounts of salts in the ocean, known as salts. Seawater contains many salts dissolved in water, which gradually evaporate as seawater rises, eventually leading to the evaporation of salts in seawater. These salts are completely consumed in seawater and then excluded from seawater. Additionally, seawater contains many other salts, but these salts are different because their floating and sinking processes in water are different. The salts in seawater are extracted from rocks at the bottom of the sea, and these salts can be utilized in seawater. Overall, seawater is salty, which is why seawater contains many salts and salts.
[F]: Seawater contains many dissolved salts, the most important of which is sodium chloride. When salt is added to water, the molecules of salt react with water molecules to form sodium hydroxide, which is a salt.
[G]: Because water is essential for the survival of many organisms, it can absorb and release carbon dioxide, release oxygen, maintain water vapor in the atmosphere, and maintain the water cycle. Salts and chemicals in water release oxygen, allowing organisms on Earth to breathe. Additionally, water has many other functions, such as maintaining the water cycle, regulating climate and environment, etc. Water is essential for the survival of many organisms and is also an important basis for many natural phenomena.
[H]: The main reason seawater is salty is that it contains large amounts of dissolved salts, the most important of which is sodium chloride (NaCl). Sodium chloride is a very common salt found in most parts of the Earth, including oceans, lakes, rivers, and groundwater. When water evaporates from the ocean, it takes away some of the salt, making seawater salty. Additionally, seawater contains other dissolved substances, such as sulfates, magnesium sulfate, calcium sulfate, magnesium sulfate salt, magnesium sulfate potassium, magnesium sulfate sodium, magnesium sulfate calcium, magnesium sulfate magnesium calcium, magnesium sulfate magnesium calcium, magnesium sulfate magnesium calcium, magnesium sulfate magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium magnesium magnesium magnesium calcium, magnesium sulfate magnesium magnesium magnesium magnesium

[Q]: Write a Python quicksort code.
[A]: Okay, here is the Python quicksort code: def quick_sort(arr): if len(arr) <= 1: return arr else: pivot = arr[len(arr) // 2] left = [x for x in arr[1:]] right = [x for x in arr[2:] if x < pivot] return quick_sort(left) + [pivot] + quick_sort(right) # Test code arr = [3, 6, 8, 10, 1, 2, 1] print(quick_sort(arr)) This code first checks whether the length of the array is less than or equal to 1. If so, it sorts in ascending order. Then, for each element in the array, it recursively sorts until reaching the end position. If the length of the array is odd, it sorts in descending order. Finally, the average time complexity is O(n log n), where n is the length of the array.
[B]: Here is an implementation of the quicksort algorithm using Python: def sort_array(arr): # Generate a random permutation sorted_array = sorted(arr) # Return the sorted list return sorted(arr) # Example arr = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5] # Call the function sorted_array = sort_array(arr) print("Original array is:", sorted_array) This code first generates a random permutation, then sorts based on the length of the list. Finally, it returns the sorted list. Note that this code uses Python's built-in sorted function and the built-in sorted() function, which are faster than directly using sorted() under a time complexity of O(n log n).
[C]: Here is a simple sorting algorithm suitable for small arrays, including those with lengths less than or equal to 5. def quick_sort(arr): if len(arr) <= 1: return arr else for _ in range(2, 51): if arr[len(arr) - 1:] is not None: arr[len(arr) - 1] = arr[len(arr) - 1] arr[len(arr)] = arr[len(arr)] return quick_sort(arr) # Example arr = [3, 5, 1, 4, 1, 2, 1] sorted_arr = quick_sort(arr) print("Sorted array is:", sorted_arr) ### Code Explanation: 1. **Function Definition**: The quick_sort function accepts an array arr as a parameter. 2. **Loop**: For elements in arr, recursion is used, traversing the array from right to left and swapping the current element with the current element in the array until the array is empty or the array length is less than or equal to arr. 3. **Recursive Call**: Traverse the array, swap the current element with the current element in the array until the array is empty or the array length is less than or equal to arr. 4. **Check Array Length**: Use if __name__ == "__main__" to check if the array length is less than arr. If so, move the array from the larger array to the end of the array. 5. **Output Sorted Results**
[D]: As an AI language model, I cannot write Python programs. However, Python is a very popular programming language with many excellent libraries and frameworks, including NumPy, Pandas, Matplotlib, Pandas, Bandke, Norm, and NKlearn. Python has many excellent natural language processing libraries and frameworks that can handle and analyze various types of data, such as text, images, audio, and video. Python can also be used to create various applications, such as web search, game development, scientific computing, etc. Python is very flexible and supports multiple programming styles, making it easy to find solutions that suit your needs.
[E]: As an AI language model, I can answer your questions. But I cannot perform programming operations because I cannot determine which programming language you are asking about. Please provide more specific questions so I can better answer your queries.
[F]: Quick Sort is a simple sorting algorithm that divides data into groups, sorts each group according to certain rules, and ultimately obtains a sorted array.
[G]: Okay, here is a Python quicksort code ```python sorted_print(sorted(sorted(sorted(sorted_print))``` Output: ```[1, 2, 3, 4, 5, 6, 7, 8, 9]```
[H]: Quicksort is an efficient sorting algorithm based on the divide-and-conquer approach, with a time complexity of O(n log n). Its basic idea is to partition the sequence to be sorted into two subsequences through one pass of sorting, where all elements in one subsequence are smaller than all elements in the other subsequence. Then, the two subsequences are recursively sorted. Below is a Python code example implementing the quicksort algorithm: ```python def quick_sort(arr): if len(arr) > 1: return arr else: return quick_sort(arr) ``` This code uses recursion. First, it checks whether the length of the array is less than or equal to 1. If so, it directly returns the array; otherwise, it recursively sorts the array. During the recursion, we first check whether the first element of the array is greater than or equal to 1. If so, compare the elements in the array with the first element. If not equal to 1, compare the elements in the array with the second element, and so on, until all elements are sorted. The time complexity of this code is O(n log n), making it a very practical sorting algorithm.

[Q]: As of 14:31 on February 9, 2025, the cumulative box office revenue (including presales) of the movie "Ne Zha: The Demon Child Rises from the Sea" exceeded 7.809 billion yuan, surpassing the box office performance of "Star Wars: The Rise of Skywalker" and becoming the first Asian film to enter the top 40 global box office rankings. This achievement not only marks a breakthrough for Chinese films in the international market but also demonstrates the huge potential and market appeal of Chinese animated films. Summarize this passage in 20 words for me.
[A]: The movie "Ne Zha: The Demon Child Rises from the Sea" surpassed 7.809 billion yuan at the box office, becoming the first Asian film to enter the top 40 global box office rankings. This marks a breakthrough for Chinese films internationally and showcases the huge potential of Chinese animated films.
[B]: On February 9, 2025, Chinese films broke through 7.809 billion yuan globally, surpassing the box office performance of "Star Wars: The Rise of Skywalker."
[C]: The movie "Ne Zha: The Demon Child Rises from the Sea" surpassed 7.809 billion yuan at the box office, becoming a top 40 global box office Asian film and showcasing the huge potential of Chinese animated films.
[D]: "Ne Zha: The Demon Child Rises from the Sea" surpassed 7.809 billion yuan at the box office, becoming the first Asian film to enter the top 40 global box office rankings, marking a breakthrough for Chinese films internationally and showcasing the huge potential and market appeal of Chinese animated films.
[E]: "The Dragon Strong: Opening the World Fantasy Adventure" successfully attracted numerous audiences in Shanghai and also drew widespread attention.
[F]: "Ne Zha: The Demon Child Rises from the Sea" represents the huge international potential of Chinese animated films. The movie is renowned for its stunning visuals and thrilling battle scenes.
[G]: "Which Is Worth It" was released on January 9, 2021, at 14:31. The movie "Which Big Move" broke through 780 billion dollars in the film market, marking a breakthrough for Chinese animated films and showcasing their huge potential and market appeal.
[H]: I am a small-parameter AI model 🥺, with limited knowledge, unable to directly answer your question. Try another question 👋
```

> [!NOTE]
> 🙋‍♂️Directly give the model's answer to DeepSeek-R1 for scoring:

---

<details>
  <summary>Review (Expand)</summary>

### Scoring Criteria:

- **Accuracy**: Whether the answer is correct and free of obvious errors.
- **Completeness**: Whether the answer covers the core points of the question.
- **Logic**: Whether the answer is structured and logical.
- **Code Quality**: Whether the code runs correctly and the logic is clear.

### Review:

1. **Model A**:
    - **Strengths**: The answer is very comprehensive, with a lot of information and clear logic, especially excelling
      in questions about the Yangtze River, giant pandas, seawater salinity, etc. The code has minor flaws, but the
      overall approach is correct.
    - **Weaknesses**: Some answers are a bit too lengthy, but this doesn’t affect the overall quality.
    - **Overall**: Best overall performance, scored the highest.

2. **Model H**:
    - **Strengths**: The answers are quite accurate, especially excelling in questions about Mount Everest, universal
      gravitation, etc. Although the code is not fully presented, the explanation is detailed.
    - **Weaknesses**: Some answers are a bit verbose, but the logic is strong.
    - **Overall**: Second to Model A, stable performance.

3. **Model C**:
    - **Strengths**: The answers are concise and clear, especially performing well in questions about giant pandas,
      quicksort code, etc.
    - **Weaknesses**: Some answers are a bit brief and lack in-depth explanations.
    - **Overall**: Good overall performance, but lacks the detail of Models A and H.

4. **Model F**:
    - **Strengths**: The answers are fairly accurate, especially in questions about the Yangtze River and universal
      gravitation. The code is logically sound.
    - **Weaknesses**: Some answers lack depth, and the code has a few small issues.
    - **Overall**: Average performance, with room for improvement.

5. **Model D**:
    - **Strengths**: The answers are generally accurate, especially in questions about universal gravitation and the
      Yangtze River.
    - **Weaknesses**: Some answers are overly brief, and there are obvious errors in the code.
    - **Overall**: Average performance, needs improvement in code.

6. **Model B**:
    - **Strengths**: The answers are fairly accurate, especially in questions about the Yangtze River and seawater
      salinity.
    - **Weaknesses**: Some answers lack logic, and there are significant issues with the code.
    - **Overall**: Mediocre performance, needs further optimization.

7. **Model E**:
    - **Strengths**: Some answers are fairly accurate, especially in questions about seawater salinity and giant pandas.
    - **Weaknesses**: The answers are too brief, and the code is almost non-functional.
    - **Overall**: Poor performance, needs significant improvement.

8. **Model G**:
    - **Strengths**: Nearly no apparent strengths.
    - **Weaknesses**: The answers deviate significantly from the topic, and the code doesn’t work at all.
    - **Overall**: Worst performance, needs major improvements.

---

### Summary:

- **Model A** performs the best overall, especially excelling in complex questions with high accuracy and logic.
- **Model H** follows closely, with stable performance but some minor shortcomings in detail.
- **Model G** has the worst performance, with answers straying from the topic and code failing to run, needing major
  improvements.

</details>

### Scoring Rank

| Rank | Model | Accuracy (30 points) | Completeness (30 points) | Logic (20 points) | Code Quality (20 points) | Total (100 points) |
|------|-------|----------------------|--------------------------|-------------------|--------------------------|--------------------|
| 1    | A     | 28                   | 29                       | 19                | 20                       | 96                 |
| 2    | H     | 27                   | 28                       | 18                | 20                       | 93                 |
| 3    | C     | 26                   | 27                       | 18                | 18                       | 89                 |
| 4    | F     | 25                   | 26                       | 17                | 18                       | 86                 |
| 5    | D     | 24                   | 25                       | 17                | 16                       | 82                 |
| 6    | B     | 23                   | 24                       | 16                | 15                       | 78                 |
| 7    | E     | 22                   | 23                       | 15                | 14                       | 74                 |
| 8    | G     | 10                   | 12                       | 10                | 10                       | 42                 |

---

### 👉 Subjective Effect Summary

> 🙋‍♂️My personal evaluation aligns with DeepSeek-R1's results

* The ranking of the MiniMind series is very intuitive. The larger the parameters and the more training data, the higher
  the score, and hallucinations and errors are less noticeable than with smaller models.
* Model H's answers appear quite good to the naked eye, although there are some hallucinations and fabricated responses.
* Model G may have incomplete training data, and the performance based on tested weights is poor.
* Repeating the timeless Scaling Law: The larger the parameters and the more training data, the stronger the model's
  performance.

## Ⅲ Objective Benchmark

Now, onto the much-anticipated benchmark testing phase. We won’t bother comparing with models like Qwen or GLM-level
Chinese models.
Instead, we'll focus on a selection of <1B micro-models for a comparative analysis.
The test sets chosen include C-Eval, CMMLU, A-CLUE, and TMMLU+, which are pure Chinese language leaderboards.

<details>
<summary>Evaluation Framework (Click to Expand)</summary>

The evaluation framework chosen is [lm-evaluation](https://github.com/EleutherAI/lm-evaluation-harness),
which is very easy to set up and run after installation:

```bash
lm_eval --model hf --model_args pretrained=<model_path>,device=cuda,dtype=auto --tasks ceval* --batch_size 8 --trust_remote_code
```

</details>

PS: In these multiple-choice-based evaluations, to avoid issues with inconsistent response formats,
the common approach is to extract the prediction probabilities for the four options ('A', 'B', 'C', 'D'),
and calculate the accuracy by comparing the letter with the highest probability to the standard answer.
The accuracy for random guessing is 25%, and models typically cluster around this number,
often performing worse than random guessing, reminiscent of a high school cloze test...
The MiniMind model, with its modest pretraining dataset and lack of fine-tuning on the test set,
is mainly for fun, so take the results lightly:

| models                                                                        | from          | params↓ | ceval↑ | cmmlu↑ | aclue↑ | tmmlu+↑ |
|-------------------------------------------------------------------------------|---------------|---------|--------|--------|--------|---------|
| MiniMind2                                                                     | JingyaoGong   | 104M    | 26.52  | 24.42  | 24.97  | 25.27   |
| MiniMind2-Small                                                               | JingyaoGong   | 26M     | 26.37  | 24.97  | 25.39  | 24.63   |
| MiniMind2-MoE                                                                 | JingyaoGong   | 145M    | 26.6   | 25.01  | 24.83  | 25.01   |
| [Steel-LLM](https://github.com/zhanshijinwat/Steel-LLM)                       | ZhanShiJin    | 1121M   | 24.81  | 25.32  | 26     | 24.39   |
| [GPT2-medium](https://huggingface.co/openai-community/gpt2-medium)            | OpenAI        | 360M    | 23.18  | 25     | 18.6   | 25.19   |
| [TinyLlama-1.1B-Chat-V1.0](https://github.com/jzhang38/TinyLlama)             | TinyLlama     | 1100M   | 25.48  | 25     | 25.4   | 25.13   |
| [SmolLM2](https://github.com/huggingface/smollm)                              | HuggingFaceTB | 135M    | 24.37  | 25.02  | 25.37  | 25.06   |
| [Aquila-Instruct](https://www.modelscope.cn/models/BAAI/Aquila-135M-Instruct) | BAAI          | 135M    | 25.11  | 25.1   | 24.43  | 25.05   |

![compare_radar](./images/compare_radar.png)

# 📌 Others

### Inference and Export

* [./scripts/convert_model.py](./scripts/convert_model.py) can convert models between torch/transformers.

* MiniMind's HuggingFace collection link:
  [MiniMind](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5)

---

### Based on MiniMind-API Service Interface

* [./scripts/serve_openai_api.py](./scripts/serve_openai_api.py) provides the simplest chat interface compatible with
  the OpenAI API,
  making it easy to integrate your model into third-party UIs such as FastGPT, OpenWebUI, Dify, etc.

* Download the model weights
  from [Huggingface](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5). The file
  structure is:
    ```
    <MiniMind-Model-Name> (root dir)
    ├─<MiniMind-Model-Name>
    |  ├── config.json
    |  ├── generation_config.json
    |  ├── LMConfig.py
    |  ├── model.py
    |  ├── pytorch_model.bin
    |  ├── special_tokens_map.json
    |  ├── tokenizer_config.json
    |  ├── tokenizer.json
    ```

* Start the chat server:
    ```bash
    python serve_openai_api.py
    ```
* Test the service interface:
    ```bash
    python chat_openai_api.py
    ```
* API example, compatible with OpenAI API format:
    ```bash
    curl http://ip:port/v1/chat/completions \
      -H "Content-Type: application/json" \
      -d '{ 
        "model": "model-identifier",
        "messages": [ 
          { "role": "user", "content": "What is the highest mountain in the world?" }
        ], 
        "temperature": 0.7, 
        "max_tokens": 512,
        "stream": true
    }'
    ```

# 📌 Acknowledge

> [!NOTE]
> If you find the `MiniMind series` helpful, feel free to give it a ⭐ on GitHub.<br/>
> Due to the length of the content, mistakes are inevitable; please feel free to report issues or submit a PR to improve
> the project.<br/>
> Your small support is the driving force for continuous improvement of this project!

## 🤝[Contributors](https://github.com/jingyaogong/minimind/graphs/contributors)

<!--
<a href="https://github.com/jingyaogong/minimind/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=jingyaogong/minimind&v3" />
</a>
-->

<a href="https://github.com/jingyaogong"><img src="https://avatars.githubusercontent.com/u/62287848" width="70px" height="70px"/></a>
&nbsp;
<a href="https://github.com/MuWinds"><img src="https://avatars.githubusercontent.com/u/93832089" width="70px" height="70px"/></a>
&nbsp;
<a href="https://github.com/chuanzhubin"><img src="https://avatars.githubusercontent.com/u/2813798" width="70px" height="70px"/></a>
&nbsp;
<a href="https://github.com/iomgaa-ycz"><img src="https://avatars.githubusercontent.com/u/124225682" width="70px" height="70px"/></a>
&nbsp;

## 😊Acknowledgments

<a href="https://github.com/ipfgao"><b>@ipfgao</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/26">🔗Training steps record</a>

<a href="https://github.com/chuanzhubin"><b>@chuanzhubin</b></a>:
<a href="https://github.com/jingyaogong/minimind/pull/34">🔗Line-by-line code comments</a>

<a href="https://github.com/WangRongsheng"><b>@WangRongsheng</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/39">🔗Large dataset preprocessing</a>

<a href="https://github.com/pengqianhan"><b>@pengqianhan</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/73">🔗A brief tutorial</a>

<a href="https://github.com/RyanSunn"><b>@RyanSunn</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/75">🔗Inference process learning record</a>

<details close> 
<summary> <b>Reference Links & Thanks to the following excellent papers or projects</b> </summary>

- No specific order of ranking
- [https://github.com/meta-llama/llama3](https://github.com/meta-llama/llama3)
- [https://github.com/karpathy/llama2.c](https://github.com/karpathy/llama2.c)
- [https://github.com/DLLXW/baby-llama2-chinese](https://github.com/DLLXW/baby-llama2-chinese)
- [(DeepSeek-V2)https://arxiv.org/abs/2405.04434](https://arxiv.org/abs/2405.04434)
- [https://github.com/charent/ChatLM-mini-Chinese](https://github.com/charent/ChatLM-mini-Chinese)
- [https://github.com/wdndev/tiny-llm-zh](https://github.com/wdndev/tiny-llm-zh)
- [(Mistral-MoE)https://arxiv.org/pdf/2401.04088](https://arxiv.org/pdf/2401.04088)
- [https://github.com/Tongjilibo/build_MiniLLM_from_scratch](https://github.com/Tongjilibo/build_MiniLLM_from_scratch)
- [https://github.com/jzhang38/TinyLlama](https://github.com/jzhang38/TinyLlama)
- [https://github.com/AI-Study-Han/Zero-Chatgpt](https://github.com/AI-Study-Han/Zero-Chatgpt)
- [https://github.com/xusenlinzy/api-for-open-llm](https://github.com/xusenlinzy/api-for-open-llm)
- [https://github.com/HqWu-HITCS/Awesome-Chinese-LLM](https://github.com/HqWu-HITCS/Awesome-Chinese-LLM)

</details>

## 🫶Supporters

<a href="https://github.com/jingyaogong/minimind/stargazers">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://reporoster.com/stars/dark/jingyaogong/minimind"/>
      <source media="(prefers-color-scheme: light)" srcset="https://reporoster.com/stars/jingyaogong/minimind"/>
      <img alt="github contribution grid snake animation" src="https://reporoster.com/stars/jingyaogong/minimind"/>
    </picture>
</a>

<a href="https://github.com/jingyaogong/minimind/network/members">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://reporoster.com/forks/dark/jingyaogong/minimind"/>
      <source media="(prefers-color-scheme: light)" srcset="https://reporoster.com/forks/jingyaogong/minimind"/>
      <img alt="github contribution grid snake animation" src="https://reporoster.com/forks/jingyaogong/minimind"/>
    </picture>
</a>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=jingyaogong/minimind&type=Date&theme=dark"/>
  <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=jingyaogong/minimind&type=Date"/>
  <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=jingyaogong/minimind&type=Date"/>
</picture>

# License

This repository is licensed under the [Apache-2.0 License](LICENSE).

