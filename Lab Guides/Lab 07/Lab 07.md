# 실습 07 – 개인 맞춤형 쇼핑 도우미 생성

## 목표

이 실습의 목표는 Contoso Electronics를 위한 개인 맞춤형 쇼핑 에이전트를
만드는 것입니다. 에이전트는 Dataverse 테이블을 지식 소스로 사용하며,
고객의 최신 쇼핑 이력을 기반으로 적절한 제품 카테고리를 제안하고 쇼핑
전반에 걸쳐 지원 역할을 수행합니다.

## 연습 1 – Dataverse 테이블 만들기

이 연습에서는 **Customer**, **Product**, **Order정보**를 저장하기 위해
Dataverse에 테이블을 생성합니다.

1.  +++https://make.powerapps.com+++ 에 관리자 테넌트 계정으로 로그인한
    후,  Dev One 환경을 선택하세요. 왼쪽 탐색 창에서 Tables을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  **+ New table** 옆의 드롭다운을 클릭하고, **Create new tables**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  **Import an Excel file or .csv**를 선택해 새 테이블을 생성하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  Export an Excel or .CSV file에서 **Select from device** 옵션을
    선택하세요.

![A screenshot of a file AI-generated content may be
incorrect.](./media/image4.png)

5.  **C:\Labfiles** 폴더에서**Customers.xlsx** 엑셀 파일을 선택하세요.
    **Import** 를 클릭해 트래커의 데이터를 가져오고 테이블을 생성하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  트래커의 데이터를 기반으로 테이블이 생성됩니다.

7.  여기서는 테이블 이름이 **Customer Record**로 설정되어 있습니다. 자동
    생성되는 이름이므로 사용자마다 다를 수 있으니, 반드시 테이블 이름을
    확인하고 실습 내내 동일한 이름을 사용하세요.

8.  생성된 테이블을 클릭한 후, **View data**를 선택해 테이블에 추가된
    데이터를 확인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  **Save and exit** 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

10. 확인 창에서 **Save and exit**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. 2번부터 10번까지의 과정을 두 번 반복하세요. 첫 번째는 **Product
    Catalog.xlsx** 파일을 사용해 테이블을 생성하고, 두
    번째는 **Orders.xlsx** 파일을 사용해 테이블을 생성하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

12. 이제 세 개의 테이블이 만들어졌습니다.

    - Customer Record

    - Product Record

    - Orders

## 연습 2 – 쇼핑 에이전트 만들기

이번 실습에서는 Contoso Electronics에서 고객의 쇼핑을 돕는 쇼핑
에이전트를 생성하게 됩니다.

### 작업 1 – 에이전트 생성하기

Copilot Studio에서 Copilot을 활용해 에이전트를 생성합니다. Copilot과
대화를 통해 에이전트의 설계 방향과 동작 방식을 지시하면, Copilot이
자동으로 에이전트를 만들어 줍니다.

1.  +++https://copilotstudio.microsoft.com/+++에 접속해 Copilot Studio에
    로그인한 후, **Dev One** 환경을 선택하세요.

![](./media/image12.png)

2.  왼쪽 메뉴에서**Agents**를 선택한 후,  **+ New agent** 버튼을
    클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

3.  아래 내용을 채팅창에 입력한 후 전송하세요.

+++Create an agent that will assist the customers in shopping with
Contoso Electronics. Name it as "Shopping agent".+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

4.  다음 문장을 입력한 후 **Enter** 키를 누르세요:+++Help the users in
    finding products and their prices, give personalized suggestions and
    track order delivery.+++

![](./media/image15.png)

5.  다음 추가 지시사항을 입력하세요.

+++Maintain a polite tone+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  **Create** 버튼을 클릭해 **Shopping agent**를 생성하세요.

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image17.png)

7.  에이전트가 설정됩니다. 몇 분 정도 소요될 수 있습니다. 설정이
    완료되면 아래 스크린샷과 같이 Copilot Studio에 에이전트가
    표시됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

### 작업 2 – 지식 추가하기

에이전트에 지식을 추가하면 해당 리소스를 기반으로 작동하게 되어, 사용자
질문에 더 정확하고 효과적으로 응답할 수 있습니다. 이번 단계에서는 앞에서
생성한 Dataverse 테이블을 에이전트의 지식 소스로 추가할 것입니다.

1.  **테스트 창**에 +++What is the status of the order o1001?+++를
    입력하세요.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image19.png)

2.  에이전트가 해당 정보에 대한 연결된 데이터가 없기 때문에, 아래와
    비슷한 응답이 표시됩니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image20.png)

3.  이제 에이전트에 지식 소스를 추가해 보겠습니다.
    에이전트 **Home페이지**에서 **Knowledge** 섹션 아래에 있는 **Add
    Knowledge**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

4.  사용 가능한 옵션 목록에서**Dataverse**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

5.  +++order+++를 검색한 후, **Order Record** 테이블을 선택하고
    **Next**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  **Add** 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  지식 소스가 추가된 후, 에이전트를 다시 테스트하기 전에 몇 분 정도
    기다리세요.

8.  Once the becomes under the Knowledge 섹션에서 **Order Record**
    상태가**Ready**로 표시되면, Test 창에 이전에 입력했던 질문을 다시
    입력하세요.

이제 에이전트가 데이터베이스에서 정보를 불러와 사용자에게 응답하는 것을
확인할 수 있습니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

### 작업 3 – 엔터티 만들기

1.  에이전트 홈 화면에서**Settings**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

2.  왼쪽 메뉴에서 **Entities**를 선택한 후, **Add an entity -\> + New
    entity** 선택하세요.

![](./media/image27.png)

