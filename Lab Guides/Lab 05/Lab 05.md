# 실습 – Hiring Agent를 확장 가능한 다중 에이전트 아키텍처로 전환하기

이전 실습에서는 주용 Hiring Agent를 구축해 채용 워크플로우를 관리하는 데
탄탄한 기반으로 마련했습니다. 하지만 한명의 에이전트가 할 수 있는 일에는
한계가 있습니다.

당신의 임무는 **Operation Symphony** 입니다 - 단일 요원을 **multi-agent
system**으로 전환하는 것입니다: 복잡한 채용 문제를 함께 처리하는 전문
요원들의 조직된 팀입니다. 단독 작전에서 특수 임무 부대를 지휘하는
승급으로 생각하세요.

교향악단에서 각 연주자가 완벽한 조화로 연주하듯, 기존 Hiring Agent에 두
가지 중요한 전문가를 추가하게 됩니다: 이력서를 자동으로 처리하는 지원
접수 에이전트와 포괄적인 면접 자료를 작성하는 면접 준비 에이전트입니다.
이 에이전트들은 메인 오케스트레이터 아래에서 원활하게 협력할 것입니다.

멀티 에이전트를 만들면, 에이전트들이 인간의 입력을 기다리는 역할에서
외부 이벤트에 능동적으로 반응하고 감독 없이 지능적인 행동을 취하는
것으로 전환될 것입니다.

*질문에 답*하는 에이전트에서 *필요를 예측*하고 *독립적으로 행동*하는
에이전트로 업그레이드하는 것과 같다고 생각하세요. 이벤트 트리거와
자동화된 워크플로우를 통해 Hiring Agent는 들어오는 이력서 이메일을
감지하고, 첨부파일을 자동으로 처리하며, Dataverse에 데이터를 저장하고,
Microsoft Teams를 통해 인사 채용팀에 알림을 보내며, 당신은 더 가치 있는
업무에 집중할 수 있습니다.

## 목표

이번 업무에서 다음을 배울 것입니다:

1.  **child agents** 대 **connected agents**를 언제 사용해야 하는지

2.  확장 가능한 **multi-agent architectures** 설계 방법

3.  집중된 작업을 위한 **child agents** 생성

4.  에이전트간 **communication patterns** 수립

5.  Application Intake Agent 및 Interview Prep Agent 구축

6.  이벤트 트리거가 사용자 상호작용 없이도 자율 에이전트 행동을 가능하게
    하는 방법

7.  Copilot Studio에서 인터랙티브 에이전트와 자율 에이전트의 차이점

8.  이메일 첨부파일을 자동으로 처리하고 Dataverse에 파일을 업로드하는
    이벤트 트리거 생성하는 방법

9.  알림을 위해 Teams 채널에 적응형 카드를 게시하는 에이전트 플로우 구축
    방법

10. End-to-end 자동화를 위한 이벤트 트리거와 에이전트 플로우 간 데이터
    전달 방법

## Child agent: Application Intake Agent

멀티 에이전트 채용 시스템을 구축하기 시작합시다. 첫 번째 전문가는
**Application Intake Agent**로, 입국 이력서와 후보자 정보를 처리하는
Child agent입니다.

![](./media/image1.png)

**Application Intake Agent 책임**

- 인터랙티브 채팅을 통해 제공된 PDF에서 **이력서 내용을 분석** (앞으로
  미션에서 이력서를 자율적으로 처리하는 방법을 배우게 될 것입니다).

- **구조화된 데이터 추출** (이름, 기술, 경력, 학력)

- 자격증과 자기소개서를 기준으로 채용 **공고에 후보자를 매칭**

- **후보 정보를** Dataverse에 **저장**하여 나중에 처리

- 동일한 지원자를 두 번 생성하지 않도록 **애플리케이션 중복 제거**하고,
  이력서에서 추출한 이메일 주소를 사용해 기존 기록과 대조

**Child agent여야 할 이유**

Application Intake Agent는 child agent로서 완벽하게 어울리는 이유:

- 문서 처리와 데이터 추출에 특화되어 있습니다

- 별도의 출판이 필요하지 않습니다

- 이 시스템은 같은 팀이 관리하는 전체 채용 솔루션의 일부입니다

