## Introduction

- One way to avoid the large penalty for a change during final production is to make the right design decision in the first place and avoid the need to change later. That was the Detroit approach. Toyota and Honda had discovered a different way to avoid the penalty of incorrect design decisions: **Don't make irreversible decisions in the first place; delay design decisions as long as possible, and when they are made, make them with the best available information to make them correctly.** This thinking is very similar to the thinking behind just-in-time manufacturing, pioneered by Toyota: **Don't decide what to manufacture until you have a customer order; then make it as fast as possible.**

- **Principles (原理、原则)** are guiding ideas and insights about a discipline, while **practices** are what you actually do to carry out principles. Principles are universal, but it is not always easy to see how they apply to particular environments. Practices, on the other hand, give specific guidance on what to do, but they need to be adapted to the domain. Practices for one domain will not necessarily apply to other domains. Principles, however, are broadly applicable across domains as long as the guiding principles are translated into appropriate practices for each domain. 
原则是通用的规则，但是一般都是指导性的，具体在不同的领域实施起来肯定要有不同的“落地”方案，即为practice. 所以不能从其他领域生搬硬套practice.

### Guided Tour
seven lean principles and thinking tools for translating each principle into agile practices
- Eliminate waste.

- Amplify learning

- Decide as late as possible
>  In the face of uncertainty, most economic markets develop options to provide a way for investors to avoid locking in decisions until the future is closer and easier to predict. Delaying decisions is valuable because better decisions can be made when they are based on **fact, not speculation**.

- Deliver as fast as possible
> Without speed, you cannot delay decisions. Without speed, you do not have reliable feedback.

- Empower (授权) the team
> 1. Top-notch (一流的) execution lies in getting the details right, and no one understands the details better than the people who **actually do the work**. 
> 2. Lean practices use **pull** techniques to schedule work and contain local signaling mechanisms so workers can let each other know what needs to be done. In lean software development, the pull mechanism is an agreement to deliver increasingly refined versions of working software at regular intervals. Local signaling occurs through visible charts, daily meetings, frequent integration, and comprehensive testing.

- Build integrity in
> 1. Software with integrity has a coherent architecture, scores high on usability and fitness for purpose, and is maintainable, adaptable, and extensible. 
> 2. A system is perceived to have integrity when a user thinks, *"Yes! That is exactly what I want. Somebody got inside my mind!"* 

- See the whole
> One of the most intractable problems with product development is that experts in any area (e.g., database or GUI) have a tendency to maximize the performance of the part of the product representing their own specialty rather than focusing on overall system performance. Quite often, the common good suffers if people attend first to their own specialized interests. When individuals or organizations are measured on their specialized contribution rather than overall performance, suboptimization is likely to result. 人们容易只局限于自己所负责或者擅长的“片面”，而不是从全局角度考虑整个系统，从而会导致选择一个次优解作为解决方案。

## 消除浪费
Waste: anything that does not create value for a customer is waste.
- A part that is sitting around waiting to be used is waste. 
- Making something that is not immediately needed is waste. 
- Motion is waste. 
- Transportation is waste. 
- Waiting is waste. 
- Any extra processing steps are waste. 
- defects are waste.

**Eliminating waste is the most fundamental lean principle, the one from which all the other principles follow.**

### Tool 1: Seeing Waste
Every step in the waterfall process except **analysis and coding** is waste  

**How to find waster?**  
Good candidates include everything your organization does to develop software that is not analysis or coding. Do all of those processes really add value for customers?

Table The Seven Wastes  

| The Seven Wastes of Manufacturing  | The Seven Wastes of Software Development
| - | -: 
| Inventory (库存) |  Partially Done Work
| Extra Processing |  Extra Processes
| Overproduction |  Extra Features
| Transportation |  Task Switching
| Waiting |  Waiting
| Motion |  Motion
| Defects | Defects

#### 部分完成的工作
- 部分完成的工作有可能不会进到最终产品中，直接被遗弃
- 部分完成的工作可能阻碍其他功能的完成
- 部分完成的工作由很多不确定性，如是否解决用户问题

#### 额外的流程
Paperworks  
- Paperworks that no one cares to read adds no value.
- 纸面工作占用人力、降低响应时间、有可能被遗弃，是否对客户产生了价值？
- 如果非要进行paperwork，记住3条规则: Keep it short. Keep it high level. Do it off line.
- 如果paperwork是法规所必须的，则使文档让用户和开发者更容易理解和验证的活动是有意义的
- 验证文档是否有意义的方法：看是否有人在等待着这个文档，如果有，则此文档**可能**会add value.
- Dealy documenting the details of desired features until the iteration in which they are implemented.

#### 额外的features
系统中的任何一行代码都需要维护成本、都需要compile, test等，添加现在不用的代码就是浪费。

#### 任务切换
任务切换会降低生产效率。

#### 等待
- 软件开发过程中一个最大的浪费就是等待事情发生
- Delays in reviews and approvals

#### 移动
- 为了找相关的人员，如测试找开发，而移动一段较长距离，则是一种浪费。开发是一项需高度专注的工作，打断后需要时间再次集中精力。
- 建议相关的人员坐在一个区域，方便互相沟通讨论
- 除了人之外，产品、文档等的“移动”也可能造成浪费：它移到下一个人手中时是否包含了所有所需的信息？文档的作者会有**很多隐含的信息**难以通过文字传递给文档的接收者。

#### 缺陷
如何度量缺陷所造成的浪费：缺陷多久未被发现？3分资就发现了的严重缺陷不是一个大的浪费，好几周都没有发现的minor defect是更大的浪费。The way to reduce the waste due to defect is to test immediately, integrate often, and release to production ASAP.
