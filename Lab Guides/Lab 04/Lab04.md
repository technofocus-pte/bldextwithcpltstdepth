# 실습 04 - Gen AI 기능을 통한 부동산(Real Estate) copilot 향상시키기

**실습 소요 시간** – 80분

**목표:**

Copilot for Real Estate 앱에 엔터티, 슬롯 채우기, 변수 활용을 구현하고,
Generative AI 기능을 적용해 고객 경험을 한층 더 향상시켜 보세요.

## 연습 1: Copilot의 이해도를 높이기 위해 엔터티 사용하기

Microsoft Copilot Studio는 사용자의 의도를 파악하기 위해 엔터티를
사용합니다. 자주 사용되는 정보에 대해 미리 생성된 엔터티가 포함되어
있으며, 특정 목적에 맞게 사용자 지정 엔터티를 직접 만들 수도 있습니다.

### 작업 1: 미리 구축된 엔터티 보기

1.  !\![https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/)!!에서
    Copilot Studio를 열고 **Real Estate Booking Service** 에이전트를
    여세요.

2.  화면 왼쪽 상단에서 **Settings**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  **Entities** 탭을 선택하세요. 사전 구축된 엔터티 목록을 확인할 수
    있습니다.

![](./media/image2.png)

### 작업 2: 부동산 유형(Property Type) 엔터티 만들기

1.  **+ Add an entity** 선택하고, **+ New entity**를 선택하세요.

![](./media/image3.png)

2.  **Closed list** 타일을 선택하세요.

![](./media/image4.png)

3.  다음 정보를 입력하세요:

    - Name - !!Property Type!!

    - List items에 다음 항목 입력하세요 – !!Apartment!! – **Add**
      선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

4.  **Enter item** 필드에 !!**Condominium**!!을 입력하고, **Add**를
    선택하세요.

5.  **Enter item** 필드에 !!**Duplex**!!을 입력하고, **Add**를
    선택하세요.

6.  **Enter item** 필드에 !!**House**!!을 입력하고, **Add**를
    선택하세요.

![](./media/image6.png)

7.  **Apartment** 항목 옆의 + **Synonyms**를 선택하고, !!**Flat**!! 을
    입력한 후 **+** 아이콘을 클릭하고 **Done** 을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.   **House** 항목은 **+ Synonyms**을 선택하고 !!**Single-family
    home**!!를 입력한하세요. **+** 아이콘을 선택한 후, **Done**을
    선택하세요.

9.  **+ Synonyms** for **Condominium**에 대한 **+ Synonyms** 를 선택하고
    !!**Townhouse**!!를 입력한 후, **+** 아이콘을 선택하고 **Done**을
    선택하세요.

10. **Save**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

11. **Close**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

### 작업 3: 침실 수 엔터티 생성

1.  **+ Add an entity** 선택한 후 **+ New entity**를 선택하세요.

![](./media/image10.png)

2.  **Regular expression (Regex)** 타일을 선택하세요.

![](./media/image11.png)

3.  아래 정보를 입력하고 **Save**을 클릭하세요.

    - Name - !!**Number of Bedrooms**!!

    - Pattern - !!**\[1-5\]**!!

![A screenshot of a cell phone AI-generated content may be
incorrect.](./media/image12.png)

4.  **Close**를 선택하세요.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image13.png)

5.  **Settings** 창을 닫으세요.

![](./media/image14.png)

### 작업 4: 엔터티 사용

1.  **Topics** 탭을 선택하세요. **Book a Real Estate Showing** 주제를
    선택하세요.

![](./media/image15.png)

2.  부동산 질문 노드 위에 있는 + 아이콘을 선택하고, **Ask a question**을
    선택하세요.

![](./media/image16.png)

3.  다음 정보를 입력하세요.

    - **Enter a message** - !!What type of property do you want to
      see?!!

    - **Identify** –**Property Type**를 선택하세요.

    - **Select options for user** 을 선택하고 모든 목록 값에
      대해  **Display** 옵션을 확인하세요.

![](./media/image17.png)

4.  **Save user response as**에서 변수를 선택하고, **Variable name**에
    !!**PropertyType**!! 을 입력하세요. 

![](./media/image18.png)

5.  새로운 질문 노드 아래에 있는 + 아이콘을 선택하고, **Ask a
    question**을 선택하세요.

