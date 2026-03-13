# 实验室——将招聘代理转变为可扩展的多代理架构

在之前的实验室里，你构建了主招聘代理，为管理招聘流程打下了坚实基础。但一个代理人能做的有限。

如果你接受这项任务，那就是 **Operation Symphony** -
将你手下的单个特工转型为**多特工系统**：一支由各领域专家组成的协同作战团队，共同应对复杂的招聘挑战。你可以把它理解为从单打独斗的特工升级为指挥一支特种部队。

就像交响乐团中每位音乐家完美和声地演奏自己的部分一样，你将为现有的招聘代理增加两位关键专家：一位自动处理简历的申请接待员，以及一位负责制作全面面试材料的面试准备员。这些代理将在你的主编排器下无缝协作。

创建多智能体后，您将将智能体从等待人类输入转变为主动响应外部事件，并在无监督下采取智能行动。

可以把它看作是从回答*问题的代理*升级为能够*预见需求*并*独立行动*的代理。通过事件触发器和自动化工作流程，您的招聘代理将检测收到的简历邮件，自动处理附件，将数据存储在Dataverse中，并通过Microsoft
Teams通知人力资源招聘团队——而您则专注于更高价值的任务。

## 目标

在这次任务中，你将学到东西:

1.  何时使用**子代理**与**连接代理**

2.  如何设计 可扩展的**多智能体架构**

3.  为聚焦任务创建**子代理**

4.  建立 代理之间的**通信模式**

5.  构建申请接待代理和面试准备代理

6.  事件触发器如何实现无需用户交互即可自主代理行为

7.  Copilot Studio 中交互代理与自主代理的区别

8.  如何创建自动处理邮件附件并将文件上传到 Dataverse 的事件触发器

9.  如何构建能够向Teams频道发布自适应卡片以发送通知的代理流程

10. 如何在事件触发器和代理流程之间传递数据，实现端到端自动化

## 子代理：申请接收代理

让我们开始构建我们的多代理人招聘系统。我们的首位专家将是**申请接纳代理**——一位负责处理新简历和候选人信息的儿童代理。

![](./media/image1.png)

**应用接收代理的职责**

- **解析**通过互动聊天提供的PDF**简历内容**（在未来的任务中，你将学会如何自主处理简历）。

- **提取结构化数据**（姓名、技能、经验、教育背景）

- 根据资历和求职信**匹配候选人与空缺职位**

- 将候选信息**存储在Dataverse中以便后续处理**

- **减少申请重叠**，避免重复创建同一候选人，并利用简历中提取的电子邮件地址与现有记录匹配。

**为什么这应该是儿童代理人**

申请接收代理作为子代理非常合适，因为:

- 它专门用于文档处理和数据提取

- 它不需要单独出版

- 这是我们整体招聘解决方案的一部分，由同一团队管理

- 它聚焦于特定触发条件（收到新简历），由招聘代理调用。

## 关联代理：面试准备代理

我们的第二位专家是**面试准备代理**——一个互联的代理，帮助制作全面的面试材料并评估候选人回答。

**面试准备代理职责**

- **制作**包含公司信息、职位要求和评估标准的**面试包**

- 针对特定职位和候选人背景**生成针对面试问题**

- **回答**关于职位岗位和申请的**常见问题**，以便与利益相关者沟通

**为什么这应该是一个连接的代理**

面试准备代理作为联络代理工作效果更好，因为:

- 人才招聘团队可能希望在多个招聘流程中独立使用它

- 它需要自己的面试最佳实践和评估标准知识库

- 不同的招聘经理可能希望为他们的团队定制其行为

- 它可以被用于内部职位，而不仅仅是外部招聘

## 练习1 - 添加应用接收代理

让我们把我们的第一位子代理添加到你现有的招聘代理中。

### 任务1 - 解决方案设置

1.  在 Copilot Studio 中，选择左侧导航工具下方的省略号（...）。

2.  选择 **Solutions**。

    ![](./media/image2.png)

3.  找到您的**Operative**解决方案，点击其旁边的**省略号
    (...)**，然后选择“**Set preferred
    solution**”。在弹出的对话框中点击“**Apply**”。这将确保您的所有工作都添加到此解决方案中。

    ![](./media/image3.png)

