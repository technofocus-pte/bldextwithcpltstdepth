# 实验 01：从 Copilot Studio 创建和使用代理来管理房地产应用程序

**实验室持续时间** – 90 分钟

**介绍**

Contoso Real Estate
专门从事商业和住宅物业的销售和管理。目前，客户信息有效地存储在其
Dataverse 实例中，从而简化了数据管理。然而，预订过程带来了重大挑战。

目前，客户只能通过电话申请预订，导致电话线不堪重负，等待时间长。这种情况不仅让客户感到沮丧，而且还有可能失去潜在业务，因为许多人无法与办公室联系以请求服务。

为了解决这些问题，Contoso Real Estate
致力于开发全面的数字解决方案。该解决方案将使客户能够轻松访问有关预订流程的信息并在线提交预订请求。

**目标**

- 从 Copilot Studio 为 Contoso Real Estates
  构建独立代理（这将允许客户发现有关房地产预订流程的信息，并创建预订请求供办公室查看。

- Create Topics （创建主题） 以设置预订的逻辑。

- 创建预订所需的 Dataverse 表。

- 发布 Copilot。

:::danger **实验 03** 需要在第 1 天结束前完成，才能执行第 2
天的实验。即使实验 01 和 02 未完成，也请确保在第 1 天结束时完成实验
03。:::

## 练习 0：设置环境

### 任务 1：登录到 VM

1.  使用 **Home** 选项卡中的 **Username** 和 **Password** 登录到 VM。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

### 任务 2：同步 VM 时钟

1.  登录到 VM 后，右键单击屏幕右下角的时钟。

2.  选择 **Adjust date and time**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  在打开的 设置 屏幕上，单击 其他设置 下的 **Sync now 。**

![](./media/image3.png)

4.  这负责同步时间，以防自动同步不起作用。

5.  **关闭** Settings 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

6.  如果有 **Sign in required** 警报，请单击  **Sign In** ，然后选择
    **Sign in with a different account** ，然后使用 VM 的 **Home**
    选项卡中提供的 **admin credentials** 登录。

![A blue screen with white text AI-generated content may be
incorrect.](./media/image5.png)

![](./media/image6.png)

7.  选择 **Sign in to this app only** 。

![](./media/image7.png)

8.  登录后，**关闭** **Teams** 应用程序。我们将在第 3 天的实验中使用它。

## 练习 1：设置 Power Apps 和 Dataverse

### 任务 1：注册 Microsoft Power Apps 开发人员计划

1.  打开浏览器并导航到
    !\!<https://powerapps.microsoft.com/free/>!!，然后选择 **Start
    free** 或 **Try for free** 。

![](./media/image8.png)

2.  如果出现提示，请在 **Home** 选项卡中使用 Office Tenant
    Credentials **Username** 和 **Password** 登录。这将是您实验室所有
    Microsoft 网站和应用的 **login credentials** 。

![](./media/image9.png)

3.  在 **Let's get started**
    下，在文本框中输入 **Home** 选项卡中的 **Administrative
    Username**，选中协议框并选择 **Start free**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

4.  如果您看到一条提示，指出您已有 Microsoft 账户。选择 **Sign in**
    。输入您的密码。

5.  如果出现提示，请选择 **Yes** 以保持登录状态。

6.  单击 屏幕右上角的 **Environment** 并确保选中 **Dev
    One**。如果没有，请选择 **Dev One**。

![](./media/image11.png)

### 任务 2：创建解决方案

1.  来自 Power Apps Maker 门户 (!\!<https://make.powerapps.com/>!!)，从
    左侧窗格中选择 **Solutions**。

![](./media/image12.png)

2.  单击 **+ New solution**。

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image13.png)

3.  进入 **!!Bookings!!** 对于显示名称，在 **Publisher** 下选择
    **Contoso （contoso），**然后单击 **Create**。

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image14.png)

如果 **Contoso** 选项未列在 **Publisher** 下，请执行接下来的 2
个步骤，否则从步骤 6 继续。

