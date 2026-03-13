# 实验室——将招聘代理升级为自主系统

在本实验中，你将深入研究**事件触发器**，从而将你的智能体系统从被动响应提升到**自主运行**。你将使你的智能体不再等待人类输入，而是主动响应外部事件，并在无需监督的情况下采取智能行动。

您可以将其视为从回答问题的客服人员升级为能够预测需求并独立行动的客服人员。通过事件触发和自动化工作流程，您的**招聘代理**将检测收到的简历**邮件**，自动处理附件，将数据存储在
**Dataverse** 数据库中，并通过 **Microsoft Teams**
**通知**您的**人力资源招聘团队**——所有这些都能让您专注于更有价值的任务。

**目标**

在这个实验室里，你会学到东西:

1.  事件触发器如何实现无需用户交互即可自主代理行为

2.  Copilot Studio 中交互代理与自主代理的区别

3.  如何创建自动处理邮件附件并将文件上传到 Dataverse 的事件触发器

4.  如何构建能够向Teams频道发布自适应卡片以发送通知的代理流程

5.  如何在事件触发器和代理流程之间传递数据，实现端到端自动化

**什么是事件触发器？**

*事件触发*器让代理在
其他系统发生事件时自动行动——无需用户消息。当配置事件触发时——例如“新SharePoint项目”、“新邮件”、“规划工具任务分配中”，甚至基于时间的重复事件，连接器会向你的代理发送触发负载。代理人随后按照你的指示决定调用哪些动作或话题。

**交互代理与自主代理——比较**

既然你已经了解了事件触发器和主题触发的区别，接下来让我们了解交互代理和自主代理之间的区别。

用Copilot
Studio的术语来说，“互动”映射到主要通过聊天或频道中话题互动的客服。
“**自主**”映射到那些同样利用**事件触发**器在用户输入下运行的代理。

## 练习一：自动化候选人申请邮件

接下来我们将为**招聘代理**添加事件触发器，并在子**应用接收代理**中构建代理流程，以处理后续的自主处理。

**用例场景**

**作为**人力资源招聘人员

**我希望**当简历邮件到达我的收件箱并自动上传到Dataverse时，能收到通知

**这样我就能**随时收到通过邮件发送的简历，这些简历会自动上传到Dataverse

我们将通过两种技术实现这一点

1.  邮件到达时触发事件，

    - 检查内容，文件的格式类型等于PDF。

    - 通过 Dataverse 连接器的作提取文件并上传到 Dataverse。

    - 然后通过传递Dataverse动作中的输入参数，向代理发送提示，以便进一步处理。

2.  一个代理流会被添加到子**应用接收代理**中，该流程由事件触发器中的提示调用。

    - 利用事件触发提示中传递的输入参数，通过一张自适应卡片发布到Microsoft
      Teams的频道，通知人力资源招聘团队。自适应卡会有一个指向Dataverse行的链接，可以在**招聘代理中查看**。

### 任务一：自动将通过电子邮件收到的简历上传到 Dataverse

1.  在招聘代理中，向下滚动到“**Overview**”**选项卡**中的“**Triggers**”部分，然后选择**+
    Add trigger**。

    ![](./media/image1.png)

2.  此时将显示触发器列表。选择“**When a new email arrives
    (V3)** ”，然后选择“**Next**”。

    ![](./media/image2.png)

3.  在下一个屏幕中选择“**Continue**”。

    ![](./media/image3.png)

4.  现在我们将看到所列应用程序的**触发器名称**和**登录**连接引用。将触发器名称重命名为以下内​​容:

    +++When a new email arrives from an applicant+++

    **注意：**
    确保你看到每个应用连接引用旁的绿色标记。如果没有看到绿色勾选，通过省略号（...）登录，选择 ** + New connection reference** 以创建新的连接引用。

    ![](./media/image4.png)

5.  最后一步是设置触发器的输入属性。将以下属性更新为以下内容，

    | **财产**  | **如何设置**  | **详情**  |
    |:--------|:--------|:-------|
    | 附带附件（可选）  | 下拉菜单  |  是 |
    | 主体滤镜（可选）  |  键盘输入/回车 |  +++Application+++ |
    |  仅带附件（可选） | 下拉菜单  |  是 |

6.  选择 **Create trigger**。

    ![](./media/image5.png)

7.  创建完成后，将显示一条确认消息，提示触发器已添加到代理。选择“**Close**”，触发器将列在“**Triggers**”部分。

    ![](./media/image6.png)

8.  我们现在将更新事件触发器，增加更多自动化功能。选择触发器旁的**省略号（...）**，然后选择
    **Edit in Power Automate**。

    ![](./media/image7.png)