4.  在“Set your preferred solution”对话框中选择应用。

    ![](./media/image4.png)

### 任务2 - 配置你的招聘代理指示

1.  **导航**到Copilot Studio。确保你的环境在右上角的 **Environment
    Picker** 中被选中**。**

2.  打开 **Hiring Agent**。

3.  在代理的“**Overview** ”选项卡的“**Instructions**”部分中选择“**Edit** ”。

    ![](./media/image5.png)

4.  复制粘贴以下指令到指令输入中。

    +++**You are the central orchestrator for the hiring process. You coordinate activities, provide summaries, and delegate work to specialized agents.**+++

5.  选择**Save**。

    ![](./media/image6.png)

6.  选择屏幕右上角的 **Settings** 按钮。

    ![](./media/image7.png)

7.  检查页面，确保以下设置已应用，然后选择 **Save**。

    | **设置**  | **价值**  |
    |:-----|:--------|
    | 使用 generative AI 编排来生成你的代理的响应  |  是 |
    |  深度推理 | 关闭  |
    | 让其他代理连接并使用这个  | 开启  |
    |  继续使用退役型号 | 关闭  |
    | 内容审核  | 中等  |
    | 收集用户对代理消息的反应  |  开启 |
    | 使用常识  | 关闭  |
    | 利用网络信息  |  关闭 |
    | 文件上传  | 开启  |
    | 代码解释器  | 关闭  |

    ![](./media/image8.png)

    ![](./media/image9.png)

    ![](./media/image10.png)

    ![](./media/image11.png)

8.  点击 右上角的**X**键可以关闭设置菜单

    ![](./media/image12.png)

### 任务3 - 添加应用接收子代理

在此任务中，你将向招聘代理添加一个子代理。

1.  在您的招聘代理中**导航**到“**Agents**”选项卡（您可以在这里添加专业代理），然后选择“**Add**”。

    ![](./media/image13.png)

2.  选择 **New child agent**。

    ![](./media/image14.png)

3.  填写您的代理人**姓名** +++Application Intake Agent+++

4.  选择“**The agent chooses**  - **When will this be
    used?** ’下拉菜单中的描述”。这些选项类似于可以为主题配置的触发器。

5.  将**描述**设置为 - +++Processes incoming resumes and stores
    candidates in the system+++

    ![](./media/image15.png)

6.  展开**Advanced**，并将优先级设置为10000。这样可以确保面试代理在本次采访前会被用来回答一般性问题。这里也可以设定一个条件，比如确保至少有一个附件。

    ![](./media/image16.png)

7.  确保“**Web
    Search**”开关设置为“**Disabled**”。这是因为我们只想使用父代理提供的信息。选择“**Save**”。

    ![](./media/image17.png)

### 任务4 - 配置恢复上传代理流程

代理在没有工具或主题的情况下无法执行任何作。

我们使用**代理流程工具**而非主题来完成*上传简历*步骤，因为这个多步后台流程需要确定性执行并与外部系统集成。虽然主题是引导对话对话的最佳选择，但代理流程提供了结构化自动化，能够可靠地处理文件处理、数据验证和数据库更新（插入新内容或更新现有内容），而无需依赖用户交互。

1.  在申请接收代理页面中找到“**Tools**”部分。 

    **重要提示：**这不是父代理的工具标签，但如果你在子代理指示下方向下滚动可以找到。

2.  选择 **+ Add**。

    ![](./media/image18.png)

3.  选择 **+ New tool**。

    ![](./media/image19.png)

4.  选择 **Agent
    flow**。代理流程设计器会打开，这里我们会添加上传简易逻辑。  
    ![](./media/image20.png)

5.  选择“**When an agent calls the flow**”，然后选择“ **+ Add an
    input**” 

    ![](./media/image21.png)

6.  为 下表中列出的每个参数添加
    **inputs**。选择表格中显示的正确输入类型，并确保同时添加名称和描述。包含描述很重要，因为这能帮助代理知道该填写哪些内容。

    | **类型**  |  **名称** |  **描述** |
    |:----|:-----|:-------|
    | 文件  |  简历 | 简历PDF文件  |
    | 文本  |  消息 |  从上下文中提取求职信式的信息。消息必须少于2000字符。 |
    | 文本  | 用户邮箱  | 简历来源的邮箱地址。这会是用户在聊天中上传简历，或者如果收到邮件，则是发送邮箱。  |

    ![](./media/image22.png)