- 이 명령은 특정 트리거(새 이력서 접수)에 초점을 맞추며, Hiring
  Agent로부터 발동됩니다.

## 연결된 에이전트: Interview Prep Agent

두 번째 전문가는 **Interview Prep Agent**로, 포괄적인 인터뷰 자료를
작성하고 후보자 답변을 평가하는 데 도움을 주는 연결 에이전트입니다.

**Interview Prep Agent 책임**

- 회사 정보, 역할 요구사항, 평가 기준을 포함한 **인터뷰 팩을 생성**

- 특정 역할과 후보자 배경에 맞춘 **면접 질문을 생성**

- 직무 역할과 지원서에 관한 **일반적인 질문에 답변**하여 이해관계자
  소통을 지원

**연결된 에이전트여야 할 이유**

면접 준비 에이전트는 연결된 에이전트가 더 잘 작동하는 이유:

- 인재 확보 팀은 여러 채용 프로세스에서 독립적으로 활용하고 싶어 할 수
  있습니다

- 면접 모범 사례와 평가 기준에 대한 자체 지식 기반이 필요합니다

- 채용 담당자마다 팀에 맞게 그 동작을 맞춤화하고 싶어 할 수 있습니다

- 외부 채용뿐만 아니라 내부 직책에도 재사용할 수 있습니다

## 연습 1 - Application Intake Agent 추가하기

기존 Hiring Agent에 첫 번째 child agent를 추가해 보겠습니다.

### 작업 1 – 솔루션 설정

1.  Copilot Studio에서 왼쪽 탐색에서 Tools 아래의 ellipsis (...)를
    선택하세요.

2.  **Solutions**을 선택하세요.

> ![](./media/image2.png)

3.  **Operative** 솔루션을 위치하고 옆의 **ellipsis (...)**를 클릭하고
    **Set preferred solution**을 선택하세요. 팝업된 대화 상자에서
    **Apply**를 선택하세요. 이렇게 하면 모든 작업이 이 솔루션에 추가될
    수 있습니다.

> ![](./media/image3.png)

4.  Set your preferred solution 대화 상자에서 Apply를 선택하세요 dialog
    box.

![](./media/image4.png)

### 작업 2 – Hiring Agent 지침을 구성하기

1.  Copilot Studio로 **이동하세요**. 오른쪽 상단의 **Environment
    Picker**에서 환격이 선택되었는지 확인하세요.

2.  **Hiring Agent**를 여세요.

3.  에이전트의 **Overview** 탭의 **Instructions** 섹션에서 **Edit**를
    선택하세요.

![](./media/image5.png)

4.  명령어 입력에 다음 명령어를 복사해서 붙여넣으세요.

**You are the central orchestrator for the hiring process. You
coordinate activities, provide summaries, and delegate work to
specialized agents.**

5.  **Save**를 선택하세요.

> ![](./media/image6.png)

6.  회면의 오른쪽 상단에서 **Settings** 버튼을 선택하세요.

> ![](./media/image7.png)

7.  페이지를 검토하고 다음 설정들이 적용되었는지 확인한 후 **Save**를
    선택하세요.

[TABLE]

> ![](./media/image8.png)
>
> ![](./media/image9.png)
>
> ![](./media/image10.png)
>
> ![](./media/image11.png)

8.  오른쪽 상단의 **X** 버튼을 클릭하면 설정 메뉴에서 닫으세요

> ![](./media/image12.png)

### 작업 3 – Application Intake child agent를 추가하기

이 작업에서는 Hiring Agent에 child agent를 추가하게 됩니다.

1.  Hiring Agent (여기서 전문 에이전트를 추가하게 됩니다) 내
    **Agents** 탭으로 **이동**하고 **Add**를 선택하세요.

![](./media/image13.png)

2.  **New child agent**를 선택하세요.

![](./media/image14.png)

3.  에이전트 이름을 +++Application Intake Agent+++로 정하세요

4.  **The agent chooses**를 선택하세요 - **When will this be used?**
    드롭다운의 설명을 바탕으로. 이 옵션들은 주제별로 설정할 수 있는
    트리거와 유사합니다.

5.  **Description**을 +++Processes incoming resumes and stores
    candidates in the system+++로 설정하세요

