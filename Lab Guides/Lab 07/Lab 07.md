# Lab 07 – 创建个性化的购物助手

## 目标

本实验室的目标是为 Contoso Electronics 创建个性化购物代理。这将使用
Dataverse
表作为代理的知识源。它将根据买家的最新购物情况向他们推荐商品类别，并在整个购物体验中为他们提供帮助。

## 练习 1 - 创建 Dataverse 表

在本练习中，您将在 Dataverse 中创建表来存储 **Customer**、 **Product**
和 **Order** 详细信息。

1.  登录 +++https://make.powerapps.com+++
    使用您的管理员租户凭证，然后选择 Dev One 作为您的环境。从 eft
    导航窗格中选择 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  选择 **+ New table 旁边的下拉列表** ，然后选择 **其下的 Create new
    tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  选择 **Import an Excel file or .csv** 以创建新表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  在“导出 Excel”或“导出 .CSV 文件中，选择 **Select from device**
    选项。

![A screenshot of a file AI-generated content may be
incorrect.](./media/image4.png)

5.  从 **C：\Labfiles** 中，选择 excel – **Customers.xlsx**。选择
    **Import** 以从跟踪器导入数据并创建表格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  该表是使用跟踪器中的数据创建的。

7.  此处，该表名称为 **Customer
    Record**。在您的案例中，名称可能略有不同，因为它是自动生成的。记下它，并在整个实验室执行过程中使用适当的
    Table name。

8.  单击表，然后选择 **View data** 以查看添加到表中的数据。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  选择**Save and exit**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

10. 单击 确认对话框中的 **Save and exit。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. 重复 2 到 10 的步骤两次，一次使用跟踪链接 **Product Catalog.xlsx**
    创建表格，下次使用 **Orders.xls**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

1.  现在，我们将有 3 张表，

    - Customer Record

    - Product Record

    - Orders

## 联系2 – 创建 Shopping 代理

在本练习中，您将创建一个 Shopping 代理，该代理将协助客户在 Contoso
Electronics 中购物。

### 任务 1 – 创建代理

使用 Copilot 在 Copilot Studio 中创建代理。与 Copilot
聊天，并就代理的设计和行为提供说明，以便 Copilot 为您创建代理。

1.  登录 Copilot Studio： +++https://copilotstudio.microsoft.com/+++
    并选择 **Dev One** 环境。

![](./media/image12.png)

2.  选择 **代理** ，然后单击 **+ 新建代理**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  在聊天中输入以下内容并发送。

+++Create an agent that will assist the customers in shopping with
Contoso Electronics. Name it as "Shopping agent".+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  输入 +++Help the users in finding products and their prices, give
    personalized suggestions and track order delivery.+++ 并按 **Enter
    键**.

![](./media/image15.png)

5.  输入以下附加说明。

+++Maintain a polite tone+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  点击 **Create** 以创建 **Shopping agent**.

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image17.png)

7.  代理已设置完毕。这可能需要几分钟时间。代理准备就绪后，它将显示在
    Copilot Studio 中，如下面的屏幕截图所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

### 任务 2 – 添加知识

向代理添加知识使其以这些知识资源为基础，使其能够更有效地回答用户查询。在此任务中，您将把在前面的练习中创建的
Dataverse 表作为知识源添加到此代理。

1.  输入 +++What is the status of the order o1001?+++ 在 Test （测试）
    窗格中.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image19.png)

2.  响应将类似于下面的响应，因为代理没有任何相关信息。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image20.png)

3.  现在，我们将向代理添加 knowledge source. 在 代理的主页上，选择
    **Knowledge** 部分**下的** Add Knowledge.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

4.  从 **可用选项列表中选择** Dataverse。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

5.  搜索+++order+++, 选择 **Order Record** 表，然后单击 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  选择 **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  添加数据源后，请等待几分钟，然后再次测试代理。

8.  一旦 **Order Record** 在 Knowledge 部分**下变为** Ready, 在 Test
    （测试） 窗格中提出相同的问题。

现在，您可以看到代理从数据库中检索信息并将其提供给用户。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

### 任务 3 – 创建实体

1.  从代理的 Home 屏幕**中选择** Settings 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

2.  从 **左侧窗格中选择** Entities。选择 **Add an entity -\> + New
    entity**

![](./media/image27.png)

3.  选择 **Closed list**.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image28.png)

4.  输入以下详细信息。

名称 - +++Laptop+++

描述 - +++Contains products under Laptop category+++

