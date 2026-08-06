# 参考材料与补充阅读：大语言模型（上）大语言模型是如何训练的

### 1. 训练流程总览

**概述：**
现代大语言模型通常经历 Pre-training、Mid-training 和 Post-training 等阶段，并在训练过程中持续穿插数据治理、能力评价和安全测试。不同阶段分别塑造其基础表征、能力分布和面向用户或环境的行为策略。

**补充阅读：**

* [Ai2, Olmo 3: Charting a Path through the Model Flow](https://allenai.org/blog/olmo3)
* [Vintage Data, Training as We Know It Will End](https://vintagedata.org/blog/posts/training-as-we-know-it-will-end)
* [Sebastian Raschka, New LLM Pre-training and Post-training Paradigms](https://magazine.sebastianraschka.com/p/new-llm-pre-training-and-post-training)
* [PyTorch, A Primer on LLM Post-Training](https://pytorch.org/blog/a-primer-on-llm-post-training/)

### 2. Pre-training：用数据和计算建立能力基础

**概述：**
Pre-training 以统一的预测目标吸收大规模数据。模型架构决定计算方式，数据构成决定模型可以学习的知识和能力边界，Scaling Law 决定参数、数据与计算应如何配置，而分布式系统与训练稳定性则决定一套方案能否在现实规模上运行。Pre-training 更接近建设模型的“能力底座”，其成果会深刻影响后续训练能够塑造出的行为上限。

**补充阅读：**

* [Hugging Face, The Ultra-Scale Playbook: Training LLMs on GPU Clusters](https://huggingface.co/spaces/nanotron/ultrascale-playbook)
* [Google DeepMind, An Empirical Analysis of Compute-Optimal Large Language Model Training](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/)
* [Ai2, Investigating Pretraining Dynamics and Stability with OLMo Checkpoints](https://allenai.org/blog/investigating-pretraining-dynamics-and-stability-with-olmo-checkpoints-ece6f0c4947a)
* [Hugging Face, SmolLM3: A Complete Modern Training Recipe](https://huggingface.co/blog/smollm3)
* [Hugging Face, FineWeb: Decanting the Web for the Finest Text Data at Scale](https://huggingface.co/spaces/HuggingFaceFW/blogpost-fineweb-v1)

### 3. Mid-training

**概述：**
Mid-training 通常指广泛预训练之后、面向行为对齐的 Post-training 之前的一段定向塑造过程。它可以通过更高质量或更专门的数据强化数学、代码、科学和长上下文等能力，使基础模型的能力分布更适合后续训练和部署目标。

**补充阅读：**

* [Vintage Data, What’s the Deal with Mid-training?](https://vintagedata.org/blog/posts/what-is-mid-training)
* [IBM Research, How an Extra Training Step Can Unlock AI’s Reasoning Power](https://research.ibm.com/blog/mid-training-for-better-ai-reasoning)
* [Midtraining Bridges Pretraining and Posttraining Distributions](https://arxiv.org/abs/2510.14865)
* [Ai2, OLMo 2 32B: An Open Pre-training, Mid-training and Post-training Recipe](https://allenai.org/blog/olmo2-32b)

### 4. Post-training I：监督微调（SFT）

**概述：**
Post-training 的第一类信号来自“优秀行为是什么样的”。SFT 通过专家或教师生成的高质量示范，让基础模型学会遵循指令、组织回答、采用稳定的交互格式，并为推理、工具使用等复杂能力提供初始策略。它适合行为规范明确、可以直接展示理想输出的任务，但主要在固定的示范分布上训练，难以覆盖模型自己生成时可能进入的全部状态。

**补充阅读：**

* [Nathan Lambert, A Recipe for Frontier Model Post-training](https://www.interconnects.ai/p/frontier-model-post-training)
* [Netflix TechBlog, Scaling LLM Post-Training at Netflix](https://netflixtechblog.com/scaling-llm-post-training-at-netflix-0046f8790194)
* [Meta, How to Fine-tune: Focus on Effective Datasets](https://ai.meta.com/blog/how-to-fine-tune-llms-peft-dataset-curation/)

### 5. Post-training II：On-Policy Distillation（OPD）

**概述：**
OPD 让学生模型先按照当前策略生成自己的轨迹，再由更强的教师模型在学生实际到达的状态上提供逐 token 的密集指导。它结合了 On-policy 训练与知识蒸馏：相比 SFT，更贴近学生模型真实运行时的分布；相比只依赖最终奖励的强化学习，又能提供更细粒度、更稳定的过程反馈。

**补充阅读：**

* [Thinking Machines, On-Policy Distillation](https://thinkingmachines.ai/blog/on-policy-distillation/)

### 6. Post-training III：偏好学习、RLHF 与 DPO

**概述：**
开放式回答往往没有唯一标准答案，因此模型需要从人类或 AI 对多个输出的比较中学习“哪一种行为更好”。RLHF 将偏好转化为奖励并优化模型策略，DPO 则更直接地利用偏好对更新模型。偏好学习的难点在于反馈究竟代表真实性、有用性、安全性还是表达风格；当评价者偏好与真实目标不一致时，模型也会学习迎合、投机或其他意外行为。

**补充阅读：**

* [Nathan Lambert, How RLHF Actually Works](https://www.interconnects.ai/p/how-rlhf-works)
* [Hugging Face, Illustrating Reinforcement Learning from Human Feedback](https://huggingface.co/blog/rlhf)
* [Nathan Lambert, Do We Need RL for RLHF?](https://www.interconnects.ai/p/the-dpo-debate)
* [Anthropic, Towards Understanding Sycophancy in Language Models](https://www.anthropic.com/research/towards-understanding-sycophancy-in-language-models)
* [Anthropic, Training a Helpful and Harmless Assistant with RLHF](https://www.anthropic.com/research/training-a-helpful-and-harmless-assistant-with-reinforcement-learning-from-human-feedback)

### 7. Post-training IV：RLVR 与推理模型

**概述：**
当任务结果可以被程序、测试或形式规则可靠验证时，模型可以直接从结果成败中学习，而不再完全依赖人类偏好。RLVR 推动了数学、代码和形式推理等领域的 Post-training，也使强化学习重新成为前沿模型训练的核心方法。这里的关键是拥有可扩展的任务分布、有效探索机制和足够可靠的 Verifier，并理解训练究竟扩展了能力边界，还是提高了已有解法被采样到的概率。

**补充阅读：**

* [OpenAI, Learning to Reason with LLMs](https://openai.com/index/learning-to-reason-with-llms/)
* [Nathan Lambert, An Unexpected RL Renaissance](https://www.interconnects.ai/p/an-unexpected-rl-renaissance)
* [RLVR Book](https://rlvrbook.com/)
* [Sebastian Raschka, The State of Reinforcement Learning for LLM Reasoning](https://magazine.sebastianraschka.com/p/the-state-of-llm-reasoning-model-training)
* [Hugging Face, Advanced Understanding of GRPO](https://huggingface.co/learn/llm-course/chapter12/3b)

### 8. Post-training V：Agentic RL 与环境经验

**概述：**
Agentic RL 将训练对象从一次回答扩展为一段包含规划、工具调用、环境观察和错误恢复的完整轨迹。此时，训练的核心瓶颈逐渐从单一优化算法转向环境设计：任务是否足够丰富，行动结果是否可以验证，失败是否能形成有效经验，训练环境与真实部署是否一致。模型也由模仿人类静态数据，进一步走向通过与环境互动获得自己的经验。

**补充阅读：**

* [David Silver & Richard Sutton, Welcome to the Era of Experience](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)
* [A Taxonomy of RL Environments for LLM Agents](https://leehanchung.github.io/blogs/2026/03/21/rl-environments-for-llm-agents/)
* [Cameron Wolfe, Agentic RL: Frameworks and Best Practices](https://cameronrwolfe.substack.com/p/agentic-rl)
* [NVIDIA, Mastering Agentic Techniques: AI Agent Reinforcement Learning](https://developer.nvidia.com/blog/mastering-agentic-techniques-ai-agent-reinforcement-learning/)

---

## 推荐的公开课程

1. [DeepLearning.AI：Generative AI for Everyone](https://www.deeplearning.ai/courses/generative-ai-for-everyone)  
   Andrew Ng 主讲的非技术入门课。

2. [Stanford CS224N：Natural Language Processing with Deep Learning](https://web.stanford.edu/class/cs224n/)  
   自然语言处理领域最具代表性的公开课程之一。

3. [DeepLearning.AI：Agentic AI](https://www.deeplearning.ai/courses/agentic-ai)  
   Andrew Ng 主讲的 Agent 系统课程。