7.  选择代理调用流程节点下方的 **+ 图标**，搜索 +++Dataverse
    add+++，然后在 **Microsoft Dataverse** 部分选择“**Add a new
    row** ”操作。

    ![](./media/image23.png)

    ![](./media/image24.png)

    **注意**

    添加动作后，可能会提示你创建新的Dataverse连接。输入连接的任意名称，点击添加即可创建该连接。

8.  将节点命名为 +++Create Resume+++，方法是选择 3 点并选择 **Rename**。
     

    ![](./media/image25.png)

9.  将 **Table name**  设置为“**Resumes**”，然后选择“**Show
    all**”，以显示所有参数。

    ![](./media/image26.png)

10. 设置以下**属性**:

    |  **财产** | **如何设置**  | **细节 / 表达**  |
    |:----|:-----|:------|
    | 简历标题  | 动态数据（闪电图标）  | 当代理调用流程→恢复名称时，如果你看不到恢复名称，请确保你已将上述恢复参数配置为数据类型。  |
    | 求职信  | 表达式（fx 图标）  | if(greater(length(triggerBody()?['text']), 2000), substring(triggerBody()?['text'], 0, 2000), triggerBody()?['text'])  |
    |来源邮箱地址   |  动态数据（闪电图标） |  当代理调用 UserEmail →  流时 |
    | 上传日期  | 表达式（fx 图标）  | utcNow() |

    ![](./media/image27.png)

    ![](./media/image28.png)

    ![](./media/image29.png)

11. 选择“Create Resume”节点下方的**“+”图标**，搜索 +++Dataverse
    upload+++ ，然后选择“**Upload a file or an image** ”操作。

    ![](./media/image30.png)

12. 将节点命名为 +++**Upload Resume File**+++。

    ![](./media/image31.png)

13. 设置以下**属性**:

    |  **财产** | **如何设置**  | **详情**  |
    |:----|:------|:------|
    |  内容名称 | 动态数据（闪电图标）  | 当代理呼叫流程时→ Resume 名称  |
    | 表名  | 选择  |  简历 |
    | 行 ID  |  动态数据（闪电图标） | 创建简历 → 查看更多 → 简历  |
    | 列名  |  选择 | 简历PDF  |
    |  内容 | 动态数据（闪电图标）  | 当代理调用流程时→恢复contentBytes  |

    ![](./media/image32.png)

14. 选择“**Respond to the agent**”**节点**，然后选择“ **+ Add an
    output**”。创建一个具有下表中定义的属性的输出。

    ![](./media/image33.png)

    | **财产**  | **如何设置**  | **详情**  |
    |:-----|:-----|:------|
    | 类型  | 选择  | 文本  |
    |  名称 |  输入 |  ResumeNumber |
    | 价值  |  动态数据（闪电图标） | 创建简历 → 查看更多 → 简历编号  |
    | 描述  |  输入 | 创建的简历的 [ResumeNumber]  |


    ![](./media/image34.png)

15. 在右上角选择“**Save draft** ”

    ![](./media/image35.png)

16. 选择“**Overview** ”选项卡，在“**Details** ”面板中选择“**Edit** ”。按照如下所示填写名称和描述，然后选择“**Save**”

    1.  **流程名称**:+++Resume Upload+++

    2.  **描述**:+++Uploads a Resume when instructed+++

    ![](./media/image36.png)

17. 再次选择“**Designer**”选项卡，然后选择“**Publish**”。

>   ### 任务5 - 将流程连接到你的代理

现在你将发布的流程连接到你的申请接收代理。

1.  返回 **Hiring Agent**，选择“代理”选项卡。打开**Application Intake
    Agents**代理，找到“**Tools**”面板，然后选择“**+Add**”。  
    ![](./media/image38.png)

2.  选择“**Flow**”筛选器，然后选择“**Resume Upload**”流程。 

    ![](./media/image39.png)

3.  选择 **Add and configure**。

    ![](./media/image40.png)

