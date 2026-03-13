# 실습 – 자율적 시스템으로 hiring agent를 업그레이드하기

이 실습에서는 **event triggers**에 대해 더 깊이 탐구하여 에이전트
시스템을 반응적에서 **autonomous operation** 전환하는 방법을 배웁니다.
에이전트들이 인간의 입력을 기다리는 것에서 외부 사건에 능동적으로
대응하고 감독 없이 지능적인 행동을 취하는 것으로 전환시킬 수 있습니다.

질문에 답하는 에이전트에서 필요를 예측하고 독립적으로 행동하는
에이전트로 업그레이드하는 것과 같다고 생각하세요. 이벤트 트리거와
자동화된 워크플로우를 통해 **Hiring Agent**는 들어오는 이력서 이메일을
**감지**하고, 첨부파일을 **자동으로** 처리하며, **Dataverse**에 데이터를
**저장**하고, **Microsoft Teams**를 통해 **HR 채용팀**에 알림을
제공합니다 - 이 모든 동안 당신은 더 가치 있는 업무에 집중할 수 있습니다

**목표**

이 실습에서 다음을 배울 것입니다:

1.  이벤트 트리거가 사용자 상호작용 없이도 자율 에이전트 행동을 가능하게
    하는 방법

2.  Copilot Studio에서 인터랙티브 에이전트와 자율 에이전트의 차이점

3.  이메일 첨부파일을 자동으로 처리하고 Dataverse에 파일을 업로드하는
    이벤트 트리거 생성하는 방법

4.  알림을 위해 Teams 채널에 적응형 카드를 게시하는 에이전트 플로우 구축
    방법

5.  End-to-end 자동화를 위한 이벤트 트리거와 에이전트 플로우 간 데이터
    전달 방법

**Event trigger란?**

**이벤트 트리거는** 다른 시스템에서 무언가가 발생했을 때 에이전트가
*스스로 행동*할 수 있게 해 줍니다 - 사용자 메시지 없이. "new SharePoint
item", "new email", "Planner task assigned", 또는 시간 기반 반복과 같은
설정된 이벤트가 발생하면, 커넥터가 트리거 페이로드를 에이전트에게
보냅니다. 에이전트는 당신의 지시에 따라 어떤 행동이나 주제를 호출할지
결정합니다.

**인터랙티브 에이전트와 자율 에이전트 - 비교**

이벤트 트리거와 주제 트리거의 차이를 알았으니, 다음으로 인터랙티브
에이전트와 자율 에이전트의 차이에 대해 알아보겠습니다.

Copilot Studio 용어로 '인터랙티브'는 주로 채팅이나 채널 내 **topics**로
소통하는 에이전트를 의미합니다. "자율" 은 **event triggers**를 활용해
사용자 입력 없이도 실행되는 에이전트에 매핑됩니다.

## 연습 1: 호부자 애플리케이션 이메일을 자동화하기

다음으로는 **Hiring Agent**에 이벤트 트리거를 추가하고, 자율 성을 위한
추가 처리를 위해 child** Application Intake Agent**에 에이전트 플로우를
구축할 예정입니다.

**사용 사례**

**HR 리크루터**로서

이 력서가 담긴 이메일이 제 받은편지함에 도착하고 자동으로 Dataverse에
업로드될 때 알림을 **받고 싶습니다**

**그래서** Dataverse에 자동으로 업로드된 지원서 이력서 이메일로 알림을
받을 수 있기 때문입니다

우리는 두 가지 기법을 사용해 이를 달성할 것입니다

1.  이메일이 도착할 때 발생하는 이벤트 트리거,

    - contentType 를 확인해 주세요. 파일의 형식이 PDF와 같을 때입니다.

    - 파일을 추출하여 Dataverse 커넥터를 통해 동작을 통해 Dataverse로
      업로드합니다.

    - 그 후 Dataverse 액션에서 입력 매개변수를 전달하여 에이전트에게
      추가 처리를 위해 프롬프트를 보냅니다.

2.  이벤트 트리거에서 프롬프트가 호출되는 child **Application Intake
    Agent**에 에이전트 플로우가 추가됩니다.

    - 이벤트 트리거 프롬프트에서 전달된 입력 매개변수를 Microsoft Teams
      채널에 게시한 적응형 카드에 사용해 HR 채용 팀에 알림을 보냅니다.
      적응형 카드에는 Dataverse 행으로 연결되는 링크 가 있으며, 이를
      **Hiring Agent**에서 확인할 수 있습니다.

### 작업 1: 이메일로 받은 이력서를 Dataverse에 자동으로 업로드하기

1.  Hiring Agent의 **Overview tab**에서 아래 **Triggers** 섹션으로
    스코롤하여 **+ Add trigger**를 선택하세요.

> ![](./media/image1.png)

2.  트리거 목록이 표시됩니다. **When a new email arrives (V3)**를
    선택하고 **Next**를 선택하세요.

> ![](./media/image2.png)

3.  다음 화면에서 **Continue**를 선택하세요.

![](./media/image3.png)

4.  이제 나열된 앱들의 **Trigger name** 및 **Sign in** 연결 참조를 볼 수
    있습니다. 트리거 이름을 다음과 같이 변경하세요:

+++When a new email arrives from an applicant+++

> **참고:** 목록에 나와 있는 앱들의 연결 참조 옆에 녹색 체크 표시가
> 있는지 확인하세요. 녹색 체크가 보이지 않으면 생략부호(...)로
> 로그인하고 **+ New connection reference**를 선택하여 새 연결 참조를
> 생성하세요.
>
> ![](./media/image4.png)

