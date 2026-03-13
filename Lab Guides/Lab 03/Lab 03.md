# 实验室 - 构建具备知识接地和实时连接器的智能代理架构

**介绍**

现代用户期望的回答是智能的、符合上下文的，超越简单的关键词匹配。本实验室将引导您创建一个智能代理，能够跨多个知识源推理并执行实时作，以提供全面、准确的答案。

**目标**

在这个实验室里，你将打造一个智能助手，超越简单的问答，提供基于上下文的多部分回答。实验结束时，你会明白的

利用对话创建体验创建一个智能代理。配置座席语气、行为和指令以体现你的品牌形象。加入像维基百科这样的公共网站作为事实基础的知识来源。关闭常识以减少幻觉并确保准确性。

## 任务1：创建一个新的代理并添加知识

利用 Copilot Studio
的对话式设置体验，创建带有自定义说明和维基百科知识集成的 Nova AI。

1.  打开浏览器，进入 +++copilotstudio.microsoft.com+++
    并用你的凭证登录。

2.  选择 **Dev One** 环境。

3.  在主页中，选择 **Create agent**。

    ![](./media/image1.png)

4.  创建代理后，选择“**Detail**”旁边的“**Edit**”。

    ![](./media/image2.png)

5.  输入以下信息并选择 **Save**。

    - 名称 - +++Researcher agent+++.

    - 描述 - +++Answers multi-part questions by combining historical
      facts, biographical data, and real-time information like weather.
      Ideal for deep research, exploration, and knowledge synthesis+++

    ![](./media/image3.png)

6.  在“**Instructions**”下输入以下内容，然后选择“**Save**”。

    +++You should answer complex questions using verified public information and real-time lookups like weather or conversions. You should give clear, concise answers and handle multiple questions one at a time. You must not speculate, share unverified or sensitive information, or compare products or companies. You should communicate clearly and professionally, using a friendly tone and light emojis when appropriate.+++

    ![](./media/image4.png)

7.  向下滚动，选择 **+ Add knowledge**以添加知识来源。

    ![](./media/image5.png)

8.  从列表中选择**“Public Website**”选项。

    ![](./media/image6.png)

9.  在下一个屏幕中选择“**Add**”，然后选择“**Add to agent**”。

    ![](./media/image7.png)

    ![](./media/image8.png)

10. 接下来，你需要关闭常识以减少幻觉。从右上角选择 **Settings** 。

    ![](./media/image9.png)

11. 将“Knowledge”部分下的“**Use general knowledge**”选项切换为 **off**
    状态。

    ![](./media/image10.png)

12. 在测试面板输入以下消息，点击 **Send** ，观察输出。

    +++Write a draft email to request refund from a toaster that is not working properly (bread keeps burning)+++

    ![](./media/image11.png)

    ![](./media/image12.png)

## 任务2：添加天气连接器

在此任务中，您将添加一个天气连接器，以实现实时数据检索和生成式编排测试。确保代理只提供基于事实、受控的响应，同时能够执行实时作，如天气查询，以获得全面、多步骤的答案。

1.  从顶部菜单选择**“Tools**”标签。

    ![](./media/image13.png)

2.  在搜索框中输入 +++MSN Weather+++，并选择 **Get current weather**。

    ![](./media/image14.png)

3.  选择“**Not connected**”消息旁边的下拉菜单，然后选择“**Create new
    connection**”。接着，在下一个屏幕中选择“**Create**”。

    ![](./media/image15.png)

    ![](./media/image16.png)

4.  选择 **Add and configure** ，将工具添加到代理中，并按需配置。

    ![](./media/image17.png)

5.  添加后，选择 **“Additional details**”。

    ![](./media/image18.png)

6.  在“Credentials to use”中，选择 **Maker-provided credentials**。

    **注意：**
    使用Maker提供的凭据时，代理的终端用户不会被提示使用自身上下文和连接来连接服务。而是利用配置代理者的上下文和连接。-
    仅在不需要用户特定数据的作中使用作者认证，因为使用他人凭证可能会暴露数据外泄风险。-
    在基于角色的访问场景中使用用户认证- 始终审查认证选择的安全影响

    ![](./media/image19.png)

7.  在输入、**Inputs**, **Units**, -> **Fill using** ->，选择 **Custom value**，然后选择**Metric**。

    ![](./media/image20.png)

8.  在“**Inputs**”下，对于“**Location**”，将“**Fill using to Dynamically
    fill with AI**”，然后选择“**Customize**”来设置描述。

    ![](./media/image21.png)

