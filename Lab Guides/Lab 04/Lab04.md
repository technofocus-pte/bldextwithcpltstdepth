# 实验室 04 - 使用 Gen AI 功能增强房地产copilot

**实验室持续时间** – 80 分钟

**目的：**

在 Copilot for Real Estate
应用程序中实施实体、槽填充和变量使用。通过实施生成式 AI 来增强为 Real
Estate 应用程序创建的 copilot，以提升客户体验。

## 练习 1：使用实体改进 Copilot

Microsoft Copilot Studio
使用实体来了解用户意图。包含许多用于常用信息的预生成实体。您可以针对您的特定目的创建自定义实体。

### 任务 1：查看预生成实体

1.  在 !\!<https://copilotstudio.microsoft.com>!! 并打开代理 **Real
    Estate Booking Service。**

2.  选择 屏幕右上角的 **Settings**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  选择 **Entities** 选项卡。您可以看到预构建实体的列表。

![](./media/image2.png)

### 任务 2：创建属性类型实体

1.  选择 **+ Add an entity**，然后选择 **+ New entity**。

![](./media/image3.png)

2.  选择 **Closed list** 磁贴。

![](./media/image4.png)

3.  输入以下详细信息

    - 名字 - !!Property Type!!

    - 在 List items下输入 item – !!Apartment!! - 选择 **Add**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

4.  进入 !!Condominium!! 在 **Enter item** 字段中，然后选择 **Add**。

5.  进入 !!Duplex!! 在 **Enter item** 字段中，然后选择 **Add**。

6.  进入!!House!! 在 **Enter item** 字段中，然后选择 **Add**。

![](./media/image6.png)

7.  选择 **Apartment** 的 ** + Synonyms**，输入 **!!Flat!!** ,然后选择
    **+** icon 并选择 **Done**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  选择 **House** 的 **+ Synonyms**，输入 **!!Single-family home!!**
    ,然后选择 **+** ** **icon 并选择 ** Done**。

9.  选择 **Condominium** 的 **+ Synonyms**，输入 !!**Townhouse**!!
    ,然后选择 **+** icon 并选择 **Done**。

10. 选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. 选择 **Close**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

### 任务 3：创建卧室数量实体

1.  选择 **+ Add an entity** ，然后选择 **+ New entity** 。

![](./media/image10.png)

2.  选择 **Regular expression （Regex）** 磁贴。

![](./media/image11.png)

3.  输入以下详细信息，然后单击 **Save** 。

    - Name - !!**Number of Bedrooms**!!

    - Pattern - !!**\[1-5\]**!!

![A screenshot of a cell phone AI-generated content may be
incorrect.](./media/image12.png)

4.  选择 **Close**。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image13.png)

5.  关闭 **Settings** 窗格。

![](./media/image14.png)

### 任务 4：使用实体

- 选择 **Topics** 选项卡。选择 **Book a Real Estate Showing** 主题。

![](./media/image15.png)

- 选择 属性问题节点上方的 + icon，然后选择 **Ask a question**。

![](./media/image16.png)

> 3\. 填写以下详细信息。

- **Enter a message** - !!What type of property do you want to see?!!

- **Identify** – 选择**Property Type**

- 选择 **Select options for user** 并选中 Display 所有列表值的
  **Display** 选项。

![](./media/image17.png)

4.  在 **Save user response as** 中选择变量 ，然后输入
    **!!PropertyType!!** 对于 **Variable name**

![](./media/image18.png)

5\. 选择 新问题节点下方的 **+** icon，然后选择 **Ask a question**。

> 6\. 输入以下详细信息，然后单击 **Save** 。

- **Enter a message** - !!How many bedrooms do you need?!!

- **Identify -** 选择 **Number of Bedrooms**

- **Save user response as** - 进入!!NumberofBedrooms!! 对于 **Variable
  name**

![](./media/image19.png)

## 练习 2：创建动作

Microsoft Copilot Studio 可以使用 Power Automate 云端流访问 Microsoft
Dataverse 中的数据

### 任务 1：创建 Power Automate 流以检索属性

1.  从 顶部菜单中选择 **Actions** 选项卡。选择 **+ Add an action**。

![](./media/image20.png)

2.  选择 **+ New action** -\> **New Power Automate flow**。

![](./media/image21.png)

3.  如果出现提示，请登录到 Power Automate。

