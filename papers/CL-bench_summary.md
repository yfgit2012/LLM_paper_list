# CL-bench: A Benchmark for Context Learning

## Paper Information

- **Title**: CL-bench: A Benchmark for Context Learning
- **Authors**: Shihan Dou, Ming Zhang, Zhangyue Yin, Chenhao Huang, Yujiong Shen, Junzhe Wang, Jiayi Chen, Yuchen Ni, Junjie Ye, Cheng Zhang, Huaibing Xie, Jianglu Hu, Shaolei Wang, Weichao Wang, Yanling Xiao, Yiting Liu, Zenan Xu, Zhen Guo, Pluto Zhou, Tao Gui, Zuxuan Wu, Xipeng Qiu, Qi Zhang, Xuanjing Huang, Yu-Gang Jiang, Di Wang, Shunyu Yao
- **Institution**: Fudan University and other institutions
- **arXiv ID**: 2602.03587
- **Submission Date**: February 3, 2026
- **Subjects**: Computation and Language (cs.CL)
- **DOI**: https://doi.org/10.48550/arXiv.2602.03587
- **License**: CC BY 4.0
- **Length**: 78 pages, 17 figures

---

## Abstract

Current language models (LMs) excel at reasoning over prompts using pre-trained knowledge. However, real-world tasks are far more complex and context-dependent: models must learn from task-specific context and leverage new knowledge beyond what is learned during pre-training to reason and resolve tasks. We term this capability **context learning**, a crucial ability that humans naturally possess but has been largely overlooked.

**CL-bench** is introduced as a real-world benchmark consisting of:
- **500 complex contexts**
- **1,899 tasks**
- **31,607 verification rubrics**

All benchmark data was crafted by experienced domain experts. Each task is designed such that the new content required to resolve it is contained within the corresponding context.

---

## Introduction and Motivation

### The Problem with Current LMs

While language models have achieved remarkable success in various tasks, they primarily rely on:
1. **Pre-trained knowledge**: Information learned during the pre-training phase
2. **In-context learning (ICL)**: Learning simple task patterns via instructions and demonstrations

However, real-world applications require:
- **Context Learning (CL)**: The ability to learn from task-specific context and leverage new knowledge not present in pre-training
- **Domain-specific knowledge**: Rule systems, complex procedures, and laws derived from empirical data
- **Complex reasoning**: Going beyond simple retrieval or reading comprehension

### What Context Learning Is NOT

- **Long-context tasks**: Primarily test retrieval or reading comprehension
- **In-context learning**: Models learn simple task patterns via instructions and demonstrations
- **Knowledge retrieval**: Requires accessing pre-trained knowledge rather than learning new information

---

## Benchmark Design

### Core Design Principles

1. **Task-specific content**: New content required to resolve each task is contained within the corresponding context
2. **Beyond pre-training**: All required information must be learned from context, not retrieved from pre-training
3. **Real-world complexity**: Tasks reflect genuine challenges encountered in practical applications

### Task Categories

The benchmark encompasses multiple types of context-dependent tasks:

1. **Domain-specific knowledge**: Medical, legal, financial, and scientific contexts
2. **Rule systems**: Tasks requiring understanding and application of complex rule sets
3. **Complex procedures**: Step-by-step processes that must be learned from context
4. **Empirical data laws**: Patterns and relationships derived from data within the context

### Verification System

Each task includes **31,607 verification rubrics** to ensure:
- Accurate evaluation of model responses
- Comprehensive assessment of context understanding
- Reliable measurement of context learning capability

---

## Methodology

### Expert Curation

All benchmark components were crafted by experienced domain experts who:
- Designed contexts representing real-world complexity
- Created tasks that genuinely require context learning
- Developed verification rubrics for rigorous evaluation

### Task Construction Process

1. **Context development**: Experts created 500 complex, realistic contexts
2. **Task design**: Each task was designed to require information from its context
3. **Rubric development**: Comprehensive evaluation criteria were established for each task

### Evaluation Framework

The benchmark was designed to test:
- **Comprehension**: Understanding of context-specific information
- **Learning**: Ability to acquire new knowledge from context
- **Application**: Proper application of learned information to task resolution
- **Reasoning**: Logical deduction based on context-derived knowledge

---

## Experimental Results

### Models Evaluated

Ten frontier language models were evaluated on CL-bench:

| Model | Performance |
|-------|-------------|
| GPT-5.1 | 23.7% (Best) |
| Other frontier models | Below average |

### Key Findings