5.  마지막 단계는 트리거의 입력 속성을 설정하는 것입니다. 다음 속성들을
    다음과 같이 업데이트하세요.

[TABLE]

6.  **Create trigger**를 선택하세요.

> ![](./media/image5.png)

7.  생성되면 트리거가 에이전트에 추가되었다는 확인 메시지가 나타납니다.
    Select **Close**를 선택하고 **Triggers** 섹션에 트리거가 나열됩니다.

> ![](./media/image6.png)

8.  이제 이벤트 트리거를 업데이트하여 자동화 기능을 추가할 예정입니다.
    트리거로 **ellipsis (...)**를 선택하고 **Edit in Power Automate**를
    선택하세요.

> ![](./media/image7.png)

9.  트리거는 Power Automate Maker 포털에서 플로우로 로드됩니다. 이
    기능은 플로우 디자이너로 열려 더 많은 로직과 동작을 추가하여
    자동화를 가능하게 할 것입니다. 트리거는 상단에 나타나고, **Sends a
    prompt to the specified copilot for processing**의 마지막 동작으로
    표시됩니다.

> ![](./media/image8.png)

10. 기본적으로 Power Automate의 **When a new email arrives** 트리거는
    여러 이메일이 동시에 도착할 경우 여러 이메일을 함께 처리하며, 배치
    전체에 대해 한 번만 플로우를 실행합니다.

> 각 이메일마다 플로우가 별도로 실행되도록 하려면 When a new email
> arrives 노드를 선택하고 **Settings**을 선택하세요.
>
> **trigger’s settings**에서 **Split On** 설정을 확성화하고 **dropdown
> array** 필드에서 **@triggerOutputs()?\['body/value'\]**를 선택하세요.
>
> **Split On**은 켜고 array 필드는 @triggerOutputs()?\['body/value'\]로
> 설정된 상태에서 여러 메시지가 동시에 도착하더라도 각 메시지마다
> 플로우가 개별적으로 실행됩니다.
>
> ![](./media/image9.png)

11. 다음으로 첨부파일 유형을 확인하는 로직을 추가해 보겠습니다. 첨부파일
    파일은 업로드하지 않고 첨부파일 .PDF만 업로드하고 싶습니다 (이메일로
    인한 이미지 포함도 있습니다). 트리거 아래의 **+** 아이콘을 선택하고
    **Built in tools** 섹션의 **Control**을 선택하세요.

> ![](./media/image10.png)

12. **Condition** 액션을 선택하세요.

> ![](./media/image11.png)

13. 이제 첨부파일 유형이 .PDF인지 확인하는 조건을 설정할 것입니다.
    왼쪽의 **Choose a value** 필드에서 **lightning bolt icon**을
    선택하세요.

> ![](./media/image12.png)

14. **Search** 필드에 field type +++content type+++를 입력하고
    트리거에서 **Attachments Content-Type** 매개변수를 선택하세요

> ![](./media/image13.png)

15. 여기서 잠시 멈추자면 **For each** 액션이 자동으로 나타난 것을
    눈치채셨을 겁니다.

> ![](./media/image14.png)
>
> 이 동작은 첨부파일 내 각 첨부파일을 반복하는 것을 의미하는데,
> **Attachments Content-Type** 매개변수가 각 첨부파일에 연결되어 있기
> 때문입니다.
>
> 내부적으로는 배열이기 때문에, **Condition** 액션에서 **Attachments
> Content-Type** 매개변수를 선택하면 **For each** 액션이 자동으로
> 추가되었습니다.

16. 다음에 **Condition** 에서 오른쪽에 있는 **Choose a value** 필드를
    선택하고 +++application/pdf+++를 입력하세요.

이렇게 하면 각 파일 첨부파일마다 확장자 형식이 .PDF 있는지 확인합니다.

> ![](./media/image15.png)

17. 이제 **True** 경로를 설정하여 이메일에서 파일을 추출해 **Resume**
    Dataverse 테이블에 업로드할 것입니다.

> **True** 경로 아래에 새 액션을 추가하고 html to text를 검색하세요. +++
> **Html to text**+++ 행동으로 변환하는 동작을 검색하여 선택하세요.
>
> **참고:** Power Automate의 **HTML to text** 동작은 HTML 형식의
> 콘텐츠를 일반 텍스트로 변환하는 데 사용됩니다. 특히 이메일, 웹 콘텐츠,
> API 응답 등 HTML 태그가 포함된 데이터를 받을 때 서식이나 코드 없이
> 읽기 쉬운 텍스트만 추출하고 싶을 때 유용합니다.
>
> ![](./media/image16.png)

18. 다음으로, **Html to text** 동작을 위한 새로운 연결 참조를 생성하려면
    **Create new**를 선택해야 합니다.

> ![](./media/image17.png)

19. 이제 액션을 구성할 수 있습니다. 트리거에서 **Body** 매개변수를
    추가해 봅시다. **Content** 필드에서 오른쪽에 **lightning bolt
    icon** 또는 **fx icon**을 선택하세요.

> ![](./media/image18.png)

20. **Dynamic content** 탭에서 +++body+++를 검색하고 **Body** 매개변수를
    선택하고 **Add**를 선택하세요.

> ![](./media/image19.png)

21. 이 액션 설정은 완료되었으니, 패널을 접기 위해 왼쪽을 가리키는 두
    개의 괄호(«)를 선택해 액션에서 종료하겠습니다.

> ![](./media/image20.png)