4.  设置以下参数，用于**描述工具以及何时使用该工具**。

    | **参数**  | **价值**  |
    |:----|:-----|
    | 描述  | +++Uploads a Resume when instructed. STRICT RULE: Only call this tool when referenced in the form "Resume Upload" and there are Attachments+++  |
    | 更多详情 → 何时可以使用此工具  |  只有在主题或代理提及时才会被提及 |

    ![](./media/image41.png)

    **注意：**此描述告诉代理何时调用此工具。请注意描述中使用了“strict rule”。这为何时使用此工具提供了额外的限制，在本例中，仅当存在附件且对话上下文为简历上传时才使用此工具。选择何时可以使用此工具也很重要。由于我们正在构建一个多代理系统，并且有一个子代理，因此我们希望确保此工具仅在子代理中调用，而不是在主代理中调用。将该值设置为“only when referenced by topics or agents”即可确保这一点**。**

5.  向下滚动到输入部分，选择** Add Input **以添加以下输入:

    |  **参数** |  **价值** |
    |:----|:-----|
    |  输入→添加输入 | contentBytes  |
    | 输入→添加输入  | 名称  |

    ![](./media/image42.png)

6.  现在我们需要设置输入框的属性。首先是 **contentBytes**
    输入框，它将存储实际的简历文件。在 **contentBytes**
    输入框旁边的“**Fill using** ”下拉菜单中选择“**Custom
    value** ”。在“**Value**”属性中，选择**三个点 (...)**。

    ![](./media/image43.png)

7.  选择“**Formula** ”选项卡。粘贴以下从聊天记录中提取文件的公式，然后单击“**Insert**”按钮。

    +++First(System.Activity.Attachments).Content+++

    ![](./media/image44.png)

8.  现在我们将配置**名称**输入框，它将存储简历文件的名称。该名称也将是硬编码的，因此请在“**Fill
    using** ”列中选择“**Custom value** ”选项。

9.  选择“**Value**”列中的**三个点（...），**粘贴以下公式，该公式可从聊天记录中提取文件名，然后单击“**Insert** ”按钮。

    +++First(System.Activity.Attachments).Name+++

    ![](./media/image45.png)

10. 现在我们来配置“**Message** ”输入框。我们希望使用人工智能动态填充此输入框，因此我们将保持默认设置。选择“**Value**”列中的“**Customize** ”按钮，以便填写更多详细信息，说明如何填充此输入框。

    ![](./media/image46.png)

11. 请在 **Description** 字段输入以下内容。然后选择 **Advanced**。

    **根据上下文提取求职信格式的信息。务必不要提示用户，并根据现有上下文创建至少一份简洁的求职信。严格规定：信息长度必须少于 2000 个字符。**

    **注意**

    填写动态输入的描述是确保代理正确填写输入的关键步骤。

    ![](./media/image47.png)

12. 展开“**Advanced**”部分，配置此输入的其他属性。在“**How many
    reprompts**”部分，选择“**Don't repeat**”。

    ![](./media/image48.png)

    **注意**

    这个设置帮助你定制用户体验，避免客服在无法识别所需数据时重复问同一个问题。

13. 向下滚动至“**No valid entity found** ”部分。在“**Action if no entity
    found**”下拉菜单中选择“**Set variable to value** ”选项。在“**Default
    entity value** ”输入框中输入+++Resume upload+++ 。

    ![](./media/image49.png)

    **注意**

    如果代理无法动态填充该消息输入，该设置允许我们硬编码备份值。

14. 我们将通过在“**Fill using**”列中选择“**Custom
    value**”选项，并在“**Value**”列中选择**三个点（...）**来填充
    **UserEmail** 输入。

    ![](./media/image50.png)

15. 选择“**System**”选项卡并搜索“**User**”。选择“**User.Email** ”变量以获取使用该代理的人员的电子邮件地址。

    ![](./media/image51.png)

16. 选择 **Save**

    ![](./media/image52.png)

### 任务6 - 定义代理指令

在此任务中，您将定义应用接收代理的代理指令。

1.  选择“**Agents**”选项卡，然后选择“**Application Intake
    Agent**”，返回到“**Application Intake Agent**”界面。 

    ![](./media/image53.png)

