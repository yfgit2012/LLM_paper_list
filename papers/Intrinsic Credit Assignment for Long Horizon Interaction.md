## Summary
- **Objective**: To develop an effective model for the 20 Questions game by focusing on data curation, supervised fine-tuning (SFT), reinforcement learning (RL) adaptations, and policy optimization techniques to ensure solvability and efficiency in multi-turn interactions.  
- **Methodologies**:  
  - **Data Curation**: Selected words from Google’s Trillion Word Corpus, filtered using LLMs (Grok 3 m, Gemini 2.0 Flash) for solvability, and split into training, validation, and test sets.  
  - **SFT**: Trained on 341 high-quality sequences with masked context, using ADAMW optimizer and cosine decay learning rates.  
  - **RL Adaptation**: Modified GRPO (Group Relative Policy Optimization) with token masking, asymmetric clipping, per-turn advantage estimation, and reward-based learning.  
  - **Ablation Studies**: Evaluated aggregation methods (e.g., seq-mean-token-mean) and learning rates (e.g., 3e-5) to optimize GRPO performance.  
- **Results**:  
  - Data curation with Gemini 2.0 Flash ensured high-quality, solvable words (4,678 total).  
  - Single-turn SFT with masked context improved performance compared to multi-turn training.  
  - GRPO enhancements (asymmetric clipping, per-turn advantage estimation) enhanced stability and performance.  
  - seq-mean-token-mean aggregation with 3e-5 learning rates achieved the best accuracy (24.36%) for Qwen3-1.7B and Qwen3-4B models.  
- **Key Contributions**:  
  - Novel data curation pipeline integrating LLM-based solvability checks.  
  - Modified GRPO for multi-turn RL with token masking and asymmetric clipping.  
  - Empirical insights on aggregation methods and hyperparameters for RL training.  
  - Framework balancing data quality, training efficiency, and policy optimization for interactive tasks.  
- **Conclusions**: The approach demonstrates a robust framework for training models in multi-turn environments, emphasizing the importance of data quality, context masking, and policy optimization. Future work could focus on iterative curriculum learning with edge-case secrets to further improve performance.  

## Title and Authors (Required)  
**Title**: A Comprehensive Approach to Training a Model for the 20 Questions Game  
**Authors**: Not specified in the provided text.  
**Affiliations**: Not specified in the provided text.

===============

## 中文翻译

## 摘要
- **目标**：通过聚焦数据整理、监督微调（SFT）、强化学习（RL）适应性及策略优化技术，开发一种高效的20个问题游戏模型，以确保多轮交互中的可解性和效率。  
- **方法**：  
  - **数据整理**：从谷歌的万亿词语料库中选取词语，利用大语言模型（Grok 3 m、Gemini 2.0 Flash）进行可解性筛选，并划分为训练集、验证集和测试集。  
  - **监督微调（SFT）**：基于341个高质量掩码上下文序列进行训练，采用ADAMW优化器和余弦衰减学习率。  
  - **强化学习适应性**：改进GRPO（组相对策略优化），引入令牌掩码、非对称裁剪、回合级优势估计和基于奖励的学习。  
  - **消融研究**：评估聚合方法（如seq-mean-token-mean）和学习率（如3e-5）以优化GRPO性能。  
- **结果**：  
  - 使用Gemini 2.0 Flash进行数据整理确保了高质量且可解的词语（共4,678个）。  
  - 掩码上下文的单轮SFT相较于多轮训练提升了性能。  
  - GRPO改进（非对称裁剪、回合级优势估计）增强了稳定性和性能。  
  - 采用seq-mean-token-mean聚合方法和3e-5学习率，在Qwen3-1.7B和Qwen3-4B模型中实现了最佳准确率（24.36%）。  
- **关键贡献**：  
  - 集成基于大语言模型可解性检查的新数据整理流程。  
  - 针对多轮强化学习改进GRPO，引入令牌掩码和非对称裁剪。  
  - 关于聚合方法和超参数的实证见解，用于强化学习训练。  
  - 平衡数据质量、训练效率和策略优化的框架，适用于交互任务。  
- **结论**：该方法展示了在多轮环境中训练模型的稳健框架，强调了数据质量、上下文掩码和策略优化的重要性。未来工作可聚焦于结合边缘案例秘密的迭代课程学习以进一步提升性能。  

## 标题与作者（必填）  
**标题**：一种用于20个问题游戏模型训练的综合方法  
**作者**：提供的文本中未指定。  
**所属机构**：提供的文本中未指定。

#### Reference: 

Source file: Intrinsic Credit Assignment for Long Horizon Interaction.pdf

---

**Title**: Intrinsic Credit Assignment for Long Horizon Interaction

**Authors & Affiliations**: - [bethgelab.github.io/delta-belief-rl](https://bethgelab.github.io/delta-belief-rl/) - [delta-belief-rl](https://github.com/bethgelab/delta-belief-rl/)
