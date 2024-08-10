# llama-3.1-8b-chinese-instruct with SFT and DPO

## 项目简介

LLAMA-3.1系列模型于2024年7月24日发布，是Meta公司迄今为止规模最大、质量最高的开源模型。Meta评估了超150个基准数据集的性能，Llama-3.1系列模型在常识、可操作性、数学、工具使用和多语言翻译等一系列任务中，可与GPT-4o、Claude 3.5 Sonnet和Gemini Ultra相媲美。其中LLAMA-3.1-8B-Instruct模型，以其庞大的参数规模、强大的上下文理解能力和灵活的指令遵循能力，在全球范围内赢得了广泛的关注与赞誉。该模型在多种自然语言处理任务上展现出卓越的性能，包括但不限于文本生成、问答系统、文本摘要等，为人工智能领域的研究与应用提供了强大的技术支持。

然而，尽管LLAMA-3.1-8B-Instruct模型在多种语言环境下均表现出色，但在中文这一特定语境下，其性能却存在一定的局限性。为了弥补这一不足，本项目旨在通过针对中文语境的深入优化，提升LLAMA 3.1-8B-Instruct模型在中文处理上的能力。

本项目基于llama-3.1-8b-instruct模型，与当前相关工作不同的是，我们采用了指令微调（Instruction Fine-tuning）和直接偏好对齐（Direct Preference Optimization, DPO）二阶段的学习方法，使用近30w条中文数据进行有监督指令微调，然后应用5000条对齐指令进行直接偏好对齐，旨在进一步提升模型在中文语境下的理解和生成能力。在两个权威的中文评测基准下，C-Eval提升了83.34%的性能，CMMLU提升了83.95%的性能。我们公开了该项目所有的模型权重和训练数据集，欢迎大家一起学习和探讨。


#### 模型特点

基础模型：基于开源的llama3.1-8b-instruct，这是一个经过指令微调的大型语言基础模型。

指令微调：通过大量高质量中文数据集进行指令微调，提升模型在中文处理上的表现。

DPO对齐：采用直接偏好对齐技术，进一步优化模型在特定任务上的性能。

 

## 安装与加载

克隆本项目到本地：https://huggingface.co/jiangfb/llama-3.1-chinese-8b-it-dpo

git clone 

cd llama-3.1-chinese-8b-it-dpo

 

## 模型测评

#### Ceval

C-Eval 是一个全面的中文基础模型评估套件。它包含了大量的多项选择题，涵盖了人文、社科、理工以及其他专业四个大方向，包括52个不同的学科和四个难度级别。

| C-Eval | Average | Average(hard) | STEM | Social Sciences | Humanities | Other |
| ------ | ------- | ------------- | ---- | --------------- | ---------- | ----- |
| 原生LLaMA3.1模型 | 24.1    | 23.5          | 23.9 | 25.3            | 24.6       | 22.7  |
| 我们的LLaMA3.1模型 | 44.7    | 32.9          | 41.8 | 52.7            | 42.0       | 44.5  |

#### Cmmlu
CMMLU是一个综合性的中文评估基准，专门用于评估语言模型在中文语境下的知识和推理能力。CMMLU涵盖了从基础学科到高级专业水平的67个主题。它包括：需要计算和推理的自然科学，需要知识的人文科学和社会科学,以及需要生活常识的中国驾驶规则等。

| CMMLU  | Average | STEM  | Social Sciences | Humanities | Other |
| ------ | ------- | ----- | --------------- | ---------- | ----- |
| 原生LLaMA3.1模型 | 25.3    | 26.04 | 25.19           | 25.79      | 25.26 |
| 我们的LLaMA3.1模型 | 46.54   | 39.31 | 47.21           | 47.41      | 51.34 |

 

## 数据集

SFT数据集：

|                         |                                  |
| --------------------- | ------------------------------------------------------------ |
| 中文微调数据集        | https://modelscope.cn/datasets/zhuangxialie/Llama3-Chinese-Dataset/files |
| train_1M_CN           | https://huggingface.co/datasets/BelleGroup/train_1M_CN       |
| chinese_modern_poetry | https://huggingface.co/datasets/Iess/chinese_modern_poetry   |
| code                  | https://huggingface.co/datasets/iamtarun/python_code_instructions_18k_alpaca |
| mathglm               | https://cloud.tsinghua.edu.cn/d/8d9ee3e52bb54afd9c16/        |

DPO数据集：

|                   |                                                            |
| ----------------- | ---------------------------------------------------------- |
| DPO-En-Zh-20k     | https://huggingface.co/datasets/hiyouga/DPO-En-Zh-20k      |
| orca_dpo_pairs    | https://huggingface.co/datasets/Intel/orca_dpo_pairs       |
| Chinese-dpo-pairs | https://huggingface.co/datasets/wenbopan/Chinese-dpo-pairs |
| DPO-zh-en-emoji   | https://huggingface.co/datasets/shareAI/DPO-zh-en-emoji    |

## 贡献者
朱万运，2909574802@qq.com，湖南师范大学，在读研究生
江沸菠，jiangfb@hunnu.edu.cn，湖南师范大学，副教授
黄鸿洁，sherlor@163.com，湖南师范大学，在读研究生
涂思伟，tusiwei@hunnu.edu.cn，湖南师范大学，在读研究生