9.  触发器随后将作为流程加载到 Power Automate
    创建门户中。它将打开流程设计器，我们可以在其中添加更多逻辑和操作以实现更高级的自动化。触发器将显示在顶部，其后的是“**Sends
    a prompt to the specified copilot for
    processing** ”作为流程中的最后一个操作。

    ![](./media/image8.png)

10. 默认情况下，如果同时收到多封电子邮件，Power Automate 中的“**When a
    new email
    arrives** ”触发器可能会同时处理多封电子邮件，并且只会为该批次运行一次流程。

    为了确保每封邮件的流程单独运行，请选择“When a new email arrives”节点，选择 **Settings**。

    在**触发器的设置**中启用“**Split On**”设置，并在下**拉数组字段**中选择 **@triggerOutputs()?\['body/value']** 。

    开**Split On**模式，且数组字段设置为@triggerOutputs（）？\['body/value'\]，即使同时收到多个消息，流程也会单独运行。

    ![](./media/image9.png)

11. 接下来，我们添加一些逻辑来检查附件的文件类型。我们只想上传 .PDF
    文件附件，而不是图片附件（图片可能来自电子邮件签名）。选择触发器下方的“**+**”图标，然后在“**Built
    in tools**”部分下选择“**Control** ”。 

    ![](./media/image10.png)

12. 选择 **Condition** 动作。

    ![](./media/image11.png)

13. 现在我们将配置条件，检查文件附件的类型是否为 .PDF。在左侧的“**Choose
    a value**”字段中，选择**闪电图标**。

    ![](./media/image12.png)

14. 在**搜索**字段中输入+++content
    type+++，然后从触发器中选择“**Attachments Content-Type** ”参数。

    ![](./media/image13.png)

15. 我们先暂停一下，你可能注意到 **For each** 动作会自动出现。

    ![](./media/image14.png)

    此操作表示遍历电子邮件中的每个附件，因为 **Attachments Content-Type** 参数与每个附件相关联。 

    从底层来看，它是一个数组，这就是为什么当我们在
    **Condition** 操作中选择**Attachments Content-Type** 参数时，会自动添加“**For each**”操作的原因。

16. 接下来，在“**Condition** ”块右侧的另一个“**Choose a
    value** ”字段中，输入+++application/pdf+++

    这样可以确保每个文件附件都会检查扩展名格式是否.PDF。

    ![](./media/image15.png)

17. 现在我们将配置 **True** 路径，从电子邮件中提取文件并将其上传到
    **Resume** Dataverse 表中。

    在**True**路径下方添加一个新操作，并搜索“html to text”。搜索并选择 +++**Html to text**+++ 操作。 

    **注意：**Power Automate 中的“**HTML to text**”操作用于将 HTML 格式的内容转换为纯文本。当您收到包含 HTML 标签的数据（例如电子邮件、网页内容或 API 响应）并且只想提取可读文本而不包含任何格式或代码时，此功能尤其有用**。** 

    ![](./media/image16.png)

18. 接下来，我们需要通过选择“**Create new**”来为 **Html to
    text** 操作创建一个新的连接引用。

    ![](./media/image17.png)

19. 现在可以配置操作了。让我们从触发器中添加“**Body**”参数。在“**Content** ”字段中，选择右侧的**闪电图标**或
    **fx 图标**。 

    ![](./media/image18.png)

20. 在“**Dynamic
    content** ”选项卡中，搜索“+++body+++”，然后选择“**Body** ”参数，再选择“**Add**”。

    ![](./media/image19.png)

21. 我们已经完成了这个动作的配置，现在选择两个指向左边的角括号（«）来折叠面板，从而退出动作。

    ![](./media/image20.png)

22. 我们将通过选择“**Html to
    text** ”操作下方的**“+”图标**来添加新操作，这将加载添加操作面板。搜索“**Dataverse
    add**”，然后选择“**Add a new row** ”操作。

    ![](./media/image21.png)

23. 在属性面板的左上角粘贴 +++Add a new Resume row+++
    作为名称，重命名该操作,

    对于“**Table name**”参数，搜索 res 并选择“**Resumes**”表。

    ![](./media/image22.png)

24. 接下来选择“**Resume Title**”字段，然后选择右侧的 **fx 图标**。 

    ![](./media/image23.png)

25. 在**Function**选项卡中，输入使用 item() 函数的以下表达式。.

    +++item()?['name']+++

    选择“**Add**”将该表达式添加到“**Resume Title** ”参数中。 

    ![](./media/image24.png)

    **关于 item（） 函数的说明:**

    - 当您使用“**Apply to each** ”操作时，Power Automate
    会遍历集合（数组）中的每个元素。

    - 它最常用于“**Apply to each** （或 **For each**）、**选择** 或 **Filter
    array**”等操作中。