在 List items （列表项**） 下**，输入 +++Apple MacBook Air M3+++
，然后单击 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

5.  同样，添加以下项目，然后选择 **Save （保存**）。

+++Dell XPS 13 Plus+++

+++HP Spectre x360 14+++

+++Lenovo ThinkPad X1 Carbon Gen 12+++

+++Asus ROG Zephyrus G14+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

6.  现在，对以下数据重复步骤 2 到 5。

Name - +++Desktop+++

Description - +++Contains products under Desktop category+++

Under **List items**, enter +++Apple iMac+++ and click on **Add**.

7.  要添加到列表中的其他项目，

+++Microsoft Surface Studio 2+++

+++HP Envy Desktop+++

+++Dell Inspiron Desktop+++

+++Lenovo IdeaCentre AIO 5i+++

8.  同样，对以下数据重复步骤 2 到 5。

Name - +++Tablet+++

Description - +++Contains products under Tablet category+++

Under **List items**, enter +++Apple iPad Pro+++ and click on **Add**.

9.  要添加到列表中的其他项目，

+++Samsung Galaxy Tab S9 Ultra+++

+++Microsoft Surface Pro 10+++

+++Lenovo Tab P12 Pro+++

+++Apple iPad Air+++

## 联系 3 – 创建 Topic 和代理流程并设计代理

设计主题是创建代理中非常重要的部分，因为它处理如何回答用户问题背后的逻辑以及细节的流程将如何。

### 任务 1 – 编辑对话开始主题

Conversation Start
主题是测试代理时要调用的第一个主题。默认情况下，它是您在 Copilot Studio
中创建的任何代理中可用的系统主题。现在，您将编辑此主题以继续来自代理的问候消息的对话。

1.  在 代理的 Overview 页面中，从 顶部菜单栏中选择 Topics 选项卡。选择
    **System** 以查看 System 主题列表。从列表中选择 Conversation Start
    主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  在现有 Message 节点后，添加 **Question 节点**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  输入以下消息，

+++Welcome to Contoso Electronics. Please enter your **Phone number** to
proceed.+++ ，然后在 **Identity** 下选择 **User's entire response**
。单击 **Save user response as** field **下的** Var1。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

4.  重命名 **Var 1** 到 +++MobileNumber+++ 并选择 **Global （全局** ）
    以跨主题使用它，然后选择 **Save （保存**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

### 任务 2 – 创建主题以处理 Customer details

1.  在代理的 Overview （概述） 页面中，从顶部菜单栏中选择 Topics
    （主题） 选项卡。选择旁边的下拉列表 **Add a topic -\> From blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  将代理命名为 +++Customer Details+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  选择 **Change trigger** 并选择 **It’s redirected to** 作为触发器。