4.  如果 **Contoso** 选项未列在 **Publisher** 下，请选择 **+ New
    Publisher。**

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image15.png)

5.  输入以下详细信息，然后单击 **Save**。

[TABLE]

> ![](./media/image16.png)

6.  选择 屏幕左上角的 **Back to solutions**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

### 任务 3：设置首选解决方案

1.  在 Maker 门户中的 Solutions 下，为 **Set your preferred solution**
    选择 **Manage**。

![](./media/image18.png)

2.  在 **Unless otherwise specified** 下选择**“Bookings
    （contoso）”，save my changes in **，然后选择 **Apply**。

![](./media/image19.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

### 任务 4：创建 Real Estate Properties 自定义表

有 2 种方法可以创建新表。一种是传统的手动方法，另一种是使用 Copilot。

#### 任务 4.1：使用 Copilot 创建房地产属性自定义表

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

创建具有以下列和数据类型的表 “Real Estate Property” -  
1. Property Name - Single line of text  
2. Asking Price - Currency   
3. Street - Single line of text  
4. City - Single line of text  
5. Client - Data type Lookup, Related table - Contact  
  
在 Real Estate Property 表中再添加两列 Bedrooms 和 Bathrooms，每列都有
Datatype 选项 -  
1. Label - 1, Value - 1  
2. Label - 2, Value -2  
3. Label - 3, Value 3  
4. Label - 4, Value 4  
5. Label - 5, Value 5

 

使用以下列和数据类型创建表 “Booking Request” -  
1. Booking Name - Single line of text  
2. Property - Data type Lookup, Related table - real estate property  
3. View name - Single line of text  
4. Viewer Email - Single line of text  
5. Booking Date - Date and time  
6. Notes - Multiple lines of text

 

在具有数据类型选项的 Booking Requests 表中添加另一列 Decision -  
1. Label - Undecided, Value - 1  
2. Label - Accepted, Value -2  
3. Label - Declined, Value 3

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image27.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

创建所有列后，在 **Real Estate Property columns and data**
下，输入以下测试数据：

- Property Name: !!**1100 High Villas**!!

- Asking Price: !!**250,000**!!

- Bathrooms: **3**

- Bedrooms: **2**

- City: !!**Redmond**!!

- Street: !!**Main Avenue**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

#### 任务 4.2：使用 Copilot 创建 Real Estate Properties 自定义表

按照以下步骤在 Dataverse 中手动为房地产属性创建新的自定义表。

1.  在左侧导航窗格中，选择 **Tables，**选择 **+ New table**
    旁边的下拉列表 ，然后选择 **Create new tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  单击 **Let's set up your data** 对话框中的 **Got it** 。

![](./media/image32.png)

3.  在 Create new tables 屏幕上，单击 **+ New table -\> Add columns and
    data**。

![](./media/image33.png)

4.  将表名称从 **Table1** 重命名为 !!**Real Estate
    Property**!!，然后单击 **Save and exit**。

![](./media/image34.png)

5.  单击 确认对话框中的 **Save and exit**。

![](./media/image35.png)

6.  保存后，单击 **Custom** 选项卡以在此处找到新创建的表。单击 **Real
    Estate Property** 表。

![](./media/image36.png)

7.  在 **Real Estate Property columns and data**下，将名为  **New
    Column** 的列的名称更改为 **New
    Column**（单击新列旁边的下拉列表**，**然后选择 **Edit Column**
    并更新 **Display name**）更改为 !!**Property Name**!!，然后选择
    **Save** 。

![](./media/image37.png)

8.  选择 + 按钮，在 columns and data 窗格中添加新列。在 New column
    窗格中，输入以下值，然后选择 **Save**。

    - Display name: !!**Asking Price**!!

    - Data type: Currency

![](./media/image38.png)

![](./media/image39.png)

9.  添加以下两列。

[TABLE]

10. 添加另一个具有以下值的列

    - **Display name**: !!Bedrooms!!

    - **Data type**: Choice -\> Choice

![](./media/image40.png)

创建选择值:

在 **Sync this choice with**下选择 **+ New Choice**

![](./media/image41.png)

- 在 **Choices** 下，将 Display name 提供为 !!**Bedrooms**!!.

&nbsp;

- 您会看到两个标题为 **Label** 和 **Value** 的输入字段。 在标签下输入
  **1**。Power Apps 会自动分配一个值，但您可以将该值更改为 **1**。

&nbsp;

- 选择 **+ New choice **，并将 **2** 作为 Label 的新条目，将 **2** 作为
  Value 的新条目。

 

- 选择 **+ New choice**，并将 **3** 作为 Label 的新条目，将 **3** 作为
  Value 的新条目。

 

- 选择 **+ New choice**，并将 **4** 作为 Label 的新条目，将 **4** 作为
  Value 的新条目。

 

- 选择 **+ New choice**，并将 **5** 作为 Label 的新条目，将 **5** 作为
  Value 的新条目。

 

- 选择 **Save** 。

![](./media/image42.png)

通过单击 S**ync this choice with**的下拉列表，选择添加的选项
**Bedrooms**

![](./media/image43.png)

点击 **Save** 。

![](./media/image44.png)

11. 选择 **+** 按钮，在 columns and data 窗格中添加新列。

12. 在 New column 窗格中，输入以下值，然后选择 **Save** :

    - **Display name**: !!Bathrooms!!

    - **Data type**: Choice -\> Choice

![](./media/image45.png)

创建选择值:

在 **Sync this choice with**下选择 **+ New choice** 。

- 在 **Choices** 下，将 Display name 提供为 !!Bathrooms!!。

- 您会看到两个标题为 **Label** 和 **Value** 的输入字段。在标签下输入
  **1**。Power Apps 会自动分配一个值，但您可以将其更改为 **1**。

- 选择 **+ New choice**，并将 **2** 作为 Label 的新条目，将 **2** 作为
  Value 的新条目。

- 选择 **+ New choice**，并将 **3** 作为 Label 的新条目，将 **3** 作为
  Value 的新条目。

- 选择 **+ New choice**，并将 **4** 作为 Label 的新条目，将 **4** 作为
  Value 的新条目。

- 选择 **+ New choice**，并将 **5** 作为 Label 的新条目，将 **5** 作为
  Value 的新条目。

- 选择 **Save**。

![](./media/image46.png)

选择创建的选择，然后单击 **Save** 在列添加窗格中。

![](./media/image47.png)

13. 通过在列和数据窗格中再次选择 **+** 按钮来添加另一列。

在 New column 窗格中，输入以下值，然后选择 **Save** ：

- **Display name**: !!**Client**!!

- **Data type**: Lookup -\> Lookup

- **Related Table**: Contact

![](./media/image48.png)

14. 创建所有列后，在 **Real Estate Property columns and data**
    下，输入以下测试数据：

:::secondary 注意：如果未显示所需的列，请通过选择 **+\<number\>more**
来调整显示的列 :::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

- 属性名称: !!**1100 High Villas**!!

- 要价: !!**250,000**!!

- 浴室: **3**

- 卧室: **2**

- 城市: !!**Redmond**!!

- 街: !!**Main Avenue**!!

- 客户: **选择任何联系人**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

:::secondary 注意：如果  **Contact** 表中没有 **client ** 端记录
，请忽略向该列添加数据。:::

### 任务 5：创建 Bookings 表

按照以下步骤在 Dataverse 中为房地产预订创建新的自定义表。

1.  从左侧导航窗格中，选择 **Tables** ，然后选择 **Create new tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

2.  在 **Create new tables** 屏幕上，单击 **+ New table -\> Add columns
    and data**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

3.  将表名称从 **Table1** 重命名为 !!**Booking Request**!! ，然后单击
    **Save and exit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

4.  单击 确认对话框中的 **Save and exit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

5.  保存后，单击 **Custom** 选项卡以在此处找到新创建的表。单击 **Booking
    Request** 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  将名为 **New Column 的**列的名称更改为 !!Booking
    Name!!（单击旁边的下拉菜单 **New Column** 并选择 **Edit Column**
    并更新 **Display name**）。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  单击 列名称旁边的 **+** symbol。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  使用下面指定的名称和数据类型创建以下列。选择 **Save** 。

- Display name – !!Property!!

- Data type – Lookup -\> Lookup

- Related Table – Real Estate Property

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

- Display name – !!Viewer Name!!

- Data type – **Single line of text**

 

- Display name – !!Viewer Email!!

- Data type – **Single line of text**

- Format – **Email**

 

- Display name – !!Booking Date!!

- Data type – **Date and time**

 

- Display name – !!Notes!!

- Data type – **Multiple lines of text**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

1.  添加包含以下详细信息的 choice 数据类型列。

- Display name – !!Decision!!

- Data type – Choice -\> Choice

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

在 **Sync this choice with下**，单击 **+ New Choice**。输入**Display
name**为 **!!Decision!!.**

输入以下详细信息，然后单击 **Save** 。

- Label – !!**Undecided**!!

- Value – 1

- Label – !!**Accepted**!!

- Value – 2

- Label – !!**Declined**!!

- Value – 3

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

在 **Sync this choice with** 字段下选择添加的 Choice **Decision**，指定
**Undecided** 作为 **Default choice**，然后单击 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

## 练习 2：使用 Copilot Studio

### 任务 1：注册 Copilot Studio 试用版

1.  在浏览器中的新选项卡中，导航到 url
    !\!<https://copilotstudio.microsoft.com/>!!.

2.  将 **Choose your country/region** 保留为 **default**，然后单击
    **Start free trial**。

![A person sitting at a computer AI-generated content may be
incorrect.](./media/image63.png)

3.  单击 左上角的 **Environments**，然后选择 **Dev One**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

4.  如果您 收到 Welcome to Copilot Studio，请选择 **Skip**！提示。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

### 任务 2：创建 Real Estate Booking Service 代理

1.  从 左侧导航窗格中选择  **Create** 创建 ，然后选择 ** New agent**
    磁贴。

![A screenshot of a software AI-generated content may be
incorrect.](./media/image66.png)

2.  选择 **Skip to configure**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  填写以下详细信息。

    - Name - !!**Real Estate Booking Service**!!

    - Description - !!**Create bookings for real estate properties**!!

    - Instructions - !!**Create a copilot for topics relating to
      creating bookings for real estate properties!!**

    - Language **–** Select **English**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  选择屏幕右上角的 Create 按钮旁边的三个点，然后选择 **Edit advanced
    settings**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  选择 **Bookings** 解决方案，然后选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  在屏幕的右上角，选择 **Create**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  创建代理后，在 Test your copilot 窗格中，输入 !**How do I make a
    booking?!!，**然后单击 **Enter** 并观察响应。您将收到一个通用响应。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

### 任务 3：配置安全性

1.  选择 屏幕右上角的 **Settings。**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image73.png)

