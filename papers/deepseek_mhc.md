The provided document outlines the **architectural specifications and hyperparameters** for three variants of a large language model (LLM) based on the **DeepSeek-V3 architecture** (Liu et al., 2024b). Below is a structured summary of the key details:

---

### **Model Specifications**
| **Attribute**                | **3B**       | **9B**        | **27B**       |
|-----------------------------|--------------|---------------|---------------|
| **Vocab Params**            | 331M         | 496M          | 662M          |
| **Active Params**           | 612M         | 1.66B         | 4.14B         |
| **Total Params**            | 2.97B        | 9.18B         | 27.0B         |
| **Layers**                  | 12           | 18            | 30            |
| **Leading Dense Layers**    | 1            | 1             | 1             |
| **Routed Experts**          | 64           | 64            | 72            |
| **Active Experts**          | 6            | 6             | 6             |
| **Shared Experts**          | 6            | 6             | 6             |
| **Dimension**               | 1280         | 1920          | 2560          |
| **FFN Dimension**           | 896          | 1280          | 1536          |
| **Attention Heads**        | 16           | 24            | 32            |
| **Attention Dimension**     | 128          | 128           | 128           |
| **KV Rank**                 | 512          | 512           | 512           |
| **Position Embedding**     | RoPE (64, 10000) | RoPE (64, 10000) | RoPE (64, 10000) |
| **Sequence Length**         | 4096         | 4096          | 4096          |
| **Batch Size**              | 320          | 512           | 1280          |
| **Training Steps**          | 30,000       | 50,000        | 100,000       |
| **Training Tokens**         | 39.3B        | 105B          | 262B          |
| **Base Learning Rate**      | 8.6e-4       | 5.9e-4        | 4.0e-4        |

---

### **Key Observations**
1. **Model Scaling**:
   - The 3B, 9B, and 27B models scale linearly in parameters, layers, and training tokens, but the **27B model** has a higher dimension (2560) and more layers (30) compared to the smaller variants.
   - **Inconsistency**: The 3B and 27B models share the same **Vocab Params** (331M vs. 662M), which may indicate a typo or misunderstanding in terminology (e.g., "Vocab Params" might refer to embedding parameters, not vocabulary size).

2. **Hyperparameters**:
   - **Loss-Free Load Balancing**: The models use a loss-free approach for distributed training, likely to optimize resource allocation.
   - **Attention Mechanism**: All models use **RoPE (Rotary Position Embedding)** with a fixed dimension (64) and rotation factor (10000).
   - **Optimization**: AdamW optimizer with **beta parameters (0.9, 0.95)** and **epsilon (1e-20)** for numerical stability.

3. **Training Configuration**:
   - Larger models (9B/27B) have **higher training tokens** (105B/262B) and **larger batch sizes** (512/1280) to leverage distributed computing.
   - The **27B model** has the longest training steps (100,000) and the lowest base learning rate (4.0e-4), suggesting careful fine-tuning for convergence.

4. **Potential Issues**:
   - The **Batch Size** for the 27B model is listed as **1280**, but the last entry under "Batch Size" appears to be **2560**, which may be a formatting error.
   - The **Base Learning Rate** for the 27B model is **4.0e-4**, while the last entry shows **9.0e-4**, which could be a typo.

---

### **Summary**
This document provides a detailed breakdown of the **DeepSeek-V3 architecture** for three model sizes, emphasizing scalability in parameters, layers, and training data. The hyperparameters (e.g., AdamW, RoPE, loss-free balancing) are tuned for efficiency and performance, with the largest model (27B) requiring the most computational resources. Minor inconsistencies in the table (e.g., Vocab Params, Batch Size) may require clarification but do not detract from the overall technical insights.
===============
<document>该文档概述了基于**DeepSeek-V3架构**（Liu等，2024b）的三种大型语言模型（LLM）的**架构规格和超参数**。以下是关键细节的结构化总结：

---

### **模型规格**
| **属性**                | **3B**       | **9B**        | **27B**       |
|-----------------------------|--------------|---------------|---------------|
| **词汇参数**            | 331M         | 496M          | 662M          |
| **活跃参数**           | 612M         | 1.66B         | 4.14B         |
| **总参数**            | 2.97B        | 9.18B         | 27.0B         |
| **层数**                  | 12           | 18            | 30            |
| **主密集层**    | 1            | 1             | 1             |
| **路由专家**          | 64           | 64            | 72            |
| **活跃专家**          | 6            | 6             | 6             |
| **共享专家**          | 6            | 6             | 6             |
| **维度**               | 1280         | 1920          | 2560          |
| **FFN维度**           | 896          | 1280          | 1536          |
| **注意力头数**        | 16           | 24            | 32            |
| **注意力维度**     | 128          | 128           | 128           |
| **KV秩**                 | 512          | 512           | 512           |
| **位置嵌入**     | RoPE (64, 10000) | RoPE (64, 10000) | RoPE (64, 10000) |
| **序列长度**         | 4096         | 4096          | 4096          |
| **批量大小**              | 320          | 512           | 1280          |
| **训练步骤**          | 30,000       | 50,000        | 100,000       |
| **训练令牌**         | 39.3B        | 105B          | 262B          |
| **基础学习率**      | 8.6e-4       | 5.9e-4        | 4.0e-4        |

---

### **关键观察**
1. **模型扩展**：
   - 3B、9B和27B模型在参数、层数和训练令牌上呈线性扩展，但**27B模型**的维度（2560）和层数（30）均高于较小版本。
   - **不一致**：3B和27B模型的**词汇参数**（331M vs. 662M）相同，可能表明术语理解错误（例如，“词汇参数”可能指嵌入参数而非词汇量）。

2. **超参数**：
   - **无损失负载均衡**：模型使用无损失方法进行分布式训练，以优化资源分配。
   - **注意力机制**：所有模型均采用**RoPE（旋转位置嵌入）**，固定维度（64）和旋转因子（10000）。
   - **优化**：使用**AdamW优化器**，参数（0.9, 0.95）和**epsilon（1e-20）**以确保数值稳定性。

3. **训练配置**：
   - 较大模型（9B/27B）具有更高的**训练令牌**（105B/262B）和更大的**批量大小**（512/1280），以利用分布式计算。
   - **27B模型**的训练步骤最长（100,000）且基础学习率最低（4.0e-4），表明需精细调优以实现收敛。

4. **潜在问题**：
   - **27B模型的批量大小**列为**1280**，但“批量大小”最后一行显示为**2560**，可能是格式错误。
   - **27B模型的基础学习率**为**4.0e-4**，而最后一行显示为**9.0e-4**，可能是拼写错误。

---

### **总结**
该文档详细介绍了**DeepSeek-V3架构**三种模型规模的规格，强调参数、层数和训练数据的扩展性。超参数（如AdamW、RoPE、无损失负载均衡）经过调优以实现效率和性能，其中最大模型（27B）需最多计算资源。表格中的小错误（如词汇参数、批量大小）可能需澄清，但不影响整体技术洞察。</document>

#### Reference: 

Source file: deepseek_mhc.pdf