6.  다음 정보를 입력하고 **Save**을 선택하세요.

    - **Enter a message** - !!How many bedrooms do you need?!!

    - **Identify -**  **Number of Bedrooms** 선택하세요.

    - **Save user response as** - **Variable name**을
      !!NumberofBedrooms!!으로 입력하세요.

![](./media/image19.png)

## 연습 2: 액션 생성

Microsoft Copilot Studio는 Power Automate 클라우드 플로우를 사용해
Microsoft Dataverse의 데이터에 액세스할 수 있습니다.

### 작업 1: 부동산 정보를 가져오는 Power Automate 흐름 만들기

1.  상단 메뉴에서 **Actions** 탭을 선택하고, **+ Add an action**를
    선택하세요.

![](./media/image20.png)

2.  **+ New action** -\> **New Power Automate flow**를 선택하세요.

![](./media/image21.png)

3.  메시지가 표시되면 Power Automate에 로그인하세요.

4.  오른쪽 상단에서 **New designer** 토글을 활성화하세요(아직 활성화되지
    않았다면). **Save and switch**를 선택하세요.

![](./media/image22.png)

5.  화면 왼쪽 상단에서 **Run a flow from Copilot**을 선택하고, 플로우
    이름으로 !!**Get Property**!!를 입력하세요.

![](./media/image23.png)

6.  **Run a flow from Copilot** 트리거 단계를 선택한 후, **+ Add an
    input**을 선택하세요.

![](./media/image24.png)

7.  **Text**를 선택하세요.

![](./media/image25.png)

8.  다음 정보를 입력하세요.

    - **Input** – !!Bedrooms!!

    - **Please enter your input** - !!Number of Bedrooms!!

![](./media/image26.png)

9.  흐름**(flow)**에서 두 단계 사이에 있는 + 아이콘을 마우스 오른쪽
    버튼으로 클릭한 후, **Add an action**을 선택하세요.

![](./media/image27.png)

10. **Searcb** 필드에 !!**Dataverse**!!를 입력하고, **Microsoft
    Dataverse connector**에서 **See more**을 선택하세요.

\![\](./media/image27.png)

11. **List rows** 작업(action)을 선택하세요.

![](./media/image28.png)

12. 인증 요청 메시지가 표시되면 **OAuth**를 선택하고 Sign in을
    클릭하세요. 필요할 경우 테넌트 ID로 로그인하세요.

![](./media/image29.png)

13. 테이블 이름을 **Real Estate Properties** 으로 선택하세요.

14. 모든 옵션이 자동으로 표시되지 않으면 **Show all**을 선택하세요.

15. **Filter Rows** 필드에 !!contoso_bedrooms eq!!를 입력하세요.

16. **eq** 옆에 spacebar을 눌러 값을 띄어쓰기 후에 입력하세요. **Dynamic
    conten**t에서 **Bedrooms** 매개변수를 선택하고 **Add**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

17. **Respond to Copilot** 액션을 선택한 후, **+ Add an output**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

18. **Text**를 선택하세요.

19. 다음 정보를 입력하세요.

    - **Enter a name** - !!PropertyId!!

    - **Enter a value to respond with** - **Insert Expression** 선택하고
      다음 표현식을 입력하세요:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_realestatepropertyid'\]!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

20. **Add**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

21. From
    !\![https://make.powerapps.com](https://make.powerapps.com/)!!에서
    **Real Estate Property** 테이블을 여세요. 해당 테이블의 Property
    Name 열로 이동합니다 (Copilot으로 생성했을 경우 이름이 Real Estate
    Property 또는 약간 다를 수 있음) → Edit Column → Advanced options로
    들어갑니다. **Logical name** 값을 확인하세요. 일반적으로
    **contoso\_**로 시작하며, 예: **contoso_newcolumn**처럼 표시됩니다.
    여기서 **contoso\_** 이후의 부분, 즉 **newcolumn**을 기억해 두세요.
    다음 단계에서 이 값을 사용할 것입니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

22. Power Automate flow 페이지로 돌아가서 **+ Add an output**을
    선택하세요.

23. **Text**를 선택하세요.

    - **Enter a name** - !!PropertyName!!

    - **Enter a value to respond with** - **Insert Expression**를
      선택하고 다음 표현식을 입력하세요:
      !!first(outputs('List_rows')?\['body/value'\])\['contoso_propertyname'\]!!

위 표현식에서 **contoso_propertyname**의 **propertyname**을 이전
단계에서 저장한 값(**newcolumn**)으로 변경하세요.

::: secondary 이 값 교체는 해당 열의 Logical(놀리적) 이름이 표준 값이
아니기 때문에, 테이블에서 값을 확인하고 업데이트해야 합니다. :::

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

24. **Settings**을 선택하고, **Asynchronous Response**이 **Off**으로
    설정되어 있는지 확인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

25. **Save draft**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

26. 저장되면 **Publish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

27. Power Automate 탭을 닫으세요.

### 작업 2: 부동산 정보를 가져오는 Copilot 액션 추가하기

1.  Copilot Studio 페이지로 돌아가서 **Refresh**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

2.  **Get Property** 플로우를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

3.  **Add action**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image41.png)