22. **Html to text** 작업 아래 **+ icon** 을 선택하면 패널을 불러와
    액션을 추가하세요. **Dataverse add**를 검색하세요. **Add a new
    row** 액션을 선택하세요.

> ![](./media/image21.png)

23. 속성 패널 왼쪽 상단에 +++Add a new Resume row+++를 붙여넣어 행동
    이름을 변경하세요,

**Table name** 매개변수에 res를 검색하고 **Resumes** 테이블을
선택하세요.

> ![](./media/image22.png)

24. 다음으로 **Resume Title** 필드를 선택하고 오른쪽에서 **fx icon**을
    선택하세요.

> ![](./media/image23.png)

25. **Function tab**에서 item() 함수를 사용하는 다음 표현을 입력하세요.

+++item()?\['name'\]+++

> **Resume Title** 매개변수에 표현식을 추가하려면 **Add**를 선택하세요.
>
> ![](./media/image24.png)

**item() 함수에 대한 주의:**

- **Apply to each** 액션을 사용할 때, Power Automate는 컬렉션(배열) 내
  각 요소를 다룹니다.

- 이 기능은 주로 **Apply to each** (또는 **For each), Select, filter
  array** 같은 액션 안에서 사용됩니다.

26. 아직 몇 가지 매개변수를 더 설정해야 해서 **Show all**을 선택하세요.

> ![](./media/image25.png)

27. **Cover Letter** 필드에서 오른쪽에서 **fx icon**을 선택하세요.

> **Function tab**에서 다음 표현을 입력하세요.
>
> +++if(greater(length(body('Html_to_text')), 2000),
> substring(body('Html_to_text'), 0, 2000), body('Html_to_text'))+++
>
> 이 표현식은 **Html to text** 동작의 텍스트가 2000자를 초과하는지
> 검사하며, 초과하면 처음 2000자만 반환합니다. 그렇지 않으면 전체
> 텍스트를 반환합니다.
>
> ![](./media/image26.png)

28. 이제 이 표현은 **Cover Letter**필드에 추가됩니다.

> ![](./media/image27.png)

29. **Source Email Address** 필드에 **lightning bolt icon**을
    선택하고 이메일 주소 값이 포함한 트리거에서 **From** 매개변수를
    선택하세요.

> ![](./media/image28.png)

30. **Upload Date** 필드의 오른쪽에서 **fx icon**을 선택하세요.
    **Function tab**에서 +++utcNow()+++를 입력하고 **Add**를 선택하세요.

**참고: utcNow() 함수란?**

- Power Automate의 utcnow() 함수는 ISO 8601 형식으로 현재 날짜와 시간을
  Coordinated Universal Time (UTC)로 반환합니다. 예를 들어
  2025-09-23T04:32:14Z

> ![](./media/image29.png)

31. 이제**Add a new resume row** 액션 설정이 완료되었으니, 패널을 접어
    나가겠습니다.

> ![](./media/image30.png)

32. 새로운 액션을 추가하려면 **Add a new Resume row** 액션 아래 **+
    icon**을 선택해 패널을 불러와서 액션을 추가합니다. +++**Dataverse
    Upload**+++를 검색하세요. **Upload a file or an image** 액션을
    선택하세요.

> ![](./media/image31.png)

33. 작업의 이름을 +++Upload Resume File+++로 붙여넣어 이름을 변경하세요.

> ![](./media/image32.png)

34. 다음으로 **Content name** 필드를 선택하고 (이미 사용 가능한 제목
    없는 메시지는 삭제하세요) 오른쪽에서 **fx icon**을 선택하세요.

> **Function tab**에서 항목() 함수를 사용하는 다음 표현식을 입력하세요.
> 이 과정에서 현재 항목(첨부 파일)의 이름 속성이 부여됩니다.
>
> +++item()?\['name'\]+++
>
> ![](./media/image33.png)

35. **Table name** 매개변수에서 +++resumes+++를 검색하고
    **Resumes** 테이블을 선택하세요.

> ![](./media/image34.png)

36. 다음으로 **Row ID** 필드를 선택하고 오른쪽에서 **lightning bolt
    icon**을 선택하세요.

> +++ID+++를 검색하고 이 명령에는 PDF 파일을 업로드할 행의 ID 값이
> 포함되어 있기 때문에 **Add a new row** Dataverse 액션에서
> **Resume** 매개변수를 선택하세요.
>
> ![](./media/image35.png)

37. **Column name** 필드를 선택하고 **Resume PDF** 옵션을 선택하세요.

> ![](./media/image36.png)

38. **Content** 필드를 선택하고 오른쪽에서 **fx icon**을 선택하세요.

> **Function tab**에서, 다음 표현식을 입력하는데, 이 표현식은 item ()
> 함수를 사용합니다. 이 기능은 현재 항목(첨부 파일)의 contentBytes
> 속성을 얻습니다. contentBytes는 Base64 문자열로 인코딩된 파일이나
> 첨부파일의 원시 이진 데이터를 의미합니다.
>
> +++item()?\['contentBytes'\]+++
>
> ![](./media/image37.png)

39. 이 액션 설정은 완료되었으니, 패널을 접기 위해 왼쪽을 가리키는 두
    개의 괄호(«)를 선택해 액션에서 종료하겠습니다.

> ![](./media/image38.png)

40. 다음으로 **Sends a prompt to the specified copilot for
    processing**을 선택하고 이 동작을 드래그 앤 드롭하여 조건의
    **True** 경로에서 **Upload Resume File**작업 아래에 위치시킵니다.

> ![](./media/image39.png)