26. 我们还需要配置更多参数，选择**“Show all**”。

    ![](./media/image25.png)

27.  在 **Cover Letter** 栏中，选择右侧的 **fx 图标**。

    在**“Function”**标签页中，输入以下表达式。

    +++if(greater(length(body('Html_to_text')), 2000), substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))+++

    此表达式检查从 **Html to text** 操作返回的文本是否超过 2000 个字符，如果超过，则仅返回前 2000 个字符；否则，返回全文。

    ![](./media/image26.png)

28. 该表达式现在将被添加到 **Cover Letter** 字段中。

    ![](./media/image27.png)

29. 对于“**Source Email
    Address** ”字段，选择**闪电图标**，并从触发器中选择“**From**”参数，因为其中包含电子邮件地址值。

    ![](./media/image28.png)

30. 在“**Upload Date**”字段中，选择右侧的 **fx
    图标**。在“**Function**”**选项卡**中，输入 +++utcNow()+++
    并选择“**Add**”。 

    **注意：什么是utcNow（）函数？**

    - Power Automate中的utcnow（）函数以ISO
    8601格式返回当前协调世界时（UTC）的日期和时间，类似：2025-09-23T04：32：14Z

    ![](./media/image29.png)

31. 我们现在已经完成了“**Add a new Resume
    row** ”作，所以让我们通过折叠面板退出。

    ![](./media/image30.png)

32. 我们将通过点击“**Add a new Resume
    row** ”操作下方的**“+”图标**来添加新操作，这将打开添加操作的面板。搜索+++**Dataverse
    Upload**+++。选择“**Upload a file or an image** ”操作。

    ![](./media/image31.png)

33. 通过将 +++Upload Resume File+++ 作为名称来重命名动作。

    ![](./media/image32.png)

34. 接下来选择“**Content
    name** ”字段（如果已有“未命名”消息，请将其删除），然后选择右侧的
    **fx 图标**。

    在**Function 标签页**中，输入以下使用项项（）函数的表达式。这会获得当前项目（附件文件）的名称属性。

    +++item()?['name']+++

    ![](./media/image33.png)

35. 对于“**Table
    name** ”参数，搜索“+++resumes+++”，然后选择“**Resumes**”表。

    ![](./media/image34.png)

36. 接下来选择 **Row ID** 字段，然后选择右侧的**闪电图标**。

    搜索 +++ID+++，然后从 Dataverse 的“**Add a new row**”操作中选择“**Resume**”参数，因为其中包含要上传 PDF 文件的行的 ID 值。

    ![](./media/image35.png)

37. 选择“**Column name**”字段，然后选择“**Resume PDF** ”选项。

    ![](./media/image36.png)

38. 选择 **Content** 字段，然后选择右侧的 **fx 图标**。 f

    在**Function 标签页**中，输入以下使用项项（）函数的表达式。这会获得当前项目（附件文件）的contentBytes属性。contentBytes 指的是文件或附件的原始二进制数据，编码为 Base64 字符串。
    
    +++item()?['contentBytes']+++

    ![](./media/image37.png)

39. 我们已经完成了这个动作的配置，现在选择两个指向左边的角括号（«）来折叠面板，从而退出动作。

    ![](./media/image38.png)

40. 接下来，选择“**Sends a prompt to the specified copilot for
    processing**”，然后将此操作拖放到条件“**True**”路径中的“**Upload
    Resume File** ”操作下方。.

    ![](./media/image39.png)

41. 选择“**Sends a prompt to the specified copilot for
    processing**”以进行配置。

    ![](./media/image40.png)

42. 在 **Body/message** 字段中，选择所有字段内容并清除/删除。

    ![](./media/image41.png)

43. 将以下文本复制并粘贴到 **Body/message** 字段中，选中“**RESUME ID
    PLACEHOLDER**”，然后选择**闪电**图标。

    ```
    Send [ResumeId (text)] = "RESUME ID PLACEHOLDER" and [ResumeTitle (text_1)] = "RESUME TITLE PLACEHOLDER" and [ResumeNumber (text_2)]= "RESUME NUMBER PLACEHOLDER" to the Tool "Notify Teams Applicant channel" in the child agent "Application Intake Agent"
    ```

    ![](./media/image42.png)

44. 搜索 +++resume+++，然后从 *Dataverse* 操作中 **Add a new
    row**，选择“**Resume** ”参数，因为其中包含已创建的“简历”行的 ID 值。

    ![](./media/image43.png)