4.  在右上角，启用切换 **New designer** 。选择 **Save and switch**。

![](./media/image22.png)

5.  选择屏幕左上角的 **Run a flow from Copilot** 并输入 **!!Get
    Property!!** 作为流程名称。

![](./media/image23.png)

6.  选择触发步骤从 **Run a flow from Copilot** ，然后选择 **+ Add an
    input**。

![](./media/image24.png)

7.  选择 **Text** 。

![](./media/image25.png)

8.  输入以下详细信息

    1.  **Input** – !!Bedrooms!!

    2.  **Please enter your input** - !!Number of Bedrooms!!

![](./media/image26.png)

9.  右键单击 流程中两个步骤之间的 + icon，然后选择 **Add an action**。

![](./media/image27.png)

10. 在 **Search** 搜索字段中输入 **!!Dataverse!!**，然后选择查**See
    more** **Microsoft Dataverse connector**。

\![\](./media/image27.png)

11. 选择 **List rows** action。

![](./media/image28.png)

12. 如果系统提示进行身份验证，请选择 **OAuth** 并选择 **Sign in**
    。如果出现提示，请使用您的租户 ID 登录。

![](./media/image29.png)

13. 选择 **Real Estate Properties** 作为表名称。

14. 如果 所有选项未自动列出**，**请选择 **Show all**

15. 进入 !!contoso_bedrooms eq!! 在 **Filter Rows** 字段中。

16. 在 **eq** 旁边使用 **spacebar **以确保在空格后添加值。使用 **Dynamic
    content** 选择 **Bedrooms** 参数，然后选择 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

17. 选择 **Respond to Copilot** action，然后选择 **+ Add an output**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

18. 选择 **Text**。

19. 输入以下详细信息

    - **Enter a name** - !!PropertyId!!

    - **Enter a value to respond with** - 选择 **Insert expression**
      并输入以下表达式:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_realestatepropertyid'\]!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

20. 选择 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

21. 从 !\!<https://make.powerapps.com>!!,打开表 **Real Estate
    Property**。导航到其列 Property Name（这可能是 Real Estate Property
    或使用 Copilot 创建时略有不同）\>编辑列 \> 高级选项。查找 **Logical
    name** 的值。它应该类似于
    **contoso_newcolumn**。也可能略有不同。在本地保存 contoso\_
    后存在的部分 。如果 Logical name （逻辑名称） 为
    **contoso_newcolumn**，请记下 **newcolumn** 以供下一步使用。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

22. 返回 Power Automate 流页面，选择 **+ Add an output**。

23. 选择**Text**。

    - **Enter a name** - !!PropertyName!!

    - **Enter a value to respond with** - 选择 **Insert expression**
      并输入以下表达式:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]!!

将上述表达式中 **contoso_propertyname** 中的 **propertyname** 替换为
this（**newcolumn）** 之前的步骤中保存的值。

::: secondary 此值替换需要完成，因为此列的 Logical name
不是标准值，我们必须根据 Table 中的值进行检查和更新. :::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

24. 选择 **Settings** 。确保 **Asynchronous Response** 设置为 **Off**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

25. 选择 **Save draft** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

26. 保存后，选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

27. 关闭 Power Automate 选项卡。

### 任务 2：添加用于检索属性的 Copilot作

1.  返回 Copilot Studio 页面，选择 **Refresh**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

2.  选择 **Get Property** 流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  选择 **Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

4.  选择 **Topics** 选项卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  选择 **Book a Real Estate Showing** 主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

6.  选择 **How many bedrooms do you need question?** 下方的 **+ icon**
    node 并选择 **Add an action**。选择 **Get Property** 流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  为 **Bedrooms** 输入参数选择 **NumberofBedrooms** 变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

8.  选择 **Which property do you want to see?**  问题节点中的 **three
    dots** ，然后选择**Delete**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  选择 作节点下的 + icon，然后选择 **Send a message** 。

10. 填写以下详细信息

    - **Enter a message** - enter !!Property!!

    - 选择 **Insert variable** 图标，然后选择 **PropertyName** 变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

11. 选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

12. 保存后，选择 **Publish ** ，然后选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

13. 单击 **Publish** 确认对话框中的 Publish。

![A close-up of a white background AI-generated content may be
incorrect.](./media/image50.png)

### 任务 3：创建 Power Automate 流以进行预订

