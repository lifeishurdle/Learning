> 课程地址：https://learn.deeplearning.ai/courses/agentic-ai/lesson/zqs9ty

# Module 1
## Lesson 2-What is agent AI
### 无代理性工作流
![[Pasted image 20260113174046.png]]
### 代理性工作流
![[Pasted image 20260113174217.png]]
中间的revision基于evaluation（可由LLM完成）
![[Pasted image 20260113174258.png]]
![[Pasted image 20260113174839.png]]
## Lesson 3-Degrees of autonomy
![[Pasted image 20260113175057.png]]
![[Pasted image 20260113175125.png]]
## Lesson 4-Benefits of agent AI
### 将模型封装到工作流以提升表现

### 并行处理
![[Pasted image 20260113180724.png]]
多个大模型并行处理问题
### 模块化设计可更换工具或模型
![[Pasted image 20260113181022.png]]
## Lesson 5-AI Applications
![[Pasted image 20260113181359.png]]
![[Pasted image 20260113182249.png]]
![[Pasted image 20260113182332.png]]
![[Pasted image 20260113182105.png]]
## Lesson 6-Task decomposition：Identifying the steps in a workflow
### Example: Writing an Essay
#### 如果考虑直接让AI写文章，可能输出一些很显而易见的东西（Surface level、Obvious facts）
![[Pasted image 20260115125147.png]]
#### 思考作为一个人如何去执行写文章这个task
![[Pasted image 20260115125426.png]]
PS：拆分步骤后注意考虑LLM对这些步骤的可执行性
Q：按照这个步骤的输出可能依旧太浅显同时文章上下文不关联
A：如果作为一个人发现文章出现这些问题会如何修改
#### 将其中steps再拆分
![[Pasted image 20260115125813.png]]
#### 总结
![[Pasted image 20260115130008.png]]
### What building blocks do you have?
![[Pasted image 20260115130721.png]]
### Generation
First-以人的视角思考一个task如何拆分为steps
Second-审视simple step，考虑是否可用Models、Tools解决
Third-如果specific step不可用上述两个模块解决，考虑从人角度出发是否可拆                   分为smaller step，从而用模块解决
##  Lesson 7-Evaluating Agentic AI(evals)
### Look for low-quality outputs
查看输出时发现其中存在竞争对手名字（这种问题在构建并运行前是不会发现的）
![[Pasted image 20260115160728.png]]
### Add an evaluation to track your error
构建key-word list，通过编码统计
![[Pasted image 20260115161146.png]]
这是一种客观标准，而对于更主观的，则可考虑使用LLM作为evaluation standard
### Using LLM as a judge
规定评分标准
![[Pasted image 20260115161513.png]]
PS：但实际上LLM并不擅长这种1-5分的评分标准
### Evaluating Agentic AI
#### [[#Module 1#Add an evaluation to track your error]]
#### [[#Module 1#Using LLM as a judge]]
#### End-to-end
评估整个agent的output quality和组件的output quality
#### Component-level
衡量代理过程中output quality of a single step
#### Examine traces to perform error analysis
检查中间输出（the traces of the LLM）
## Lesson 8-Agentic design patterns
1. Reflection
2. Tool use
3. Planning
4. Multi-agent collaboration
### Reflection
将由你提示LLM找出错误或者运行发现错误的这个过程交由另一个扮演Critic的Agent实施
![[Pasted image 20260115163512.png]]
### Tool use
![[Pasted image 20260115163713.png]]
除了大量工具的提供还可以让LLM本身决定是否使用以及如何使用tools
### Planing
![[Pasted image 20260115163919.png]]
行动顺序，这种行动顺序可由开发者给出也可由LLM自身决定
### Multi-agent collaboration
多模型collaborate完成task，它们分工角色不同
![[Pasted image 20260115164402.png]]
Q：多模型各自扮演的角色难以决定

# Module 2
## Lesson 1-Reflection to improve outputs of a task
### Reflection-humans
![[Pasted image 20260115191306.png]]
### Reflection-Agentic AI
![[Pasted image 20260115191357.png]]
### Reflection to improve code
![[Pasted image 20260115191703.png]]
reasoning model-推理模型
### Reflection with external feedback
![[Pasted image 20260115191852.png]]
PS: 这种方法并不能使LLM绝对正确，但可以使performance获得提升
PS:当LLM获得额外信息后，往往会让它more powerful
## Lesson 3-Why not just direct generation?
### Direct generation(Zero-shot prompting)
![[Pasted image 20260115192946.png]]
一次输入直接生成答案
### Zero, one and few-shot prompting
![[Pasted image 20260115193106.png]]
### Tasks where reflection works better 
![[Pasted image 20260115200143.png]]
### Tips for writing reflection prompts
![[Pasted image 20260115200424.png]]
![[Pasted image 20260115200552.png]]
## Lesson 4-Chart generation workflow
### Ungraded Lab: Chart Generation
> Lab URL: https://learn.deeplearning.ai/courses/agentic-ai/lesson/uz37vtiou/ungraded-lab%3A-chart-generation
利用regex和自定义utils等实现automatically encode和chart generation
## Lesson 5-Evaluating the impact of reflection
### Create a dataset of prompts and answers(Object tasks)
![[Pasted image 20260117181422.png]]
### What about subject tasks?
#### Using an LLM as a judge
![[Pasted image 20260121224903.png]]
![[Pasted image 20260121225149.png]]
Q 1: 即使使用具体措辞去指定评判标准，LLM与人类的判断也可能不同
Q 2: LLM存在位置偏好(bias)，有时无脑选第一个
#### Grading with rubric gives more consistent results
> A: 与其让LLM比较两个输出哪个更好，不如让它根据设定标准进行评分
![[Pasted image 20260121225629.png]]
![[Pasted image 20260121230548.png]]
这里的评分不是指打分，而是如上图中0 or 1的评估
### Generation
![[Pasted image 20260121230809.png]]
## Lesson-6 Using external feedback