2.  选择 **Security** 选项卡，然后选择 **Authentication** 磁贴。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

3.  选择 **No authentication** 并单击 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

4.  在 **Save this configuration** 提示中选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

5.  保存身份验证设置后，单击 **Close **选项以关闭 **Settings** 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

### 任务 4：禁用您不需要的主题

示例主题包含在新的 Copilot 中。删除这些示例主题。禁用不需要的系统主题。

1.  从 Copilot 概述页面的顶部菜单中选择 **Topics** 选项卡。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

2.  您将进入 **Custom** Topics 页面。

3.  选择 **System** 选项卡。将 **Sign in** 主题的 **Enabled** 切换为
    **Off**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

### 任务 5：发布和测试 Copilot

1.  选择 **Publish** 以发布此代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

2.  在 **Publish this agent** 对话框中选择 **Publish** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

### 任务 6：演示网站

Demo 网站允许没有许可证的用户测试您的
Copilot。您可以向他们提供演示网站的 URL。

1.  选择 **Settings** 旁边的 **three dots** 或 屏幕右上角的 **Publish**
    按钮，然后选择 **Go to demo website**。

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image82.png)

2.  在 **Type your message** 文本框中，输入 **! !What information is
    needed to book a viewing for a real estate property?!!**
    并观察代理的响应。