41. 구성하려면 **Sends a prompt to the specified copilot for
    processing**을 선택하세요.

![](./media/image40.png)

42. **Body/message** 필드에서 모든 필드 내용을 선택하고 삭제하세요.

> ![](./media/image41.png)

43. **Body/message** 필드에 다음 텍스트를 복사하고 붙여넣고 **RESUME ID
    PLACEHOLDER**를 강조 표시하고 **lightning** 아이콘을 선택하세요.

> Send \[ResumeId (text)\] = "RESUME ID PLACEHOLDER" and \[ResumeTitle
> (text_1)\] = "RESUME TITLE PLACEHOLDER" and \[ResumeNumber (text_2)\]=
> "RESUME NUMBER PLACEHOLDER" to the Tool "Notify Teams Applicant
> channel" in the child agent "Application Intake Agent"
>
> ![](./media/image42.png)

44. +++resume+++를 검색하고 생성된 Resume 행의 ID 값이 포함한 **Add a
    new row** *Dataverse* 액션에서 **Resume** 매개변수를 선택세요.

> ![](./media/image43.png)

45. RESUME TITLE PLACEHOLDER를 강조 표시하세요. 오른쪽에서 **lightning
    bolt icon**을 선택하세요.

> +++title+++를 검색하고 생성된 Resume 행의 resume 주제 값이 포함한
> **Add a new row Dataverse** 액션에서 **Resume Title** 매개변수를
> 선택하세요.
>
> ![](./media/image44.png)

46. RESUME NUMBER PLACEHOLDER를 강조 표시하세요. 오른쪽에서 **lightning
    bolt icon**을 선택하세요.

> +++resume number+++를 검색하고 생성된 Resume 행의 resume 숫자 값이
> 포함한 **Add a new row Dataverse** 액션에서 **Resume
> Number** 매개변수를 선택하세요.
>
> ![](./media/image45.png)

47. 이 액션과 에이전트 플로우 설정은 완료했습니다. 이제 **Save**을
    선택해 이벤트 트리거 흐름을 저장해 봅시다.

> ![](./media/image46.png)

48. 이제 에이전트 플로우의 세부 사항을 편집하고, 저장 후 **Back**을
    선택해야 합니다.

> ![](./media/image47.png)

49. **Details** 섹션에서 **Edit**를 선택하고 **Plan**을 **Copilot
    Studio** 옵션을 업데이트하세요. **Save**를 선택하세요.

> ![](./media/image48.png)

50. 모달이 나타나 Copilot Studio 요금제로 전환 여부를 확인하라는
    메시지가 나타납니다. **Confirm**을 선택하세요.

> ![](./media/image49.png)

51. 플랜을 **Copilot Studio**로 업데이터되었습니다. 에이전트의 이벤트
    트리거 플로우를 게시해야 하므로 **Edit**를 선택하세요.

> ![](./media/image50.png)

52. **Publish**를 선택하세요.

> ![](./media/image51.png)
>
> 이벤트 트리거 흐름이 이제 공개되었습니다.

![](./media/image52.png)

**child Intake Application Agent**가 호출할 새로운 에이전트 플로 우를
만들어 보겠습니다.

### 작업 2 – 적응형 카드를 사용해 Teams 채널을 알림하기

이제 이벤트 트리거에서 전달된 값을 사용하는 child **Intake Application
Agent**용 새로운 에이전트 플로우를 생성하여 Teams 채널에 적응형 카드를
게시할 예정입니다. 이 적응형 카드는 자동으로 업로드된 PDF를 인사
채용팀에 알리기 위해 검토할 수 있도록 합니다.

#### 작업 2.1: Teams에 채널을 생성하기

이 작업에서는 MS Teams에서 Team과 Channel을 생성하여 이후 이 실험에서
사용할 것입니다.

1.  +++https://teams.microsoft.com+++로 로그인하세요.

2.  **New items drop down**을 선택하고 **New team**을 선택하세요.

![](./media/image53.png)

3.  다음 세부 정보를 제공하고 Create를 선택하세요.

    - Team name - +++HR Team+++

    - First channel name - +++Applicants +++

> ![](./media/image54.png)

4.  다음 화면에서 Skip를 선택하세요.

![](./media/image55.png)

5.  새로운 Team 및 Channel이 생성되었습니다.

![](./media/image56.png)

#### 작업 2.2: 애이전트 플로우를 생성하기

1.  Copilot Studio로 돌아가고 **Hiring Agent**에서 **Agents**탭을
    선택하고 **Application Intake Agent**를 선택하세요

![](./media/image57.png)

2.  **Tools** 아래로 스크롤하고 **+ Add**를 선택하세요.

> ![](./media/image58.png)

3.  **Add tool** 모달이 나타납니다. **+ New tool**을 선택하세요.

> ![](./media/image59.png)

4.  **Agent flow**를 선택하세요.

> ![](./media/image60.png)

5.  **Agent flow designer**가 로드됩니다. **When an agent calls the
    flow** 트리거에서 **+ Add an input**을 선택하세요.

> ![](./media/image61.png)

6.  사용자 입력의 유형으로 **Text**를 선택하세요.

> ![](./media/image62.png)

7.  Input text 필드에 입력 매개변수 이름을 +++ResumeId+++로 입력하세요.

> ![](./media/image63.png)

8.  아래 매개변수에 대해 같은 과정을 반복하세요.

Text - +++ResumeTitle+++

Text - +++ResumeNumber+++

![](./media/image64.png)

![](./media/image65.png)