45. 请高亮 RESUME TITLE PLACEHOLDER。选择右侧的**闪电图标**。

    搜索 +++title+++，然后从 **Add a new row Dataverse** 操作中选择“**Resume Title** ”参数，因为其中包含已创建的简历行的简历标题值。

    ![](./media/image44.png)

46. 选中“RESUME NUMBER PLACEHOLDER”。选择右侧的**闪电图标**。

    ```
    搜索+++resume number+++，然后从“Add a new row Dataverse ”操作中选择“Resume Number ”参数，因为其中包含已创建的简历行的“简历编号”值。 
    ```

    ![](./media/image45.png)

47. 我们已经完成了此操作和代理流程的配置。现在，让我们通过选择“**Save**”来保存事件触发流程。

    ![](./media/image46.png)

48. 现在我们需要编辑代理流程的细节，保存后选择 **Back**。

    ![](./media/image47.png)

49. 在“**Details**”部分选择“**Edit**”，并将“**Plan**”更新为“**Copilot
    Studio**”选项。选择“**Save**”。

    ![](./media/image48.png)

50. 会显示一个模态，要求你确认是否切换到Copilot Studio套餐。选择
    **Confirm**。

    ![](./media/image49.png)

51. 该计划现已更新为**Copilot Studio**。选择
    **Edit **，因为我们需要为代理发布事件触发流程。

    ![](./media/image50.png)

52. 选择 **Publish**。

    ![](./media/image51.png)

    事件触发流程现已发布。

    ![](./media/image52.png)

让我们继续创建一个新的代理流，该流程将由子**Intake Application Agent**。

### 任务2 - 使用自适应卡通知Teams频道

我们现在将为子 **Intake Application Agent** 创建一个新的代理流程
，使用事件触发器传递的值，将自适应卡发布到Teams频道。这张自适应卡片会提醒人力资源招聘团队自动上传的PDF，以便他们进行审核。

#### 任务2.1：在Teams中创建频道

在这个任务中，你将在MS
Teams中创建一个团队和一个频道，这些将在后续的实验室中使用。

1.  登录 +++https://teams.microsoft.com+++

2.  选择“**New items**”**下拉菜单**，然后选择“**New team**”。

    ![](./media/image53.png)

3.  请提供以下信息并选择创建。

    - 团队名称- +++HR Team+++

    - 第一个频道名称- +++Applicants +++

    ![](./media/image54.png)

4.  在下一界面选择跳过。

    ![](./media/image55.png)

5.  你现在创建了新的团队和频道。

    ![](./media/image56.png)

#### 任务2.2：创建代理流程

1.  返回 Copilot Studio，在 **Hiring
    Agent** 中选择“**Agents**”选项卡，然后选择“**Application Intake
    Agent**”。

    ![](./media/image57.png)

2.  向下滚动到 **Tools** ，选择 **+ Add**。

    ![](./media/image58.png)

3.  此时将出现“**Add tool**”对话框。选择 **+ New tool**。

    ![](./media/image59.png)

4.  选择 **Agent flow**。

    ![](./media/image60.png)

5.  接下来将加载**代理流程设计器**。在“**When an agent calls the flow”**
    触发器中，选择**+ Add an input**。

    ![](./media/image61.png)

6.  选择**Text** 作为用户输入类型。

    ![](./media/image62.png)

7.  在输入文本字段中，输入参数名称为 +++ResumeId+++。

    ![](./media/image63.png)

8.  对以下参数重复同样步骤。

    文本- +++ResumeTitle+++

    文本- +++ResumeNumber+++

    ![](./media/image64.png)

    ![](./media/image65.png)

9.  现在，你要在代理流程中添加一张自适应卡。我们现在会在代理流程中添加另一个动作，将自适应卡片发布到Teams频道。

    选择触发器下方的**+图标**。

    ![](./media/image66.png)

10. 搜索 +++**Microsoft Teams post+++** ，然后选择在**Post card in a
    chat or channel** 操作。

    ![](./media/image67.png)

11. 需要用你登录的用户账户创建一个指向 Microsoft Teams 的连接引用。选择
    **Sign in**。

    ![](./media/image68.png)

12. 选择你的用户账户，然后选择**Allow access**。

    ![](./media/image69.png)

13. 根据以下输入参数进行配置:

    |  **参数** | **如何设置**  | **详情**  |
    |:------|:-------|:------|
    | 发布为  | 下拉菜单  |  选择Flow机器人选项 |
    | 发布  | 下拉菜单  | 下拉菜单	选择Channel选项  |
    | 团队  | 下拉菜单  | 选择 HR Team 选项  |
    |团队   | 下拉菜单  |  甄选 Applicants 者渠道  |

    ![](./media/image70.png)

