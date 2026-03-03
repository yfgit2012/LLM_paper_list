## Summary
- **Objective**: To address the limitations of existing Image-to-Video (I2V) benchmarks by introducing AIGCBench, a comprehensive and scalable benchmark that provides diverse datasets, unified evaluation metrics, and human-aligned standards to advance I2V research.  
- **Methodologies**:  
  - **Dataset Construction**: Combines open-domain video-text pairs (from WebVid-10M) and image-text pairs generated via GPT-4 and text combiners, processed by Stable Diffusion.  
  - **Evaluation Metrics**: Four dimensions (control-video alignment, motion effects, temporal consistency, video quality) with 11 metrics (e.g., MSE, SSIM, CLIP scores, flow-square-mean, DOVER).  
  - **Human Validation**: Ensures metrics align with human preferences through user studies and prompt optimization via GPT-4.  
- **Results**:  
  - **Quantitative Analysis**: Gen2 excelled in image fidelity (0.939) and video quality (0.560); Pika outperformed in motion effects (flow-square-mean: 0.281) and temporal consistency (0.823); SVD showed strong motion dynamics but lower image fidelity (0.800).  
  - **User Study**: Gen2 and Pika ranked highest in image fidelity and video quality, while Pika led in motion effects and temporal consistency.  
  - **Findings**: Current I2V models lack fine-grained control, long video generation, and inference speed. AIGCBench highlights the need for multi-modal alignment and efficient diffusion models.  
- **Key Contributions**:  
  - Introduces AIGCBench, the first open-domain I2V benchmark with diverse datasets and multi-dimensional metrics.  
  - Proposes human-aligned evaluation standards and identifies critical gaps in existing models (e.g., control, length, speed).  
  - Provides a standardized framework for future benchmarks and research in AI-generated content (AIGC).  
- **Conclusions**: AIGCBench sets a foundation for standardized I2V evaluation, exposing algorithmic weaknesses and offering a unified platform for innovation. Future work includes expanding to T2V/V2V tasks, improving inference speed, and developing fine-grained video-text alignment models.  

## Title and Authors  
**Title**: AIGCBench: A Comprehensive Benchmark for Image-to-Video Generation  
**Authors**: [Authors' Names]  
**Affiliations**: [Affiliations]

===============

## 中文翻译

## 摘要
- **目标**：通过引入AIGCBench，一个全面且可扩展的基准测试，解决现有图像到视频（I2V）基准测试的局限性，提供多样化的数据集、统一的评估指标和与人类偏好对齐的标准，以推动I2V研究。  
- **方法**：  
  - **数据集构建**：结合开放领域视频-文本对（来自WebVid-10M）和通过GPT-4及文本组合器生成的图像-文本对，并经Stable Diffusion处理。  
  - **评估指标**：四个维度（控制-视频对齐、运动效果、时间一致性、视频质量）与11项指标（如MSE、SSIM、CLIP分数、流平方均值、DOVER）。  
  - **人类验证**：通过用户研究和GPT-4提示优化确保指标与人类偏好一致。  
- **结果**：  
  - **定量分析**：Gen2在图像保真度（0.939）和视频质量（0.560）方面表现优异；Pika在运动效果（流平方均值：0.281）和时间一致性（0.823）方面表现更佳；SVD展现出强大的运动动态性，但图像保真度较低（0.800）。  
  - **用户研究**：Gen2和Pika在图像保真度和视频质量方面排名最高，而Pika在运动效果和时间一致性方面领先。  
  - **发现**：当前I2V模型缺乏细粒度控制、长视频生成和推理速度。AIGCBench突显了多模态对齐和高效扩散模型的必要性。  
- **关键贡献**：  
  - 引入AIGCBench，首个涵盖多样化数据集和多维指标的开放领域I2V基准测试。  
  - 提出与人类偏好对齐的评估标准，并识别现有模型的关键不足（如控制、长度、速度）。  
  - 为未来AI生成内容（AIGC）基准测试和研究提供标准化框架。  
- **结论**：AIGCBench为标准化I2V评估奠定了基础，揭示了算法弱点，并提供了创新的统一平台。未来工作包括扩展至文本到视频（T2V）/视频到视频（V2V）任务、提升推理速度以及开发细粒度视频-文本对齐模型。  

## 标题与作者  
**标题**：AIGCBench：图像到视频生成的全面基准  
**作者**：[作者姓名]  
**所属机构**：[所属机构]

#### Reference: 

Source file: aigcbench.pdf

---

**Title**: BenchCouncil Transactions on Benchmarks, Standards and Evaluations

**Authors & Affiliations**: Contents lists available at ScienceDirect