![A screenshot of a chatbot AI-generated content may be
incorrect.](./media/image83.png)

它将是通用的，类似于您在 在 Studio 中测试您的代理
中获得的那个，因为我们尚未配置任何特定主题，也尚未为代理实施任何逻辑。我们将在即将到来的练习中执行此作。

## 练习 3：使用 Copilot 创建和管理主题

### 任务 1：使用 Copilot 创建主题

可以使用自然语言创建和编辑主题。

1.  在 **Copilot Studio** 打开的情况下导航回浏览器选项卡。在 **Topics **
    选项卡中，选择 **Add a topic** ，然后选择 **Create from description
    with Copilot.**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

:::secondary:::
**注意：**如果提示查看复制到剪贴板的文本和图像，请选择允许 :::

2.  输入以下详细信息，然后单击 **Create**。

    - Name your topic - !!**Customer Details**!!

    - Create a topic to... - !!**Ask the customer for their name and
      email address**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

3.  此时将显示一个新主题，其中包含触发短语和问题节点。

4.  选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

### 任务 2：使用自然语言更新节点

1.  如果 屏幕右侧未显示 **Edit with copilot** 窗格，请选择创作画布上部的
    **Copilot** 图标。

2.  选择第二个问题节点 **What is your email address？**

3.  在 **Edit with Copilot** 面板的 **What do you want to
    do? **字段中，输入以下文本：