9.  设置描述如下，然后选择 **Save**。

    +++The location for the weather query. Valid inputs are City, State, Country. Always include city and country, and state only for locations where appropriate (e.g., in the US)+++

    ![](./media/image22.png)

    ![](./media/image23.png)

10. 用这个复杂的问题来测试你的增强型特工:

    +++Who is the current CEO of the company that owns GitHub? Where did they earn their MBA? What's the average rent for a one-bedroom apartment near that campus? What's the air quality index in that area today?+++

    ![](./media/image24.png)

11. 注意生成式编排如何执行多次搜索并触发天气连接器，从而提供全面的答案

    ![](./media/image25.png)

## 任务3：微调你的AI助手，使对话更顺畅

定制系统主题以提升交互性，提供更流畅的用户体验。

在本部分，您将自定义内置系统主题，以改善用户互动，打造超越知识源的更无缝体验。

定制助理的欢迎信息使其更具吸引力，添加建议启动提示以有效引导用户，并完善如Escalate等系统主题，确保其符合组织需求。

1.  从顶部菜单中选择 **“Topics**”。

    ![](./media/image26.png)

2.  在“**System**”下选择“**Conversation Start**”主题。

    ![](./media/image27.png)

3.  在主题的 **消息** 节点中，输入以下消息。

    +++Hi there! I'm Researcher agent, your intelligent assistant for deep research and discovery. I can break down complex questions and combine insights from historical facts, biographies, and real-time data like the weather. What are you curious about today?+++
    
    ![](./media/image28.png)

4.  仍在同一节点中，选择 **+ Add** -> **Quick reply**。

    ![](./media/image29.png)

5.  请补充以下问题。

    +++What caused the fall of the Roman Empire?+++

    ![](./media/image30.png)

6.  同样地，再加两个。

    +++Who is the current CEO of the company that owns GitHub? Where did they earn their MBA? What's the average rent for a one-bedroom apartment near that campus? What's the air quality index in that area today?+++

    +++What's the temperature in the city that hosted the last Olympic Games?+++

    ![](./media/image31.png)

7.  添加后，选择 **Save** 以保存主题。

    ![](./media/image32.png)

8.  定制升级体验。选择 **Topics** -> **System** -> **Escalate**。

    ![](./media/image33.png)

9.  将文字更新为以下内容，这样更有意义地解除最终用户的屏蔽，并选择
    **Save**。

    +++I'm sorry, but I can't seem to be able to help you. I recommend reaching out to our [Microsoft Copilot Studio community] (https://aka.ms/CopilotStudioCommunity) or submitting a [support request] (https://learn.microsoft.com/en-us/power-platform/admin/get-help-support).+++

![](./media/image34.png)

## 任务4：让你的经纪人公开并发布到演示网站

在本部分，你将移除认证，使代理对公众开放，然后发布到演示网站进行测试和共享。由于Researcher代理只提供一般信息，不处理私人数据，你需要关闭身份验证以实现无缝的用户体验，并将认证发布到演示网站收集反馈，然后再部署到真实网站。

1.  进入 **Settings** 。

    ![](./media/image35.png)

2.  选择“**Security** -\> **Authentication**”。选择“**No
    authentication**”，然后选择“**Save**”。

    ![](./media/image36.png)

3.  在确认提示中**Save**保存。

    ![](./media/image37.png)

4.  你现在可以关闭设置面板了。

    ![](./media/image38.png)

5.  选择 **Publish** 以使你的更改上线。

    ![](./media/image39.png)

6.  在确认对话框中选择**Publish**。

    ![](./media/image40.png)

7.  发布完成后，你会收到成功通知。

    ![](./media/image41.png)

8.  现在，从 顶部菜单选择“**Channels**”。

    ![](./media/image42.png)

9.  从可用频道列表中选择**Demo website**。

    ![](./media/image43.png)

10. 输入欢迎信息为 +++Welcome to your demo website+++，然后选择
    **Save**。

    ![](./media/image44.png)

11. 点击 **“Open demo website** ”即可打开您的网站。

    ![](./media/image45.png)

12. 你现在可以与你的代理人互动了。

    ![](./media/image46.png)

## 摘要

在这个实验室里，你们成功交付了一个面向公众的智能代理，:

- 解答复杂且多部分的研究问题

- 使用经过验证的公开知识和实时连接器

- 通过受控知识源减少幻觉

- 提供精致且用户友好的对话体验

- 已部署并通过在线演示网站访问

本实验室演示如何设计、增强并发布一款生产**准备的智能代理**，超越简单的问答，提供可信、实时且具上下文感知的洞察。