![](./media/image15.png)

6.  **Advanced**를 확장하고 Priority를 10000로 설정하세요. 이렇게 하면
    나중에 Interview Agent가 일반 질문에 답변하는 데 사용될 수 있습니다.
    여기서도 최소 하나의 부착물이 있어야 한다는 조건을 설정할 수
    있습니다.

![](./media/image16.png)

7.  **Web Search**가 **Disabled**로 설정되는지 확인하세요. 이는 parent
    agent가 제공한 정보만 사용하고 싶기 때문입니다. **Save**를
    선택하세요

![](./media/image17.png)

### 작업 4 – 재개 업로드 에이전트 플로우 구성하기

에이전트는 도구나 주제를 받지 않으면 어떤 행동도 할 수 없습니다.

*Upload Resume* 단계에서는 Topics 대신 **Agent Flow** 도구를 사용하고
있는데, 이 다단계 백엔드 프로세스는 결정론적 실행과 외부 시스템과의
통합이 필요하기 때문입니다. 대화 대화를 안내하는 데 가장 적합한 것은
Topics이지만, Agent Flows는 사용자 상호작용에 의존하지 않고도 파일 처리,
데이터 검증, 데이터베이스 업셋(새 항목 삽입 또는 기존 업데이트 포함)을
신뢰성 있게 처리할 수 있도록 구조화된 자동화를 제공합니다.

1.  Application Intake Agent 페이지에서 **Tools** 섹션을 위치하세요. 

> **중요:** 이것은 parent agent의 Tools 탭이 아니지만, child agent 지침
> 아래로 스크롤하면 찾을 수 있습니다.

2.  **+ Add**를 선택하세요.

> ![](./media/image18.png)

3.  **+ New tool**을 선택하세요.

> ![](./media/image19.png)

4.  **Agent flow**를 선택하세요. Agent Flow 디자이너가 열리고, 여기서
    업로드 이력서 로직을 추가합니다.  
    ![](./media/image20.png)

5.  **When an agent calls the flow** 노드를 선택하고 **+ Add an
    input**를 선택하세요

> ![](./media/image21.png)

6.  아래 표에 나열된 각 Parameters에 대한 **inputs을** 추가. 표에 표시된
    적절한 입력 유형을 선택하고 이름과 설명을 반드시 추가하세요. 설명을
    포함하는 것은 에이전트가 입력 항목을 입력하는 데 도움이 되기 때문에
    중요합니다.

[TABLE]

> ![](./media/image22.png)

7.  에이전트가 플로우 노드를 호출할 때 아래 **+ icon**을
    선택하고 +++Dataverse add+++를 검색하여 **Microsoft
    Dataverse** 섹션에서 **Add a new row** 액션을 선택하세요.

> ![](./media/image23.png)
>
> ![](./media/image24.png)

**참고**

액션을 추가한 후 Dataverse에 새로운 연결을 생성하라는 안내가 뜰 수
있습니다. 연결의 이름을 아무 데나 입력하고 추가를 클릭하면 해당 연결을
생성하세요.

8.  노드를 +++**Create Resume**+++로 이름 정하고 새 점을 선택하고
    **Rename**을 선택하세요.  

> ![](./media/image25.png)

9.  **Table name**을 **Resumes**로 설정하고 **Show all**을 선택하고 모든
    매개변수를 보입니다.

> ![](./media/image26.png)

10. 다음 **속성**을 설정하세요:

[TABLE]

> ![](./media/image27.png)
>
> ![](./media/image28.png)
>
> ![](./media/image29.png)

11. Create Resume 노드에서 **+ icon**을 선택하고 +++Dataverse
    upload+++를 검색하고 **Upload a file or an image** 액션을
    선택하세요.

![](./media/image30.png)

12. 노드 이름을 +++**Upload Resume File**+++로 정하세요.

> ![](./media/image31.png)

13. 다음 **속성**을 설정하세요:

[TABLE]

> ![](./media/image32.png)

14. **Respond to the agent node**를 선택하고 **+ Add an output**를
    선택하세요. 아래 표에 정의된 속성으로 출력을 생성하세요.

> ![](./media/image33.png)

[TABLE]

> ![](./media/image34.png)