9.  이제 에이전트 플로우에 적응형 카드를 추가할 것입니다. 이제 에이전트
    플로우에 또 다른 액션을 추가하여 Teams 채널에 적응형 카드를 게시할
    예정입니다.

트리거에서 **+ icon**을 선택하세요.

> ![](./media/image66.png)

10. +++**Microsoft Teams post+++**를 검색하고 **Post card in a chat or
    channel** 액션을 선택하세요.

> ![](./media/image67.png)

11. 로그인한 사용자 계정으로 Microsoft Teams에 대한 연결 참조를 생성해야
    합니다. **Sign in**을 선택하세요.

> ![](./media/image68.png)

12. 사용자 계정을 선택하고 **Allow access**를 선택하세요.

> ![](./media/image69.png)

13. 다음 입력 매개변수에 따라 구성하세요:

[TABLE]

> ![](./media/image70.png)

14. 다음으로 **Adaptive Card** 필드를 구성하겠습니다. **Adaptive
    Card** 필드를 선택하세요.

> ![](./media/image71.png)

15. 아래 코드를 복사해서 적응형 카드 필드에 붙여넣으세요.

> {
>
> "type": "AdaptiveCard",
>
> "speak": "New Resume Uploaded",
>
> "body": \[
>
> {
>
> "inlines": \[
>
> {
>
> "type": "TextRun",
>
> "size": "Small",
>
> "text": "Resume table updated",
>
> "selectAction": {
>
> "url": "https://adaptivecards.io",
>
> "type": "Action.OpenUrl"
>
> }
>
> }
>
> \],
>
> "type": "RichTextBlock"
>
> },
>
> {
>
> "columns": \[
>
> {
>
> "width": "auto",
>
> "items": \[
>
> {
>
> "type": "Icon",
>
> "name": "DocumentArrowUp",
>
> "color": "Accent"
>
> }
>
> \],
>
> "type": "Column"
>
> },
>
> {
>
> "width": "stretch",
>
> "items": \[
>
> {
>
> "size": "Large",
>
> "text": "New Resume Uploaded",
>
> "weight": "Bolder",
>
> "wrap": true,
>
> "type": "TextBlock"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center",
>
> "spacing": "Small",
>
> "type": "Column"
>
> }
>
> \],
>
> "spacing": "Small",
>
> "type": "ColumnSet"
>
> },
>
> {
>
> "type": "Table",
>
> "targetWidth": "AtLeast:Narrow",
>
> "columns": \[
>
> {
>
> "width": 1
>
> },
>
> {
>
> "width": 2
>
> }
>
> \],
>
> "rows": \[
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Resume Number",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "RESUME NUMBER PLACEHOLDER",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Name",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "RESUME NAME PLACEHOLDER",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Status",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Waiting for Review",
>
> "wrap": true
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Due Date",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "May 21, 2023",
>
> "wrap": true
>
> }
>
> \]
>
> }
>
> \]
>
> },
>
> {
>
> "type": "TableRow",
>
> "cells": \[
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "TextBlock",
>
> "text": "Priority",
>
> "wrap": true,
>
> "weight": "Bolder"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> },
>
> {
>
> "type": "TableCell",
>
> "items": \[
>
> {
>
> "type": "ColumnSet",
>
> "columns": \[
>
> {
>
> "type": "Column",
>
> "width": "auto",
>
> "items": \[
>
> {
>
> "type": "Icon",
>
> "name": "Flag",
>
> "color": "Attention",
>
> "size": "xSmall",
>
> "horizontalAlignment": "Center"
>
> }
>
> \]
>
> },
>
> {
>
> "type": "Column",
>
> "width": "stretch",
>
> "items": \[
>
> {
>
> "color": "Attention",
>
> "text": "Important",
>
> "wrap": true,
>
> "spacing": "Small",
>
> "type": "TextBlock"
>
> }
>
> \],
>
> "spacing": "Small"
>
> }
>
> \],
>
> "spacing": "Small"
>
> }
>
> \],
>
> "verticalContentAlignment": "Center"
>
> }
>
> \]
>
> }
>
> \],
>
> "firstRowAsHeaders": false,
>
> "showGridLines": false
>
> },
>
> {
>
> "actions": \[
>
> {
>
> "title": "View Resume",
>
> "type": "Action.OpenUrl",
>
> "url": "https://adaptivecards.io/"
>
> }
>
> \],
>
> "type": "ActionSet",
>
> "targetWidth": "AtLeast:Narrow",
>
> "spacing": "ExtraLarge"
>
> }
>
> \],
>
> "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
>
> "version": "1.5"
>
> }

![](./media/image72.png)

16. 이제 JSON 페이로드의 기존 값을 실제 값이나 동적 콘텐츠로 대체할
    예정입니다.

> 먼저, **selectAction** 속성 내 **URL** **속성**의 **URL**을 업데이트해
> 보겠습니다. 이 URL은 **Hiring Hub** 모델 기반 앱의 **Resumes**시스템
> 뷰 URL로 대체됩니다. 이렇게 하면 채용 담당자가 해당 작업을 선택하고
> 모델 기반 앱의 이력서 시스템 뷰로 안내할 수 있습니다
>
> **current URL** 값을 강조 표시하고 삭제하세요.

![](./media/image73.png)

17. **Hiring Hub**의 모델 기반 앱에서 왼쪽 메뉴를 이용해
    **Resumes** 시스템 뷰로 이동해 URL을 복사하세요. 그 다음 **에이전트
    플로우**로 **돌아가**서 **복사한 URL**을 selectAction 속성 내 URL
    속성에 붙여넣으세요.