3.  **Closed list** 선택하세요.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image28.png)

4.  다음 정보를 입력하세요.

Name - +++Laptop+++

Description - +++Contains products under Laptop category+++

**List items**에서 +++Apple MacBook Air M3+++ 를 입력한 후, **Add**을
클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

5.  동일한 방식으로 아래 항목들도 추가한 후  **Save**을 클릭하세요.

+++Dell XPS 13 Plus+++

+++HP Spectre x360 14+++

+++Lenovo ThinkPad X1 Carbon Gen 12+++

+++Asus ROG Zephyrus G14+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

6.  이제 아래 데이터를 사용해 2~5단계를 반복하세요.

Name - +++Desktop+++

Description - +++Contains products under Desktop category+++

**List items**에서 +++Apple iMac+++을 입력한 후**Add**를 클릭하세요.

7.  목록에 추가해야 할 다른 항목은 다음과 같습니다:

+++Microsoft Surface Studio 2+++

+++HP Envy Desktop+++

+++Dell Inspiron Desktop+++

+++Lenovo IdeaCentre AIO 5i+++

8.  다시 한 번 2단계부터 5단계까지 아래 정보를 사용해 반복해 주세요.

Name - +++Tablet+++

Description - +++Contains products under Tablet category+++

**List items**에서 +++Apple iPad Pro+++을 입력한 후 **Add**를
클릭하세요.

9.  목록에 추가해야 할 나머지 항목은 아래와 같습니다:

+++Samsung Galaxy Tab S9 Ultra+++

+++Microsoft Surface Pro 10+++

+++Lenovo Tab P12 Pro+++

+++Apple iPad Air+++

## 연습 3 – 토픽과 에이전트 흐름 만들기 및 에이전트 설계하기

에이전트를 설계할 때 **토픽(Topic)** 설정은 매우 중요한 단계입니다.
사용자의 질문에 어떻게 응답할지, 대화가 어떤 흐름으로 전개될지를
정의하는 핵심 요소이기 때문입니다.

### **작업 1 – 대화 시작(Conversation Start) 토픽 수정하기**

Conversation Start 토픽은 에이전트를 테스트할 때 가장 먼저 실행되는 기본
**시스템** 토픽입니다. Copilot Studio에서 에이전트를 생성하면 자동으로
포함되며, 사용자가 에이전트와 처음 대화를 시작할 때 호출됩니다. 이제 이
토픽을 수정해 에이전트의 인사 메시지 이후 대화를 자연스럽게 이어갈 수
있도록 구성하겠습니다.

1.  에이전트의 **Overview** 페이지 상단 메뉴에서 **Topics** 탭을 선택한
    후, **System** 을 클릭하면 시스템 토픽 목록이 표시됩니다. 이
    목록에서 Conversation Start 토픽을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  기존 메시지(Message) 노드 다음에 **Question node**를 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  다음 메시지를 입력하세요:

메시지 영역에 +++Welcome to Contoso Electronics. Please enter your
**Phone number** to proceed.+++ 를 입력한 후, **Identity** 옵션에서
**User’s entire response**을 선택하세요. 그 후, **Save user response
as** 필드에서 **Var1**을 클릭하세요.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image33.png)

4.  **Var 1**의 이름을 +++MobileNumber+++로 변경하고, 다른 토픽에서도
    사용할 수 있도록 **Global** 을 선택한 후, **Save**을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

### 작업 2 – 고객 정보를 처리하는 토픽 생성하기

1.  에이전트의 Overview 페이지 상단 메뉴에서 Topics 탭을 선택하세요. 그
    후, **Add a topic -\> From blank** 옆의 드롭다운 메뉴를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  에이전트 이름을 +++Customer Details+++로 지정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  **Change trigger** 를 선택한 후, **It’s redirected to**를 트리거로
    설정하세요.

![Screens screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

4.  **Save**을 선택해 토픽을 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

### 작업 3 – 고객 정보를 가져오는 에이전트 플로우 만들기

이번 작업에서는 고객이 입력한 전화번호를 입력값으로 받아, 해당
고객이 데이터에 존재하는지 확인한 후, 고객 정보를 조회해 에이전트에게
전달하는 에이전트 플로우를 만들어 보겠습니다.

1.  트리거 노드 아래에 새 노드를 추가한 다음, **Add a tool** -\> **New
    Agent flow**를 선택하세요.

![](./media/image39.png)

2.  에이전트 플로우 디자이너 화면이 열리면 **Save draft** 을 클릭해
    플로우를 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  상단 메뉴에서 **Overview** 를 선택한 후 **Edit** 을 클릭하고 플로우
    이름을 +++GetCustomer+++로 입력하세요. 그 후, **Save**을
    클릭하세요.![A screenshot of a computer AI-generated content may be
    incorrect.](./media/image41.png)

4.  다시**Designer** 탭으로 이동해 플로우를 설계하세요. **When an agent
    calls the flow** 노드를 선택한 후, **+ Add an input**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  **Text** 선택하세요.

![](./media/image43.png)

6.  입력란에 +++Phone number+++를 입력한 후, **Parameters** 탭을
    닫으세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  흐름 내 두 노드 사이에 있는 **Add an action** 버튼을 클릭하세요.
    검색창에 +++List rows+++를 입력한 후, **Microsoft Dataverse** 아래의
    **List rows** 작업을 선택하세요.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image45.png)

8.  연결 이름에 +++**Dataverse**+++를 입력한 후, **Sign in** 버튼을
    클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  관리자 테넌트 자격 증명으로 로그인(**Sign in)**한 후, 세스 허용
    메시지가 나타나면 **Allow access** 을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