2.  在**“Instructions**”栏中，粘贴以下清晰的指导，供您的子代理使用。

    ```
    You are tasked with managing incoming Resumes, Candidate information, and creating Job Applications.  
    Only use tools if the step exactly matches the defined process. Otherwise, indicate you cannot help.  

    Process for Resume Upload via Chat  
    1. Upload Resume  
    - Trigger only if /System.Activity.Attachments contains exactly one new resume.  
    - If more than one file, instruct the user to upload one at a time and stop.  
    - Call /Upload Resume once. Never upload more than once for the same message.  

    2. Post-Upload  
    - Always output the [ResumeNumber] (R#####).
    ```

    ![](./media/image54.png)

3.  如果指令中包含斜杠（/），选择紧随/后的文本并选择已解析的名称。为了，

    - System.Activity.Attachments（变量）

    - 上传简历（工具）

    注意：如果你点击说明中的System.Acticvity.Attachements，会看到已解析的名称。你可以选择它。选择后，如果已有文本的任何部分可用，请删除。

    ![](./media/image55.png)

    ![](./media/image56.png)

4.  说明书现在应该是这样的。

    ![](./media/image57.png)

5.  选择 **Save。**

    ![](./media/image58.png)

### 任务7 - 测试你的应用接收代理

现在让我们通过打电话给子代理并按照我们的指示确认代理是否正常工作。

1.  通过选择**“Test**”来切换打开测试面板。

    ![](./media/image59.png)

2.  选择附件图标，选择简历—— AVERY EXAMPLE pdf，点击 **Open**。

    ![](./media/image60.png)

3.  输入消息+++Process these resumes+++，然后点击 **send**。

    ![](./media/image61.png)

4.  代理人随后应发送类似如下的消息：**The resume for Avery Example has
    been successfully uploaded. The resume number is R1001**。

    ![](./media/image62.png)

5.  在 **Activity map** 中，您应该可以看到 **Application Intake Agent** 
    正在处理简历上传。

    ![](./media/image63.png)

6.  如果应用尚未打开，请访问
    +++make.powerapps.com+++。确保右上角的“环境选择器”中已选择 Dev One
    环境。选择 **Apps** → Hiring Hub → 省略号（...）菜单 → **Play**。   
    
    ![](./media/image64.png)

    **注意：**如果播放按钮呈灰色，则表示您尚未发布解决方案。请选择“**Solutions** → **Publish
all customizations**”**。**

7.  在 Power Apps – Hiring Hub
    应用中，导航至“**Resumes**”，并检查简历文件是否已上传，以及求职信是否已正确设置。

    ![](./media/image65.png)

## 练习2：添加面试准备相关代理

现在，让我们创建一个联网代理用于面试准备，并将其添加到您现有的招聘代理中。

### 任务1：创建联网面试代理

1.  在 Copilot Studio
    中，选择左侧导航栏中的“**Agents**”选项卡，然后选择**+ Create blank agent**”旁边的**下拉菜单**，并选择“**Advanced create**”。

    ![](./media/image66.png)

2.  选择 **Solution** 为“**Operative**”，然后选择“**Confirm and
    create**”。

    ![](./media/image67.png)

3.  选择 **Edit**，而不是细节。

    ![](./media/image68.png)

4.  请提供以下信息并选择 **Save**。

    - **名称**: +++Interview Agent+++

    - **描述**: +++Assists with the interview process.+++

    ![](./media/image69.png)

5.  选择“说明”旁边的“**Edit**”，输入以下**说明**，然后选择“**Save**”。

    ```
    You are the Interview Agent. You help interviewers and hiring managers prepare for interviews. You never contact candidates. 
    Use Knowledge to help with interview preparation. 

    The only valid identifiers are:
    - ResumeNumber (ppa_resumenumber)→ format R#####
    - CandidateNumber (ppa_candidatenumber)→ format C#####
    - ApplicationNumber (ppa_applicationnumber)→ format A#####
    - JobRoleNumber (ppa_jobrolenumber)→ format J#####

    Examples you handle
    - Give me a summary of ...
    - Help me prepare to interview candidates for the Power Platform Developer role
    - Create interview assistance for the candidates for Power Platform Developer
    - Give targeted questions for Candidate Alex Johnson focusing on the criteria for the Job Application
    
    How to work:
        You are expected to ask clarification questions if required information for queries is not provided
        - If asked for interview help without providing a job role, ask for it
        - If asking for interview questions, ask for the candidate and job role if not provided.

    General behavior
    - Do not invent or guess facts
    - Be concise, professional, and evidence-based
    - Map strengths and risks to the highest-weight criteria
    - If data is missing (e.g., no resume), state what is missing and ask for clarification
    - Never address or message a candidate

    ```

    ![](./media/image70.png)