4.  **Topics** 탭을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

5.  **Book a Real Estate Showing** 주제를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

6.  **How many bedrooms do you need question?** 노드 아래에 있는 +
    아이콘을 선택하고**Add an action**을 선택하세요. **Get
    Property** 플로우를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

7.  **Bedrooms** 입력 매개변수에 대한 **NumberofBedrooms** 변수를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

8.  **Which property do you want to see?** 질문 노드에서 **세 개의
    점을** 선택하고 **Delete**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

9.  액션 노드 아래의 + 아이콘을 선택하고 **Send a message**를
    선택하세요.

10. 다음 정보를 입력하세요.

    - **Enter a message** -!!Property!!를 입력하세요.

    - **Insert variable** 아이콘을 선택하고 **PropertyName** 변수를
      선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

11. **Save**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

12. 저장되면**Publish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

13. Publish 확인 대화상자에서 **Publish**  를 클릭하세요.

![A close-up of a white background AI-generated content may be
incorrect.](./media/image50.png)

### 작업 3: 예약을 위한 Power Automate 플로우 만들기

1.  **Actions** 탭을 선택하고 **+ Add an action**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

2.  **+ New action** -\> **New Power Automate flow**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

3.  화면 왼쪽 상단에서 **Run a flow from Copilot**을 선택한 후, 플로우
    이름으로 !!**Booking Reques**t!!를 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

4.  **Run a flow from Copilot** 트리거 단계를 선택한 후, **+ Add an
    input -\> Text** 를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

5.  다음 정보를 입력하세요

    - Input - !!**PropertyId**!!

    - Please enter your input **-** !!**Property**!!

6.  **+ Add an input -\> Text**를 선택하세요.

    - Input - !!**ViewerName**!!

    - Please enter your input **-** !!**Viewer Name**!!

7.  \\**+ Add an input -\>** **Text**를 선택하세요.

    - Input - !!**ViewerEmail**!!

    - Please enter your input **-** !!**Viewer Email**!!

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

8.  플로우의 두 단계 사이에 있는 **+** 아이콘을 선택하고, **Add an
    action**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

9.  **Search** 필드에 !!**Dataverse**!!를 입력하고, Dataverse 커넥터
    옆에 있는 **See more**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

10. **Add a new row** 액션을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

11. Table Name을 **Booking Requests**으로 선택하세요.

12. **Booking Name** 필드에 !!**Copilot booking**!!를 입력하세요.

13. **Show all**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

14. **Property (Real Estate Properties)** 필드에
    !!contoso_bookingrequests()!!를 입력한 후, 괄호 안으로 커서를
    이동시키고 **Dynamic content**를 사용하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

15. **PropertyId** 매개변수를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

16. **Viewer Name** 필드에서는 **Dynamic content**를 사용해
    **ViewerName** 매개변수를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

17. **Viewer Email** 필드에서는 **Dynamic content**를 사용해
    **ViewerEmail** 매개변수를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

18. 이제 매개변수들이 아래 스크린샷과 유사하게 표시될 것입니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

19. **Respond to Copilot** 작업(action)을 선택하세요. **Settings**을
    선택한 후, **Asynchronous Response** 옵션이 **Off**으로 설정되어
    있는지 확인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

20. **Save draft**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

21. 저장되면 **Publish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

22. Power Automate 탭을 닫으세요.

### 작업 4: 예약 요청을 생서하기 위한 Copilot 작업 추가