10. +++https://make.powerapps.com/+++에서 PowerApps에 접속한
    후, **Customer Record** 테이블을 여세요. **Mobile number** 필드 옆의
    드롭다운을 클릭하고, **Edit column**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

11. 아래로 스크롤해 **Advanced options** 항목에서**Logical name**이라는
    필드를 찾으세요. 해당 값(논리 이름)을 메모장 등에 꼭 기록해 두세요.

**중요:** Dataverse에서는 각 필드마다 고유한 **논리 이름(Logical
name)** 이 지정되어 있으며, Agent Flow에서 필드를 참조할 때는 반드시
이 **논리 이름만** 사용해야 합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

12. 이 예시에서는 휴대폰 번호 필드의 논리 이름이
    **cr6dd_mobilecontact**입니다. 이 값을 꼭 기록해 두세요.

13. Copilot Studio의Agent flow 탭으로 다시 이동한 후, Getcustomer
    플로우를 열고 **List rows** 업을 선택하세요.

14. Filter rows 필드에**\<Logical name of Mobile number\> eq ' '**
    형식으로 입력하세요. 이때 **\<Logical name\>** 은 이전 단계에서
    확인한 값을 사용하고, 따옴표 안에는Phone number 입력값(동적 변수)을
    넣으세요.

이 경우 **cr6dd_mobilecontact eq 'Phone number'**입니다.

![](./media/image50.png)

![](./media/image51.png)

15. **List rows** 노드 아래에 **Condition** 노드를 추가하세요.

![](./media/image52.png)