14. 接下来，我们将配置 **Adaptive Car d**片字段。选择 **Adaptive
    Card** 片字段。 

    ![](./media/image71.png)

15. 复制下面的代码并粘贴到自适应卡字段。

    ```
    {
        "type": "AdaptiveCard",
        "speak": "New Resume Uploaded",
        "body": [
            {
                "inlines": [
                    {
                        "type": "TextRun",
                        "size": "Small",
                        "text": "Resume table updated",
                        "selectAction": {
                            "url": "https://adaptivecards.io",
                            "type": "Action.OpenUrl"
                        }
                    }
                ],
                "type": "RichTextBlock"
            },
            {
                "columns": [
                    {
                        "width": "auto",
                        "items": [
                            {
                                "type": "Icon",
                                "name": "DocumentArrowUp",
                                "color": "Accent"
                            }
                        ],
                        "type": "Column"
                    },
                    {
                        "width": "stretch",
                        "items": [
                            {
                                "size": "Large",
                                "text": "New Resume Uploaded",
                                "weight": "Bolder",
                                "wrap": true,
                                "type": "TextBlock"
                            }
                        ],
                        "verticalContentAlignment": "Center",
                        "spacing": "Small",
                        "type": "Column"
                    }
                ],
                "spacing": "Small",
                "type": "ColumnSet"
            },
            {
                "type": "Table",
                "targetWidth": "AtLeast:Narrow",
                "columns": [
                    {
                        "width": 1
                    },
                    {
                        "width": 2
                    }
                ],
                "rows": [
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Resume Number",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "RESUME NUMBER PLACEHOLDER",
                                        "wrap": true
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Name",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "RESUME NAME PLACEHOLDER",
                                        "wrap": true
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Status",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Waiting for Review",
                                        "wrap": true
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Due Date",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ]
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "May 21, 2023",
                                        "wrap": true
                                    }
                                ]
                            }
                        ]
                    },
                    {
                        "type": "TableRow",
                        "cells": [
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "TextBlock",
                                        "text": "Priority",
                                        "wrap": true,
                                        "weight": "Bolder"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            },
                            {
                                "type": "TableCell",
                                "items": [
                                    {
                                        "type": "ColumnSet",
                                        "columns": [
                                            {
                                                "type": "Column",
                                                "width": "auto",
                                                "items": [
                                                    {
                                                        "type": "Icon",
                                                        "name": "Flag",
                                                        "color": "Attention",
                                                        "size": "xSmall",
                                                        "horizontalAlignment": "Center"
                                                    }
                                                ]
                                            },
                                            {
                                                "type": "Column",
                                                "width": "stretch",
                                                "items": [
                                                    {
                                                        "color": "Attention",
                                                        "text": "Important",
                                                        "wrap": true,
                                                        "spacing": "Small",
                                                        "type": "TextBlock"
                                                    }
                                                ],
                                                "spacing": "Small"
                                            }
                                        ],
                                        "spacing": "Small"
                                    }
                                ],
                                "verticalContentAlignment": "Center"
                            }
                        ]
                    }
                ],
                "firstRowAsHeaders": false,
                "showGridLines": false
            },
            {
                "actions": [
                    {
                        "title": "View Resume",
                        "type": "Action.OpenUrl",
                        "url": "https://adaptivecards.io/"
                    }
                ],
                "type": "ActionSet",
                "targetWidth": "AtLeast:Narrow",
                "spacing": "ExtraLarge"
            }
        ],
        "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
        "version": "1.5"
    }

    ```

    ![](./media/image72.png)

16. 我们现在将用实际值或动态内容替换 JSON 负载中的现有值。

    首先，我们需要更新 **selectAction** 属性中 **url** 属性的 URL。该 **URL** 将被替换为**Hiring Hub** 模型驱动应用程序中“**Resumes**”系统视图的 URL。这样，招聘人员就可以选择该操作并跳转到模型驱动应用程序中的“简历”系统视图。
    高亮当前的 **URL** 值并删除它。


    ![](./media/image73.png)

17. 在 **Hiring Hub** 模型驱动应用程序中，使用左侧菜单导航至“**Resumes**”系统视图并复制
    URL。然后**返回代理流程**，并将**复制的** **URL** **粘贴**到
    selectAction 属性中的 url 属性中。

    ![](./media/image74.png)

18. 你应该会看到以下黄色高亮显示的是**Hiring
    Hub**模型驱动应用的环境细节。

    | **参数**  |  **价值** |  **解释** |
    |:--------|:-------|:---------|:-------|
    | Organization URI  | GUID  | Dataverse/Dynamics 365 环境组织网址  |
    | appid  | GUID  | 要打开特定的模型驱动应用，查询参数是 appid 或 appname。此时使用appid  |
    |  viewid | GUID  | 查询参数，即视图的ID。  |
    
    ![](./media/image75.png)

