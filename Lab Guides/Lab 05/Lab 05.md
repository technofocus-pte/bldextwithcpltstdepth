# 실습 05 – Safe Travels 에이전트 개선 및 다중 에이전트 오케스트레이션 구현하기

## 목표

이전 실습에서 Copilot Studio에 제공된 템플릿을 사용하여 Safe Travels라는
에이전트를 만들었습니다. 이번 실습에서는 특정 고객의 요구에 맞게 해당
에이전트를 개선하는 방법을 알아봅니다.

이 과정에서 Copilot Studio에서 에이전트 흐름 생성 및 다중 에이전트
오케스트레이션의 개념을 학습합니다.

## 연습 1 – 기존 Safe Travels 에이전트 테스트하기

이 연습에서는 **Safe Travels** 에이전트가 여행 승인 요청 시 어떻게
반응하는지 테스트해 보겠습니다.

1.  브라우저에서 +++https://copilotstudio.microsoft.com+++에서 **Copilot
    Studio**를 엽니다. **Dev One** 환경으로 이동하여 **Safe Travels**
    에이전트를 엽니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  테스트 아이콘을 선택하여 에이전트를 **테스트합니다.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  테스트 창에 +++ Need travel approval +++를 입력하고 **Enter**를
    클릭합니다.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image3.png)

4.  여행 승인을 받기 위해 따라야 할 일반적인 지침 세트를 담당자가
    응답하는 것을 볼 수 있습니다.

    ![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image4.png)

## 연습 2 – 회사별 지식 자산으로 상담원 강화하기

이 연습에서는 Contoso 전용 Travel Policy지식 자산을 추가합니다.

1.  에이전트의 개요 페이지에서 아래로 스크롤하여 **+ Add knowledge**를
    선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

2.  **select to browse** 옵션을 찾아봅니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

3.  **C:\Labfiles** 폴더에서 **Travel Policy.docx**를 선택하고
    **Open**을 클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

4.  **Add**를 클릭하여 파일을 추가합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

    ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image9.png)

5.  파일이 추가되었는지 확인하세요. 상태가 **In progress**에서
    **Ready**로 변경될 때까지 기다린 후 다음 단계로 진행합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

## 연습 3 – Microsoft Teams에서 팀 및 채널 만들기

이 연습에서는 MS Teams에서 여행 승인 요청을 보낼 팀과 채널을 만들어
보겠습니다.

1.  Microsoft Teams를 열고 왼쪽 창에서 **See all your teams** 옵션을
    선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

2.  새로운 팀을 만들려면 **Create team**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  팀 이름을 +++ **HR Team** +++로, 첫 번째 채널 이름을 +++ **Travel
    Approval Channel** +++로 입력하고 **Create**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  HR 팀에 멤버 추가 대화 상자에서 **Skip**를 선택합니다.

    ![A screenshot of a email AI-generated content may be
incorrect.](./media/image15.png)

이제 팀과 채널 생성이 완료되었습니다.

## 연습 4 - 에이전트 흐름 생성하기

이 연습에서는 팀 채널에 여행 요청을 게시하는 새 에이전트
흐름(AgentFlow)을 생성합니다.

1.  왼쪽 창에서 **Flows**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  **New agent flow**을 선택하여 새 흐름을 만듭니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

3.  **Add a trigger**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

4.  **AI capabilities**에서 **When an agent calls the flow**를
    선택합니다.

    ![A screenshot of a web page AI-generated content may be
incorrect.](./media/image19.png)

5.  **+ Add an input**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

6.  **Number**를 선택하고 이름을 +++ **Employee ID** +++로 지정합니다.
    그런 다음 **+ Add an input**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image22.png)

7.  이제 **Text** 입력을 선택하고 +++ **Purpose** +++로 이름을
    지정합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

8.  트리거 노드 아래에서 **Add an action**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

9.  +++**Teams**+++를 검색하고 Teams 작업 그룹에서 **See more**를
    클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

10. **Post message in a chat or channel**를 선택합니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image26.png)

11. **Sign in**을 선택하고 자격 증명을 사용하여 로그인하세요.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

12.  아래 세부 정보를 선택합니다:

    Post as – **User**
    
    Post in – **Channel**
    
    Team – **HR Team**
    
    Channel – **Travel Approval Channel**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image29.png)

13. 메시지 필드에 다음을 입력하십시오.

    ```
    Travel Request from 
    Employee ID - <Employee ID>
    Purpose - <Purpose>
    ```

    아래 스크린샷과 같이 **\<Employee ID\>**와 **\<Purpose\>**을 동적 콘텐츠 변수인 **Employee ID**와 **Purpose**으로 바꾸세요.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