1.  选择 **Actions** 选项卡，然后选择 **+ Add an action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

2.  选择 **+ New action** -\> **New Power Automate flow**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

3.  选择屏幕左上角的 **Run a flow from Copilot** 并输入 **!!Booking
    Request!!** 作为流程名称。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

4.  选择触发步骤从 **Run a flow from Copilot** ，然后选择 **+ Add an
    input -\> Text**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

5.  输入以下详细信息

    - Input - !!**PropertyId**!!

    - Please enter your input **-** !!**Property**!!

6.  选择 **+ Add an input -\> Text**

    - Input - !!**ViewerName**!!

    - Please enter your input **-** !!**Viewer Name**!!

7.  选择 **+ Add an input -\>** **Text**.

    - Input - !!**ViewerEmail**!!

    - Please enter your input **-** !!**Viewer Email**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  选择 流中两个步骤之间的 **+** icon，然后选择 **Add an action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

9.  在 **Search** 字段中输入 **!!Dataverse!!**，然后选择 **See more**
    Dataverse connector。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

10. 选择 **Add a new row** action。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

11. 选择 **Booking Requests** 作为表名称。

12. 进入 **!!Copilot booking!!** 在 **Booking Name** 字段中。

13. 选择 **Show all**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

14. 进入 !!contoso_bookingrequests()!! 在 **Property （Real Estate
    Properties）** 字段中，将光标移动到括号内，并使用 **Dynamic
    content**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

15. 选择 **PropertyId** 参数。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

16. 使用 **Dynamic content** 为 **Viewer Name** 字段选择 **ViewerName**
    参数 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

17. 使用 **Dynamic content** 为 **Viewer Email** 字段选择
    **ViewerEmail** 参数 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

18. 这些参数现在看起来与下面屏幕截图中的参数类似。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

19. 选择  **Respond to Copilot** 作。选择 **Settings** 并确保
    **Asynchronous Response** 设置为 **Close**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

20. 选择 **Save draft**。![A screenshot of a computer AI-generated
    content may be incorrect.](./media/image67.png)

21. 保存后，选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

22. 关闭 Power Automate 选项卡。

### 任务 4：添加用于创建预订请求的 Copilot作

1.  返回 Copilot Studio 页面，选择 **Refresh**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

2.  选择 **Booking Request** 流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

3.  选择 **Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

4.  在 Review inputs and outputs 中选择 **Next** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

5.  在 **Review and finish** 屏幕中选择 **Finish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

6.  选择 **Topics** 选项卡，然后选择 **Book a Real Estate Showing**
    主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

7.  选择 **What date and time do you want to see the
    property?** 节点下方的 + icon，然后选择 **Add an action**。

8.  选择 **Booking Request** 流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

9.  为 **PropertyId** 输入参数选择 **PropertyId** 变量。

为 **ViewerName** 输入参数选择 **Name** 变量。

为 **ViewerEmail** 输入参数选择 **EmailAddress** 变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

10. 选择 作节点下方的 + icon。选择 **Topic management，**然后选择  **Go
    to another topic **并选择 **End of conversation**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

11. 选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

12. 保存后，选择 **Publish** ，然后在 确认对话框中再次选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 练习 3：测试代理

### 任务 1：测试代理并发出预订请求

1.  选择 屏幕右上角的 **Test** 按钮以打开测试面板。选择
    屏幕右上角的测试面板顶部的 **three dots**。选择 **Track between
    topics**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  当 **Conversation Start** 消息出现时，您的代理将启动对话。

3.  作为响应，输入您创建的主题的触发短语:

!!I want to book a real estate showing!!

4.  Copilot 回答说：**What is your name?"** 问题。

5.  输入您的姓名。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image82.png)

6.  然后在系统提示输入电子邮件时输入您的电子邮件。输入详细信息后，将提示一个问题，询问信息是否正确，以及选择
    **Yes** 或 **No** 的选项。选择 **Yes**。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image83.png)

7.  选择 **House** 作为属性提示的类型。

8.  进入 !!**2**!! 以获取 Number of Bedrooms 提示。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image84.png)

9.  进入 !!Tomorrow 2:00 PM!! 到 **What date and time you want to see
    the property？** 提示。

10. 选择 **Yes** 到 Did **that answer your question？** 提示。

11. 选择任意评级。

12. 对 **Can I help with anything else?** 选择 **No** 提示。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image85.png)

