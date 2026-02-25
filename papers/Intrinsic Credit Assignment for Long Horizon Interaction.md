The document outlines a comprehensive approach to training a model for the 20 Questions game, emphasizing data curation, training strategies, and hyperparameter optimization. Here's a structured breakdown of its key components and insights:

---

### **1. Data Curation for 20Qs**
- **Secret Words Selection**:  
  - Words are sourced from Google’s Trillion Word Corpus, filtered to select the 10,000 most common nouns.  
  - A Grok 3 m LLM (as a judge) further filters words to ensure they are solvable in the game.  
  - **Validation**: 32 iterations of 20 Questions with Gemini 2.0 Flash are conducted to discard words that cannot be solved, resulting in **4,678 valid words**.  
  - **Splitting**: Dataset is divided into:  
    - **Validation**: 238 words  
    - **Test**: 487 words  
    - **Training**: 3,953 words (341 for SFT, 3,612 for RL).  
    - **Final Training Set**: 1,000 words (neither too hard nor too easy) for RL experiments.

---

### **2. SFT (Supervised Fine-Tuning) Settings**
- **Training Data**:  
  - 341 words are used, with **Gemini 2.0 Flash**'s successful game sequences (lowest turns) selected as training examples.  
  - **Total Sequences**: 562 (including ties in turn counts).  
- **Training Method**:  
  - Trajectories are split into individual turns, with **context masking** (prompts, chat tokens, previous questions, judge responses) to focus only on the final question.  
  - **Single-Turn Training**: Outperforms multi-turn training due to hybrid chat templates and reduced off-policy gaps.  
  - **Hyperparameters**:  
    - 2 epochs with cosine decay, max learning rate 1e-5, 10% warm-up.  
    - ADAMW optimizer (weight decay 0.01, β₁=0.9, β₂=0.95).  
    - Global batch size: 256, max tokens per sequence: 650.

---

### **3. GRPO (Group Relative Policy Optimization) Settings**
- **Adaptations for Multi-Turn RL**:  
  - **Token Masking**: Masks environment-generated tokens to train only on the agent's outputs.  
  - **KL Divergence Omission**: Excluded KL penalty as it didn’t improve performance.  
  - **Asymmetric Clipping**: Uses a range of [0.2, 0.28] for policy updates to balance stability and exploration.  
  - **Per-Turn Advantage Estimation**: Calculates advantages per turn to reduce variance and improve credit assignment for specific actions.

---

### **4. Ablation Studies (StarPO Baselines)**
- **Key Findings**:  
  - **Aggregation Method**: `seq-mean-token-mean` outperformed `token-mean` in both 1.7B and 4B models.  
  - **Learning Rate**: Higher learning rates (3e-5) yielded better results than 1e-5, especially for the 4B model.  
  - **Results**:  
    - **STARPO-1.7B**: Best accuracy 15.85% (3e-5 LR).  
    - **STARPO-4B**: Best accuracy 24.36% (3e-5 LR).  
  - **Implications**: Aggregation strategy and learning rate tuning are critical for optimizing model performance.

---

### **5. Practical Implications**
- **Curriculum Learning**: Iteratively incorporating edge-case secrets (words at the agent’s capacity limit) could further improve performance.  
- **Efficiency**: The final training set (1,000 words) balances difficulty, ensuring models are neither too easy nor too hard to train.  
- **Scalability**: The approach is adaptable to other multi-turn tasks, leveraging GRPO and SFT for robust policy optimization.

---

### **Summary**
This document details a meticulous pipeline for training a model to master the 20 Questions game. By combining rigorous data curation, tailored SFT strategies, and GRPO adaptations, the authors achieve efficient and effective training. The ablation studies highlight the importance of hyperparameter tuning and aggregation methods, offering actionable insights for similar reinforcement learning tasks.

===============

## 中文翻译

### **1. 20Qs 数据整理**
- **秘密词语选择**：  
  - 词语来源于 Google 的万亿词语料库，筛选出 10,000 个最常见的名词。  
  - 通过 Grok 3 m 大语言模型（作为裁判）进一步筛选，确保词语能够在游戏中被解答。  
  - **验证**：进行 32 轮 20 个问题游戏，使用 Gemini 2.0 Flash 排除无法解答的词语，最终得到 **4,678 个有效词语**。  
  - **数据集划分**：  
    - **验证集**：238 个词语  
    - **测试集**：487 个词语  
    - **训练集**：3,953 个词语（其中 341 个用于监督微调，3,612 个用于强化学习）。  
    - **最终训练集**：1,000 个词语（难度适中，既不难也不易）用于强化学习实验。

---

### **2. 监督微调（SFT）设置**
- **训练数据**：  
  - 使用 341 个词语，选取 Gemini 2.0 Flash 的成功游戏序列（最少回合数）作为训练示例。  
  - **总序列数**：562（包括回合数相同的情况）。  
- **训练方法**：  
  - 将轨迹拆分为单个回合，通过 **上下文掩码**（提示、聊天标记、之前的问题、裁判回答）仅关注最终问题。  
  - **单回合训练**：由于混合聊天模板和减少离策略偏差，表现优于多回合训练。  
  - **超参数**：  
    - 2 轮训练，余弦衰减，最大学习率 1e-5，10% 预热。  
    - ADAMW 优化器（权重衰减 0.01，β₁=0.9，β₂=0.95）。  
    - 全局批大小：256，每序列最大标记数：650。

---

### **3. GRPO（群体相对策略优化）设置**
- **多回合强化学习的适应**：  
  - **标记掩码**：掩码环境生成的标记，仅训练代理的输出。  
  - **KL 散度省略**：排除 KL 惩罚，因其未提升性能。  
  - **非对称裁剪**：使用 [0.2, 0.28] 范围进行策略更新，平衡稳定性与探索。  
  - **每回合优势估计**：计算每回合的优势，以减少方差并改进特定动作的归因。

---

### **4. 消融研究（StarPO 基线）**
- **关键发现**：  
  - **聚合方法**：`seq-mean-token-mean` 在 1.7B 和 4B 模型中均优于 `token-mean`。  
  - **学习率**：较高学习率（3e-5）比 1e-5 表现更好，尤其是对 4B 模型。  
  - **结果**：  
    - **STARPO-1.7B**：最佳准确率 15.85%（3e-5 学习率）。  
    - **STARPO-4B**：最佳准确率 24.36%（3e-5 学习率）。  
  - **启示**：聚合策略和学习率调优对优化模型性能至关重要。

---

### **5. 实践启示**
- **课程学习**：逐步引入边缘案例秘密（代理能力极限的词语）可能进一步提升性能。  
- **效率**：最终训练集（1,000 个词语）平衡了难度，确保模型既不难也不易训练。  
- **可扩展性**：该方法可适应其他多回合任务，利用 GRPO 和 SFT 实现稳健的策略优化。

---

### **总结**
本文详细介绍了训练模型掌握 20 个问题游戏的精密流程。通过结合严谨的数据整理、定制化的 SFT 策略和 GRPO 适应，作者实现了高效且有效的训练。消融研究突显了超参数调优和聚合方法的重要性，为类似强化学习任务提供了可操作的见解。

#### Reference: 

Source file: Intrinsic Credit Assignment for Long Horizon Interaction.pdf

---

**Title**: Intrinsic Credit Assignment for Long Horizon Interaction

**Authors & Affiliations**: - [bethgelab.github.io/delta-belief-rl](https://bethgelab.github.io/delta-belief-rl/) - [delta-belief-rl](https://github.com/bethgelab/delta-belief-rl/)