15. 오른쪽 상단에서 **Save draft**를 선택하세요

> ![](./media/image35.png)

16. **Overview** 탭을 선택하고 **Details** 패널에서 **Edit**를
    선택하세요. 아래 이름과 설명을 입력하고 **Save**를 선택하세요

    1.  **Flow name**:+++Resume Upload+++

    2.  **Description**:+++Uploads a Resume when instructed+++

> ![](./media/image36.png)

17. **Designer** 탭을 다시 선택하고 **Publish**를 선택하세요.

> ![](./media/image37.png)

### 작업 5 – 에이전트에 플로우를 연결하기

이제 게시된 플로우를 Application Intake Agent에 연결하면 됩니다.

1.  **Hiring Agent**로 다시 돌아가고 **Agents** 탭을 선택하세요.
    **Application Intake Agent**를 열고 **Tools** 패널을 위치하고
    **+Add**를 선택하세요.  
    ![](./media/image38.png)

2.  **Flow** 필터를 선택하고 **Resume Upload** 플로우를 선택하세요.

> ![](./media/image39.png)

3.  **Add and configure**를 선택하세요.

> ![](./media/image40.png)

4.  **Description** 및 **when the tool should be used**에 대해 다음
    매개변수를 설정하세요.

[TABLE]

> ![](./media/image41.png)
>
> **참고:** 이 설명은 에이전트가 언제 이 도구를 호출해야 하는지
> 알려줍니다. 설명에서 '엄격한 규칙'이라는 표현이 사용된 것을
> 주목하세요. 이 방법은 첨부파일이 있고 대화의 맥락이 이력서 업로드일
> 때만 도구를 언제 사용해야 하는지에 대한 추가 보호 조치를 제공할 수
> 있습니다. 이 도구를 언제 사용할 수 있을지 선택하는 것도 중요합니다.
> 멀티 에이전트 시스템을 구축하고 자식 에이전트가 있기 때문에, 이 도구는
> 메인 에이전트가 아닌 자식 에이전트에서만 호출되도록 하고 싶습니다.
> 값을 '주제나 에이전트가 참조할 때만'으로 설정하면 이를 보장합니다.

5.  입력 섹션으로 스크롤하여 **Add Input**를 선택해 다음 입력을
    추가하세요:

[TABLE]

> ![](./media/image42.png)

6.  이제 입력의 속성을 설정해야 합니다. 먼저 **contentBytes** 입력부터
    시작하겠습니다. 이 입력은 실제 재개 파일을 저장합니다.
    **contentBytes** 입력 옆에 있는**Fill using** 드롭다운에서 **Custom
    value**를 선택하세요. **Value** 속성에서 **three dots (...)**를
    선택하세요.

> ![](./media/image43.png)

7.  **Formula** 탭을 선택하세요. 다음 공식에 첨부해서 채팅에서 파일을
    추출하고 **Insert** 버튼을 클릭하세요.

+++First(System.Activity.Attachments).Content+++

> ![](./media/image44.png)

8.  이제 이력서 파일 이름을 저장하는 **name** 입력을 설정할 것입니다. 이
    역시 하드코딩되어 있으니, **Fill using** 열에서 **Custom value**를
    선택하세요.

9.  **Value** 열에서 **three dots (...)**를 선택하고 채팅에서 파일
    이름을 추출하는 다음 공식을 붙여넣고 **Insert **버튼을 클릭하세요.

+++First(System.Activity.Attachments).Name+++

> ![](./media/image45.png)

10. 이제 **Message** 입력을 구성할 것입니다. 이 글은 AI로 동적으로
    채우고 싶어서 채우기는 그대로 두겠습니다. **Value** 열에서
    **Customize** 버튼을 선택하면 이 서류를 어떻게 작성해야 하는지에
    대한 추가 세부사항을 작성할 수 있습니다.

![](./media/image46.png)

11. 입력의 **Description** 필드에서 다음을 입력하세요. **Advanced**를
    선택하세요.

**Extract a cover letter style message from the context. Be sure to
never prompt the user and create at least a minimal cover letter from
the available context. STRICT RULE - the message must be less than 2000
characters.**

**참고**

