The integration of large language models (LLMs) with external tools to enable complex reasoning and task execution is a critical area of research. This process is categorized into three main approaches: **in-context tool integration**, **post-training tool integration**, and **orchestration-based tool integration**, each with distinct strategies and trade-offs.

---

### **1. In-Context Tool Integration**
This approach relies on pre-trained LLMs to interact with tools **without additional training**, using **in-context prompts** and **few-shot learning**. Key methods include:

- **ReAct**: Combines reasoning and acting in a loop, allowing models to dynamically gather information from external environments (e.g., APIs, knowledge bases). It enables adaptive action planning and real-time interaction.
- **ART**: Uses a library of task demonstrations as few-shot prompts, guiding LLMs to follow proven reasoning paths for new tasks.
- **GEAR**: Delegates tool selection to a smaller model to reduce costs, while reserving the LLM for final reasoning.
- **AVATAR**: Enhances robustness through "contrastive reasoning" before acting, improving tool selection accuracy.

**Limitations**: Performance is constrained by the frozen LLM's inherent capabilities and context window size. These methods are less effective for large or complex toolsets.

---

### **2. Post-Training Tool Integration**
This involves **fine-tuning** or **reinforcement learning (RL)** to improve LLMs' ability to interact with tools. 

#### **Supervised Fine-Tuning (SFT)**
- **Toolformer**: A self-supervised framework where LLMs generate and validate API calls, followed by fine-tuning for accuracy.
- **ToolLLM**: Scales SFT to over 16,000 APIs, enabling robust planning and invocation.
- **ToolAlpaca**: Extends SFT to compact LLMs by automatically constructing diverse toolsets and simulating multi-agent interactions.

**Challenges**: SFT risks overfitting to training data patterns, leading to brittle tool-selection strategies and limited adaptability in new scenarios.

#### **Reinforcement Learning (RL)**
- **SWE-RL**: Optimizes code-editing policies using RL, improving both software resolution and general reasoning.
- **ReSearch**: Embeds search operations into multi-hop reasoning chains for adaptive retrieval in QA.
- **ReTool**: Integrates real-time code execution into reasoning, excelling in advanced math benchmarks.
- **ToolRL**: Generalizes RL to diverse toolsets with principled reward designs, achieving scalable and robust tool-use policies.

**Advantages**: RL outperforms SFT in adaptability and generalization, effectively transferring to out-of-domain tasks.

---

### **3. Orchestration-Based Tool Integration**
This approach addresses complex systems requiring **multiple tools** and **coordinated execution**, often involving planning, sequencing, and dependency management.

#### **Key Frameworks**
- **HuggingGPT**: Uses a centralized agent to plan tool invocations, enabling multi-tool task solutions.
- **TaskMatrix.AI**: Connects foundation models with millions of APIs, automating sub-task assignment to specialized systems.
- **OctoTools**: A training-free, extensible framework with hierarchical planning and standardized tool cards, improving multi-domain reasoning.
- **Chain-of-Tools**: Dynamically composes unseen tools using frozen LLMs' semantic representations, avoiding fine-tuning.
- **PyVision**: Enables MLLMs to generate, execute, and refine Python-based tools for visual reasoning.
- **ConAgents**: Extends tool frameworks to multi-agent interactive settings.

#### **Tool Representation Optimization**
- **ToolExpNet**: Models tools and usage experiences as semantic networks, aiding selection and dependency management.
- **T2Agent**: Uses Bayesian optimization and Monte Carlo Tree Search for efficient multi-source verification in multimodal tasks.
- **ToolChain***: Frames tool orchestration as a structured process, enhancing coordination across diverse toolsets.

---

### **Challenges and Future Directions**
- **Overfitting**: SFT struggles with generalization, while RL requires careful reward design.
- **Scalability**: Orchestration frameworks must handle dynamic tool interactions and large-scale systems.
- **Tool Representation**: Optimizing tool metadata (e.g., semantic similarity, dependencies) improves selection accuracy.

---

### **Applications**
- **Chemistry**: Agentic frameworks are applied to complex tasks like molecular property prediction.
- **Multi-Domain Reasoning**: Tools like Chain-of-Tools and OctoTools enable cross-domain adaptability.

---

### **Conclusion**
Agentic reasoning through tool integration represents a paradigm shift, enabling LLMs to handle complex, real-world tasks by combining pre-trained knowledge with dynamic tool interactions. While in-context methods offer flexibility, post-training techniques like RL provide robust adaptability, and orchestration frameworks address multi-tool coordination. Future work will focus on scalable, efficient, and generalizable tool integration strategies.

