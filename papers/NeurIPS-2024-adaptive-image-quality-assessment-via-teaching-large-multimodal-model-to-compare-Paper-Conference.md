## Summary
- **Objective**: The paper aims to address the challenge of translating relative quality comparisons (e.g., "better than," "similar to") into continuous perceptual quality scores for no-reference image quality assessment (NR-IQA), enabling robust generalization across diverse datasets and distortions.  
- **Methodologies**: The authors propose **Compare2Score**, an LMM-based NR-IQA model that leverages **relative ranking** (paired comparisons) instead of absolute ratings. Key methods include: (1) generating comparative instructions from MOS scores, (2) a multi-image LMM structure with mPLUG-Owl2, (3) **soft comparison** via probability matrices for inference, and (4) **anchor image selection** for robustness.  
- **Results**: Compare2Score outperforms state-of-the-art models (e.g., Q-Align, UNIQUE, LIQE) on six standard datasets (LIVE, CSIQ, KADID-10k, BID, CLIVE, KonIQ-10k) with median SRCC/PLCC scores of **0.972–0.974**/**0.969–0.969**. It achieves strong cross-dataset generalization (SRCC: 0.914–0.939) and surpasses open-source LMMs in prediction accuracy (0.849–0.858). The **probability matrix** significantly outperforms count matrices (e.g., 0.974 vs. 0.354 on LIVE).  
- **Key Contributions**: (1) A novel training dataset with comparative instructions, (2) a **soft comparison mechanism** for translating relative rankings into continuous scores, (3) joint training across datasets for robust generalization, and (4) a framework bridging relative comparisons to continuous quality assessments.  
- **Conclusions**: Compare2Score effectively bridges relative comparisons to continuous scores, achieving superior performance in both synthetic and real-world scenarios. Future work includes reducing computational complexity, improving interpretability, and expanding its impact on AI trustworthiness in critical applications.  

## Title and Authors (Required)  
**Title**: *Compare2Score: Bridging Relative Comparisons to Continuous Quality Scores for No-Reference Image Quality Assessment*  
**Authors**: Not provided in the extracted text.  
**Affiliations**: Not provided in the extracted text.

===============

## 中文翻译

## 摘要  
- **目标**：本文旨在解决将相对质量比较（例如“优于”、“类似”）转化为连续感知质量评分的挑战，以实现无参考图像质量评估（NR-IQA）在多样化数据集和失真类型上的鲁棒泛化。  
- **方法**：作者提出**Compare2Score**，一种基于LMM的NR-IQA模型，利用**相对排名**（配对比较）而非绝对评分。关键方法包括：(1) 从MOS评分生成比较指令，(2) 基于mPLUG-Owl2的多图像LMM结构，(3) 通过概率矩阵实现**软比较**进行推理，(4) **锚图像选择**以提升鲁棒性。  
- **结果**：Compare2Score在六个标准数据集（LIVE、CSIQ、KADID-10k、BID、CLIVE、KonIQ-10k）上优于现有先进模型（如Q-Align、UNIQUE、LIQE），中位SRCC/PLCC得分为**0.972–0.974**/**0.969–0.969**。其在跨数据集泛化方面表现优异（SRCC: 0.914–0.939），且预测精度超越开源LMM（0.849–0.858）。**概率矩阵**显著优于计数矩阵（例如在LIVE数据集上为0.974 vs. 0.354）。  
- **关键贡献**：(1) 具有比较指令的新颖训练数据集，(2) **软比较机制**将相对排名转化为连续评分，(3) 跨数据集联合训练以实现鲁棒泛化，(4) 连接相对比较与连续质量评估的框架。  
- **结论**：Compare2Score有效将相对比较转化为连续评分，在合成与现实场景中均表现出优越性能。未来工作包括降低计算复杂度、提升可解释性，并扩展其在关键应用中AI可信度的影响。  

## 标题与作者（必填）  
**标题**：*Compare2Score: 连接相对比较与连续质量评分的无参考图像质量评估*  
**作者**：提取文本中未提供。  
**所属机构**：提取文本中未提供。

#### Reference: 

Source file: NeurIPS-2024-adaptive-image-quality-assessment-via-teaching-large-multimodal-model-to-compare-Paper-Conference.pdf

---

**Title**: Adaptive Image Quality Assessment via Teaching Large Multimodal Model to Compare