> ![](./media/image74.png)

18. 노란색으로 강조된 아래는 **Hiring Hub** 모델 기반 앱의 환경 세부
    정보를 확인할 수 있을 것입니다 .

[TABLE]

> ![](./media/image75.png)

19. 다음으로, 여러 속성에 대해 동적 콘텐츠 값을 추가할 것입니다. 이벤트
    트리거가 자율적으로 생성한 행의 Resume Number 참조를 표시하는
    텍스트부터 시작해 보겠습니다.

액션 패널을 불러오려면 **panel **아이콘을 선택하세요 .

![](./media/image76.png)

20. RESUME NUMBER PLACEHOLDER 텍스트 속성이 보이는 줄까지 스크롤하세요.
    자리 표시자 값을 강조 표시하고 삭제하세요.

![Delete placeholder](./media/image77.png)

21. 이중 따옴표 사이를 클릭하고 오른쪽에서 **lightning bolt icon**을
    선택하세요.

![](./media/image78.png)

22. **Dynamic Content** 탭에서 **ResumeNumber** 매개변수를 선택하세요.

> ![](./media/image79.png)

23. **ResumeNumber** 매개변수는 이제 텍스트 속성에 동적 콘텐츠로
    추가됩니다.

> ![](./media/image80.png)

24. RESUME NAME 자리 표시자에 대해서도 같은 과정을 반복하겠습니다.
    아래로 스크롤하여 RESUME NAME PLACEHOLDER 텍스트 속성이 보이는 줄로
    이동하세요. 임시 값을 선택하고 삭제하세요. 이중 따옴표 사이를
    클릭하고 오른쪽에서 **lightning bolt icon**을 선택하세요.

> ![](./media/image81.png)

25. **Dynamic Content** 탭에서 **ResumeTitle** 매개변수를 선택하세요

> ![](./media/image82.png)

26. **ResumeTitle** 매개변수가 이제 텍스트 속성에 동적 콘텐츠로
    추가됩니다.

> ![](./media/image83.png)

27. 채용 담당자가 이력서를 검토해야 할 시기를 나타내는 **Due Date** 값에
    대해서도 같은 과정을 반복하겠습니다. 2023년 5월 21일자 텍스트 속성이
    보이는 줄까지 스크롤하세요.

![Select Allow access](./media/image84.png)

28. 이 날짜 자리 표시자 값을 삭제하고 이중 따옴표 사이를 클릭한 후
    오른쪽에서 **fx icon**을 선택하세요.

> ![](./media/image85.png)

29. **Function** 탭에서 다음 표현식을 입력하고 **Add**를 선택하세요.

> +++addDays(utcNow(), 3, 'MMM dd, yyyy')+++

이 식은 두 가지 기능을 사용합니다.

[TABLE]

utcNow 값의 경우, 날짜를 월과 날짜로 포맷하고, 그 뒤에 연도를 붙입니다.

> ![](./media/image86.png)

30. 이제 이 표현식이 텍스트 속성에 추가됩니다.

![](./media/image87.png)

31. 마지막으로, JSON 페이로드 하단의 **actions** array 속성 내 **URL
    속성**을 업데이트할 예정입니다. 이 현재의 자리 표시자 URL은 **Hiring
    Hub** 모델 기반 앱의 **Resume row** URL로 대체될 예정입니다. 이렇게
    하면 리크루터가 적응형 카드의 **Action.OpenURL** 액션을 선택하고
    모델 기반 앱에서 **Resume**로 **안내**할 수 있습니다.

> ![](./media/image88.png)

32. **Hiring Hub** 모델 기반 앱에서 왼쪽 메뉴를 통해 **Resumes** 시스템
    뷰의 한 행을 열어보세요. 이력서 행은 모델 기반 앱에서 폼으로
    로드됩니다.

Resume row에 URL을 복사하세요.

![](./media/image89.png)

> ![](./media/image90.png)

33. 그 다음 에이전트 플로우로 돌아가 현재 자리 표시자 URL 값을
    하이라이트한 뒤 **삭제**하세요.

> ![](./media/image91.png)

34. 그 다음 **복사한 URL** 을 URL 속성 내에 붙여넣으세요.

> ![](./media/image92.png)

35. 다음 내용을 보실 수 있습니다. 끝에 있는 GUID ID 값을 삭제하세요. 이
    동적 콘텐츠인 **ResumeId** 매개변수를 교체할 것입니다.

![](./media/image93.png)

36. 오른쪽에서 **lightning bolt icon**을 선택하세요.

**Dynamic Content** 탭에서 **ResumeId** 매개변수를 선택하세요.

> ![](./media/image94.png)

37. **ResumeId**는 동적 콘텐츠로 추가됩니다. 노란색으로 강조된 다음은
    **Hiring Hub** 모델 기반 앱의 환경 정보입니다.

[TABLE]

> ![](./media/image95.png)

38. **Post card in a chat or channel**에서 엽서 설정을 완료했습니다.
    액션 설정 패널에서 **x** 아이콘을 선택하여 👏🏻 종료합니다.

> ![](./media/image96.png)

39. 마지막 액션을 구성하겠습니다. 에이전트에서 처리 종료 텍스트를 보내
    **Respond to the agent**하세요.

**Respond to the agent** 액션에서 **+Add an output**을 선택하세요.

> ![](./media/image97.png)

40. 출력 유형으로 **Text**를 선택하세요.

> ![](./media/image98.png)

41. 다음 세부 정보를 입력하세요

    - Name - +++EndConversation+++

    - Value - +++ Finished+++

