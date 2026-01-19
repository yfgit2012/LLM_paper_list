The provided document details the architecture, hyperparameters, and performance benchmarks of the **DeepSeek-Engram** model series, which includes variants like **Dense-4B**, **MoE-27B**, **Engram-27B**, and **Engram-40B**. Below is a structured summary of the key components and insights:

---

### **1. Model Architecture Overview**
#### **Key Variants**
- **Dense-4B**: A dense model with 4.1B parameters.
- **MoE-27B**: A Mixture-of-Experts (MoE) model with 26.7B parameters.
- **Engram-27B/40B**: Engram-based models with 26.7B and 39.5B parameters, respectively.

#### **Core Components**
- **Layers**: 30 layers.
- **Dimension**: 2560-dimensional embeddings.
- **Attention Mechanism**: MLA (Multi-Head Attention) from DeepSeek-AI.
- **RoPE (Rotary Position Embedding)**: θ = 10000.
- **Sequence Length**: 4096 tokens.
- **Vocabulary Size**: 129,280.
- **Batch Size**: 1280.
- **Training Steps**: 50,000.

#### **Engram-Specific Features**
- **Engram Dim (mem)**: 1280 for Engram-27B and 1280 for Engram-40B.
- **Engram Vocab Size**: 2,262,400 (Engram-27B) and 7,239,680 (Engram-40B).
- **Engram Heads**: 8 attention heads.
- **Engram Layers**: [2,15] for both variants.
- **Engram n-grams**: [2,3] for n-gram tokenization.
- **Tokenizer Compression**: Enabled for both variants, reducing vocabulary size by **23.43%** (Table 6).

---

### **2. Hyperparameters**
- **Optimizer**: 
  - **Backbone**: Muon (Jordan et al., 2024).
  - **Embedding**: Adam (Kingma, 2014).
- **Learning Rate**: Base = 4e-4, scheduled with **Step Decay**.
- **Weight Decay**: 0.1 (for backbone), 0.0 (for Engram).
- **Load Balancing**: **Loss-Free** method (Wang et al., 2024a).

---

### **3. Benchmark Performance**
- **Pile-test**: Scores of 96–98–00 (likely accuracy percentages across tasks).
- **MMLU MoE-27B**: Scores of 56–58–60.
- **MMLU-PRO**: Scores of 55–70–85–00.
- **CMMLU**: Scores of 75–00 (likely varying difficulty levels).
- **CEval**: Scores of 00–25–50–75.
- **ARC-Easy/Challenge**: Scores of 70–85/40–55.
- **CCPM**: Scores of 84–87/81–78.
- **BBH**: Scores of 54–48–51.
- **C3**: Scores of 81–78–78.
- **Cruxeval-o/i**: Scores of 44–28–36–30–2.
- **GSM8K/MATH**: Scores of 26–28–30.

**Note**: The benchmark curves (images) show performance trends across pre-training steps, with the last 10k steps visualized in Figure 8.

---

### **4. Tokenizer Compression Case Study**
- **Compression Ratio**: 23.43% reduction in vocabulary size for the 128k tokenizer.
- **Merged Tokens** (Top 5):
  1. **Whitespace/Control Characters** (e.g., `'␣'`, `'\t'`, `'\n'`).
  2. **Lowercase 'a'** (merged with uppercase and variations).
  3. **Lowercase 'o'** (merged with uppercase and accents).
  4. **Lowercase 'e'** (merged with uppercase and diacritics).
  5. **Lowercase 'i'** (merged with uppercase and accents).

This compression likely improves efficiency without sacrificing performance, as seen in the benchmark results.

---

### **5. Key Technical Insights**
- **MoE Efficiency**: The MoE-27B model uses **72 experts** with **6 active experts**, balancing computational load and performance.
- **Engram Design**: The Engram variants leverage **n-gram tokenization** and **shared experts** to handle diverse tasks, with specialized parameters for embedding optimization.
- **Tokenizer Optimization**: Compression reduces vocabulary size, enabling faster inference and lower memory usage while maintaining accuracy.

---

### **6. Implications**
- **Scalability**: The Engram-40B model (39.5B params) demonstrates the scalability of the architecture for large-scale tasks.
- **Efficiency**: Tokenizer compression and loss-free load balancing suggest a focus on **resource efficiency** without compromising performance.
- **Benchmark Leadership**: High scores on tasks like MMLU-PRO, GSM8K, and MATH indicate strong reasoning and generalization capabilities.