![Screens screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

4.  选择 **Save** 以保存主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

### 任务 3 – 创建 Agent 流以获取客户的详细信息

在此任务中，您将创建一个代理流程，将客户输入的电话号码作为输入传递给该流程，并设计流程以检查用户是否存在，并检索信息并将详细信息返回给代理。

1.  在 Trigger 节点下，添加一个节点，选择 **Add a tool** -\> **New Agent
    flow**.

![](./media/image39.png)

2.  代理流程设计器随即打开。选择 **Save draft** 以保存流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  选择 **Overview** 从顶部菜单中，单击 **Edit （编辑** ）
    并输入流的名称 +++GetCustomer+++. 然后选择 **Save**. ![A screenshot
    of a computer AI-generated content may be
    incorrect.](./media/image41.png)

4.  再次导航到 **Designer （设计器**） 选项卡以设计流程。选择节点
    **当代理调用流时**，然后选择 **+ Add an input**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  选择 **Text**.

![](./media/image43.png)

6.  将输入为 +++Phone number+++，然后折叠 **Parameters** 选项卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  单击 **Add an action** between the 2 nodes in the flow.搜索 +++List
    rows+++ ，然后选择 **Microsoft Dataverse** 下的 列出行**作**。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

8.  将连接名称输入为 +++Dataverse+++，然后单击 **登录**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  使用您的管理员租户凭据**登录**，并在 **出现提示时单击** Allow access
    。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. 导航到 PowerApps，网址为 +++https://make.powerapps.com/+++ 并打开
    **Customer Record** 表。单击 **Mobile number**
    字段旁边的下拉列表，然后选择 **Edit column**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. 向下滚动和下方 **Advanced options**, 有一个名为 **Logical name**
    的字段。在记事本中记下它的值。

**重要:** 每个字段在 Dataverse 中都有一个关联的逻辑名称。在 Agent
流中使用它时，您只需为所有字段指定逻辑名称。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. 在这种情况下，对于 Phone number （电话号码），它是
    **cr6dd_mobilecontact**。记下它

13. 导航回 Copilot Studio – 代理流程选项卡。打开 Getcustomer
    流程，然后选择列出 **行** 作。

14. 在 Filter rows （筛选行） 下，输入 **\<Logical name of Mobile
    number\> eq ' '**.将 **\<Logical name\>**
    替换为您在前面的步骤中检索到的值。将光标保留在引号内，并添加 Phone
    number – dynamic 变量。

在这种情况下，它将cr6dd_mobilecontact **eq 'Phone number'**

![](./media/image50.png)

![](./media/image51.png)

15. 在 List rows 节点下，添加 **Condition** 节点。

![](./media/image52.png)

16. 输入 **/** 并选择 **Insert expression**。

![](./media/image53.png)

17. 输入+++length(outputs('List_rows')?\['body'\]?\['value'\])+++
    ，然后选择 **Add**.这将检查 List rows 是否返回值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

18. 点击 **Add an action** 在 添加的条件的 True 分支下，然后添加新的
    **Condition** 节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

19. 输入 +++not(empty(first(outputs('List_rows')?\['body/value'\])?\[
    cr6dd_lastpurchasedproduct '\]))+++ 在 Condition 的 function area
    中。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

> **重要** – 确保将 **cr6dd_lastpurchasedproduct** 替换为 **Customer
> Record** 表中**的 Recent Products Purchased** 字段 **的**逻辑名称
>
> ![](./media/image58.png)

20. 将条件设置为 **等于 true**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

21. 在 Condition1 的 **True** 路径**下添加新作** ，然后选择 **Respond to
    the agent** 节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

22. 选择添加的 **Respond to the agent （响应代理） 节点** 并将其重命名为
    +++If the customer has made a previous purchase+++ 并选择 **+ Add an
    output**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

23. 选择 **Text**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

24. 进入 +++Customer ID+++ 作为名称，然后单击 **Insert expression**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

25. 输入
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
    +++ **cr6dd_customeridentifier** 是 Customer Record 表的 Customer ID
    的逻辑名称。 **将其替换为**您的值。

26. 选择 **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

27. 同样，将以下输出变量和表达式添加到每个变量中。对于每个变量，请确保将逻辑名称替换为您的变量。

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_lastpurchasedproduct'\]+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

28. **Respond to the agent （响应代理）** 节点将具有 3
    个输出变量，如下面的屏幕截图所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

29. 在 Condition1 **节点的** False **路径**下添加 Respond to agent
    节点。将其重命名为 +++If the customer has not made a previous
    purchase+++. 点击 **+ Add an output**.

![](./media/image68.png)

30. 输入以下输出变量，将列逻辑名称替换为相应列的逻辑名称。

- +++Customer ID+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
  +++

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ - +++’1’+++

31. False **路径下的 Respond to the agent** 节点
    将类似于下面屏幕截图中的节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

32. 现在，在 Condition 节点的 **False 路径下添加一个** Respond to the
    agent **节点** ，将其重命名为 +++If the customer does not exist+++
    and add outputs to it as below.

- +++Customer ID+++ - +++’1’+++

- +++Customer Name+++ - +++’1’+++

- +++Product Category+++ - +++’1’+++

![](./media/image70.png)

33. **GetCustomer** 流将类似于下面屏幕截图中的流。

![](./media/image71.png)

34. 右键单击 **流末尾作为常见**代理的 Respond to the agent
    （响应代理），然后选择 **Delete （删除**） 将其删除。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

35. 选择 **Save Draft** 以保存实验室。保存后，单击 **Publish （发布** ）
    以发布流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

### 任务 4 – 创建代理流程以添加客户

在此任务中，您将创建一个代理流，以便在客户是新客户时将新客户添加到
Dataverse 中。

1.  从 **Agent flows** 选项卡中，选择 **+ New agent flow。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  选择 **Add a trigger node** 并将其替换为 **When an agent calls the
    flow** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

3.  选择 **+ Add an input** 并添加 **Text** input。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

4.  输入 +++Name+++ 作为输入名称。

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

5.  同样，添加以下输入值。

+++Phone Number+++

+++Email ID+++

+++Address+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image79.png)

6.  在节点下方添加作，然后选择 **Add a new row**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

7.  选择 Table Name（表名称）作为 **Customer
    Record（客户记录**），然后在 **Advanced
    parameters（高级参数）中选择** Show all（全部显示）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

8.  单击 **Address** 字段，选择 **Dynamic 值** ，然后选择 **Address**
    动态值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image83.png)

9.  同样，添加

- 客户名称 – Name

- Email ID – Email ID

- 手机号码 - Phone Number

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

10. 打开 Customer ID **的 insert 表达式**，输入 +++guid()+++ ，然后选择
    **Add**。这是为了添加唯一值作为客户的 ID。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

11. 添加新作，然后选择 **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

12. 添加名为 +++Customer ID+++ 并插入表达式并输入
    +++string(outputs('Add_a_new_row')?\['body/cr6dd_customeridentifier'\])+++
    as the value.

将 **cr6dd_customeridentifier 替换为列 Customer ID 的逻辑名称**。

选择 **Add**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

13. 选择 **Save draft** 以保存流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

14. 保存流程后，选择 **Publish （发布** ） 以发布流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

15. 选择 **Overview** tab. **点击 Edit.** 将流的名称输入为 +++Add
    Customer+++ ，然后选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

### 任务 5 – 添加流程并设计 Customer Details 主题

在此任务中，您将设计客户详细信息主题，该主题将获取客户的电话号码，检查
Dataverse 中是否已存在详细信息，如果尚不存在，则添加详细信息。

1.  导航回 **Customer Details** 主题。

2.  在 Trigger 节点下添加节点，选择 **Add a tool -\> GetCustomer**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

3.  在 Inputs （输入） 中，选择变量 **MobileNumber**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

4.  选择 **输出** 变量，并将 Customer ID 和 ProductCategory 标记为
    **Global** ，如下面的屏幕截图所示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

5.  在 **Action （作** ） 节点下，添加一个 **condition** （条件） 节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

6.  选择 **CustomerID** in **Select a variable**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

7.  选择条件 as **不等于** 并输入 +++ '1'+++ 在 **Value**
    字段中。这将检查数据库中是否已存在客户详细信息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

8.  在 condition 节点下，添加 **Set a variable** 节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

9.  单击 **Select a variable** ，然后选择 **Create a new variable**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

10. 将变量命名为 +++IsNewCustomer+++ 并将其标记为 **Global**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

11. 将值设置为 +++‘No’+++. 这意味着客户是其数据已存在于 Dataverse
    中的老客户。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

12. 您将在变量节点旁边添加一个新节点，并向客户提供 Welcome 消息。

13. 选择 Add a node ，然后选择 **Send a message** node
    。在消息区域中，键入 +++Welcome+++ 然后单击 {x} 图标以选择变量。选择
    **Customer Name** 变量。

![](./media/image101.png)

现在，我们已经调用了代理流程
**GetCustomer**，检查客户记录是否已经存在，如果是，则向客户添加了欢迎消息。

现在，如果客户记录尚不存在，我们将设计主题的部分。

14. 在 **All other conditions** 节点下，添加 Set a variable 节点，并将
    **isNewCustomer** 变量的值设置为 +++’Yes’+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

15. 在变量节点旁边，添加 **Message** 节点并输入 +++We do not have your
    details in our system. Please fill in your details below to help us
    serve you better.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

16. 在 Message 节点旁边，添加 **Ask with adaptive card** 节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

17. 单击屏幕右上角的 3 个点，然后选择 **Properties（属性**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

18. 选择 **“编辑自适应卡**”。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

19. 在 **Card payload editor** 区域中输入以下 **JSON**。选择 **Save
    （保存**）。

> {
>
> "type": "AdaptiveCard",
>
> "body": \[
>
> {
>
> "type": "TextBlock",
>
> "size": "Medium",
>
> "weight": "Bolder",
>
> "text": "Please enter your details"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Name",
>
> "label": "Name"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Mobile Number",
>
> "label": "Mobile Number"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Email ID",
>
> "label": "Email ID"
>
> },
>
> {
>
> "type": "Input.Text",
>
> "id": "Address",
>
> "label": "Address"
>
> }
>
> \],
>
> "actions": \[
>
> {
>
> "type": "Action.Submit",
>
> "title": "Submit"
>
> }
>
> \],
>
> "version": "1.5",
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json"
>
> }
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image107.png)

20. 选择 **Close** 关闭编辑器。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

21. 展开创建的自适应卡片节点的 Outputs 部分，选择 Mobile Number
    值，然后选择 Global.MobileNumber 变量以保存用户输入的电话号码值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

22. 将其他值保留为默认值。

23. 自适应卡已准备好表单以获取客户详细信息。

24. 在 自适应卡 节点旁边，调用流 **添加客户.**

![](./media/image110.png)

25. 单击 Enter **中的**三个点**，或选择一个值**，然后选择
    **CustomerName** 变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

26. 同样，为要传递给流的其他字段添加输入变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

27. 选择 **Global.CustomerID** 作为输出变量，流的输出将保存到该变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

28. 在 action 节点后，添加 **Message 节点** 并输入值, +++Thank You!
    Customer detail has been added to the database. Please select a
    product type to shop.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

29. **保存** 主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

30. 打开 Conversation Start 主题，然后从那里调用 Customer Details 主题。

31. 在主题中的 Question 节点后添加一个节点。选择 **Topic management -\>
    Go to another topic（主题管理转到其他主题**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

32. 选择 **Customer Details** 主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

33. 选择 **Save （保存**） 以保存主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### 任务 6 – 创建代理流程以获取产品详细信息

在此任务中，您将创建一个代理流，该流将根据所选产品从 Dataverse
获取产品详细信息。

1.  从 Copilot Studio **中选择** 流 选项卡，然后选择 **+ 新建代理流**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  选择触发器节点，然后选择 **When an agent calls the flow** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  添加 Text input 并将其命名为 +++Product Name+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

4.  选择 **Save draft （保存草稿** ） 以保存流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

5.  选择 **Overview** 选项卡，然后单击 **Edit**。将名称输入为
    +++GetProductDetails+++ ，然后选择 **Save （保存**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

6.  导航回 **Designer** 选项卡，然后选择 **When an agent calls the
    flow** 节点下的 **Add an action**。搜索 +++list rows+++ ，然后选择
    **Microsoft Dataverse** 下的 列出行**作**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

7.  输入以下值

- **表名称 –** 选择 **产品记录**

筛选行 – +++cr6dd_producttitle eq '**\<Product Name\>**'+++ 将 \<Product
Name\> 替换为动态值 ProductName。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image125.png)

1.  在 List rows **节点下添加** Respond to the agent **节点** 。选择 **+
    Add an output** 并添加 Text Output 变量。输入以下值，然后单击 Add in
    **insert expression。**

- 输入名称 – Enter +++Product Name+++

> 表达 -
> +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_producttitle'\]+++
> (将 **cr6dd_producttitle** 替换为表中 tha 列 Product Name 的逻辑名称。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image126.png)

2.  同样，添加另一个具有以下详细信息的输出节点

- 输入名称 – Enter +++Price+++

- 表达 -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_productprice'\]+++
  Replace **cr6dd_productprice** with the logical name of the column
  **Price** in your table

> 节点现在应如下所示。
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image127.png)

1.  选择 **Save draft （保存草稿**） 以保存主题，然后选择 **Publish
    （发布**） 以发布流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

### 任务 7 – 创建主题以从客户处检索 Product category

1.  从 Copilot Studio 主题选项卡中，选择 **+ Add a topic -\> From
    blank**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

2.  将主题重命名为 +++Place Order+++. 将触发器节点的触发器更改为 **It's
    redirected to**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

3.  **保存** 主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image131.png)

4.  从 Copilot Studio 主题选项卡中，选择 **+ Add a topic -\> From
    blank**.

![](./media/image129.png)

5.  将主题重命名为 +++Get Product Categories+++. 在 **Trigger
    节点中选择** Change trigger **选项** ，然后选择 **It's redirect to**
    选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

6.  在 **Trigger** 节点下，添加 **Condition** 节点。

选择全局变量 **IsNewCustomer** 并添加条件 **IsNewCustomer** **is equal
to** +++**'Yes'**+++.

选择 **+ New condition.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

7.  选择 **Or**.

在 Or 条件下，选择全局变量 **ProductCategory** 添加条件，等于 +++'1'+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

![](./media/image136.png)

8.  在 Condition 节点下，添加一个 question 节点并输入 +++Select a
    category+++ 并选择 **+ 新建选项**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

9.  输入选项 +++Laptop+++ ，然后再次选择 + 新建选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

10. 同样，添加两个其他选项 +++**Desktop**+++ and +++**Tablet**+++. 在
    Save user response as （将用户响应另存为**）
    下选择变量**，并将变量命名为 +++**ProdCatchoice**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

11. 在 question 节点下，添加 **Set a variable value** 节点，以将从
    question 节点收到的选择转换为 String （字符串）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

12. 在 Set variable （设置变量） 下选择全局变量 **ProductCategory**。在
    **To value** 字段中，单击 3 个点，选择 **Formula**
    选项卡。输入表达式 +++Text(Topic.ProdCatchoice)+++ and select
    **Insert**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

13. 在 Set variable value 节点下，添加新节点 **Topic management** -\>
    **Go to another topic** -\> **Place Order**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

14. 现在，一条路径已完全完成。它将从用户那里获取类别并调用 Place Order
    主题。

15. 导航回本主题的开头。在所有其他条件下，添加 **Question （问题** ）
    节点。添加消息 +++Based on your recent purchase we suggest you
    products in \<Product Category\> category. Would you like to
    continue?+++

在消息中，将 **\<Product Category\>** 替换为 **Global.ProductCategory**
变量。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image143.png)

16. 添加 2 个选项, +++Yes+++ and +++No+++. 单击将用户响应另存为 （Save
    user response as） 下的变量，并将其重命名为
    +++Userschoiceofcategory+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

17. 在 **question** 节点下，添加 **condition** 节点。

将第一个条件设置为 **Userschoiceofcategory is equal to Yes**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

18. 在此节点下，添加 **Topic management 节点** 并调用 **Place Order**
    主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

19. 在 condition 节点中，选择 condition 节点右上角的三个点，然后选择
    **Insert new condition** 。

![](./media/image147.png)

20. 添加条件, **Userschoiceofcategory is equal to No**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

21. 在 Condition 节点下，添加一个 question 节点并输入 +++Select a
    category+++ 并选择 **+ 新建选项**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

22. 输入选项 +++Laptop+++ and select + 又是新选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

23. 同样，添加两个其他选项 +++**Desktop**+++ and +++**Tablet**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

24. 在 question 节点下，添加 **Set a variable value** 节点，以将从
    question 节点收到的选择转换为 String （字符串）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

25. 在 Set variable （设置变量） 下选择全局变量 **ProductCategory**。在
    **To value** 字段中，单击 3 个点，选择 **Formula**
    选项卡。输入表达式 +++Text(Topic.Var1)+++ ，然后选择 **Insert**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

26. 在 Set variable value 节点下，添加新节点 **Topic management** -\>
    **Go to another topic** -\> **Place Order**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

27. 选择 **Save** 以保存主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image151.png)

28. 打开 Customer **Details** 主题并移至最后一个节点。

29. **添加新节点** 以调用主题 **Get Product Categories**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image152.png)

30. 选择 **Save** 以保存主题。

![](./media/image153.png)

### 任务 8 – Create Agent flow 来下订单

在此任务中，您将创建一个代理流程，以根据客户选择的产品下订单。

1.  从 **Agent flows** 选项卡中，选择 **+ New agent flow。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image154.png)

2.  单击 **Add a trigger 节点** ，然后选择 **When an agent calls the
    flow** 节点时。

![](./media/image155.png)

3.  添加 2 个 **Text** 变量 +++Product Name+++ and +++Customer ID+++
    作为 **Input**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image156.png)

4.  单击 **Save Draft** 以保存流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image157.png)

5.  从 **顶部菜单中选择** Overview ，单击 **Edit** 并输入流的名称
    +++PlaceOrder+++. 然后选择 **Save （保存**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image158.png)

6.  导航回 **设计器** 选项卡。选择 添加新作 ，然后在 **Dataverse
    下**选择 添加新行。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image159.png)

7.  选择 Table name 作为 **Order Record**，然后单击 **Advanced
    parameters 下的** Show all。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image160.png)

8.  输入以下值。

客户标识符 - **客户 ID** （动态值）

Order identifier – 在 Insert expression 中输入 guid（）

订单状态 - +++**Order Placed**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image161.png)

9.  添加节点, **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image162.png)

10. 添加输出 Text 变量并将其命名为 +++Order ID+++.

将其值输入为 +++
string(outputs('Add_a_new_row')?\['body/cr6dd_orderidentifier'\])+++
（将 **cr6dd_orderidentifier** 替换为 Order Record 表中列 Order ID
的逻辑名称值。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image163.png)

11. 单击 **Save Draft** 以保存流程，然后单击 **Publish** 以发布流程。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image164.png)

### 任务 9 – 设计 Place Order 主题 

在此任务中，您将设计主题来下订单并更新 Dataverse 表。

1.  从 Agent 的 **Topic** 选项卡中**打开主题** Place Order 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image165.png)

2.  添加包含消息 +++Options based on the category will be listed
    below.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image166.png)

3.  添加 condition 节点。输入条件 ProductCategory（全局变量） 等于
    +++Laptop+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image167.png)

4.  在节点下，添加 question 节点并输入消息 +++Select a Laptop
    product+++. 在 **Identity** 下选择 **Laptop** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image168.png)

5.  单击 **Select** options for user 并选择所有 5 个可用选项。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image169.png)

6.  将变量名称输入为 +++ProdNameLapChoice+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image170.png)

7.  现在，按照相同的过程并为 ProductCategory 等于 +++Desktop+++ and
    +++Tablet+++.

8.  将值保存在变量名称中。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image171.png)

9.  在 Select a Laptop product **问题节点**下选择 **Set variable value**
    节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image172.png)

10. 将创建的变量重命名为 +++ProdNameSelected+++ 并将其设置为
    **Global**.![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image173.png)

11. 将 Formula （公式） 字段中的值设置为
    +++Text(Topic.ProdNameLapChoice)+++
    （如果您使用了其他变量名称，请替换变量名称）

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image174.png)

12. 同样，在 **Desktop** 和 **Tablet 分支下添加** Set variable value
    **节点** 。选择 **将变量**值设置为 **ProdNameSelected**，然后插入 To
    value 字段的表达式，其中包含您所使用的变量名称。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image175.png)

13. 在所有这些共同节点下添加一个 Action 节点，并调用 GetProductDetails
    流。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image176.png)

14. 选择要传递到流的 **ProdNameSelected**
    输入变量。将其他值保留为默认值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image177.png)

15. 在 Action （作） 下方添加 Message （消息）
    节点，然后输入以下消息。将 \<roductName\> 和 \<Price\>
    替换为相应的变量名称

产品详情

- 产品名称 - \<ProductName\>

> ​

- 价格 - \<Price\>

​

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image178.png)

16. 在 message 节点下方，添加带有 **消息的** Question 节点, +++Would you
    like to place order for this item?+++ in it. 添加选项 **Yes** 和
    **No** 到它，并将变量命名为 +++PlaceOrder+++.

![](./media/image179.png)

17. 在 Question 节点下，添加一个 condition
    节点，并在一个分支中添加一个条件 **PlaceOrder isequal to Yes**
    ，所有其他 **条件** 将成为 **第二个分支**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image180.png)

18. 调用流 **PlaceOrder** 作为下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image181.png)

19. 选择 **ProductName** 和 **CustomerID** 作为流的输入。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image182.png)

20. 现在，在此下方添加一个消息节点，其中包含消息, +++Your order is
    placed. This is your Order ID for reference -\<OrderID\>+++ (将
    **\<OrderID\>** 替换为变量 **OrderID** （流的输出变量）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image183.png)

21. 这样，**PlaceOrder isequal to Yes**
    分支就完成了。现在，导航到**所有其他条件分支**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image184.png)

22. 在此下方，添加一个 Question 节点，其中包含消息, +++Do you want to go
    to the main menu?+++ 使用选项 **Yes （是**） 和 **No**
    （否）。将变量命名为 +++**GoToMainMenu**+++.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image185.png)

23. 在此节点下，添加一个条件节点，并在一个分支中添加一个条件，其中
    **GoToMainMenu is equal to Yes**。此条件的另一个分支将是 **All other
    conditions**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image186.png)

24. 在此 condition 节点下，添加一个带有 message 的 question 节点
    +++**Select Product Category**+++ 并添加 3 个选项, +++**Laptop**+++,
    +++**Desktop**+++ 和 +++**Tablet**+++.

记下保存结果的变量名称。我们将在下一步中将其转换为文本。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image187.png)

25. 添加 **设置变量值** 节点，然后在 **设置变量 下选择** ProductCategory
    **变量** ，然后输入值作为 +++**Text(Topic.Var1)**+++ 在下面 **公式**
    标签。

如果变量名称不同，**请将** Var1 替换为变量名称。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image188.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image189.png)

26. 在 Set variable value 节点下，添加 **Go to step** 节点。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image190.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image191.png)

27. 添加节点后，您必须选择**步骤**，此时**控件应传递到**该步骤。
    **向上滚动**并选择**本主题开头的 Message
    节点**，因为您现在已从客户那里获得
    **ProductCategory**，需要从头开始执行。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image192.png)

28. 在带有消息的末尾添加一个公共消息节点 +++Thank you for shopping with
    us! Please visit again!+++ 然后选择 **Save （保存**） 以保存主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image193.png)

## 练习 4 – 添加触发器 

在本练习中，您将添加一个触发器，以便在 Order
表添加新行或修改现有行时启动，并自动向客户发送电子邮件。这定义了代理在此场景中的自主能力，

1.  选择代理的 Overview （概述） 选项卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image194.png)

2.  向下滚动页面，然后选择 **Add trigger。**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image195.png)

3.  选择 **When a row is added, modified or deleted** 选项，然后选择
    **Next**.

![](./media/image196.png)

4.  连接 Microsoft Copilot Studio **和** Dataverse **后** ，单击下一步。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image196.png)

5.  选择以下选项，将其余选项保留为默认值，然后选择 **Create
    trigger（创建触发器**）。

- Change Type – Added or Modified or Deleted

- Table name – Order Record

- 范围 - 组织

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image197.png)

6.  这可能需要几分钟才能完成。完成后，在 **Add trigger 对话框中**选择
    Close。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image198.png)

7.  在代理的 概述 页面**的 触发器 部分中** ，单击 **添加的触发器旁边的**
    3 个点，然后选择 **在 Power Automate 中编辑**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image199.png)

8.  选择流程中的第一个节点并添加列名称 +++cr6dd_orderidentifier,
    cr6dd_customeridentifier+++ 在 **Select columns**
    下。（将它们**替换为** Order Record 表中 **Order ID** 和 **Customer
    ID** 列的**逻辑名称**）。

![](./media/image200.png)

9.  添加新节点，然后选择 **List rows** 作。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image201.png)

10. 在 List rows （列出行）作中，选择 **Table name （表名称** ） 作为
    **Customer Record （客户记录**）。

在 Filter rows （筛选行**） 下**，输入 +++**cr6dd_customeridentifier eq
''**+++, 将列名称替换为您的客户 **ID
的逻辑名称**。将**光标保持在单引号内**。

![A screenshot of a list AI-generated content may be
incorrect.](./media/image202.png)

11. 选择 Insert expression（插入表达式），输入
    +++String(triggerOutputs()?\['body/cr6dd_customeridentifier'\])+++,
    将 **cr6dd_customeridentifier** 替换为 CustomerID
    的逻辑名称，然后选择 **Add**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image203.png)

12. 在 **List 行**旁边，添加作 **Send an email （V2）。**

![A screenshot of a mail box AI-generated content may be
incorrect.](./media/image204.png)

13. 单击 **Sign in （登录** ） 并使用您的凭证登录。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image205.png)

14. 在 **To** 字段中，插入表达式并输入
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_emailaddress'\]+++，将
    **cr6dd_emailaddress** 替换为客户记录表中电子邮件 ID
    字段的逻辑名称，然后选择 **添加**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image206.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image207.png)

15. 输入以下详细信息，

主题 - +++Order Placement+++

内容 –

Hi,

这是为了通知您您的订单已下达。感谢您在我们这里购物。

谢谢。

16. 保存流程，然后选择 Publish it 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image208.png)

17. 返回 Copilot Studio 代理页面，选择 **发布** 以发布代理。

![](./media/image209.png)

18. 在 确认对话框中选择 **Publish**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image210.png)

19. ewqewqew

## 练习5 – 测试代理

在本练习中，您将测试代理的工作原理。

1.  在代理页面中，选择 **Test （测试**） 以打开 Test （测试） 窗格。

2.  输入 +++3148987666+++. 这是现有客户的电话号码。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image211.png)

3.  从 **给定的选项**中选择 Yes。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image212.png)

4.  从给定的选项**中选择一个**产品。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image213.png)

5.  从给定的选项中选择 Yes。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image214.png)

6.  下订单并将参考 ID 提供给客户。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image215.png)

7.  您还可以询问其他问题，例如跟踪您收到的 ID
    的订单交付。虽然我们没有为此配置主题，但它会根据知识来源给你回复。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image216.png)

通过选择不同的选项来测试其他方案。添加新客户，并检查您的电子邮件 ID
中是否已收到已添加到 Customer Record 表的邮件。

## 总结:

在本实验中，您学习了如何设计自主购物代理。涵盖的主题包括：

- 变量

- 实体

- 主题

- 代理流程

- 触发

- 知识来源