19. 接下来，我们将为多个属性添加动态内容值。我们先从文本开始，它将显示由事件触发自动创建的行的
    Resume Number 引用。

    选择**面板**图标加载动作面板。

    ![](./media/image76.png)

20. 向下滚动到你看到“RESUME NUMBER
    PLACEHOLDER”文本属性的那一行。高亮占位值并删除它。

    ![Delete placeholder](./media/image77.png)

21. 点击双引号之间，选择右侧的**闪电图标**。

    ![](./media/image78.png)

22. 在“**Dynamic Content**”选项卡中，选择“**ResumeNumber**”参数。 

    ![](./media/image79.png)

23. **ResumeNumber** 参数现在将作为动态内容添加到文本属性中。

    ![](./media/image80.png)

24. 我们会重复同样的步骤，针对简历名称占位符。向下滚动到你看到“RESUME
    NAME
    PLACEHOLDER”文本属性的那一行。高亮占位值并删除它。点击双引号之间，从右侧选择**闪电图标**。

    ![](./media/image81.png)

25. 在“**Dynamic Content** ”选项卡中，选择“**ResumeTitle**”参数。

    ![](./media/image82.png)

26. **ResumeTitle** 参数现在将作为动态内容添加到文本属性中。

    ![](./media/image83.png)

27. 我们将重复同样的步骤，确定截**止日期值**，代表招聘人员应在何时审阅简历。向下滚动到你看到2023年5月21日文本属性的那一行。

    ![Select Allow access](./media/image84.png)

28. 删除这个日期占位符，点击双引号之间，选择右侧的 **fx图标**。

    ![](./media/image85.png)

29. 在 **Function** 标签页中，输入以下表达式并选择 **Add**。

    +++addDays(utcNow(), 3, 'MMM dd, yyyy')+++

    该表达式利用两个函数。

    |  **功能** | **解释**  |
    |:------|:-----|
    |  addDays | 给指定日期添加指定天数，并以字符串格式返回结果日期  |
    |  utcNow | 以字符串形式返回当前的日期和时间，格式为协调世界时（UTC）。  |

    对于UTC现在的值，我们将日期格式化为月份和日期，后面是年份。

    ![](./media/image86.png)

30. The expression will now be added to the text property.

    ![](./media/image87.png)

31. 最后，我们将更新 JSON 有效负载底部 **actions** 数组属性中 **url
    属性**的 **URL**。当前占位符 URL 将被替换为 **Hiring Hub**
    模型驱动应用程序中“**简历”行**的
    URL。这样，招聘人员就可以选择自适应卡片的 **Action.OpenURL**
    操作，并跳转到模型驱动应用程序中的“**Resume**”页面。

    ![](./media/image88.png)

32. 在 **Hiring
    Hub** 模型驱动应用中，使用左侧菜单打开“**Resumes**”系统视图中的一行。该简历行将以表单的形式加载到模型驱动应用中。

    复制简历行的URL。

    ![](./media/image89.png)

    ![](./media/image90.png)

33. 然后返回代理流程，选中当前占位URL值并 **删除** 它。

    ![](./media/image91.png)

34. 然后将**复制的 URL 粘贴**到 **url** 属性中的 url 属性中。

    ![](./media/image92.png)

35. 你应该看到以下内容。删除结尾的GUID
    ID值。我们将替换这个动态内容——**ResumeId**参数。

    ![](./media/image93.png)

36. 从右侧选择闪电图标。

    在 **Dynamic Content **标签中，选择 **ResumeId** 参数。

    ![](./media/image94.png)

37. **ResumeId**将作为动态内容添加。黄色标示的以下内容是**Hiring
    Hub**模型驱动应用的环境详情。

    | **参数**  | **价值**  |  **解释** |
    |:-------|:------------|:------|:-------|
    |  组织 URI | GUID  |  Dataverse/Dynamics 365 环境组织网址 |
    |  appid |  GUID | 要打开特定的模型驱动应用，查询参数是 appid 或 appname。此时使用appid  |
    | id  |GUID   | 查询参数，即Resume行的ID。 |

    ![](./media/image95.png)

38. 我们已经完成了在 **Post card in a chat or channel** 中配置帖子卡片
    👏🏻 选择 **x** 图标退出操作配置面板。

    ![](./media/image96.png)

39. 最后，我们将配置最后一个动作，通过**Respond to the
    agent** 发送文本来响应，以结束处理。

    在“**Respond to the agent** ”动作中，选择 **+Add a output**。

    ![](./media/image97.png)

40. 选择**Text**作为输出类型。

    ![](./media/image98.png)