---

This document provides a comprehensive view of the DeepSeek-Engram series, emphasizing its architectural innovations, efficiency strategies, and performance across diverse benchmarks. For further analysis, the benchmark curves (images) and detailed hyperparameter tuning would be critical.
===============
<document>以下是**DeepSeek-Engram**模型系列的架构、超参数和性能基准的详细说明，该系列包括**Dense-4B**、**MoE-27B**、**Engram-27B**和**Engram-40B**等变体。以下是关键组件和洞察的结构化摘要：

---

### **1. 模型架构概述**
#### **关键变体**
- **Dense-4B**：一个具有41亿参数的密集模型。
- **MoE-27B**：一个具有267亿参数的专家混合（MoE）模型。
- **Engram-27B/40B**：分别具有267亿和395亿参数的Engram基础模型。

#### **核心组件**
- **层数**：30层。
- **维度**：2560维嵌入。
- **注意力机制**：来自DeepSeek-AI的多头注意力（MLA）。
- **RoPE（旋转位置嵌入）**：θ = 10000。
- **序列长度**：4096个标记。
- **词汇量**：129,280。
- **批量大小**：1280。
- **训练步数**：50,000步。

#### **Engram特定功能**
- **Engram Dim（mem）**：Engram-27B和Engram-40B均为1280。
- **Engram词汇量**：Engram-27B为2,262,400，Engram-40B为7,239,680。
- **Engram头数**：8个注意力头。
- **Engram层数**：[2,15]（两个变体均相同）。
- **Engram n-gram**：[2,3]（n-gram分词）。
- **分词器压缩**：两个变体均启用，词汇量缩减**23.43%**（表6）。

---

### **2. 超参数**
- **优化器**：
  - **主干**：Muon（Jordan等，2024）。
  - **嵌入**：Adam（Kingma，2014）。
- **学习率**：基础值为4e-4，采用**步长衰减**调度。
- **权重衰减**：主干为0.1，Engram为0.0。
- **负载均衡**：**无损失**方法（Wang等，2024a）。

---

### **3. 基准性能**
- **Pile-test**：得分96–98–00（可能为任务准确率百分比）。
- **MMLU MoE-27B**：得分56–58–60。
- **MMLU-PRO**：得分55–70–85–00。
- **CMMLU**：得分75–00（可能为不同难度等级）。
- **CEval**：得分00–25–50–75。
- **ARC-Easy/Challenge**：得分70–85/40–55。
- **CCPM**：得分84–87/81–78。
- **BBH**：得分54–48–51。
- **C3**：得分81–78–78。
- **Cruxeval-o/i**：得分44–28–36–30–2。
- **GSM8K/MATH**：得分26–28–30。

**注**：基准曲线（图像）显示了预训练步数的性能趋势，最后10,000步可视化于图8中。

---

### **4. 分词器压缩案例研究**
- **压缩率**：128k分词器的词汇量缩减**23.43%**。
- **合并的标记**（前5名）：
  1. **空格/控制字符**（例如 `'␣'`、`'\t'`、`'\n'`）。
  2. **小写 'a'**（与大写及变体合并）。
  3. **小写 'o'**（与大写及变体合并）。
  4. **小写 'e'**（与大写及变体合并）。
  5. **小写 'i'**（与大写及变体合并）。

此压缩可能在不牺牲性能的情况下提高效率，如基准结果所示。

---

### **5. 关键技术洞察**
- **MoE效率**：MoE-27B模型使用**72个专家**，其中**6个活跃专家**，平衡计算负载和性能。
- **Engram设计**：Engram变体利用**n-gram分词**和**共享专家**处理多样化任务，并针对嵌入优化进行专门参数调整。
- **分词器优化**：压缩减少了词汇量，实现更快推理和更低内存使用，同时保持准确性。

---

### **6. 启示**
- **可扩展性**：Engram-40B模型（395亿参数）展示了该架构在大规模任务中的可扩展性。
- **效率**：分词器压缩和无损失负载均衡表明对**资源效率**的重视，而不过度牺牲性能。
- **基准领先**：在MMLU-PRO、GSM8K和MATH等任务中的高分表明其强大的推理和泛化能力。

---

本文档全面概述了DeepSeek-Engram系列，强调其架构创新、效率策略以及在多样化基准中的表现。进一步分析需结合基准曲线（图像）和详细超参数调优。</document>

#### Reference: 

Source file: deepseek_engram.pdf