!!**Update the message in this question node to say thank you to the
Name variable from the previous node and then proceed to ask the email
address question**!!

::: :::

4.  选择 **Update**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

5.  选择 **Save**。![A screenshot of a computer AI-generated content may
    be incorrect.](./media/image88.png)

### 任务 3：使用自然语言添加节点

除了添加更新现有节点外，您还可以使用 Copilot 添加新节点。

1.  通过单击节点周围的空白区域，确保未选择任何节点。

2.  在 **What do you want to do?** 字段中，输入以下文本，然后选择
    **Update。**

!!**Add a new multiple-choice question to prompt the user if the details
are correct with two options Yes or No**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

3.  新的问题节点将添加到主题末尾，其中包含供用户选择的选项。

4.  在问题部分，内容下方的细节 **Are the details
    correct?**，输入以下内容。

> \<h3\>Summary\</h3\>
>
> \<p\>\<strong\>Full Name:\</strong\>
>
> Name string
>
> \</p\>
>
> \<p\>\<strong\>Email Address:\</strong\>
>
> EmailAddress string
>
> \</p\>
>
> 通过选择 **{x}** 符号，将 \<p\> 标记内的 **Name string** 和 **Email
> address string** 替换为相应的变量。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

5.  选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### 任务 4：配置变量的范围

1.  选择 **Variables** 以打开 Variables 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

2.  我们有接收值的变量和返回值的变量。我们的 topic 变量将返回原始 topic
    的值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

3.  选中主题变量的右侧复选框，然后单击 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

## 练习 4：手动创建和管理主题

### 任务 1：从零开始创建主题

1.  选择 **Topics** 选项卡。

2.  选择 **Add a topic** ，然后选择 **From blank** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

3.  选择 **Details** 以打开 主题详细信息 对话框。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

4.  填写以下详细信息，然后单击 **Save**。

    - **Name** - !!Book a Real Estate Showing!!

    - **Display Name –** !!**Book**!!

    - **Description** - !!Select the property and requested date and
      create a booking request!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

5.  选择 **Details** 以关闭 Topic details 对话框。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

### 任务 2：添加触发短语