동적으로 입력된 입력에 대한 설명을 작성하는 것은 에이전트가 입력을
올바르게 입력할 수 있도록 하는 데 매우 중요한 단계입니다.

> ![](./media/image47.png)

12. **Advanced** 섹션을 확장하여 이 입력에 대한 추가 속성을 설정하세요.
    **How many reprompts** 섹션에서 **Don't repeat**를 선택하세요

> ![](./media/image48.png)

**참고**

이 설정은 에이전트가 필요한 데이터를 식별하지 못할 경우 같은 질문을 여러
번 하지 않도록 사용자 경험을 맞춤화하는 데 도움을 줍니다.

13. **No valid entity found** 섹션으로 아래로 스크롤하세요. **Action if
    no entity found** 드롭다운에서 **Set variable to value** 옵션을
    선택하세요. **Default entity value** 입력에 +++Resume upload+++를
    입력하세요.

> ![](./media/image49.png)
>
> **참고**
>
> 이 설정을 통해 에이전트가 이 메시지 입력을 동적으로 채울 수 없을 경우
> 백업 값을 하드코딩할 수 있습니다.

14. **Fill using** 열에 **Custom value** 옵션을 선택하면
    **UserEmail** 입력을 체웁니다. **Value** 열에서 **three dots
    (...)**를 선택하세요.

> ![](./media/image50.png)

15. **System** 탭을 선택하고 **User**를 검색하세요.
    **User.Email** 변수를 선택하면 에이전트를 사용하는 사람의 이메일을
    받을 수 있습니다

> ![](./media/image51.png)

16. Save를 선택하세요

> ![](./media/image52.png)

### 작업 6 – 에이전트 지침을 정의하기

이 작업에서는 Application Intake agent에 대한 에이전트 지침을 정의할
것입니다.

1.  Agent탭을 선택하고 Application Intake agent를 선택하여 Application
    Intake agent로 다시 이동하세요.

> ![](./media/image53.png)

2.  Instructions 필드에서 child agent에게 다음과 같은 명확한 지침을
    붙여넣으세요.

