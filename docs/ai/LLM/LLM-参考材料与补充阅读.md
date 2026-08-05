# 参考材料与补充阅读：大语言模型

---

## 主题一：大语言模型的发展历史

### 1. 语言与智能的关系

**概述：**  
这一话题讨论语言究竟是一套形式规则、一种概率分布，还是人类知识与认知活动的外在痕迹。语言模型能够从文本中学习语法、概念和部分世界结构，但语言形式并不等于真实世界、交际意图或完整的意义。这一张力构成了理解大语言模型能力与局限的起点。

**补充阅读：**

- [Lena Voita, Language Modeling](https://lena-voita.github.io/nlp_course/language_modeling.html)
- [Stephen Wolfram, What Is ChatGPT Doing … and Why Does It Work?](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/)
- [Bender & Koller, Climbing towards NLU](https://aclanthology.org/2020.acl-main.463/)

### 2. 早期自然语言处理方法

**概述：**  
早期自然语言处理经历了从人工规则、符号系统和专家知识，到统计语言模型、词向量和神经网络的转变。关键变化是知识进入机器的方式从显示的规则写入，逐渐转为由模型从语料中学习表示和规律。

**补充阅读：**

- [Chris Olah, Deep Learning, NLP, and Representations](https://colah.github.io/posts/2014-07-NLP-RNNs-Representations/)
- [Andrej Karpathy, The Unreasonable Effectiveness of Recurrent Neural Networks](https://karpathy.github.io/2015/05/21/rnn-effectiveness/)
- [Jay Alammar, The Illustrated Word2vec](https://jalammar.github.io/illustrated-word2vec/)

### 3. Transformer

**概述：**  
Transformer 将语言处理的核心转变为上下文中的动态信息交互。Self-Attention 使每个 token 能够根据当前任务选择相关上下文，多层计算则不断更新其情境化表示。它同时改善了长距离建模和训练并行性，为后来扩大模型、数据和计算规模提供了关键架构基础。

**补充阅读：**

- [Jay Alammar, The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/)
- [Harvard NLP, The Annotated Transformer](https://nlp.seas.harvard.edu/annotated-transformer/)
- [Attention Is All You Need](https://arxiv.org/abs/1706.03762)

### 4. Scaling Law 与大模型

**概述：**  
Scaling Law 将“大模型为什么有效”从经验判断变成了可以研究和规划的工程问题。模型能力并非只由参数量决定，而是来自参数、数据、训练计算和数据质量的共同配置。规模化的深层意义，是通用学习方法的理念开始持续超过大量面向单项任务的人工设计。

**补充阅读：**

- [Richard Sutton, The Bitter Lesson](http://www.incompleteideas.net/IncIdeas/BitterLesson.html)
- [Google DeepMind, An Empirical Analysis of Compute-Optimal Large Language Model Training](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/)
- [Andrej Karpathy, Software 2.0](https://karpathy.medium.com/software-2-0-a64152b37c35)

### 5. ChatGPT：从语言模型到助手

**概述：**  
预训练模型学习的是人类文本中大量可能的知识、角色和行为模式，但它并不天然知道面对用户时应该采取哪一种行为。ChatGPT 所代表的转变，是通过指令微调和偏好学习，将通用语言模型塑造成相对稳定、能够理解请求并持续对话的助手。

**补充阅读：**

- [OpenAI, Introducing ChatGPT](https://openai.com/index/chatgpt/)
- [Anthropic, The Persona Selection Model](https://alignment.anthropic.com/2026/psm/)
- [OpenAI, Aligning Language Models to Follow Instructions](https://openai.com/index/instruction-following/)

### 6. GPT o1 与 DeepSeek-R1：从生成到推理

**概述：**  
推理模型将能力扩展从训练阶段延伸到回答阶段：模型不仅依赖参数中已经压缩的知识，还可以针对当前问题投入更多计算，进行尝试、检查和策略调整。o1 与 DeepSeek-R1 也使强化学习、可验证奖励和推理时计算成为大模型发展的新主线。

**补充阅读：**

- [OpenAI, Learning to Reason with LLMs](https://openai.com/index/learning-to-reason-with-llms/)
- [Jay Alammar, The Illustrated DeepSeek-R1](https://newsletter.languagemodels.co/p/the-illustrated-deepseek-r1)
- [DeepSeek-R1](https://arxiv.org/abs/2501.12948)

### 7. Claude Code：从回答问题到完成工作

**概述：**  
Claude Code 代表模型从语言交互进入真实工作环境。模型能够读取项目状态、调用工具、修改文件并根据测试结果继续行动；能力也因此从模型参数内部扩展到 Context、Tools、Skills、Harness 和环境反馈所构成的完整系统。

**补充阅读：**

- [Anthropic, Best Practices for Claude Code](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Anthropic, Building Effective AI Agents](https://www.anthropic.com/engineering/building-effective-agents)
- [Anthropic, Effective Context Engineering for AI Agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Anthropic, Harness Design for Long-Running Application Development](https://www.anthropic.com/engineering/harness-design-long-running-apps)

---

## 主题二：大语言模型是如何训练的

### 1. 训练流程总览

**概述：**  
现代大语言模型通常经历 Pre-training、Mid-training 和 Post-training 等阶段，并在训练过程中持续穿插数据治理、能力评价和安全测试。不同阶段分别塑造其基础表征、能力分布和面向用户或环境的行为策略。

**补充阅读：**

- [Ai2, Olmo 3: Charting a Path through the Model Flow](https://allenai.org/blog/olmo3)
- [Vintage Data, Training as We Know It Will End](https://vintagedata.org/blog/posts/training-as-we-know-it-will-end)

### 2. Pre-training：用数据和计算建立能力基础

**概述：**  
Pre-training 以统一的预测目标吸收大规模数据，但真正的训练实践远不只是“堆更多 token”。模型架构决定计算方式，数据构成决定模型可以学习的知识和能力边界，Scaling Law 决定参数、数据与计算应如何配置，而分布式系统与训练稳定性则决定一套方案能否在现实规模上运行。Pre-training 更接近建设模型的“能力底座”，其成果会深刻限制后续训练能够塑造出的行为上限。

**补充阅读：**

- [Hugging Face, The Ultra-Scale Playbook: Training LLMs on GPU Clusters](https://huggingface.co/spaces/nanotron/ultrascale-playbook)
- [Google DeepMind, An Empirical Analysis of Compute-Optimal Large Language Model Training](https://deepmind.google/blog/an-empirical-analysis-of-compute-optimal-large-language-model-training/)
- [Ai2, Investigating Pretraining Dynamics and Stability with OLMo Checkpoints](https://allenai.org/blog/investigating-pretraining-dynamics-and-stability-with-olmo-checkpoints-ece6f0c4947a)

### 3. Mid-training

**概述：**  
Mid-training 通常指广泛预训练之后、面向行为对齐的 Post-training 之前的一段定向塑造过程。它可以通过更高质量或更专门的数据强化数学、代码、科学和长上下文等能力，使基础模型的能力分布更适合后续训练和部署目标。

**补充阅读：**

- [Vintage Data, What’s the Deal with Mid-training?](https://vintagedata.org/blog/posts/what-is-mid-training)
- [IBM Research, How an Extra Training Step Can Unlock AI’s Reasoning Power](https://research.ibm.com/blog/mid-training-for-better-ai-reasoning)
- [Midtraining Bridges Pretraining and Posttraining Distributions](https://arxiv.org/abs/2510.14865)

### 4. Post-training I：示范、指令与蒸馏

**概述：**  
Post-training 的第一类信号来自“优秀行为是什么样的”。SFT 通过专家或教师生成的示范，让基础模型学会遵循指令、组织回答和采用稳定的交互格式；蒸馏则把更强模型的行为与策略迁移到学生模型。On-Policy Distillation 进一步让学生从自身生成的轨迹中暴露真实错误，再由教师提供密集反馈，缓解固定示范数据与模型实际推理分布之间的错位。

**补充阅读：**

- [Nathan Lambert, A Recipe for Frontier Model Post-training](https://www.interconnects.ai/p/frontier-model-post-training)
- [Thinking Machines, On-Policy Distillation](https://thinkingmachines.ai/blog/on-policy-distillation/)
- [Netflix TechBlog, Scaling LLM Post-Training at Netflix](https://netflixtechblog.com/scaling-llm-post-training-at-netflix-0046f8790194)

### 5. Post-training II：偏好学习、RLHF 与 DPO

**概述：**  
开放式回答往往没有唯一标准答案，因此模型需要从人类或 AI 对多个输出的比较中学习“哪一种行为更好”。RLHF 将偏好转化为奖励并优化模型策略，DPO 则更直接地利用偏好对更新模型。偏好学习的难点不只在算法，还在于反馈究竟代表真实性、有用性、安全性还是表达风格；当评价者偏好与真实目标不一致时，模型也会学习迎合、投机或其他意外行为。

**补充阅读：**

- [Nathan Lambert, How RLHF Actually Works](https://www.interconnects.ai/p/how-rlhf-works)
- [Hugging Face, Illustrating Reinforcement Learning from Human Feedback](https://huggingface.co/blog/rlhf)
- [Nathan Lambert, Do We Need RL for RLHF?](https://www.interconnects.ai/p/the-dpo-debate)
- [Anthropic, Towards Understanding Sycophancy in Language Models](https://www.anthropic.com/research/towards-understanding-sycophancy-in-language-models)

### 6. Post-training III：RLVR 与推理模型

**概述：**  
当任务结果可以被程序、测试或形式规则可靠验证时，模型可以直接从结果成败中学习，而不再完全依赖人类偏好。RLVR 推动了数学、代码和形式推理等领域的 Post-training，也使强化学习重新成为前沿模型训练的核心方法。这里的关键不只是使用 RL，而是拥有可扩展的任务分布、有效探索机制和足够可靠的 Verifier，并理解训练究竟扩展了能力边界，还是提高了已有解法被采样到的概率。

**补充阅读：**

- [OpenAI, Learning to Reason with LLMs](https://openai.com/index/learning-to-reason-with-llms/)
- [Nathan Lambert, An Unexpected RL Renaissance](https://www.interconnects.ai/p/an-unexpected-rl-renaissance)
- [Nathan Lambert, Quick Recap on the State of Reasoning](https://www.interconnects.ai/p/the-state-of-reasoning)
- [RLVR Book](https://rlvrbook.com/)

### 7. Post-training IV：Agentic RL 与环境经验

**概述：**  
Agentic RL 将训练对象从一次回答扩展为一段包含规划、工具调用、环境观察和错误恢复的完整轨迹。此时，训练的核心瓶颈逐渐从单一优化算法转向环境设计：任务是否足够丰富，行动结果是否可以验证，失败是否能形成有效经验，训练环境与真实部署是否一致。模型也由模仿人类静态数据，进一步走向通过与环境互动获得自己的经验。

**补充阅读：**

- [David Silver & Richard Sutton, Welcome to the Era of Experience](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)
- [Ai2, DR Tulu: An Open Training Recipe for Deep Research Agents](https://allenai.org/blog/dr-tulu)
- [NVIDIA, How to Train Scientific Agents with Reinforcement Learning](https://developer.nvidia.com/blog/how-to-train-scientific-agents-with-reinforcement-learning/)
- [A Taxonomy of RL Environments for LLM Agents](https://leehanchung.github.io/blogs/2026/03/21/rl-environments-for-llm-agents/)

---

## 主题三：大语言模型应用

### 1. LLM for Research and Science

**概述：**  
大模型正在从文献检索、代码辅助和数据分析，逐渐进入假设生成、实验设计、计算执行和结果评价等科研环节。这一方向既包括帮助研究者完成开放式信息探索的 Research Agent，也包括尝试覆盖假设、实验与验证闭环的 AI Scientist。真正的瓶颈是建立可靠的证据链、实验反馈和评价机制，判断哪些结果真正构成新的知识。

**补充阅读：**

- [Anthropic, How We Built Our Multi-Agent Research System](https://www.anthropic.com/engineering/multi-agent-research-system)
- [FutureHouse, What Is an AI Scientist?](https://www.futurehouse.org/ai-scientist)
- [Sakana AI, The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery](https://sakana.ai/ai-scientist/)
- [Ai2, Evaluating Agents for Scientific Discovery](https://allenai.org/blog/evaluating-scientific-discovery-agents)

### 2. LLM for Productivity

**概述：**  
生产力应用正在从搜索、写作和编程等单步辅助，走向能够管理上下文、调用软件并持续交付成果的 Working Agent。模型如何重新分配人与软件之间的任务边界并改变完整工作流成为核心的讨论问题。

**补充阅读：**

- [Anthropic Economic Index](https://www.anthropic.com/economic-index)
- [Anthropic, Best Practices for Claude Code](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Anthropic, Effective Harnesses for Long-Running Agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents)

### 3. LLM for Humanities and Social Sciences

**概述：**  
大模型为人文社科提供了连接大规模阅读与自然语言解释的新接口，可用于历史材料、概念演化、话语结构、访谈和社会行为研究。但这一领域尤其需要警惕模型抹平语境差异、制造合理但不存在的证据，以及把语言中的平均模式误认为真实人群的行为。

**补充阅读：**

- [Programming Historian](https://programminghistorian.org/en/lessons/)
- [Humanities Data Analysis](https://www.humanitiesdataanalysis.org/)
- [Stanford HAI, Simulating Human Behavior with AI Agents](https://hai.stanford.edu/policy/simulating-human-behavior-with-ai-agents)

### 4. LLM for High-Value Domains

**概述：**  
金融、法律、医疗和公共服务等领域具有较高的专业门槛与错误成本。模型在这些领域的价值不只取决于专业知识，还取决于实时数据、工具权限、证据链、合规要求、领域评价和人类责任是否被组织成一个可靠系统。

**补充阅读：**

- [Anthropic, Finance Agents](https://www.anthropic.com/news/finance-agents)
- [Anthropic, Healthcare and Life Sciences](https://www.anthropic.com/news/healthcare-life-sciences)
- [NIST, AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

---

## 主题四：大模型的安全、理解与社会治理

### 1. 大模型治理与公共事务

**概述：**  
大模型治理不仅是对技术公司的外部监管，也包括政府作为采购者、部署者、数据持有者和公共服务提供者时应承担的责任。核心议题包括标准与审计、数据和隐私、公共采购、透明度、权利救济、国际协调，以及能力快速变化下制度如何保持适应性。

**补充阅读：**

- [NIST, AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- [Stanford HAI, Policy and Society](https://hai.stanford.edu/policy)
- [Narayanan & Kapoor, AI as Normal Technology](https://knightcolumbia.org/content/ai-as-normal-technology)

### 2. LLM Safety、Alignment 与 Control

**概述：**  
大模型安全既包括幻觉、偏见和鲁棒性等可靠性问题，也包括危险能力、恶意使用、目标偏离和高权限 Agent 带来的系统风险。Alignment 关注如何塑造模型目标和行为，Control 则进一步追问：即使模型并不完全可信，系统仍能否限制其造成严重后果。

**补充阅读：**

- [Anthropic, Recommended Directions for Technical AI Safety](https://alignment.anthropic.com/2025/recommended-directions/)
- [Anthropic, Reward Tampering](https://www.anthropic.com/research/reward-tampering)
- [OpenAI, Detecting Misbehavior in Frontier Reasoning Models](https://openai.com/index/chain-of-thought-monitoring/)

### 3. Evaluation、Auditing 与 Red Teaming

**概述：**  
评价体系是连接模型研发、应用质量和社会治理的基础设施。随着任务从单轮问答扩展到开放式交付和 Agent 轨迹，评价需要同时覆盖能力、可靠性、安全性、过程行为和部署后的真实结果，并通过审计和 Red Teaming 主动寻找系统盲点。

**补充阅读：**

- [Anthropic, Demystifying Evals for AI Agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)
- [OpenAI, Why Language Models Hallucinate](https://openai.com/index/why-language-models-hallucinate/)
- [Anthropic, Auditing Language Models for Hidden Objectives](https://www.anthropic.com/research/auditing-hidden-objectives)

### 4. LLM Interpretability

**概述：**  
可解释性试图从外部行为进一步进入模型内部，研究模型表示了哪些概念、信息如何在层间流动，以及哪些机制最终形成特定输出。它既是一种理解人工智能的基础科学，也可能服务模型审计、风险定位和定向干预，但目前仍远未达到完整读取模型思维过程的程度。

**补充阅读：**

- [Chris Olah, Mechanistic Interpretability, Variables, and the Importance of Interpretable Bases](https://transformer-circuits.pub/2022/mech-interp-essay)
- [Anthropic, Mapping the Mind of a Large Language Model](https://www.anthropic.com/research/mapping-mind-language-model)
- [Anthropic, On the Biology of a Large Language Model](https://transformer-circuits.pub/2025/attribution-graphs/biology.html)

### 5. 大模型的社会影响

**概述：**  
大模型可能改变劳动分工、教育方式、信息生产和知识权力结构，但影响不会仅由模型能力决定，还取决于组织采用、制度安排、成本分配和不同群体获得技术的机会。研究社会影响需要同时观察自动化、增强、生产率、就业质量、数字鸿沟和文化多样性。

**补充阅读：**

- [Anthropic Economic Index](https://www.anthropic.com/economic-index)
- [Stanford AI Index](https://hai.stanford.edu/ai-index)
- [Narayanan & Kapoor, AI as Normal Technology](https://knightcolumbia.org/content/ai-as-normal-technology)

---

## 主题五：（部分）大模型的前沿研究

### 1. Self-Evolving Models 与持续学习

**概述：**  
Self-evolving 研究希望模型能够利用自身生成的任务、轨迹、批评和环境经验持续改进，而不是每次能力更新都依赖新一轮大规模人工数据生产。真正的难点在于建立可靠的外部约束，否则自生成数据可能只是循环放大模型已有的错误和偏见。

**补充阅读：**

- [Silver & Sutton, Welcome to the Era of Experience](https://storage.googleapis.com/deepmind-media/Era-of-Experience%20/The%20Era%20of%20Experience%20Paper.pdf)
- [A Survey on Self-Evolution of Large Language Models](https://arxiv.org/abs/2404.14387)
- [A Survey of Self-Evolving Agents](https://arxiv.org/abs/2507.21046)

### 2. Memory、Personalization 与 Long-Horizon Agents

**概述：**  
长期 Agent 需要在多个任务和会话之间保存目标、经验、用户偏好和环境状态。长上下文并不等同于真正的记忆，系统还需要决定什么值得写入、如何检索、何时遗忘、如何解决冲突，以及怎样避免个性化演变为隐私和控制风险。

**补充阅读：**

- [Anthropic, Effective Context Engineering for AI Agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Anthropic, Effective Harnesses for Long-Running Agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents)
- [Anthropic, Harness Design for Long-Running Application Development](https://www.anthropic.com/engineering/harness-design-long-running-apps)

### 3. Multimodal Models、World Models 与 Embodied AI

**概述：**  
多模态和具身研究试图让模型从文字扩展到图像、视频、声音、动作与环境状态。World Model 不只识别当前世界，还要预测行动可能产生的后果；它代表智能从学习人类对世界的描述，进一步走向通过感知和互动建立经验。

**补充阅读：**

- [Google DeepMind, Genie 3](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/)
- [Google DeepMind, Gemini Robotics](https://deepmind.google/models/gemini-robotics/)
- [Google DeepMind, SIMA 2](https://deepmind.google/blog/sima-2-an-agent-that-plays-reasons-and-learns-with-you-in-virtual-3d-worlds/)

### 4. 新模型架构与效率

**概述：**  
Transformer 仍是主流，但训练与推理成本正在推动 Mixture-of-Experts、稀疏计算、混合架构、长上下文机制和新型记忆结构的发展。这一方向关注如何让模型以更少的激活参数、更低的显存占用和更长的有效上下文完成同等或更复杂的任务，并在能力、成本、延迟和系统复杂度之间取得平衡。

**补充阅读：**

- [Hugging Face, Mixture of Experts Explained](https://huggingface.co/blog/moe)
- [Lilian Weng, Large Transformer Model Inference Optimization](https://lilianweng.github.io/posts/2023-01-10-inference-optimization/)
- [Google Research, Titans + MIRAS: Helping AI Have Long-Term Memory](https://research.google/blog/titans-miras-helping-ai-have-long-term-memory/)

---

## 推荐的公开课程

Stanford CS224N 需要一定 Python、线性代数和概率基础，其余课程更适合直接入门。

1. [DeepLearning.AI：Generative AI for Everyone](https://www.deeplearning.ai/courses/generative-ai-for-everyone)  
   Andrew Ng 主讲的非技术入门课，适合先建立生成式 AI、LLM、应用边界与社会影响的整体认识。

2. [Stanford CS224N：Natural Language Processing with Deep Learning](https://web.stanford.edu/class/cs224n/)  
   自然语言处理领域最具代表性的公开课程之一，适合希望系统理解词向量、神经语言模型、Attention 和 Transformer 的技术型入门者。

3. [DeepLearning.AI：Agentic AI](https://www.deeplearning.ai/courses/agentic-ai)  
   Andrew Ng 主讲的 Agent 系统课程，从基本组件和设计模式出发，介绍 Reflection、Tool Use、Planning 与 Multi-Agent Collaboration，并强调从第一性原理构建 Agentic Workflow，而不是只学习某个短期流行的框架。适合在掌握基础 LLM 概念后，系统理解模型如何从生成回答走向执行多步任务。