1. **Poor overall performance**: Models solve only **17.2% of tasks on average**
2. **Significant gap**: Even the best-performing model (GPT-5.1) achieves only **23.7%** accuracy
3. **Critical limitation**: LMs have yet to achieve effective context learning
4. **Bottleneck identification**: Context learning poses a critical bottleneck for tackling real-world, complex context-dependent tasks

### Performance Analysis

The results reveal that current frontier models:
- Struggle with learning new information from context
- Cannot effectively apply context-specific knowledge to tasks
- Face significant limitations in domain-specific reasoning
- Require substantial improvement in context learning capabilities

---

## Contributions

### 1. Novel Benchmark

- **CL-bench**: The first comprehensive benchmark specifically designed to evaluate context learning
- **Scale**: 500 contexts, 1,899 tasks, and 31,607 verification rubrics
- **Quality**: Expert-crafted, real-world aligned benchmark

### 2. New Perspective

- **Context Learning Definition**: Formalized the concept of context learning as distinct from in-context learning
- **Capability Gap Identification**: Revealed critical limitations in current LMs' context learning abilities

### 3. Research Direction

- **Foundation for Improvement**: Established a baseline for future research on context learning
- **Real-world Applicability**: Highlighted the importance of context learning for practical applications

---

## Implications

### For Research

1. **New Research Direction**: Context learning represents a crucial research area for LM advancement
2. **Evaluation Standard**: CL-bench provides a standardized benchmark for evaluating context learning
3. **Progress Tracking**: Enables systematic tracking of improvements in context learning capabilities

### For Applications

1. **Real-world Deployment**: Context learning is essential for deploying LMs in practical scenarios
2. **Domain Adaptation**: Highlights the need for better domain-specific context learning
3. **Reliability**: Shows that current models may fail in contexts requiring new knowledge acquisition

### For Model Development

1. **Architecture Improvements**: Suggests areas where LM architectures may need enhancement
2. **Training Objectives**: Indicates potential need for training objectives focused on context learning
3. **Evaluation Metrics**: Provides clear metrics for measuring context learning progress

---

## Limitations and Future Work

### Current Limitations

1. **Coverage**: While comprehensive, the benchmark may not cover all possible context learning scenarios
2. **Evolution**: As models improve, the benchmark may need updates to remain challenging
3. **Domain Balance**: May need expansion to include more diverse domains

### Future Directions

1. **Extended Benchmarks**: Development of more specialized context learning benchmarks
2. **Improved Evaluation**: Enhanced verification systems with more nuanced criteria
3. **Training Methods**: Research into effective methods for improving context learning
4. **Architecture Development**: Investigation of LM architectures better suited for context learning

---

## Related Work

### Context and Knowledge in LMs

1. **Long-context models**: Models capable of processing very long contexts
2. **Retrieval-augmented generation (RAG)**: Combining retrieval with generation
3. **Knowledge editing**: Updating model knowledge without full retraining
4. **Domain adaptation**: Specialized training for specific domains

### Evaluation Benchmarks

1. **General reasoning benchmarks**: Testing logical reasoning and problem-solving
2. **Domain-specific benchmarks**: Evaluating performance in specialized fields
3. **Reading comprehension**: Testing understanding of provided text
4. **Instruction following**: Evaluating adherence to given instructions

---

## Conclusion

**CL-bench** represents a significant step forward in evaluating and understanding the context learning capabilities of language models. The benchmark reveals a critical gap in current LMs' abilities to learn from and apply context-specific information.

Key takeaways:
- **Current models struggle significantly** with context learning (average 17.2% accuracy)
- **GPT-5.1 leads** with only 23.7% accuracy, showing room for substantial improvement
- **Context learning is essential** for real-world applications where models must acquire new knowledge
- **Research is needed** to improve this fundamental capability of language models

The benchmark serves as both a diagnostic tool and a motivation for future research into making language models more intelligent and better suited for real-world deployment.

---

## References

- Original paper: [arXiv:2602.03587](https://arxiv.org/abs/2602.03587)
- Benchmark website: [www.clbench.com](http://www.clbench.com)

---

## Technical Details

### Benchmark Statistics

| Component | Count |
|-----------|-------|
| Complex contexts | 500 |
| Tasks | 1,899 |
| Verification rubrics | 31,607 |
| Pages | 78 |
| Figures | 17 |

### Authors and Affiliations

The research was conducted by a large team from Fudan University and collaborating institutions, including experts in natural language processing, machine learning, and various domain specialties.

### License

This benchmark is released under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**, allowing for broad use and adaptation with appropriate attribution.

---

*Summary generated on: February 10, 2026*
*Paper submission date: February 3, 2026*