14. 매개변수 탭은 이제 아래와 같이 표시됩니다.

    ![](./media/image32.png)

15. 매개변수 탭을 닫습니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

16. Post message 노드 뒤에 다른 **action**을 추가합니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image34.png)

17. **Skills**아래에서 **Respond to the agent**을 선택합니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image35.png)

18. Add an output를 선택합니다. 이름을 +++ Output +++로 지정하고 값을
    +++Request submitted+++로 입력합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

19. **Save draft**을 클릭하여 흐름을 저장합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

20. 흐름이 ​​저장되면 **Publish**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

21. 흐름이 ​​게시되었는지 확인합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

22. 에이전트 흐름의 **Overview**탭을 클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

23. **Edit**을 선택하고 **Details**창에서 흐름 이름을 +++ Request Travel
    Approval Flow+++로 지정합니다. **Save**을 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

## 연습 5 - 에이전트에 도구로 에이전트 플로우 추가하기

이 연습에서는 플로우 기능을 활용하기 위해 에이전트 Safe Travels에
에이전트 플로우 생성을 추가합니다.

1.  왼쪽 창에서 **Agents**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

2.  **Safe Travels** 에이전트를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

3.  Overview 페이지에서 아래로 스크롤하여 **Add tool**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

4.  생성된 **Request Travel Approval Flow**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

5.  **Add to agent**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

6.  흐름이 ​​추가되면 **agent**의 **Overview** 페이지의 **Tools** 섹션에
    나열됩니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

## 연습 6 - 주제 생성하기

이 연습에서는 생성된 여행 승인 흐름을 사용할 주제를 생성합니다.

1.  상단 메뉴에서 **Topics**를 선택합니다. **+ Add a topic** -\> **Add
    from description with Copilot**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

2.  아래 세부 정보를 입력한 후 **Create**를 선택합니다.

    **Name** - +++Travel Approval+++
    
    **Create a topic to** - +++This topic should get the Employee ID
    (Number) and Purpose of travel (Text) details from the user and invoke
    the Tool "Request Travel Approval Flow"+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

3.  **Topic**는 아래와 같이 생성됩니다.

    ![](./media/image50.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image51.png)

4.  플로우가 실제로 호출되는지 확인합니다. 이 경우, 플로우가
    호출되었음을 나타내는 메시지 노드만 추가됩니다. 이 경우, 해당 메시지
    노드를 삭제하고 사용자에게 목적(Purpose)을 요청한 노드 뒤에 있는
    'Add node' 아이콘을 클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

5.  **Add a tool** -\> **Request Travel Approval Flow**을 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

6.  흐름 변수 **Employee ID**에 대한 변수 **EmployeeID**를 추가합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

7.  마찬가지로 여행 목적을 입력합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  **Send a message**노드를 추가하고 아래 스크린샷과 같이 output 변수를
    추가합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  **Save**을 선택한 다음 **Publish**를 선택하여 에이전트를 게시합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image60.png)

10. 확인 대화 상자에서 **Publish**를 선택합니다.

    ![A close-up of a white background AI-generated content may be
incorrect.](./media/image61.png)

11. 테스트 아이콘을 선택하고 +++ Travel Approval +++을 입력하고 테스트
    창에서 보냅니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

12. 아래 세부 정보를 에이전트에게 제공하여 대화하세요

    Employee ID – +++1234+++
    
    Purpose of travel - +++Client meeting for finalizing proposal of XYZ project+++

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image63.png)

13. 에이전트로부터 **Request submitted**메시지를 받게 됩니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image64.png)

14. 팀 채널을 열면 여행 승인을 위한 세부 정보가 게시된 것을 볼 수
    있습니다.

    ![](./media/image65.png)

## 연습 7 - 휴가 관리 에이전트 만들기 

이 연습에서는 휴가, 직원 휴가 잔액 등에 대한 정보를 파악하는 데 사용할
수 있는 휴가 관리 에이전트를 만들어 보겠습니다.

1.  Copilot Studio 홈페이지에서 **Agents** -\> **+ New agent**를
    선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

2.  **Skip to configure**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

3.  구성 페이지에서 아래 세부 정보를 입력하고 **Create**를 선택합니다.

    - Name - +++Leave Manager Agent+++

    - Description - +++This agent is to track the leaves of all the
      employees, their leave balance and leave history to approve or
      reject any new leave requests.+++

    - Instructions - +++Track the leaves of employees. Track their leave
      balance. Apply/Reject leaves based on their balance.+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

4.  에이전트가 생성되면 개요 페이지에서 아래로 스크롤하여
    **Knowledge**섹션에서 **Add knowledge**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

5.  **select to browse**를 클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