41. 请输入以下细节

    - 名称 - +++EndConversation+++

    - 价值 - +++ Finished+++

    ![](./media/image99.png)

42. 我们现在已经完成了代理流程的配置。选择 **Save
    draft** 以保存代理流程。保存后会出现确认消息。

    ![](./media/image100.png)

43. 发布代理流程之前，我们需要更新代理流程的详细信息。选择“**Overview**”选项卡，然后选择“**Edit**”。

    ![](./media/image101.png)

44. 输入名称 +++Notify Teams Applicant
    channel+++，然后选择描述下的刷新图标，使用 AI 更新它。

    ![](./media/image102.png)

45. 描述填充后，选择 **Save** 以保存代理流程的更新细节。

    ![](./media/image103.png)

46. 返回 **Designer** 选项卡，选择“**Publish**”以发布代理流程。 

    ![](./media/image104.png)

47. 发布后将显示确认信息。

    ![](./media/image105.png)

48. 现在需要将代理流程作为工具添加到 **Application Intake Agent**
    中。返回**Hiring Agent**，选择“**Agents**”选项卡，然后选择
    **Application Intake Agent**。

    ![](./media/image106.png)

49. 在代理人的“**Details**”部分，我们将更新“**Description**”字段。复制以下内容并粘贴到描述文本的末尾。 

    +++and also notifies the Teams Applicant channel+++

    选择 **Save**。

    ![](./media/image107.png)

50. 接下来，我们将把代理流程添加为一个工具。向下滚动到
    **tools** 部分，然后选择 **+ Add**。 

    ![](./media/image108.png)

51. 选择“**Flow**”选项卡，然后选择之前创建的代理流程“**Notify Teams
    Applicant Channel**”。

    ![](./media/image109.png)

52. 选择 **Add and configure**下一步。

    ![](./media/image110.png)

53. 在“**Inputs**”部分，可以看到我们之前在代理流程中配置的三个输入。默认情况下，“**Fill
    using** ”配置设置为“**Dynamically fill with
    AI**”。我们将保持此设置不变，因为事件触发器的提示将包含 AI
    将提取的参数值。

    ![](./media/image111.png)

54. 现在该工具已添加到 **Application Intake Agent**
    程序中，需要更新代理程序的指令。选择**后退箭头**。

    [](./media/image112.png)

55. 在 **Hiring Agent** 的 **Agents** 选项卡中选择 **Application Intake
    Agent**。

    ![](./media/image113.png)

56. 在“**Instructions**”栏中，在“**2.上传后说明**”之后另起一行。复制并粘贴以下说明。

    ```
    Process for Resume Upload via Email
1. When you receive a message, **Send [ResumeId (text)] = "1680265f-5793-f011-b41b-7c1e525be9f7" and [ResumeTitle (text_1)] = "TAYLOR TESTPERSON (FICTITIOUS).pdf" and [ResumeNumber (text_2)]= "R01026" to the Tool "Notify Teams Applicant channel"** in the child agent "Application Intake Agent", call [AGENT FLOW PLACEHOLDER]

    ```
    
    ![](./media/image114.png)

57. 高亮\[AGENT FLOW PLACEHOLDER\] 文本。

    ![](./media/image115.png)

58. 输入正斜杠字符 /，然后选择“**Notify Teams Applicant
    Channel** ”工具。

    ![](./media/image116.png)

59. 现在，应用 **Application Intake
    Agent** 将按照指示调用代理流程，在事件触发器中的最后一个操作（**向指定的
    copilot 发送提示进行处理**）之后，将包含参数值的提示发送回代理。

    选择“**Save**”以保存更新后的 **Application Intake Agent** 指令。

    ![](./media/image117.png)

60. 一旦代理被保存，说明将会更新。

    ![](./media/image118.png)

61. 现在我们需要**发布** **Hiring Agent**
    信息。选择右上角的“**Publish**”，然后在出现的“**Publish this agent
    modal **”对话框中选择“**Publish**”。![](./media/image119.png)

    ![](./media/image120.png)

62. 发布后，会出现确认提示，表示代理已被发布。

    ![](./media/image121.png)

    我们现在可以测试该药剂了！

## 练习 3：测试事件触发

在这个练习中，你将测试实验室中创建的事件触发器。