1.  在 **Trigger** 中的 **Phrases** 下选择 **Edit** 。进入

> **!!I want to book a real estate showing!!** ，然后选择 **+** 图标。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

2.  逐个输入以下短语。输入 **+** 后选择图标。

    - !!**Schedule a real estate showing**!!

    - !!**Arrange the viewing for a real estate property**!!

    - !!**Set up an appointment to view a house**!!

    - !!**Plan a property viewing**!!

&nbsp;

1.  添加所有短语后，选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

### 任务 3：添加消息节点

1.  选择 **Trigger** 节点下的 + icon，然后选择 **Send a message**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

2.  在 **Enter a message** 字段中，输入以下文本：

!!Hi, I can help you with booking a real estate property showing.!!

3.  选择 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

### 任务 4：添加 Topic 管理节点

1.  选择 **send a message** 节点下的 **+** icon，然后选择 **Topic
    management -\> Go to another topic**。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image103.png)

2.  选择 **Customer Details** 主题。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

3.  选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

### 任务 5：添加条件节点

1.  选择 主题管理节点下的 + 图标，然后选择 **Add a condition**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

2.  选择 **DetailsCorrect** for variable。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image107.png)

3.  选择 **Condition** as **is equal to**

4.  选择 **value **作为 **Yes** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

5.  选择 **Save** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

### 任务 6：添加问题节点

1.  选择 左侧条件节点下的 **+** icon，然后选择 **Ask a
    question**。填写以下详细信息，然后单击 **Save**。

    - **Enter a message**  - !!Which property do you want to see?!!

    - **Identify** - 选择**User's entire response**.

    &nbsp;

    - **Save user response as** Enter **!!PropertyName!!** 对于
      **Variable name**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

1.  选择 问题节点下的 + 图标，然后选择 **Ask a
    question**。填写以下详细信息，然后单击 **Save。**

    - **Enter a message** - !!What date and time do you want to see the
      property?!!

    - Identify - 选择**Date and Time**

    - **Save user response as** – 单击 **Var1** 打开 Variable properties
      窗格并输入 **!!DateTime!!** 对于 **Variable name**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

### 任务 7：测试 Copilot

1.  选择 屏幕右上角的 Test 按钮以打开测试面板。选择
    屏幕右上角的测试面板顶部的 **three dots** 。选择 **Track between
    topics** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

2.  当 **Conversation Start** 消息出现时，您的 Copilot 将开始对话。

3.  作为响应，输入您创建的主题的触发短语：

!!I want to book a real estate showing!!

4.  Copilot 回答说：**"What is your name?"** 问题。

5.  输入您的姓名。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image113.png)

6.  然后在 系统提示输入 **email**
    时输入您的电子邮件。输入详细信息后，将显示一个问题，询问信息是否正确，并提供用于选择
    **Yes** 或 **No** 的选项。选择 **Yes**。

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image114.png)

7.  进入 !!555 Oak Lane, Denver, CO 80203!! 到 **Which property to you
    want to see？** 提示。

8.  进入 **!!Tomorrow 10:00 AM!!** 到 **What date and time you want to
    see the property？** 提示。

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image115.png)

## 练习 5：构建一个 Autonomous 代理，在创建或更新预订时自动发送电子邮件

本练习旨在展示 Autonomous 代理的 **When a row is added， modified or
deleted** 触发器。

### 任务 1：创建代理

1.  单击 左侧导航窗格中的 **Agents**。

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image116.png)

2.  单击 **+ New agent** 创建新代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

3.  单击 **Skip to configure** 以配置代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

4.  输入以下详细信息，然后单击 **Create**。

**Name** - !!Autonomous agent!!

**Description** - !!You are an agent to detect the updates to the
Booking Requests table!!

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image119.png)

5.  代理设置需要几秒钟才能完成。完成后，Autonomous 代理将打开，并显示
    **Your agent is ready** 消息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

6.  选择 **Settings ** 从右上角。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

7.  必须启用 Generative AI 选项才能继续为代理创建 Trigger。