6.  C:\Labfiles에서 **Leave balance Tracker** 파일을 선택하고 **Open**를
    클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

7.  **Add**를 선택하여 추적기를 에이전트에 추가합니다.

    ![](./media/image72.png)

8.  파일이 추가됩니다. 상태가 Ready로 바뀔 때까지 기다린 후 다음 단계로
    넘어갑니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

9.  주제 탭에서 **+ Add a topic** -\> **Add from description with
    Copilot**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

10. 아래 세부 정보를 입력하고 **Create**를 클릭합니다.

    - Name - +++Leave Balance Checker+++
    
    - Create a topic to - +++Get the Employee ID from the user and check and
      reply with the leave balance based on the tracker added as knowledge
      source+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

11. 주제에 직원 ID를 가져오는 노드가 있는지 확인한 다음 save을
    클릭합니다. 여기에는 Emp ID를 가져오는 노드와 잔액을 가져오는 중임을
    알리는 메시지 노드가 있습니다..

    주제를 한 번 확인하고 위에 생성된 노드 외에 생성된 다른 노드를 제거합니다..

    그런 다음 주제를 **저장합니다.**

    ![](./media/image76.png)

12. 테스트 창에서 +++ Check Leave balance +++ 메시지를 보냅니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image77.png)

13. 직원 ID에 +++1234+++를 입력합니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image78.png)

14. 에이전트의 응답을 확인하세요. 이는 에이전트에 추가된 지식 자산에서
    검색됩니다.

    ![A screenshot of a chat AI-generated content may be incorrect.](./media/image79.png)

15. Publish를 선택하고 에이전트가 게시될 때까지 기다리세요.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 연습 8 - Copilot Studio에서 다중 에이전트 오케스트레이션 구현하기

단일 에이전트에 모든 작업을 맡기거나, 연결이 끊긴 에이전트를 개별적으로
관리하는 대신, 이제 Copilot Studio(미리 보기)에서 에이전트들이 서로
작업을 위임하는 다중 에이전트 시스템을 구축할 수 있습니다. 여기에는
Microsoft 365 에이전트 빌더, Microsoft Azure AI Agents Service,
Microsoft Fabric을 기반으로 구축된 시스템이 포함됩니다. 이제 이러한
에이전트들은 시스템, 팀, 워크플로를 아우르는 복잡하고 비즈니스에 중요한
작업을 완료하는 공동의 목표를 달성하기 위해 함께 협력할 수 있습니다.

이 연습에서는 Safe travels 에이전트에 휴가 관리 에이전트를 추가하여 여행
계획 시 휴가에 대한 정보를 파악하는 데 활용할 수 있습니다.

1.  Copilot Studio에서 **Safe Travels** 에이전트를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  먼저 이 에이전트가 휴가에 대해 어떤 정보를 제공할 수 있는지 테스트해
    보겠습니다. 테스트 창에서 +++ Check Leave balance +++을 입력하고
    Enter 키를 누릅니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

3.  담당자가 휴가 잔액 확인 방법에 대한 일반적인 정보를 제공하는 것을 볼
    수 있습니다. 또한 이 과정에서 여행 정책 문서를 참조합니다.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image83.png)

4.  상단 메뉴에서 **에이전트** 탭을 선택하고 **+ Add**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

5.  **Choose how do you want to extend your agent**에서 **Copilot
    Studio**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

6.  목록에서 **Leave Manager Agent**를 선택합니다. 게시된 경우에만
    추가할 수 있습니다. 게시 중이면 잠시 기다려 주세요.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

7.  **Add agent**를 선택하여 이 에이전트를 **Safe Travels**에
    추가합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

8.  에이전트가 추가된 후 몇 분간 기다린 후 **Publish**를 클릭합니다.

    ![](./media/image89.png)

9.  에이전트가 게시된 후 몇 분 더 기다린 후 **Safe Travels agent**의
    테스트 창에 +++ Check Leave balance +++을 입력합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

10. **Leave Manager**에이전트가 자동으로 접속되고, 에이전트가 **Leave
    Manager agent’s topic**에서 **Enter Employee ID**질문으로 응답하는
    것을 확인할 수 있습니다.

11. 직원 ID를 +++1234+++로 입력하면 에이전트가 Leave Manager agent의
    지식 자산을 기반으로 응답하는 것을 확인할 수 있습니다.

    ![](./media/image91.png)

## 요약

이 실습에서는 템플릿을 기반으로 생성된 에이전트를 개별 요구 사항에 맞게
개선하는 방법을 알아보았습니다. 또한 Copilot Studio에서 다중 에이전트
오케스트레이션을 구현하는 방법도 배웠습니다.

