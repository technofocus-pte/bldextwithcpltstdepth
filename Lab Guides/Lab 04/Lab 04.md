# 实验1：打造智能招聘人才招聘代理

在这个实验室中，你将为招聘自动化系统奠定基础。您将首先导入一个预配置的解决方案，其中包含管理候选人、职位和招聘工作流程所需的所有Dataverse表和数据结构。接下来，你将用样本数据填充这些表格，支持本模块的学习，并为测试提供真实情景。最后，你将在Copilot
Studio中创建招聘代理，建立基础的对话界面，这将成为未来任务中所有其他功能的基石。

## 练习1：导入解法

在这个练习中，你将导入一个已有的解决方案。

1.  访问 Copilot Studio 的 +++https://copilotstudio.microsoft.com+++

2.  选择...... 在左侧导航中选择**Solutions。**

    ![](./media/image1.png)

3.  选择“**Import
    solution**”。单击“**Browse**”，选择以“**Operative**”开头的
    **C:\LabFiles** 压缩文件，然后选择“**Open**”。

    ![](./media/image2.png)

    ![](./media/image3.png)

    ![](./media/image4.png)

4.  选择后，选择“**Next**”，然后选择“**Import**”。

    ![](./media/image5.png)

    ![](./media/image6.png)

5.  这大约需要 3 到 5
    分钟。成功后，您将看到一个绿色通知栏，其中包含以下消息："Solution
    "Operative"已成功导入。”

    ![](./media/image7.png)

6.  看到"imported
    successfully"消息后，通过在解决方案列表中选择解决方案的显示名称(**Operative**)来查看您导入的内容。

    ![](./media/image8.png)

7.  请审查解决方案，并确保以下组件已导入。

    ![](./media/image9.png)

8.  点击页面顶部的“Publish all customizations”按钮。

    ![](./media/image10.png)

## 练习2 - 导入样本数据

在这个练习中，你将向上一个练习中导入的一些表格添加样本数据。

1.  从你在上一个练习中导入的解决方案中，选择“**Hiring
    Hub** 模型驱动应用程序”，方法是选中该行前面的勾选标记，然后选择顶部的“**Play**”按钮。

    ![](./media/image11.png)

2.  在左侧导航中选择 **Job
    Roles** 。在命令栏中选择“**More**”图标（上下三个点），然后选择“**Import
    from Excel**”旁边的**右箭头**。

    ![](./media/image12.png)

3.  选择 **Import from CSV**。

    ![](./media/image13.png)

4.  选择“**Choose File**”按钮，从 **C:\LabFiles**
    中选择**job-roles.csv**文件，然后选择**Open**。

    ![](./media/image14.png)

5.  选择“**Next**”。下一步保持默认设置，然后选择“**Review Mapping**”。

    ![](./media/image15.png)

    ![](./media/image16.png)

6.  确保映射正确，然后选择**“Finish Import**”。

    ![](./media/image17.png)

7.  选择 **Done**。这可能需要一些时间，但你可以点击
    **Refresh** 按钮查看导入是否成功。

    ![](./media/image18.png)

    ![](./media/image19.png)

8.  现在，你将导入 **评估标准样本数据**

9.  在左侧导航中选择**Evaluation Criteria**。

10. 像之前一样选择“**Import from CSV**”。选择“**Choose File** ”按钮，从
    **C:\LabFiles** 中选择 **evaluation-criteria.csv** 文件。

    ![](./media/image20.png)

11. 选择 **Next**。保持下一步不变，选择“**Review Mapping**”。

    ![](./media/image21.png)

    ![](./media/image22.png)

12. 现在我们需要对映射关系进行一些补充工作。选择“**Job
    Role**”字段旁边的**放大镜图标。**

    ![](./media/image23.png)

13. 确保这里选中了**Job Title**，如果没有，添加并选择**OK**。

    ![](./media/image24.png)

14. 确保其余映射也正确，然后选择“**Finish Import**”，再选择“**Done**”。

    ![](./media/image25.png)

15. 这可能需要一些时间，但你可以点击 **Refresh **按钮查看导入是否成功。

    ![](./media/image26.png)

## 练习 3 - 创建招聘代理

既然你已经完成了先修课程的设置，就该开始真正的工作了！我们先加入招聘代理吧！

1.  在Copilot Studio中，从左侧面板选择特工。选择 + Create blank
    agent旁边的下拉菜单，选择高级创建。

    ![](./media/image27.png)

2.  在代理设置中，选择 Solution 作为**Operative**，然后选择 **Confirm
    and create**。

    ![](./media/image28.png)

3.  在已创建代理的详细信息中选择“**Edit**”。

    ![](./media/image29.png)

4.  输入名称 +++**Hiring Agent**+++和描述 +++**Central orchestrator for
    all hiring activities**+++并选择**Save**。

    ![](./media/image30.png)

## 摘要

在这个实验室里，你现在需要完成以下任务。

- **情景理解**: 全面了解招聘自动化挑战及您将构建的解决方案。

- **解决方案部署**: 成功导入并配置了招聘管理系统的构建模块。

- **代理创建**:
  构建了一个招聘代理，作为你作为特工学院特工将要构建的场景的起点