### 任务 2：验证预订请求

1.  导航到 Power Apps 门户
    !\![**https://make.powerapps.com**](https://make.powerapps.com)!!.

2.  在左侧导航窗格中，选择 **Tables** ，然后选择 **Custom**。

3.  选择 **Booking Request** 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

4.  在 ** Booking Request columns and data **下，您应该会看到 Copilot
    预订请求现已创建。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

## 练习 4：设置 Generative AI

在本练习中，您将学习如何使用 Generative answers 功能来改进 Copilot
的响应。

### 任务 1：启用 Generative AI

1.  使用您的租户凭据登录 Copilot Studio
    !\!<https://copilotstudio.microsoft.com>!! 如果尚未登录。

2.  选择代理 **Real Estate Booking Service**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

3.  选择 屏幕右上角的 **Settings。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

4.  选择 **Generative AI** 选项卡。

在 **How should your copilot decide how to respond**下选择
**Generative(preview) **。

对于 **how strict should the content moderation be?**请选择 **Medium**。

选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

5.  **关闭** Settings 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### 任务 2：启用知识

1.  单击 **Overview** 选项卡。

2.  验证是否在 Knowledge 部分启用了 general knowledge。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

### 任务 3：从网站添加知识

1.  选择 **Knowledge** 部分下的 **+ Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

2.  选择 **Public websites** 磁贴。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

3.  进入公共网站链接
    !\!<https://create.microsoft.com/templates/real-estate>!! 选择
    **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

4.  给名字 !!Real Estate Website!! 在 Name 字段中，然后选择 **Add** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

### 任务 4：从 Dataverse 添加知识

1.  选择 **knowledge** 选项卡。选择 **+ Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

2.  选择 **Dataverse(preview)** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

3.  选择 **Real estate Property** 表，然后选择 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

4.  在下一个屏幕中预览数据，然后选择 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

5.  查看详细信息，然后单击 Review and finish 屏幕中的 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

### 任务 5：从文件添加知识

1.  从 **Knowledge** 选项卡中，选择 **+ Add knowledge**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

2.  在 **Upload files** 部分下，选择 **click to browse**，然后浏览以在
    **C：\LabFiles SummitRealtyCaseStudy.docx** 找到文件并选择它。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

3.  选择 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

:::danger
**Important：**文件上传将完成，索引将需要一些时间才能完成。检查
Knowledge 选项卡中的状态，以确保文件可用。 :::

### 任务 6：在系统回退主题中使用生成式答案

1.  选择 **Topics** 选项卡，然后选择 **System**。选择 **Fallback**
    主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

2.  选择 消息节点中的 **three dots**，然后选择 **Delete** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

3.  选择 Condition 节点下的 **+** icon，选择 **Advanced**，然后选择
    **Generative answers**。

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image107.png)

4.  选择 **Input** 字段，在 **Select a variable** 窗格中选择
    **System**。从中选择 **Activity.Text**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

5.  在 **Data sources**下选择 **Edit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

6.  选择 **Search only selected sources**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

7.  选择 **SummitRealtyCaseStudy** 文档。取消选择 **Allow the AI to use
    its own general knowledge**。选择 **Medium** 作为 **Content
    moderation**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

8.  选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

### 任务 7：配置安全性

1.  选择 **Overview** 选项卡。

2.  选择 屏幕右上角的 **Settings**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

3.  选择 **Security** 选项卡，然后选择 **Authentication** 磁贴。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

4.  选择使用 Microsoft 进行身份验证 **(Entra ID authentication in Teams
    and Power App)。**

5.  选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

6.  选择 **Save**。

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image116.png)

7.  选择 **Close**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

8.  选择 **Overview** 选项卡。

9.  选择 **Publish**，然后在对话框中再次选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### 任务 8：测试代理的知识

1.  选择 屏幕右上角的 **Test** 按钮以打开测试面板。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  选择 **Activity map** 如果尚未选择。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  选择 **Refresh** 按钮 测试 面板 **Start a new conversation**。

4.  输入 !!What is Summit Realty group?!! 然后点击 **Send**。

5.  您将从上传的文件获得响应，如下面的屏幕截图所示，因为它已添加为要在
    Fallback 主题中查找的知识源。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

**总结：**

在本实验中，我们学习了

- 使用实体和槽填充

- 实施 Flow actions

- 向代理添加知识

- 启用 Generative AI

 