> ![](./media/image99.png)

42. 이제 에이전트 플로우 설정을 완료했습니다. 에이전트 플로우를
    저장하려면 **Save draft**을 선택하세요. 저장 시 확인 메시지가
    나타납니다.

> ![](./media/image100.png)

43. 에이전트 플로우를 게시하기 전에 에이전트 플로우의 세부 사항을
    업데이트해야 합니다. **Overview** 탭을 선택하고 **Edit**를
    선택하세요.

> ![](./media/image101.png)

44. 이름을 +++Notify Teams Applicant channel+++로 입력하고
    Description에서 Refresh 아이콘을 선택하고 AI를 사용하여
    업데이트하세요.

![](./media/image102.png)

45. 설명이 채 워지면 **Save **을 선택하여 에이전트 흐름의 최신 세부
    정보를 저장하세요.

> ![](./media/image103.png)

46. **Designer** 탭으로 돌아가고 에이전트 플로우를 게시하려면
    **Publish**를 선택하세요.

> ![](./media/image104.png)

47. 게시되면 확인 메시지가 표시됩니다.

> ![](./media/image105.png)

48. 에이전트 플로우는 이제 **Application Intake Agent**에 도구로
    추가되어야 합니다. **Hiring Agent**로 돌아가고 **Agents** 탭을
    선택하고 **Application Intake Agent**를 선택하세요.

![](./media/image106.png)

49. 에이전트의 **Details** 섹션에서 **Description** 필드를
    업데이트하겠습니다. 다음 내용을 복사해서 붙여넣고 설명 텍스트의 끝을
    붙여넣으세요.

+++and also notifies the Teams Applicant channel+++

**Save**를 선택하세요.

> ![](./media/image107.png)

50. 다음으로, 에이전트 플로우를 도구로 추가하겠습니다. **Tools**
    섹션으로 스크롤 해서 **+ Add**를 선택하세요.

> ![](./media/image108.png)

51. **Flow** 탭을 선택하고 이전에서 생성된 에이전트 플로우를
    선택하세요, **Notify Teams Applicant Channel**.

> ![](./media/image109.png)

52. 다음에 **Add and configure**를 선택하세요.

> ![](./media/image110.png)

53. **Inputs** 색션애서 에이전트 플로우에서 이전에 설정한 세 가지 입력이
    보입니다. 기본적으로 **Fill using** 구성은 **Dynamically fill with
    AI**로 설정되어 있습니다. 이벤트 트리거의 프롬프트에는 AI가 추출할
    매개변수 값이 포함되어 있으므로 이 설정을 그대로 유지하겠습니다.

> ![](./media/image111.png)

54. 이제 도구가 **Application Intake Agent**에 추가되었으니, 에이전트의
    지침도 업데이트해야 합니다. **Back arrow**를 선택하세요.

![](./media/image112.png)

55. **Hiring Agent**의 **Agents** 탭에서 **Application Intake Agent**를
    선택하세요.

![](./media/image113.png)

56. **Instructions** 필드에서 **2.Post-Upload** 지침 다음에 새 줄을
    입력하세요. 다음 지침을 복사해서 붙여넣으세요.

> Process for Resume Upload via Email
>
> 1. When you receive a message, \*\*Send \[ResumeId (text)\] =
> "1680265f-5793-f011-b41b-7c1e525be9f7" and \[ResumeTitle (text_1)\] =
> "TAYLOR TESTPERSON (FICTITIOUS).pdf" and \[ResumeNumber (text_2)\]=
> "R01026" to the Tool "Notify Teams Applicant channel"\*\* in the child
> agent "Application Intake Agent", call \[AGENT FLOW PLACEHOLDER\]
>
> ![](./media/image114.png)

57. \[AGENT FLOW PLACEHOLDER\] 텍스트를 강조 표시하세요.

> ![](./media/image115.png)

58. 앞 슬래시 문자 /를 입력하고 **Notify Teams Applicant Channel**
    도구를 선택하세요.

> ![](./media/image116.png)

59. 에이전트 흐름은 이제 **Application Intake Agent** 가 명령에 따라
    호출하게 되며, 이벤트 트리거에서 마지막 동작(**Sends a prompt to the
    specified copilot for processing**)이 매개변수 값이 포함된
    프롬프트를 에이전트에게 다시 전송한 후 호출됩니다.

**Application Intake Agent**의 업데이트된 지침을 저장하려면 **Save**를
선택하세요.

> ![](./media/image117.png)

60. 에이전트가 저장되면 지침이 업데이터됩니다.

> ![](./media/image118.png)

61. 이제 **Hiring Agent**를 **Publish**해야 합니다. 오른쪽 상단과
    **Publish this agent modal**에서 **Publish**를
    선택하고 **Publish**를 선택하세요.

> ![](./media/image119.png)
>
> ![](./media/image120.png)

62. 게시되면 에이전트가 게시되었다는 확인 메시지가 나타납니다.

> ![](./media/image121.png)

이제 에이전트를 테스트할 수 있어!

## 연습 3: 이벤트 트리거 테스트하기

이 연습에서는 이 실습에서 생성된 이벤트 트리거를 테스트할 것입니다.

1.  이벤트 트리거를 실행하려면 Resume PDF 파일과 함께 이메일을 보내야
    합니다. Outlook에서 새 이메일 메시지를 작성하세요.

[TABLE]