===============

## 中文翻译

大语言模型（LLMs）与外部工具的集成，以实现复杂推理和任务执行，是研究的关键领域。此过程分为三种主要方法：**上下文工具集成**、**后训练工具集成**和**编排式工具集成**，每种方法都有其独特的策略和权衡。

---

### **1. 上下文工具集成**
该方法依赖预训练的LLMs在**无需额外训练**的情况下，通过**上下文提示**和**少样本学习**与工具交互。关键方法包括：

- **ReAct**：结合推理和行动，在循环中允许模型动态地从外部环境中获取信息（如API、知识库），实现自适应行动规划和实时交互。
- **ART**：使用任务演示库作为少样本提示，引导LLMs遵循已验证的推理路径完成新任务。
- **GEAR**：将工具选择委托给较小的模型以降低成本，同时保留LLM用于最终推理。
- **AVATAR**：通过“对比推理”在行动前增强鲁棒性，提高工具选择的准确性。

**局限性**：性能受冻结LLM的固有能力和上下文窗口大小的限制。这些方法对大型或复杂工具集效果较差。

---

### **2. 后训练工具集成**
该方法涉及通过**微调**或**强化学习（RL）**来提升LLMs与工具交互的能力。

#### **监督微调（SFT）**
- **Toolformer**：一种自监督框架，LLMs生成并验证API调用，随后进行微调以提高准确性。
- **ToolLLM**：将SFT扩展至超过16,000个API，实现稳健的规划和调用。
- **ToolAlpaca**：通过自动构建多样化工具集和模拟多智能体交互，将SFT扩展至紧凑型LLMs。

**挑战**：SFT容易过度拟合训练数据模式，导致工具选择策略脆弱，且在新场景中适应性有限。

#### **强化学习（RL）**
- **SWE-RL**：使用RL优化代码编辑策略，提升软件修复和通用推理能力。
- **ReSearch**：将搜索操作嵌入多跳推理链中，实现问答中的自适应检索。
- **ReTool**：将实时代码执行集成到推理中，在高级数学基准测试中表现优异。
- **ToolRL**：通过原则性奖励设计将RL扩展到多样化工具集，实现可扩展且稳健的工具使用策略。

**优势**：RL在适应性和泛化能力上优于SFT，能有效迁移到领域外任务。

---

### **3. 编排式工具集成**
该方法解决需要**多个工具**和**协调执行**的复杂系统，通常涉及规划、顺序执行和依赖管理。

#### **关键框架**
- **HuggingGPT**：使用集中式代理进行工具调用规划，实现多工具任务解决方案。
- **TaskMatrix.AI**：将基础模型与数百万API连接，自动将子任务分配给专用系统。
- **OctoTools**：一种无需训练、可扩展的框架，具有分层规划和标准化工具卡片，提升多领域推理能力。
- **Chain-of-Tools**：利用冻结LLMs的语义表示动态组合未见过的工具，避免微调。
- **PyVision**：使MLLMs能够生成、执行和优化基于Python的工具，用于视觉推理。
- **ConAgents**：将工具框架扩展至多智能体交互场景。

#### **工具表示优化**
- **ToolExpNet**：将工具及其使用经验建模为语义网络，辅助选择和依赖管理。
- **T2Agent**：使用贝叶斯优化和蒙特卡洛树搜索，在多模态任务中实现高效的多源验证。
- **ToolChain**：将工具编排框架为结构化流程，提升多样化工具集间的协调能力。

---

### **挑战与未来方向**
- **过拟合**：SFT在泛化能力上存在不足，而RL需要谨慎设计奖励机制。
- **可扩展性**：编排框架需处理动态工具交互和大规模系统。
- **工具表示**：优化工具元数据（如语义相似性、依赖关系）可提升选择准确性。

---

### **应用**
- **化学**：代理框架被应用于分子性质预测等复杂任务。
- **多领域推理**：工具如Chain-of-Tools和OctoTools实现跨领域适应性。

---

### **结论**
通过工具集成实现的代理推理代表了一种范式转变，使LLMs能够结合预训练知识与动态工具交互，处理复杂现实任务。尽管上下文方法提供灵活性，但后训练技术如RL提供了更强的适应性，而编排框架解决了多工具协调问题。未来的研究将聚焦于可扩展、高效且通用的工具集成策略。

#### Reference: 

Source file: 2601.12538v1.pdf