1.  要执行事件触发器，需要发送一封带有简历PDF文件的电子邮件。在Outlook中，撰写一封新的电子邮件。

    | **电子邮件组件**  |  **详情** |
    |:-----|:----|
    | 致获奖者  | 用你登录的用户账户作为数值  |
    | 文件附件  |  上传 TAYLOR TESTPERSON (FICTITIOUS) 文件 |
    | 主题  | +++Job Application+++  |
    | 正体  | 请复制粘贴以下内容作为邮件正文  |


    ```
    Dear Hiring Manager,

    I am writing to express my interest in the Senior Power Platform Engineer position at your organization. With over nine years of experience delivering secure and scalable solutions on Microsoft cloud platforms, I am confident in my ability to contribute effectively to your team.

    In my most recent role as Lead Power Platform Engineer, I developed an automated resume-intake pipeline, reducing manual triage and improving searchability. I have delivered HR case management applications, introduced solution-aware flows, and implemented PR checks to enhance deployment lead times. My expertise includes Power Apps, Power Automate, Power Pages, Dataverse, and a range of Microsoft 365 services, as well as integration with Graph/REST APIs and Azure Functions.

    Previously, I developed Teams approvals with adaptive cards, cutting approval times to the same day, and created robust error-handling frameworks. My background also includes migrating legacy workflows to Power Automate and building self-service portals adopted by hundreds of employees.

    I hold a B.Sc. in Computer Science and am certified as a Power Platform Developer (PL-400) and Solution Architect (PL-600). I am also passionate about mentoring and have volunteered with local maker groups.

    Please find my CV attached for your consideration. I would welcome the opportunity to discuss how my skills and experience align with your needs.

    Thank you for your time and consideration.

    Kind regards,
    Taylor Testperson

    ```

2.  邮件从邮箱**发送**。

    ![](./media/image122.png)

3.  在事件触发流程的 +++https://make.powerautomate.com/+++
    中，选择刷新图标以查看发送邮件成功运行的流程。你可以看到这股流动已经成功了。

    ![](./media/image123.png)

4.  返回 Copilot
    Studio，在招聘代理中选择“**Activity**”选项卡。“**Activity**”选项卡将加载，其中显示**Hiring
    Agent**的所有活动。其中会有一个名为“**Automated**”且状态为“**Complete**”的活动。此活动代表触发的事件以及调用的代理流程。

    ![](./media/image124.png)

5.  选择活动，然后在活动地图中选择事件触发器。在右侧面板中，请注意提示中的输入参数包含从已创建的
    **Dataverse** 行中获取的“简历
    ID”、“简历标题”和“简历编号”参数值。这些值来自之前在“**Automate
    uploading resumes to Dataverse received by
    email**”中配置的动态内容值。

    ![](./media/image125.png)

6.  返回 **Hiring Hub** 模型驱动应用，在 **Resumes system view**
    中，选择“**Refresh**”以刷新视图。现在，通过电子邮件发送的简历的新创建行将显示出来，因为它是通过事件触发器创建的。

    ![](./media/image126.png)

7.  返回 Copilot Studio，在活动地图的“**Application Intake
    Agent**”中选择“**Notify Teams Applicant
    Channel** ”代理流程。在右侧面板中，请注意输入值来自 Dataverse
    行。这是由事件触发器中最后一个操作（**Sends a prompt to the
    specified copilot for
    processing**）发送的提示信息，该事件触发器包含来自新创建的 Dataverse
    行的参数值。这就是我们如何将参数值从事件触发器传递到代理流程的方法。

    ![](./media/image127.png)

8.  最后，我们来看一下发布到 **Microsoft Teams**
    频道中的自适应卡片。在频道中，我们会看到一张自适应卡片，它显示了
    Dataverse
    中新创建的简历行的信息。将鼠标悬停在自适应卡片开头的超链接上，你会发现该
    URL 是我们之前在自适应卡片的 JSON 有效负载中配置的简历系统视图 URL。

    ![](./media/image128.png)

9.  选择超链接后，您将被引导到浏览器中**Hiring
    Hub**模型驱动应用中的简历系统视图。

    ![](./media/image129.png)

10. 返回Microsoft
    Teams中该频道发布的自适应卡片。这次，将鼠标悬停在**“View
    Resume**”上，即自适应卡的
    Action.OpenURL作。注意URL是我们之前在自适应卡JSON负载中配置的Resumes行。

    ![](./media/image130.png)

11. 选择作后，你会被引导到浏览器中 Hiring Hub
    模型驱动应用中的“简历”行表单。

    ![](./media/image131.png)

## 摘要

在这个实验室里，

1.  你创建了一个事件触发器，将Dataverse参数值传递给代理流程。

2.  构建了代理流程：消耗Dataverse参数值，将自适应卡片发布到Microsoft
    Teams的某个渠道，以通知人力资源招聘团队。

3.  更新的子代理指令：事件触发完成后调用流程。

4.  这使得 **Hiring Agent**
    能够在收到简历时自主工作，并通知人力资源招聘团队进行人工审核。