8.  从 **Settings** 屏幕左侧的选项列表中选择 **Generative AI** 选项。在
    **Using generative AI in conversations**下，选择 **Generative**
    式点击 **Save**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

9.  关闭 **Settings** 窗格。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

### 任务 2：向代理添加触发器

1.  返回 自治代理 页面，向下滚动到 **Triggers (preview) **部分，然后选择
    **+ Add trigger** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

2.  从 **Add trigger** 屏幕中选择 **When a row is added， modified or
    deleted** 触发器。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image125.png)

3.  在 下一个屏幕中单击 **Continue**。

4.  选择后， **Trigger name** 和 **Sign in options**
    将加载到下一个屏幕中。这将需要几分钟时间才能填充。对于我们选择的触发器，将有两个应用程序，一个是
    **Microsoft Copilot Studio**，另一个是 **Microsoft Dataverse**。

5.  加载后，确保登录选项的连接状态为绿色，然后单击 **Next** 继续。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image126.png)

6.  在 Add trigger 屏幕中，选择以下详细信息，然后单击 **Create
    trigger**。

    - 更改类型 – **Added or modified**

    - 表名称 – **Booking Requests**

    - 范围 – **Organization**

    - 触发指令 – 保留为 **default**。这会将整个响应返回给代理。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image127.png)

7.  触发器创建可能需要 3 到 5 分钟才能完成。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

8.  完成后，单击 **Close** in the **Time to test your trigger! **屏幕。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

9.  单击 **Actions** 选项卡，然后选择 **+ Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

10. 寻找 !!Send an email!!，然后选择 **Send an email （V2） action**。

![A screenshot of a email conversation AI-generated content may be
incorrect.](./media/image131.png)

11. 建立连接后，单击 **Next**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

12. 选择 **Copilot author Authentication** 作为 **End user
    authentication**下拉列表中的选项，然后选择 **Add action**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

13. 选择 created Action。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

14. Select the **Inputs** tab.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

15. 在 **Description** 字段中提供邮件需要传送到的电子邮件 ID，然后单击
    **Save**。这可以是您可以访问的任何邮件 ID。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image136.png)

### 任务 3：向代理添加说明

1.  选择 **Overview** 转到 Overview 页面，然后单击 Overview 页面中的
    **Edit**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

2.  将下面的说明粘贴到 **instructions** 文本区域内，将下面 b
    部分中\<邮件 ID\> 的占位符替换为 需要将详细信息发送到的邮件
    ID，然后单击 **Save**。

!!a. Read the details of the row that gets added or modified!! !!b. Mail
the modified information only to \<Mail ID\> with a proper subject and
body added to the email!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

3.  单击 **Publish** 将代理发布到它所连接的所有渠道。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

4.  单击 **Publish this agent** 对话框中的 **Publish**。

![A screen shot of a computer AI-generated content may be
incorrect.](./media/image140.png)

5.  发布后，您将收到一条成功消息。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

### 任务 4：更新 Bookings 表

1.  登录 ！！<https://make.powerapps.com/>！！，然后从
    左侧导航窗格中选择 **Tables**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

2.  选择  **Custom**  ，然后从中选择 **Booking Request** 表。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image143.png)

3.  在表中添加或更新值。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

### 任务 5：测试代理

1.  在代理页面中，选择 Test，然后打开 **Activity Map**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

2.  在代理页面中，选择 **Test trigger** 选项。我们在 Bookings
    表中所做的更新将触发触发器。我们将使用它从 copilot studio 进行
    **test** 。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

3.  选择最新条目，然后单击 **Start testing**。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image147.png)

4.  触发器被调用。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

5.  邮件将发送到指定的邮件 ID。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

6.  检查相应的邮箱，查看您是否收到了如下邮件。

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

**总结**

在本实验中，我们学习了

- 从 Copilot Studio 构建代理并在其中创建主题。

- 从 Copilot Studio 测试代理并将其发布到演示网站。

- 构建自治代理并进行测试

 