16. **/**를 입력한 뒤, **Insert expression**을 선택하세요.

![](./media/image53.png)

17. 함수 입력란에 다음 식을 입력한 뒤 **Add**를 선택하세요:
    +++length(outputs('List_rows')?\['body'\]?\['value'\])+++. 이
    식은 List rows에서 반환된 결과의 항목 수를 확인해 고객 정보가
    존재하는지를 판단합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

18. 조건 노드의 **True** 분기 아래에서 **Add an action**를 클릭한 후, 새
    **Condition** 노드를 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

19. 조건의 함수 영역에
    +++not(empty(first(outputs('List_rows')?\['body/value'\])?\[
    cr6dd_lastpurchasedproduct '\]))+++를 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

> **중요** – Make sure to replace the **cr6dd_lastpurchasedproduct**를
> **Customer Record** 테이블의 **Recent Products Purchased** 필드에
> 해당하는 **logical name**으로 바꿔서 입력하세요.
>
> ![](./media/image58.png)

20. 조건을 **is equal to true**으로 설정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

21. **Condition1**의 **True** 경로 아래에 새 작업을 추가하고, **Respond
    to the agent** 노드를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

22. 추가한 **Respond to the agent node**를 선택하고, 이름을 기존 구매
    이력이 있는 경우로 변경한 후, **+ Add an output**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

23. **Text** 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

24. 출력 이름란에 +++Customer ID+++를 입력한 후, **Insert expression**을
    클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

25. 다음 표현식을 입력하세요:
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
    +++ 여기서 **cr6dd_customeridentifier**는 Customer Record 테이블에서
    Customer ID 필드의 논리 이름입니다. 본인의 환경에서 확인한 값으로
    **바꿔** 입력하세요.

26. **Add** 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

27. 위와 같은 방식으로 다음 출력 변수(Output variable)와 해당 표현식을
    추가하세요. 각 변수의 논리 이름(Logical name)은 본인의 환경에 맞게
    수정해야 합니다.

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_lastpurchasedproduct'\]+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

28. **Respond to the agent** 노드에는 아래 스크린샷처럼 3개의 출력
    변수(Output variable)가 포함되어 있어야 합니다:

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

29. **Condition1** 노드의 **False** 경로 아래에 Respond to the
    agent 노드를 추가하세요. 해당 노드의 이름을 +++If the customer has
    not made a previous purchase+++로 변경하세요. 그런 후, **+ Add an
    output** 버튼을 클릭하세요.

![](./media/image68.png)

30. 아래 출력 변수(Output variable)를 입력하세요. 각 필드에 대해 앞서
    확인한 **해당 열의 논리 이름(Logical Name)**으로 값을 교체해야
    합니다.

- +++Customer ID+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_customeridentifier'\]
  +++

- +++Customer Name+++ -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_fullname'\]+++

- +++Product Category+++ - +++’1’+++

31. **False** 경로 아래의 **Respond to the agent** 노드는 아래
    스크린샷과 같이 표시됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

32. 이제 Condition노드의 **False** 경로 아래에 **Respond to the
    agent** 노드를 추가하고, 이름을 +++If the customer does not
    exist+++로 변경한 후, 아래와 같이 출력 변수를 추가하세요:

- +++Customer ID+++ - +++’1’+++

- +++Customer Name+++ - +++’1’+++

- +++Product Category+++ - +++’1’+++

![](./media/image70.png)

33. **GetCustomer** 플로우는 아래 스크린샷과 유사한 형태로 구성됩니다.

![](./media/image71.png)

34. 플로우 마지막에 공통으로 생성되어 있는 **Respond to the agent**
    노드에서 마우스 오른쪽 버튼을 클릭한 후, **Delete**를 선택해 해당
    노드를 제거하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

35. **Save Draft** 를 선택해 플로우를 임시 저장하세요. 저장이
    완료되면, **Publish**를 클릭해 플로우를 게시하세요.![A screenshot of
    a computer AI-generated content may be
    incorrect.](./media/image73.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

### 작업 4 – 신규 고객 추가를 위한 에이전트 플로우 만들기

이 작업에서는 고객이 신규 고객일 경우, Dataverse에 고객 정보를 추가하는
에이전트 플로우를 생성할 것입니다.

1.  **Agent flows** 탭에서 **+ New agent flow**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

2.  **Add a trigger** 를 선택한 후, 이를 **When an agent calls the
    flow** 노드로 교체하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

3.  **+ Add an input** 를 선택한 후, **Text** 입력을 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

1.  입력 이름으로 +++Name+++을 입력하세요.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image78.png)

4.  마찬가지로 다음 입력 값을 추가하세요.

+++Phone Number+++

+++Email ID+++

+++Address+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image79.png)

5.  해당 노드 아래에 작업을 추가하고 **Add a new row**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

6.  Table Name으로**Customer Record** 를 선택한 후, Advanced
    parameters에서 **Show all**을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

7.  **Address** 필드를 클릭한 후, **Dynamic value** 를 선택하고,
    **Address** 동적 값을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image82.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image83.png)

8.  마찬가지로 아래 항목들에 대해서도 동적 값을 추가하세요:

- Customer Name – Name

- Email ID – Email ID

- Mobile Number - Phone Number

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image84.png)

9.  **Customer ID** 필드에 대해 \*\*표현식 삽입을 열고, +++guid()+++를
    입력한 후**Add**를 선택하세요. 이 함수는 고객 ID로 사용할 **고유한
    값**을 생성합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image85.png)

10. 새 작업(Action)을 추가하고  **Respond to the agent**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

11. +++Customer ID+++ 라는 이름의 출력 값을 추가하고,
    표현식(Expression)을 삽입한 후 다음 값을 입력하세요:
    +++string(outputs('Add_a_new_row')?\['body/cr6dd_customeridentifier'\])+++.

여기서**cr6dd_customeridentifier** 는 **Customer ID** 열의 논리
이름입니다.  
사용자의 논리 이름으로 교체하세요.

**Add**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

12. **Save draft** 를 선택해 플로우를 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

13. 플로우가 저장되면**Publish**를 선택해 플로우를 게시하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

14. **Overview** 탭을 선택한 후 **Edit**을 클릭하세요. 플로우 이름을
    +++Add Customer+++로 입력한 다음 **Save**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

### 작업 5 – 플로우 추가 및 고객 정보(Customer Details) 토픽 구성하기

이번 작업에서는 고객의 휴대폰 번호를 입력받아 Dataverse에 해당 정보가
이미 등록되어 있는지 확인한 뒤, 등록되어 있지 않다면 자동으로
추가하는 **Customer Details** 토픽을 구성합니다.

1.  다시 **Customer Details** 토픽으로 이동하세요 .

2.  **Trigger 노드** 아래에 새 노드를 추가한 후, **Add a tool -\>
    GetCustomer**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

3.  **Inputs(입력값)** 항목에서 변수 **MobileNumber**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

4.  **Output** 변수 중Customer ID와 ProductCategory를 선택한 후,
    스크린샷과 같이 이 두 변수를 **Global** 변수로 설정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

5.  **Action** 노드 아래에 **condition** 노드를 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

6.  **Select a variable**에서 **CustomerID**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

7.  조건을 **is not equal to**로 설정한 후, **Value** 입력란에 +++
    '1'+++ 을 입력하세요. 이는 고객 정보가 데이터베이스에 **이미
    존재하지 않는 경우**를 확인하기 위한 조건입니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

8.  조건 노드 아래에 **Set a variable** 노드를 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

9.  **Select a variable**을 클릭한 후, **Create a new variable**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

10. 변수 이름을 +++IsNewCustomer+++로 지정하고, **Global** 변수로
    설정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

11. 값은 +++‘No’+++로 설정하세요. 이는 해당 고객의 정보가 이미
    Dataverse에 존재하는 기존 고객임을 의미합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

12. 변수 노드 옆에 새로운 노드를 추가하고 고객에게 환영 메시지를
    전달합니다.

13. Add a node를 선택한 후, **Send a message** 노드를 선택하세요. 메시지
    입력란에 +++Welcome+++을 입력한 후, {x} 아이콘을 클릭해 변수
    목록에서**Customer Name** 변수를 선택하세요.

![](./media/image101.png)

> 이제 Agent 플로우인 **GetCustomer**를 호출해 고객 정보가 이미
> 존재하는지 확인하고, 기존 고객일 경우 환영 메시지를 추가했습니다.
>
> 이제 고객 정보가 존재하지 않을 경우의 흐름을 설계하겠습니다.

13. **All other conditions** 노드 아래에 Set a variable 노드를 추가하고,
    **isNewCustomer** 변수의 값을 +++’Yes’+++로 설정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

14. 변수 노드 옆에 **Message** 노드를 추가하고, 다음과 같이 입력하세요:
    +++We do not have your details in our system. Please fill in your
    details below to help us serve you better.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

15. Message 노드 옆에 **Ask with adaptive card** 노드를 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

16. 화면 오른쪽 상단에 있는 아이콘을 클릭한 후, **Properties**을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

17. **Edit adaptive card** 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

18. **Card payload editor** 영역에 아래 **JSON**을 입력한 후, **Save**을
    선택하세요.

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

19. **Close**를 선택해 편집기를 종료하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

20. 생성된Adaptive card 노드의 Outputs 섹션을 확장한 후, Mobile Number
    값을 선택하고 Global.MobileNumber 변수에 연결하여 사용자가 입력한
    전화번호 값을 해당 변수에 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

21. 나머지 값들은 기본값으로 그대로 두세요.

22. 고객 정보를 입력받기 위한 **입력 양식이 포함된 Adaptive Card**가
    준비되었습니다.

23. Adaptive Card 노드 옆에 **Add Customer** 플로우를 호출하는 노드를
    추가하세요.

![](./media/image110.png)

24. **Enter or select a value** 필드 옆의 **세 점** 아이콘을
    클릭하고** CustomerName** 변수를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

25. 같은 방식으로, 나머지 필드들도 플로우에 전달될 수 있도록 입력 변수를
    추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

26. 플로우의 출력값이 저장될 출력 변수로 **Global.CustomerID**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

27. 액션 노드 다음에 메시지 노드를 추가하고, 아래 내용을 입력합니다:
    +++Thank You! Customer detail has been added to the database. Please
    select a product type to shop.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

28. 토픽을 저장(**Save**)하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

29. Conversation Start 토픽을 열고, Customer Details 토픽을 호출하세요.

30. 해당 토픽의 Question 노드 아래에 노드를 추가하고, **Topic management
    -\> Go to another topic**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image116.png)

31. **Customer Details** 토픽을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

32. **Save**을 선택해 토픽을 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### 작업 6 – 제품 정보를 가져오는 에이전트 플로우 만들기

이 작업에서는 사용자가 선택한 제품을 기준으로 Dataverse에서 제품 정보를
가져오는 에이전트 플로우를 생성하세요.

1.  Copilot Studio에서 **Flows** 탭을 선택한 후, **+ New agent flow**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  트리거 노드를 선택한 후, **When an agent calls the flow** 동작을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  텍스트 입력 항목을 추가하고 이름을 +++Product Name+++으로
    지정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

4.  **Save draft**를 선택해 플로우를 임시 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image122.png)

5.  **Overview** 탭을 선택하고  **Edit**을 클릭한 후, 이름을
    +++GetProductDetails+++로 입력하고 **Save**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image123.png)

6.  **Designer** 탭으로 다시 이동한 후, **When an agent calls the
    flow** 노드 아래에 **Add an action**을 선택하세요. +++list rows+++를
    검색한 후, **Microsoft Dataverse** 아래에 있는 **List rows** 작업을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image124.png)

7.  다음 값을 입력하세요:

- **Table name –Product Record** 선택하세요.

- Filter rows – +++cr6dd_producttitle eq '**\<Product Name\>**'+++
  \<Product Name\> 부분을 동적 값인 ProductName으로 바꿔 입력하세요.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image125.png)

8.  **List rows** 노드 아래에 **Respond to the agent** 노드를
    추가하세요. **+ Add an output**를 선택한 후 텍스트 출력 변수를
    추가하세요. 아래 값을 입력하고 **Insert expression**에서 Add를
    클릭하세요:

    - Enter a name – +++Product Name+++ 입력

    - Expression -
      +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_producttitle'\]+++
      (여기서 **cr6dd_producttitle** 은 테이블에서 Product Name 열의
      논리 이름입니다. 사용자 환경에 맞는 이름으로 변경하세요.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image126.png)

9.  위와 같은 방식으로 출력 노드를 하나 더 추가하고 아래 내용을
    입력하세요:

- Enter a name – +++Price+++

- Expression -
  +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_productprice'\]+++
  **cr6dd_productprice** 는 테이블에서 **Price** 열의 논리 이름입니다.
  본인의 환경에 맞는 이름으로 변경하세요.

> 이제 노드가 다음과 같이 표시됩니다.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image127.png)

10. **Save draft**를 선택해 플로우를 임시 저장한 후, **Publish**를
    클릭해 플로우를 게시하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image128.png)

### 작업 7 – 고객의 제품 카테고리를 조회하는 토픽 생성하기

1.  Copilot Studio의 **Topics** 탭에서 **+ Add a topic -\> From
    blank**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image129.png)

2.  토픽 이름을 +++Place Order+++로 변경하고, 트리거 노드의 트리거
    유형을 **It’s redirected to**로 변경하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image130.png)

3.  토픽을 **save** 버튼을 눌러 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image131.png)

4.  Copilot Studio에서 **Topics** 탭으로 이동한 후, **+ Add a topic -\>
    From blank**을 선택하세요.

![](./media/image129.png)

5.  토픽 이름을 +++Get Product Categories+++로 변경하세요.
    **Trigger**노드에서 **Change trigger** 옵션을 선택한 후, **It’s
    redirect to** 옵션을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image132.png)

6.  **Trigger** 노드 아래에 **Condition** 노드를 추가하세요.

Select the Global 변수인 **IsNewCustomer** 를 선택한 후,
조건을**IsNewCustomer** **is equal to** 가 +++**'Yes'**+++와 같음으로
설정하세요.

**+ New condition**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image133.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image134.png)

7.  **Or**을 선택하세요.

Or 조건 아래에서 Global 변수**ProductCategory** 를 선택하고, 조건을
+++'1'+++과 같음으로 설정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image135.png)

![](./media/image136.png)

8.  Condition 노드 아래에 Question 노드를 추가하세요. 질문 텍스트에는
    +++Select a category+++ 를 입력하고,  **+ New option**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

9.  옵션에 +++Laptop+++ 을 입력한 후, + New option을 다시 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

10. 마찬가지로 옵션에 +++**Desktop**+++과 +++**Tablet**+++을 추가하세요.
    **Save user response as** 아래있는 변수를 선택하고, 해당 변수
    이름을 +++**ProdCatchoice**+++로 지정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image139.png)

11. 질문 노드 아래에 **Set a variable value** 노드를 추가하세요. 질문
    노드에서  받은 선택값을 **문자열(String)** 형식으로 변환하기 위한
    작업입니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

12. Set variable 단계에서 Global변수 **ProductCategory**를 선택하세요.
    **To value** 필드에서 세 점 아이콘을 클릭한 후 **Formula** 탭을
    선택하세요. 다음 수식을 입력하세요: +++Text(Topic.ProdCatchoice)+++.
    **Insert**을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image141.png)

13. Set variable 값 노드 아래에 새 노드를 추가하세요. **Topic
    management** -\> **Go to another topic** -\> **Place Order**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

14. 이제 하나의 경로가 완성되었습니다. 이 경로는 사용자로부터 카테고리를
    입력받고, Place Order 주제를 호출하게 됩니다.

15. 이 토픽의 시작 지점으로 다시 이동하세요. 모든 기타 조건 아래에
    **Question** 노드를 추가하세요. 메시지에는 다음과 같이 입력하세요:
    +++Based on your recent purchase we suggest you products in
    \<Product Category\> category. Would you like to continue?+++

메시지의 **\<Product Category\>** 부분은 **Global.ProductCategory**
변수로 바꿔 입력하세요.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image143.png)

16. 옵션을 두 개 추가하세요:  +++Yes+++ 및 +++No+++. Save user response
    as 아래에 있는 변수명을 클릭한 뒤, 변수 이름을
    +++Userschoiceofcategory+++로 변경하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image144.png)

17. **Question** 노드 아래에 **condition** 노드를 추가하세요.

첫 번째 조건을 다음과 같이 설정하세요: **Userschoiceofcategory is equal
to Yes**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image145.png)

36. 이 노드 아래에 **Topic management node**를 추가하고, **Place Order**
    토픽을 호출하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image146.png)

18. 조건 노드의 오른쪽 상단에 있는 세 개의 점을 클릭한 후, **Insert new
    condition** 을 선택하세요.

![](./media/image147.png)

19. 다음 조건을 추가하세요: **Userschoiceofcategory is equal to No**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image148.png)

20. Condition 노드 아래에 question 노드를 추가하세요. 질문 영역에
    +++Select a category+++를 입력하고, **+ New option**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image137.png)

21. 옵션에 +++Laptop+++을 입력하고, + New option을 다시 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image138.png)

22. 같은 방식으로 +++**Desktop**+++과 +++**Tablet**+++ 옵션도
    추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image149.png)

23. 질문 노드 아래에 **Set a variable value** 노드를 추가한 후, 질문
    노드에서 받은 선택 값을 문자열(String) 형식으로 변환하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image140.png)

24. Set variable 단계에서 Global 변수 **ProductCategory**를 선택하세요.
    **To value** 입력란에서 점 3개 아이콘을 클릭한 후, **Formula** 탭을
    선택하세요. 다음 수식인 +++Text(Topic.Var1)+++ 를 입력한 뒤
    **Insert**을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image150.png)

25. Set variable 노드 아래에 새 노드를 추가하세요. **Topic management**
    -\> **Go to another topic** -\> **Place Order**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image142.png)

26. **Save**을 선택해 토픽을 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image151.png)

27. **Customer Details** 토픽을 열고 마지막 노드로 이동하세요.

28. **Add a new node** (새 노드를 추가한 후), **Get Product Categories**
    토픽을 호출하도록 설정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image152.png)

29. **Save**을 선택해 토픽을 저장하세요.

![](./media/image153.png)

### 작업 8 – 주문 접수를 위한 에이전트 플로우 생성

이 작업에서는 고객이 선택한 제품을 기반으로 주문을 접수하는 에이전트
플로우를 생성합니다.

1.  **Agent flows** 탭에서 **+ New agent flow**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image154.png)

2.  **Add a trigger node**를 클릭한 후, **When an agent calls the flow**
    노드를 선택하세요.

![](./media/image155.png)

3.  2개의 **Text** 변수 +++Product Name+++ 및 +++Customer ID+++를
    **Input**으로 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image156.png)

4.  **Save Draft**을 클릭해 플로우를 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image157.png)

5.  상단 메뉴에서 **Overview** 를 선택한 후, **Edit**을 클릭하세요.
    플로우 이름에 +++PlaceOrder+++를 입력한 후, **Save**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image158.png)

6.  **Designer** 탭으로 다시 이동하세요. Add a new action를 선택한  후,
    Dataverse 아래에서 **Add a new row**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image159.png)

7.  **Table name**에서 **Order Record**를 선택한 후, **Advanced
    parameters** 아래의 **Show all**을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image160.png)

8.  아래 값을 입력하세요:

Customer Identifier - **Customer ID** (Dynamic value)

Order identifier – guid() (Insert expression 클릭 후 입력)

Order Status - +++**Order Placed**+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image161.png)

9.  다음 노드를 추가하세요: **Respond to the agent**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image162.png)

10. 텍스트 출력 변수를 추가하고 이름을 +++Order ID+++로 지정하세요.

값에는 다음 식을 입력하세요: +++
string(outputs('Add_a_new_row')?\['body/cr6dd_orderidentifier'\])+++
(**cr6dd_orderidentifier** 는 Order Record 테이블에서 **Order
ID** 열의 논리 이름으로, 사용 중인 값으로 바꿔주세요.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image163.png)

11. 흐름을 저장하려면 **Save draft** 를 클릭하고,
    배포하려면**Publish**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image164.png)

### 작업 9 – 주문 접수 토픽 설계하기 

이 작업에서는 고객의 주문을 접수하고 Dataverse 테이블에 주문 정보를
업데이트하는 토픽을 설계합니다.

1.  에이전트의 **Topic** 탭에서 **Place Order** 토픽을 여세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image165.png)

2.  메시지 노드를 추가하고 메시지 입력란에 다음 내용을 입력하세요:
    +++Options based on the category will be listed below.+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image166.png)

3.  조건 노드를 추가하세요. ProductCategory(Global variable)가
    +++Laptop+++와 같으므로 조건을 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image167.png)

4.  해당 노드 아래에 질문 노드를 추가하고, 메시지 입력란에 다음을
    입력하세요: +++Select a Laptop product+++. **Identity** 항목에서는
    **Laptop**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image168.png)

5.  **Select** options for user을 선택한 후, 표시되는 5가지 옵션을 모두
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image169.png)

1.  변수 이름을 +++ProdNameLapChoice+++로 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image170.png)

6.  이제 동일한 방식으로 조건 노드를 추가해 ProductCategory가
    +++Desktop+++ 또는 +++Tablet+++일 때의 조건을 설정하세요.

7.  변수 이름에 값을 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image171.png)

8.  **Set variable value** 노드를 **Select a Laptop product** 질문 노드
    아래에 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image172.png)

9.  생성한 변수의 이름을 +++ProdNameSelected+++로 변경하고, **Global**
    변수로 설정하세요.![A screenshot of a computer AI-generated content
    may be incorrect.](./media/image173.png)

10. Formula 필드에 다음 값을 입력하세요:
    +++Text(Topic.ProdNameLapChoice)+++ (만약 다른 변수명을 사용했다면,
    해당 이름으로 바꿔 입력하세요.)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image174.png)

11. 마찬가지로, **Desktop** 및 **Tablet** 분기 아래에도 **Set variable
    value** 노드를 추가하세요. **Set variable** 값로는
    **ProdNameSelected**를 선택하고, To value 필드에는 해당 분기에서
    사용한 변수명을 기반으로 한 표현식(expression) 을 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image175.png)

12. 이러한 모든 노드 아래에 공통적으로 Action 노드를 추가하고
    GetProductDetails 흐름을 호출하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image176.png)

13. 플로우에 전달할 입력 변수로 **ProdNameSelected**를 선택하세요.
    나머지 값은 기본값 그대로 두세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image177.png)

14. 액션 노드 아래에 메시지 노드를 추가하고 아래 메시지를 입력하세요.
    Replace \<productName\>과 \<Price\>는 해당 변수 이름으로 교체하세요.

제품 정보

- Product Name - \<ProductName\>

> ​

- Price - \<Price\>

​

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image178.png)

15. 메시지 노드 아래에**Question node**를 추가하세요. 메시지 영역에 다음
    문장을 입력하세요: +++Would you like to place order for this
    item?+++. 옵션으로 **Yes**와 **No**를 추가하고, 사용자 응답 저장
    변수 이름을 +++PlaceOrder+++로 지정하세요.

![](./media/image179.png)

16. Question 노드 아래에  condition 노드를 추가하세요. 한
    분기에는 **PlaceOrder isequal to Yes** 추가하고, **다른 분기**에는
    **all other conditions**을 설정세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image180.png)

17. 다음 단계로 **PlaceOrder** 플로우를 호출하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image181.png)

18. 플로우 입력값으로 **ProductName** 과 **CustomerID**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image182.png)

19. 이제 그 아래에 메시지 노드를 추가하고, 아래와 같은 메시지를
    입력하세요: +++Your order is placed. This is your Order ID for
    reference -\<OrderID\>+++ (**\<OrderID\>** 부분은 플로우의 출력
    변수인 **OrderID**로 대체하세요.)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image183.png)

20. 이제 **PlaceOrder is equal to Yes** 조건 분기 처리가 완료되었습니다.
    이제 **All other conditions** 브랜치로 이동하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image184.png)

21. 그 아래에 Question 노드를 추가하고, 메시지에는 +++Do you want to go
    to the main menu?+++ 라고 입력하세요. 옵션으로 **Yes**와 **No**를
    추가하고, 사용자 응답을 저장할 변수 이름은 +++**GoToMainMenu**+++로
    지정하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image185.png)

22. 해당 노드 아래에 **조건(Condition)** 노드를 추가하세요. 첫 번째
    분기에는 조건을 다음과 같이 설정하세요: **GoToMainMenu is equal to
    Yes**. 다른 분기는 조건은 자동으로 **All other conditions**으로
    설정됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image186.png)

23. 해당 조건(Condition) 노드 아래에 질문(Question) 노드를 추가하고,
    메시지에는 +++**Select Product Category**+++라고 입력하세요.
    옵션으로는 다음 세 가지를 추가하세요: +++**Laptop**+++,
    +++**Desktop**+++ 및+++**Tablet**+++.

결과가 저장되는 변수 이름을 꼭 기록해 두세요. 다음 단계에서 해당 값을
문자열로 변환할 예정입니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image187.png)

24. **Set variable value** 노드를 추가하세요. 변수로는
    **ProductCategory** 를 선택하고, **Formula** 탭에 다음 값을
    입력하세요: +++**Text(Topic.Var1)**+++.

**Var1**은 이전 단계에서 사용한 변수 이름으로, 다를 경우 본인의
변수명으로 바꿔 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image188.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image189.png)

25. Set variable value 노드 아래에**Go to step** 노드를 추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image190.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image191.png)

26. 노드를 추가한 후, 이 시점에서 흐름이 이동해야 할 **단계(Step)** 를
    선택해야 합니다. 화면을 위로 스크롤해 이 토픽의 시작 부분에
    있는 **Message 노드**를 선택하세요. 이제
    고객으로부터 **ProductCategory** 정보를 받았으므로, 대화 흐름을
    처음부터 다시 실행해야 합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image192.png)

27. 마지막에 공통 **메시지(Message)** 노드를 추가하고, 메시지 영역에
    +++Thank you for shopping with us! Please visit again!+++ 를
    입력하세요. 그 후, **Save**을 클릭해 토픽을 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image193.png)

## 연습 4 – 트리거 추가하기

이 실습에서는 **Order 테이블**에 새 행이 추가되거나 기존 행이 수정될 때
자동으로 고객에게 이메일을 보내는 트리거를 추가합니다. 이 작업을 통해
에이전트가 자율적으로 동작할 수 있는 기능을 정의하게 됩니다.

1.  에이전트의 Overview 탭을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image194.png)

2.  페이지를 아래로 스크롤한 후 **Add trigger**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image195.png)

3.  **When a row is added, modified or deleted** 옵션을 선택한 후,
    **Next**를 선택하세요.

![](./media/image196.png)

4.  Microsoft Copilot Studio와 Dataverse 간 연결이 완료되면, **Next**를
    클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image196.png)

5.  아래 옵션들을 선택하고, 나머지는 기본값으로 두고 **Create
    trigger**를 선택하세요.

- Change Type – 추가됨, 수정됨 또는 삭제됨 (Added or Modified or
  Deleted)

- Table name – Order Record

- Scope - Organization

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image197.png)

6.  이 작업은 몇 분 정도 소요될 수 있습니다. 완료되면 **트**리거
    추가(Add trigger**)** 대화 상자에서 **Close**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image198.png)

7.  에이전트 **Overview** 페이지의 트리거 섹션에서, 추가된 트리거
    오른쪽에 있는 **점 3개 메뉴**를 클릭한 후 **Edit in Power
    Automate**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image199.png)

8.  로우의 첫 번째 노드를 선택한 후 **Select columns** 필드에
    +++cr6dd_orderidentifier, cr6dd_customeridentifier+++를 입력하세요.
    (이 값들은 Order Record 테이블의 **Order ID** 및 **Customer
    ID** 열의 논리 이름이므로, 사용 중인 테이블에 맞는 논리 이름으로
    바꿔 입력하세요.)

![](./media/image200.png)

9.  새 노드를 추가한 후, 해당 노드에서 **List rows** 액션을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image201.png)

10. List rows 액션에서 **Table name**은 **Customer Record**로
    선택하세요. **Filter rows** 필드에는 **+++cr6dd_customeridentifier
    eq ''+++** 를 입력하되, cr6dd_customeridentifier 부분은 본인의
    Customer ID 컬럼 논리명으로 교체하세요. 작은따옴표('') 안에 커서를
    위치시키세요.

![A screenshot of a list AI-generated content may be
incorrect.](./media/image202.png)

11. Insert expression를 선택한 후,
    +++String(triggerOutputs()?\['body/cr6dd_customeridentifier'\])+++를
    입력하세요. 여기서 **cr6dd_customeridentifier** 부분은 본인의
    Customer ID 논리명으로 바꿔주고, **Add**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image203.png)

12. **List rows** 작업 옆에 새 작업을 추가하고, **Send an email (V2)**를
    선택하세요.

![A screenshot of a mail box AI-generated content may be
incorrect.](./media/image204.png)

13. **Sign in** 버튼을 클릭하고, 본인 계정으로 로그인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image205.png)

14. **To** 필드에 표현식을 삽입하고,
    +++first(outputs('List_rows')?\['body/value'\])\['cr6dd_emailaddress'\]+++
    를 입력하세요. 여기서 **cr6dd_emailaddress** 고객 기록(Customer
    Record) 테이블의 이메일 필드 논리 이름으로 변경해 주시고, 완료되면
    **Add**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image206.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image207.png)

15. 다음 정보를 입력하세요:

Subject - +++Order Placement+++

Body –

Hi,

This is to update you that your order has been placed. Thank you for
shopping with us.

Thank You.

16. 플로우를 저장(Save)한 후, 게시(Publish)하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image208.png)

17. Copilot Studio의 에이전트 페이지로 돌아가서, \[Publish\]를 선택하여
    에이전트를 게시하세요.

![](./media/image209.png)

18. 확인 창에서**Publish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image210.png)

19. ewqewqew

## 연습 5 – 에이전트 테스트하기

이 연습에서는 에이전트의 작동 방식을 테스트하게 됩니다.

1.  에이전트 페이지에서 Test를 선택해 테스트 창을 여세요.

2.  기존 고객의 전화번호인 +++3148987666+++을 입력하세요.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image211.png)

3.  제공된 옵션 중에서**Yes**를 선택하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image212.png)

4.  제공된 옵션 중에서 원하는 **제품을** 선택하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image213.png)

5.  제공된 옵션 중에서 Yes를 선택하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image214.png)

6.  주문이 완료되면, 고객에게 참조 ID가 제공됩니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image215.png)

7\. 받은 주문 ID로 배송 상황을 조회하는 등 다른 질문도 할 수 있습니다.
비록 해당 주제는 아직 설정하지 않았지만, 지식 기반을 바탕으로 답변을
제공합니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image216.png)

다른 시나리오들도 선택해서 테스트해 보세요. 새로운 고객을 추가한 후,
고객 정보가 Customer Record 테이블에 제대로 저장되었는지 확인하고, 해당
고객 정보가 등록되었다는 이메일이 본인의 이메일로 잘 도착했는지
확인하세요.

## 요약:

이번 실습에서는 자율 쇼핑 에이전트를 설계하는 방법을 배웠습니다. 주요
학습 내용은 다음과 같습니다.

- 변수(Variables)

- 엔터티(Entities)

- 토픽(Topics)

- 에이전트 플로우(Agent flows)

- 트리거(Trigger)

- 지식 소스(Knowledge sources)