> Dear Hiring Manager,
>
> I am writing to express my interest in the Senior Power Platform
> Engineer position at your organization. With over nine years of
> experience delivering secure and scalable solutions on Microsoft cloud
> platforms, I am confident in my ability to contribute effectively to
> your team.
>
> In my most recent role as Lead Power Platform Engineer, I developed an
> automated resume-intake pipeline, reducing manual triage and improving
> searchability. I have delivered HR case management applications,
> introduced solution-aware flows, and implemented PR checks to enhance
> deployment lead times. My expertise includes Power Apps, Power
> Automate, Power Pages, Dataverse, and a range of Microsoft 365
> services, as well as integration with Graph/REST APIs and Azure
> Functions.
>
> Previously, I developed Teams approvals with adaptive cards, cutting
> approval times to the same day, and created robust error-handling
> frameworks. My background also includes migrating legacy workflows to
> Power Automate and building self-service portals adopted by hundreds
> of employees.
>
> I hold a B.Sc. in Computer Science and am certified as a Power
> Platform Developer (PL-400) and Solution Architect (PL-600). I am also
> passionate about mentoring and have volunteered with local maker
> groups.
>
> Please find my CV attached for your consideration. I would welcome the
> opportunity to discuss how my skills and experience align with your
> needs.
>
> Thank you for your time and consideration.
>
> Kind regards,
>
> Taylor Testperson

2.  **메일함을 작성한 후** 이메일을 보내세요.

> ![](./media/image122.png)

3.  이벤트 트리거 플로우의 +++https://make.powerautomate.com/+++에서
    새로 고침 아이콘을 선택해 전송된 이메일에 성공한 플로우 실행을
    확인하세요. 흐름이 성공한 것을 볼 수 있습니다.

> ![](./media/image123.png)

4.  Copilot Studio의 Hiring Agent에서 **Activity**탭을 선택하세요.
    **Activity**탭이 로드되어 **Hiring Agent**의 모든 활동이 표시됩니다.
    **Automated**라는 이름값의 활동이 **Complete**상태입니다. 이 활동은
    이벤트 트리거와 호출된 에이전트 플로우를 나타냅니다.

> ![](./media/image124.png)

5.  활동을 선택한 후 활동 맵에서 이벤트 트리거를 선택하세요. 오른쪽
    패널에서 프롬프트의 입력 매개변수에 **Dataverse** 행에서 생성된
    Resume ID, Resume Title, Resume Number 매개변수 값이 포함되어 있음을
    알 수 있습니다. **Automate uploading resumes to Dataverse received
    by email**에서 이전에 설정한 동적 콘텐츠 값에서 나온 것입니다.

> ![](./media/image125.png)

6.  **Hiring Hub** 모델 기반 앱으로 돌아가 **Resumes system view**에서
    **Refresh**를 선택하고 새로고침하세요. 이메일로 보낸 이력서용 새로
    생성된 행은 이벤트 트리거를 통해 생성된 상태로 표시됩니다.

> ![](./media/image126.png)

7.  Copilot Studio로 돌아가 활동 지도의 **Application Intake Agent**
    내에서 **Notify Teams Applicant Channel** 에이전트 플로우를
    선택하세요. 오른쪽 패널에서 입력값이 Dataverse 행에서 가져온 것을
    확인할 수 있습니다. 이는 새로 생성된 Dataverse 행의 매개변수 값이
    포함된 이벤트 트리거에서 마지막 동작**(Sends a prompt to the
    specified copilot for processing**)에서 보낸 프롬프트에서 나온
    것입니다. 이것이 이벤트 트리거에서 에이전트 플로우로 매개변수 값을
    전달하는 방법입니다.

> ![](./media/image127.png)

8.  마지막으로, **Microsoft Teams**에서 채널에 게시된 적응형 카드를
    살펴보겠습니다. 채널에서는 Dataverse에서 새로 생성된 이력서 행에
    대한 정보를 보여주는 적응형 카드를 볼 수 있습니다. 적응형 카드 시작
    부분의 하이퍼링크 위에 마우스를 올리면, URL이 적응형 카드의 JSON
    페이로드에서 이전에 설정한 Resumes system view URL임을 확인하세요.

> ![](./media/image128.png)

9.  하이퍼링크를 선택하면 브라우저의 **Hiring Hub** 모델 기반 앱에서
    Resumes system view로 이동하세요.

> ![](./media/image129.png)

10. Microsoft Teams에서 해당 채널에 게시된 적응형 카드로 다시
    이동하세요. 이번에는 적응형 카드의 Action.OpenURL 액션인 **View
    Resume** 위에 마우스를 올려주세요. URL이 적응형 카드의 JSON
    페이로드에서 이전에 설정한 Resumes 행임을 주목하세요.

> ![](./media/image130.png)

11. 액션을 선택하면 브라우저의 Hiring Hub 모델 기반 앱에서 Resume row
    양식으로 이동합니다.

> ![](./media/image131.png)

## 요약

이 실습에서,

1.  Dataverse 매개변수 값을 에이전트 플로우에 전달하는 이벤트 트리거를
    만들었죠.

2.  에이전트 플로우를 구축: Dataverse 매개변수 값을 소모해 Microsoft
    Teams 채널에 적응형 카드를 게시하여 HR 채용팀에 알림을 보냅니다.

3.  업데이트 자식 에이전트 명령어: 이벤트 트리거가 완료된 후 플로우를
    호출하는 것입니다.

4.  이로 인해 **Hiring Agent**는 이력서가 이메일 첨부파일로 접수될
    때마다 자율적으로 업무를 수행하고, 인사 채용 팀에 수동으로 검토를
    요청할 수 있습니다.
