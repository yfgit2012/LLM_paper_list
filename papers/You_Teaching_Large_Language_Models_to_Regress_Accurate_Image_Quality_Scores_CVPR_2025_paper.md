## Summary
- **Objective**: The paper aims to address the challenge of accurately scoring image quality using Multi-modal Large Language Models (MLLMs) by overcoming limitations in continuous quality scoring due to discrete token outputs and distribution gaps, introducing the DeQA-Score model.  
- **Methodologies**: The methodologies include soft label construction to discretize Gaussian-distributed scores into five levels (e.g., “bad,” “good,” “excellent”), a fidelity loss based on Thurstone’s model to handle dataset variations, and training the DeQA-Score model with next-token prediction and KL divergence losses to predict score distributions and adapt to dataset variations.  
- **Results**: DeQA-Score outperforms baselines in score regression (e.g., +1.3% PLCC on KonIQ, +4.6% on LIVE-Wild), achieves lower JS divergence and Wasserstein distance in score distribution prediction, and improves co-training performance across datasets (e.g., +33.1% SRCC on TID2013), aligning closely with human annotations.  
- **Key Contributions**: Introducing DeQA-Score with a distribution-based approach and soft labels to preserve inter-image relationships, a fidelity loss for intra-dataset relationships, and demonstrating superior performance in score regression and distribution prediction.  
- **Conclusions**: The paper concludes that DeQA-Score effectively improves image quality scoring via distribution-based methods, emphasizing the importance of quality score distributions in MLLM-based IQA, with future work focusing on AI-generated assessments and adaptability to diverse distortions.  

## Title and Authors  
**Title**: DeQA-Score: A Distribution-Based Multi-modal Large Language Model for Accurate Image Quality Scoring  
**Authors**: [Authors’ Names]  
**Affiliations**: [Affiliations of Authors]

===============

## 中文翻译

## 摘要
- **目标**：本文旨在通过克服连续质量评分中的离散token输出和分布差异限制，解决使用多模态大语言模型（MLLMs）准确评分图像质量的挑战，引入DeQA-Score模型。  
- **方法**：方法包括软标签构建，将高斯分布评分离散化为五个等级（如“差”、“好”、“优秀”），基于Thurstone模型的保真度损失以处理数据集差异，以及通过next-token预测和KL散度损失训练DeQA-Score模型，以预测评分分布并适应数据集差异。  
- **结果**：DeQA-Score在评分回归中优于基线模型（如KonIQ上提升+1.3% PLCC，LIVE-Wild上提升+4.6%），在评分分布预测中实现更低的JS散度和Wasserstein距离，并提升跨数据集的协同训练性能（如TID2013上提升+33.1% SRCC），与人类标注高度一致。  
- **关键贡献**：引入基于分布的DeQA-Score模型和软标签以保留图像间关系，基于数据集内关系的保真度损失，并在评分回归和分布预测中展示出卓越性能。  
- **结论**：本文结论认为，DeQA-Score通过基于分布的方法有效提升了图像质量评分，强调基于质量评分分布的重要性，未来工作将聚焦于AI生成的评估及对多样化失真类型的适应性。  

## 标题与作者  
**标题**：DeQA-Score：一种基于分布的多模态大语言模型用于精确图像质量评分  
**作者**：[作者姓名]  
**所属机构**：[作者所属机构]

#### Reference: 

Source file: You_Teaching_Large_Language_Models_to_Regress_Accurate_Image_Quality_Scores_CVPR_2025_paper.pdf

---

**Title**: Teaching Large Language Models to Regress Accurate Image Quality Scores Using Score Distribution

**Authors & Affiliations**: the final published version of the proceedings is available on IEEE Xplore. zhiyuanyou@link.cuhk.edu.hk, caixin@link.cuhk.edu.hk, jinjin.gu@sydney.edu.au tfxue@ie.cuhk.edu.hk, chao.dong@siat.ac.cn _†_ Corresponding Author