1.  Copilot Studio 페이지로 돌아가 **Refresh**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

2.  **Booking Request** 플로우를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

3.  **Add action**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image71.png)

4.  Review inputs and outputs에서 **Next**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

5.  **Review and finish** 화면에서 **Finish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

6.  **Topics** 탭을 선택하고 **Book a Real Estate Showing** 주제를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

7.  **What date and time do you want to see the property?** 노드 아래
    있는 + 아이콘을 선택하고 **Add an action**를 선택하세요.

8.  **Booking Request** 플로우를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

9.  **PropertyId** 입력 매개변수에 대해**PropertyId** 변수를 선택하세요.

**ViewerName** 입력 매개변수에는 **Name** 변수를 선택하세요.

**ViewerEmail** 입력 매개변수에 대해 **EmailAddress** 변수를 입력하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

10. Action 노드 아래의 + 아이콘을 선택하세요. 그 후, **Topic
    management을** 선택하고, **Go to another topic**을 선택한 후 **End
    of conversation**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

11. **Save**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

12. 저장되면 **Publish**를 선택하고 확인 대화상자에서 다시 한
    번**Publish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

## 연습 3: 에이전트 테스트

### 작업 1: 에이전트를 테스트하고 예약 요청을 진행

1.  화면 오른쪽 상단에 있는 **Test** 버튼을 선택하여 테스트 패널을
    엽니다. 그런 다음, 테스트 패널 상단 오른쪽에 있는 **점 세 개**
    아이콘을 클릭하고, 표시되는 옵션 중에서 **Track between topics**을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image81.png)

2.  **Conversation Start** 메시지가 나타나면, 에이전트가 대화를
    시작합니다.

3.  이에 응답으로, 여러분이 생성한 주제에 대한 트리거 문구(trigger
    phrase)를 입력하세요:

!!I want to book a real estate showing!!

4.  Copilot이 “What is your name?” 라는 질문으로 응답합니다**.**

5.  이름을 입력하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image82.png)

6.  이후 이메일을 입력하라는 메시지가 표시되면 이메일을 입력하세요.
    입력이 완료되면, 정보가 정확한지 확인하는 질문과 함께 **Yes** 또는
    **No**를 선택할 수 있는 옵션이 나타납니다. **Yes**를 선택하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image83.png)

7.  부동산 유형 질문에서 **House**를 선택하세요.

8.  !!**2**!! 를 침실 수 질문에 입력하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image84.png)

9.  **What date and time do you want to see the property?** 질문에
    !!Tomorrow 2:00 PM!!를 입력하세요.

10. **Yes** to the **Did that answer your question?** 질문에 **Yes**를
    선택하세요.

11. 아무 별점이나 선택하세요.

12. **Can I help with anything else?** 질문에 대해 **No** 를 선택하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image85.png)

### 작업 2: 예약 요청 확인

1.  Power Apps 포털로
    !\![**https://make.powerapps.com**](https://make.powerapps.com/)!!
    이동하세요.

2.  왼쪽 탐색 창에서 **Tables**을 선택한 후, **Custom**을 선택하세요.

3.  **Booking Request** 테이블을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image86.png)

4.  **Booking Request columns and data** 섹션에서, 이제 Copilot 예약
    요청이 생성된 것을 확인할 수 있습니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image87.png)

## 연습 4: Generative AI 설정

이번 실습에서는 생성형 답변(Generative answers) 기능을 활용해 copilot의
응답 품질을 향상시키는 방법을 배우게 됩니다.

### 작업 1: Generative AI를 활성화하기

1.  아직 로그인하지 않았다면,
    !\![https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com/)!!
    에 접속하여 테넌트 자격 증명으로 **Copilot Studio**에 로그인하세요.

2.  **Real Estate Booking Service** 에이전트를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image88.png)

3.  화면 오른쪽 상단에서 **Settings**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image89.png)

4.  **Generative AI** 탭을 선택하세요.

**How should your copilot decide how to respond** 항목에서
**Generative(preview)** 를 선택하세요.

**How strict should the content moderation be?** 항목에서는 **Medium**을
선택하세요.

**Save**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image90.png)

5.  Settings 창을 닫으세요(**Close)**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image91.png)

### 작업 2: 지식 사용

1.  **Overview** 탭을 클릭하세요.