> You are tasked with managing incoming Resumes, Candidate information,
> and creating Job Applications.
>
> Only use tools if the step exactly matches the defined process.
> Otherwise, indicate you cannot help.
>
> Process for Resume Upload via Chat
>
> 1. Upload Resume
>
> - Trigger only if /System.Activity.Attachments contains exactly one
> new resume.
>
> - If more than one file, instruct the user to upload one at a time and
> stop.
>
> - Call /Upload Resume once. Never upload more than once for the same
> message.
>
> 2. Post-Upload
>
> - Always output the \[ResumeNumber\] (R#####).
>
> ![](./media/image54.png)

3.  지침에 슬래시(/)가 포함된 경우, / 뒤에 오는 텍스트를 선택하고 해결된
    이름을 선택하세요. 이걸 위해서,

    - System.Activity.Attachments (Variable)

    - Upload Resume (Tool)

> 참고: 설명서에서 System.Acticvity.Attachements를 클릭하면 해결된
> 이름이 표시됩니다. 선택할 수 있습니다. 선택 후 기존 텍스트의 일부가
> 남아 있다면 삭제해 주세요.
>
> ![](./media/image55.png)
>
> ![](./media/image56.png)

4.  이제 설명서는 이렇게 보여야 합니다.

> ![](./media/image57.png)

5.  Save를 선택하세요.

> ![](./media/image58.png)

### 작업 7 – Application Intake Agent를 테스트하기

이제 자식 에이전트에게 전화해서 지시를 따라 정상적으로 작동하는지 확인해
보겠습니다.

1.  테스트 패널을 열려면 Test를 선택해 열어보세요.

> ![](./media/image59.png)

2.  첨부서 아이콘을 선택하고, 이력서를 선택하고 – AVERY EXAMPLE pdf,
    Open을 클릭하세요.

> ![](./media/image60.png)

3.  +++Process these resumes+++메시지를 제공하고 send를 누르세요.

> ![](./media/image61.png)

4.  에이전트는 The resume for Avery Example has been successfully
    uploaded. The resume number is R1001와 유사한 메시지를 보내야
    합니다. ![](./media/image62.png)

5.  Activity 지도에서 이력서 업로드를 담당하는 Application Intake
    Agent를 볼 수 있을 것입니다.

> ![](./media/image63.png)

6.  앱이 열려 있지 않으면 +++make.powerapps.com+++로 이동하세요. 오른쪽
    상단의 Environment Picker에서 Dev One 환경이 선택되었는지
    확인하세요. Apps → Hiring Hub → ellipsis(...) menu → Play를
    선택하세요  
    ![](./media/image64.png)

참고: 재생 버튼이 비활성화되어 있으면 해결책을 게시하지 않은 상태임을
의미합니다. Solutions → Publish all customizations를 선택하세요.

7.  Power Apps – Hiring Hub 앱에서 Resumes로 이동하고 이력서 파일이
    업로드되어 있고 자기소개서가 그에 맞게 설정되어 있는지 확인하세요.

> ![](./media/image65.png)

## 연습 2: Interview Prep 연결된 에이전트를 추가하기

이제 인터뷰 준비를 위한 연결된 에이전트를 생성하여 기존 Hiring Agent에
추가해 봅시다.

### 작업 1: 연결된 Interview Agent 생성하기

1.  Copilot Studio의 왼쪽 탐색에서 Agents 탭을 선택하고 + Create blank
    agent 옆의 드롭다운을 선택하고 Advanced create를 선택하세요.

> ![](./media/image66.png)

2.  Solution을 Operative로 선택하고 Confirm and create를 선택하세요.

> ![](./media/image67.png)

3.  Details에 Edit를 선택하세요.

> ![](./media/image68.png)

4.  아래 정보를 입력하고 Save를 선택하세요.

    - Name: +++Interview Agent+++

    - Description: +++Assists with the interview process.+++

> ![](./media/image69.png)

5.  Instructions에 Edit를 선택하고 아래 지침을 입력한 후 Save를
    선택하세요.

> You are the Interview Agent. You help interviewers and hiring managers
> prepare for interviews. You never contact candidates.
>
> Use Knowledge to help with interview preparation.
>
> The only valid identifiers are:
>
> - ResumeNumber (ppa_resumenumber)→ format R#####
>
> - CandidateNumber (ppa_candidatenumber)→ format C#####
>
> - ApplicationNumber (ppa_applicationnumber)→ format A#####
>
> - JobRoleNumber (ppa_jobrolenumber)→ format J#####
>
> Examples you handle
>
> - Give me a summary of ...
>
> - Help me prepare to interview candidates for the Power Platform
> Developer role
>
> - Create interview assistance for the candidates for Power Platform
> Developer
>
> - Give targeted questions for Candidate Alex Johnson focusing on the
> criteria for the Job Application
>
> How to work:
>
> You are expected to ask clarification questions if required
> information for queries is not provided
>
> - If asked for interview help without providing a job role, ask for it
>
> - If asking for interview questions, ask for the candidate and job
> role if not provided.
>
> General behavior
>
> - Do not invent or guess facts
>
> - Be concise, professional, and evidence-based
>
> - Map strengths and risks to the highest-weight criteria
>
> - If data is missing (e.g., no resume), state what is missing and ask
> for clarification
>
> - Never address or message a candidate
>
> ![](./media/image70.png)

6.  Web Search가 Disabled되어 있는지 확인하세요.

> ![](./media/image71.png)

### 작업 2: 데이터 액세스 및 게시 구성하기

이 작업에서는 데이터 접근 권한을 설정한 후 에이전트를 게시합니다.

1.  Knowledge 섹션에서 + Add knowledge를 선택하세요.

> ![](./media/image72.png)

2.  Dataverse를 선택하세요  
    ![](./media/image73.png)

3.  Search 상자에서 +++ppa\_+++를 입력하세요. 이전 실습에서 가져온
    테이블의 접두사입니다.

4.  5개의 표 모두 (Candidate, Evaluation Criteria, Job Application, Job
    Role, Resume)를 선택하세요. Add to agent를 선택하세요

> ![](./media/image74.png)

5.  오른쪽 상단의 Settings 버튼을 선택하세요

> ![](./media/image75.png)

6.  다음 설정들이 설정되어 있는지 확인하세요.

    - Let other agents connect to and use this one: On

    - Use general knowledge: Off

    - File uploads: Off

    - Content moderation level: Medium

> ![](./media/image76.png)
>
> ![](./media/image77.png)
>
> ![](./media/image78.png)

7.  Save를 선택하고 오른쪽 상단의 X 버튼을 선택해 settings 메뉴를
    닫으세요.

> ![](./media/image79.png)

8.  Publish를 선택하세요.

> ![](./media/image80.png)

9.  확인 상자에서 Publish를 선택하고 게시가 완료될 때까지 기다리세요.

![](./media/image81.png)

### 작업 3: Interview Prep Agent를 Hiring Agent와 연결하기

이 작업에서는 Interview Prep Agent를 Hiring Agent와 연결하여 다중
에이전트 오케스트레이션을 구현합니다.

1.  Hiring Agent로 다시 돌아가세요. Agents 탭을 선택하고 +Add an agent를
    선택하세요.

> ![](./media/image82.png)

2.  Interview Agent를 선택하세요.

> ![](./media/image83.png)
>
> 참고
>
> Interview Agent가 회색으로 표시되어 선택 불가능하다면, 게시되지 않은
> 것입니다. 먼저 Interview Agent에게 돌아가서 게시하세요.

3.  설명을 다음과 같이 설정하세요,

> Assists with the interview process and provides information about
> Resumes, Candidates, Job Roles, and Evaluation Criteria.
>
> 이 에이전트와의 Pass대화 기록이 확인된 것을 주목하세요. 이를 통해 부모
> 에이전트가 연결된 에이전트에게 완전한 맥락을 제공할 수 있습니다.
>
> Add and configure를 선택하세요.

![](./media/image84.png)

4.  Application Intake Agent 및 Interview Agent 모두를 꼭 보세요. 한
    명은 child이고 다른 한 개의 연결된 행위자라는 점을 주목하세요.

> ![](./media/image85.png)
>
> ![](./media/image86.png)

### 작업 4: 멀티 에이전트 협업 테스트하기

1.  테스트 패널을 열려면 Test를 선택해 열어보세요.

2.  테스트 재개 파일 중 하나를 업로드하고, 다음 설명을 입력하여 parent
    에이전트가 연결된 에이전트에게 위임할 수 있는 작업을 알려줍니다:

> Upload this resume, then show me open job roles, each with a
> description of the evaluation criteria, then use this to match the
> resume to at least one suitable job role even if not a perfect match.
>
> ![](./media/image87.png)

3.  Hiring Agent가 업로드를 child 에이전트에게 위임하고, Interview
    Agent에게 자신의 지식을 바탕으로 요약과 직무 매칭을 요청한 점을
    주목하세요.

> ![](./media/image88.png)

4.  Resumes, Job Roles and Evaluation Criteria에 대해 다양한 질문 방식을
    시도해 보세요. 예시:

> +++Give me a summary of active resumes+++
>
> +++Summarize resume R1006+++
>
> +++Which active resumes are suitable for the Power Platform Developer
> role?+++

## 요약

당신은 단일 Hiring Agent를 전문화된 기능을 갖춘 다중 에이전트 조직으로
성공적으로 탈바꿈시켰습니다.

이 실습에서 이룬 성과는 다음과 같습니다.

멀티 에이전트 아키텍처 숙련도이제 자식 에이전트와 연결 에이전트를 언제
사용해야 할지, 그리고 확장 가능한 시스템을 설계하는 방법을 이해하게
되었습니다.

지원 접수 자식 에이전트 Hiring Agent에 이력서를 처리하고 후보자 데이터를
추출하며 Dataverse에 정보를 저장하는 전문 자식 대리인을 추가하셨습니다.

인터뷰 준비 연결 에이전트 면접 준비를 위해 재사용 가능한 연결 에이전트를
생성하고 Hiring Agent와 성공적으로 연결했습니다.

에이전트 커뮤니케이션 메인 에이전트가 전문 에이전트와 조율하고, 맥락을
공유하며, 복잡한 워크플로우를 조율하는 모습을 보셨을 겁니다.

자율성의 기반강화된 채용 시스템은 이제 앞으로 미션에서 추가할 고급
기능들인 자율 트리거, 콘텐츠 중재, 심층 추론을 위한 준비가 되었습니다.