6.  确保**关闭** **Web Search**。 

    ![](./media/image71.png)

### 任务2：配置数据访问并发布

在这个任务中，你需要配置数据访问，然后发布代理。

1.  在 **Knowledge** 部分，选择 **+ Add knowledge**。

    ![](./media/image72.png)

2.  选择 **Dataverse**  
    ![](./media/image73.png)

3.  在**搜索框**中，输入+++ppa_+++。这是你之前在实验中导入的表格的前缀。

4.  **选择**全部 5
    个表格（候选人、评估标准、职位申请、职位角色、简历）。选择“**Add to
    agent**”**。**

    ![](./media/image74.png)

5.  选择右上角的 **Settings** 按钮

    ![](./media/image75.png)

6.  确保以下设置已配置。

    - **允许其他代理连接并使用此代理：**开启

    - **运用常识：**关闭

    - **文件上传：**关闭

    - **内容审核级别：**中等

    ![](./media/image76.png)

    ![](./media/image77.png)

    ![](./media/image78.png)

7.  选择“**Save**”，然后选择右上角的 **X** 关闭设置菜单。 

    ![](./media/image79.png)

8.  选择 **Publish**。

    ![](./media/image80.png)

9.  在确认对话框中选择 **Publish**，等待发布完成。

    [](./media/image81.png)

### 任务3：将面试准备代理与你的招聘代理连接起来

在此任务中，您将将面试准备代理与招聘代理连接，实现多代理协调。

1.  返回您的 **Hiring Agent** 页面。选择“**Agents** ”选项卡，然后选择
    **+Add an agent**。

    ![](./media/image82.png)

2.  选择 **Interview Agent**。

    ![](./media/image83.png)

    **注意**

    如果面试代理显示为灰色且无法选择，那说明它没有发布。先回面试代理那里发布。

3.  将 **Description** 设置为，

    +++Assists with the interview process and provides information about Resumes, Candidates, Job Roles, and Evaluation Criteria.+++

    请注意，已检查与该代理的“Pass”对话记录。这使得父代理能够为连接的代理提供完整的上下文。

    选择 **Add and configure**。

    ![](./media/image84.png)

4.  请确保您同时看到 **Application Intake Agent** 和 **Interview
    Agent**。请注意，一位是子专员，另一位是关联专员。

    ![](./media/image85.png)

    ![](./media/image86.png)

### 任务4：测试多智能体协作

1.  通过选择“**Test**”来**切换**打开测试面板。

2.  **上传**其中一个测试恢复，输入以下描述，告诉父代理可以委派给连接代理的内容:

    上传这份简历，然后给我展示一些空缺职位，每个职位都描述了评估标准，然后用这些来匹配至少一个合适的职位，即使不是完全匹配。

    ![](./media/image87.png)

3.  注意招聘代理将上传工作委托给儿童代理，然后让面试代理根据其知识提供摘要和职位匹配。

    ![](./media/image88.png)

4.  尝试用不同的方式询问有关简历、职位描述和评估标准的问题。**例如:**

    +++Give me a summary of active resumes+++

    +++Summarize resume R1006+++

    +++Which active resumes are suitable for the Power Platform Developer role?+++

## 摘要

你成功地将单一的招聘代理转变为一个复杂、多代理协同、具备专业能力的代理。

这是你在这个实验室取得的成就。

**多智能体架构掌握**  
你现在明白了何时使用子代理，何时使用连接代理，以及如何设计可扩展的系统。

**应用接收子代理**  
你已经在招聘代理中添加了一个专门的子代理，负责处理简历、提取候选人数据并在Dataverse中存储信息。

**面试准备相关代理**  
你已经为面试准备搭建了一个可重复使用的联网代理，并成功将其连接到了你的招聘代理。

**代理通信**  
你已经见识过主客服如何与专业客服协调、共享上下文并协调复杂的工作流程。

**自治基础**  
你们的增强版招聘系统现在已经准备好支持我们将在未来任务中添加的高级功能：自主触发、内容审核和深度推理。