2.  Knowledge 섹션에서 General knowledge가 활성화되어 있는지 확인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image92.png)

### 작업 3: 웹 사이트에서 지식 추가

1.  **Knowledge**  섹션에서 **+ Add knowledge**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image93.png)

2.  **Public websites** 타일을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image94.png)

3.  다음 공개 웹 사이트 링크를 입력하세요:
    !\!<https://create.microsoft.com/templates/real-estate>!!. **Add**을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image95.png)

4.  Name 필드에 !!Real Estate Website!!라고 입력한 후, **Add**를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image96.png)

### 작업 4: Dataverse에서 지식 추가

1.  **Knowledge** 탭을 선택하세요. **+ Add knowledge**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image97.png)

2.  **Dataverse(preview)**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image98.png)

3.  **Real Estate Property** 테이블을 선택한 후 **Next**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image99.png)

4.  다음 화면에서 데이터를 미리 확인한 후 **Next**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image100.png)

5.  **Review and finish** 화면에서 세부 정보를 확인한 후, **Add** 버튼을
    클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image101.png)

### 작업 5: 파일에서 지식 추가

1.  **Knowledge** 탭에서 **+ Add knowledge**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image102.png)

2.  **Upload files** 섹션에서 **click to browse**를 선택한 후,
    **C:\LabFiles**  경로로 이동하여 **SummitRealtyCaseStudy.docx** 
    파일을 찾아 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image103.png)

3.  **Add**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image104.png)

:::danger **중요 사항:** 파일 업로드가 완료되고 인덱싱이 완료되는 데
다소 시간이 걸릴 수 있습니다. 파일이 사용 가능한 상태인지 확인하려면
**Knowledge** 탭에서 상태를 확인하세요. :::

### 작업 6: System fallback 주제에서 생성적 답변 사용하기

1.  **Topics** 탭에서 **System**을 선택하세요. **Fallback** 주제를
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image105.png)

2.  메시지 노드에서 **세 개의 점**을 선택하고 **Delet**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image106.png)

3.  Condition 아래에서 + 아이콘을 선택하고, **Advanced**을 선택한
    후, **Generative answers**를 선택하세요.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image107.png)

4.  **Input** 필드를 선택하고 **Select a variable** 창에서 **System**을
    선택하세요. 여기서 **Activity.Text**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image108.png)

5.  **Data sources**에서 **Edit**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image109.png)

6.  **Search only selected sources**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image110.png)

7.  **SummitRealtyCaseStudy** 문서를 선택하세요. **Allow the AI to use
    its own general knowledge**를 선택 취소하세요. **Content
    moderation**은 **Medium** 으로 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image111.png)

8.  **Save**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image112.png)

### 작업 7: 보안 구성

1.  **Overview** 탭을 선택하세요.

2.  화면 오른쪽 상단에서 **Settings**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image113.png)

3.  **Security** 탭을 선택한 후, **Authentication** 타일을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image114.png)

4.  Authenticate with Microsoft **(Entra ID authentication in Teams and
    Power App)**를 선택하세요.

5.  **Save**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image115.png)

6.  **Save**을 선택하세요.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image116.png)

7.  **Close**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image117.png)

8.  **Overview** 탭을 선택하세요.

9.  **Publish**를 선택하고 대화 상자에서 **Publish**를 다시 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image118.png)

### 작업 8: 에이전트의 지식 테스트

1.  화면 오른쪽 상단에 있는 **Test**  버튼을 선택하여 테스트 패널을
    여세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image119.png)

2.  아직 선택하지 않았다면, **Activity map**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image120.png)

3.  Test 패널에서 **Refresh** 버튼을 선택해 새로운 대화를
    시작하세요**(Start a new conversation**).

4.  !!What is Summit Realty group?!!를 입력하고 **send** 버튼을
    누르세요.

5.  해당 파일이 Fallback 주제의 지식 소스로 추가되었기 때문에, 아래
    스크린샷과 같이 업로드한 파일로부터 응답을 받을 수 있습니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image121.png)

**요약:**

이번 실습에서는 다음과 같은 내용을 배웠습니다:

- 엔터티와 슬롯 채우기(slot filling) 사용하기

- 플로우(Flow) 작업 구현하기

- 에이전트에 지식 추가하기

- Generative AI 활성화하기
