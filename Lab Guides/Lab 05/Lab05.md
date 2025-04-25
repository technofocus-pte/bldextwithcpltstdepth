# **실습 05 - 에이전트를 Dynamics 365 Customer Service 앱과 통합하고, 실시간 에이전트에게 자동으로 케이스를 이관(escalation)하는 기능 구현하기**

## 연습 1: Dynamics 365 Customer Service workspace워크스페이스 구성

### 작업 1: Omnichannel Power Virtual Agent 확장 구성

1.  아래 링크를 열고, Omnichannel Power Virtual Agent Extension
    페이지에서 **Get it now** 버튼을 클릭하세요:
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com>+++

![A screenshot of a computer Description automatically
generated](./media/image1.png)

![A screenshot of a computer Description automatically
generated](./media/image2.png)

![A screenshot of a computer Description automatically
generated](./media/image3.png)

2.  **Select an environment**에서 **CustomerService Trial**을 선택하고,
    체크박스를 선택한 후 **Install**을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Dynamics 365 apps 페이지에서 **Update available**이라고 표시된 항목을
클릭한 후, 약관에 동의하는 **check box**를 선택하고 **Update** 버튼을
클릭하세요. **Update available** 상태(Status)인 **모든** 항목에 대해 이
작업을 반복해야 합니다.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

![A screenshot of a computer Description automatically
generated](./media/image6.png)

### 작업 2: Power Platform 관리 센터에서 검색 설정 구성

1.  테넌트 정보를 사용해
    +++<https://admin.powerplatform.microsoft.com/>+++에 로그인하세요.
    **Environments** -\> **CustomerService Trial**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

2.  상단 창에서 **Resource** 옆의 드롭다운을 선택한 후, **Dynamics 365
    apps**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  **Omnichannel for Customer Service**가 설치(**installed**)되어
    있는지 확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

4.  관리자 센터에서 **Environments -\> CustomerService** **Trial**
    페이지로 돌아가서 상단 메뉴에서 **Settings**를 선택하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image10.png)

5.  **Product** -\> **Features**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

6.  **Dataverse Search** 및 **Single table search** 옵션을 **ON**으로
    전환하세요.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

화면을 아래로 스크롤한 후, 오른쪽 하단에 있는 Save 버튼을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

## 연습 2: 에이전트 생성하기

1.  Copilot Studio 홈 페이지 !!https://copilotstudio.microsoft.com!!
    에서 오른쪽 상단에 있는 **CustomerService Trial** Environment을
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  왼쪽 메뉴에서 Agents를 선택한 후, **+ New Agent**를 클릭하여 새
    에이전트를 생성하세요.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

3.  Type your message(메시지 입력) 입력란에 다음 문장을 입력하고
    **send**를 누르세요: **!!You are a customer service agent who helps
    in identifying stores nearby.**!!

![A screenshot of a chat Description automatically
generated](./media/image16.png)

4.  다음 메시지를 입력하고 **send**를 누르세요: !!**Maintain a polite
    tone**!!

![A screenshot of a chat Description automatically
generated](./media/image17.png)

5.  **Create**를 클릭하세요.

![A screenshot of a chat Description automatically
generated](./media/image18.png)

6.  생성된 에이전트가 열리며, **Your agent is ready**라는 메시지가
    표시됩니다.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

## 연습 3: Copilot을 Dynamics 365 Customer Service에 연결하고 Escalate 주제를 구성하기

### 작업 1: Escalate 주제 구성

이번 작업에서는 실시간 에이전트로의 전환(Escalation) 기능을 보여주는 데
중점을 둡니다. 따라서 다른 새 주제를 만들지 않고 바로 Escalate 주제를
구성하는 데 집중하겠습니다.

1.  **Topics** 탭을 선택한 후, **System** 탭을 선택하세요. **Escalate**
    주제를 선택하세요..

![A screenshot of a computer Description automatically
generated](./media/image20.png)

2.  주제의 메시지 노드를 선택한 후, 기존 내용을 다음으로 변경해주세요:
    !!**You will be transferred to a live agent shortly**!!

![A screenshot of a computer Description automatically
generated](./media/image21.png)

3.  Message 노드 옆에 있는 **+ 기호를 클릭하여 새 노드를 추가**하세요.

4.  **Topic management** -\> **Transfer conversation**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  Transfer conversation 노드에 다음 메시지를 입력하세요: !!The
    customer wants to talk to a live agent!!

![A screenshot of a chat Description automatically
generated](./media/image23.png)

6.  Topic을 저장(**save)**하세요.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  에이전트를 **Publish**하세요.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

### 작업 2: Copilot을 Dynamics 365 Customer Service에 연결

1.  게시되면 오른쪽 상단의 copilot 페이지에서 **Settings**을
    클릭하세요.![A screenshot of a computer Description automatically
    generated](./media/image26.png)

2.  **Security**를 선택한 후, Security에서 **Authentication**을
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  **No authentication** 옵션을 선택한 후, **Save**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  확인 대화 상자에 **Save** 버튼을 선택하세요.

![A screenshot of a computer screen Description automatically
generated](./media/image29.png)

5.  **Settings** 창을 닫으세요.

6.  **Channels**을 클릭하세요.(**Channels** 옵션이 보이지 않는 경우,
    **+1**을 클릭하여 **Channels** 옵션을 표시).

![A screenshot of a chat Description automatically
generated](./media/image30.png)

7.  Customer engagement hub 창에서 **Dynamics 365 Customer Service**를
    선택하세요.

![](./media/image31.png)

8.  Dynamics 365 Customer Service 페이지에서 **Connect**를 클릭하세요.

![A screenshot of a message Description automatically
generated](./media/image32.png)

9.  **successfully connected** 메시지가 표시되면 **Close**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

## 연습 4: Dynamics 365 관리자 센터에서 워크스트림 및 채널 생성하기

### 작업 1: Omnichannel for Customer Service에서 사용자 관리

1.  관리자 테넌트 자격 증명을 사용해
    !!https://admin.powerplatform.microsoft.com!! 에 로그인하고 왼쪽
    탭에서를 선택하세요. 여기에서 CustomerService Trial이 표시됩니다.
    이를 **선택**하세요**.**

![A screenshot of a computer Description automatically
generated](./media/image34.png)

2.  **Environment URL**에서 **url value**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

이제 **Apps** 페이지가 열립니다. 여기서 **Customer Service admin
center**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

3.  그러면 **Dynamics 365 Customer Service admin center** 페이지가
    열립니다.

![A screenshot of a customer service Description automatically
generated](./media/image37.png)

4.  **Dynamics 365 Customer Service admin center**의 사이트 맵에서
    **Customer support** 그룹 아래에 있는 **User management**를
    선택하세요.

5.  **User management** 페이지에서 **Users** 옆에 있는 **Manage** 버튼을
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

6.  **Enabled Users** 옆의 드롭다운을 클릭하고 **Omnichannel Users**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

7.  **Omnichannel Users** 페이지의 목록에서 사용자 **MOD
    Administrator**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

8.  **MOD Administrator** 페이지에서 **Omnichannel** 텝을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

9.  아래 표에 따라 값이 정확히 설정되어 있는지 확인하세요.

\- Capacity: 100

\- Default Presence: available

![A screenshot of a computer Description automatically
generated](./media/image42.png)

10. **Save and close**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

### 작업 2: 워크스트림 구성 

1.  Admin center 페이지에서 왼쪽 메뉴의 **Customer support** 아래에 있는
    **Workstreams**을 선택한 후, **+ New workstream** 옵션을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image44.png)

2.  다음 정보를 입력하고 아래로 스크롤하여 **Create**를 클릭하세요.

- Name - +++**New Workstream**+++

- Owner – **MOD Administrator** (Selected by default)

- Type – **Messaging**

- Channel – **Chat**

> ![A screenshot of a chat Description automatically
> generated](./media/image45.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image46.png)

3.  워크스트림이 생성되면 **Set up chat**을 클릭하여 채팅 채널을
    설정하세요.

![A screenshot of a chat Description automatically
generated](./media/image47.png)

4.  **Live chat setup**에서 **– Channel details** 화면에서 다음 정보를
    입력하고**Next**를 클릭하세요.

- Name - +++**Chat Channel**+++

- Language – **English -** **United States**

![A screenshot of a chat channel Description automatically
generated](./media/image48.png)

5.  Live chat setup 에서 – Chat widget 화면에 이름을 +++**Store Locator
    Assistant**+++으로 입력하고 기본 설정은 그대로 두고 **Next**를
    클릭하세요.

![A screenshot of a chat Description automatically
generated](./media/image49.png)

6.  **Live chat setup – Behaviors** 화면에서 기본 설정을 그대로 두고
    **Next**를 클릭하세요.

![A screenshot of a computer screen Description automatically
generated](./media/image50.png)

7.  **Live chat setup – User features** 화면에서 **File attachment** 및
    **Voice and video calls** 옵션을 **off**으로 설정하고 **Next**를
    클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

8.  **Live chat setup – Review and finish** 화면에서 **Create
    channel**를 선택하세요.

![A screenshot of a chat setup Description automatically
generated](./media/image52.png)

9.  **Live chat setup** - **Success** 화면에서 나타나는 위젯을
    복사(**copy**)하여 메모장에 저장(**save**)한 후, 연습에서 웹
    페이지에 추가할 수 있도록 준비하세요. 그런 다음 **Done**을 클릭하여
    구성을 완료하세요.

![A screenshot of a chat Description automatically
generated](./media/image53.png)

### 작업 3: 워크스트림에 copilot 추가

1.  **New Workstream** 페이지로 돌아가서, 아래로 스크롤하여 Bot 섹션에서
    **+ Add bot**을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image54.png)

2.  **Add bot** 화면에서, 목록에 있는 **Store Locator Assistant**
    copilot을 선택하고 **Connect**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image55.png)

3.  아래 스크린샷과 같이 해당 봇이 워크스트림에 정상적으로 추가되었는지
    확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image56.png)

4.  왼쪽 창에서 **Bots**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image57.png)

5.  Real Estate Booking Service copilot가 연결되어 있는지 확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image58.png)

## 연습 5: 웹페이지를 생성하고 에이전트로의 에스컬레이션 기능을 테스트하기

1.  테넌트 관리자 자격 증명을 사용하여
    +++https://make.powerpages.microsoft.com/+++에 로그인하세요.

![A screenshot of a computer Description automatically
generated](./media/image59.png)

2.  **CustomerService Trial** 환경에 있는지 확인하세요.

3.  **Get started**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

4.  **Tell us about yourself** 페이지에서 Skip를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image61.png)

5.  다음 페이지에서 아래로 스크롤한 후 **Start with a template** 옵션을
    클릭하여 사이트를 템플릿으로 생성하세요.

![A screenshot of a web page Description automatically
generated](./media/image62.png)

6.  템플릿을 선택하고 **Choose this template**을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

7.  Give your site a name 텍스트 상자에 +++**Contoso Store
    assistant**라고 입력한 후, 나머지 기본 설정은 그대로 두고 **Done**
    버튼을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

8.  사이트가 생성되면, **Company name** 제목 부분에 있는 **Edit site
    header**을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

9.  **Edit site header** 창에서 **Site title**을 !!**Contoso Store
    assistant**!!로 입력하세요.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

10. 페이지 오른쪽 상단에서 **Edit code**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

11. **Open Visual Studio Code**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

12. **Allow**를 클릭하세요.

![A black screen with white text Description automatically
generated](./media/image69.png)

13. 웹 페이지의 홈 페이지가 Visual Studio Code에서 열립니다.

![A screenshot of a computer program Description automatically
generated](./media/image70.png)

14. 파일의 끝으로 스크롤을 내린 후, 워크스트림을 생성할 때 복사한
    **script**를 이 파일의 마지막 줄 뒤에 추가하세요.

![A screen shot of a computer screen Description automatically
generated](./media/image71.png)

15. 파일을 저장하고, Visual Studio Code 탭을 닫은 후 Power Pages로
    돌아가서 **Sync**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

16. Sync가 완료되면, **Preview** -\> **Desktop**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image73.png)

17. 웹 페이지가 새 탭에서 열리면, 페이지 오른쪽 하단에 임베드된 **Store
    Locator Assistant**를 찾아 클릭(**click**)하세요.

![A screenshot of a website Description automatically
generated](./media/image74.png)

18. +++Talk to agent+++를 입력하세요.

![A screenshot of a phone Description automatically
generated](./media/image75.png)

19. From the Customer Service admin 페이지에서 **Customer Service admin
    center**를 클릭한 후, 여기서**Customer Service workspace** 앱을
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image76.png)

![A screenshot of a computer Description automatically
generated](./media/image77.png)

20. Customer Service 워크스페이스 페이지에서 **chat request**을 받게
    됩니다. 요청을 수락(**accept)**하세요.

![A screenshot of a computer Description automatically
generated](./media/image78.png)

21. 수락하면, 채팅 화면이 열리며 Escalate 주제에서 설정한 메시지가
    표시됩니다. 또한, 사용자가 제공한 다른 정보를 라이브 에이전트에게
    전달할 수 있습니다.

![A screenshot of a chat Description automatically
generated](./media/image79.png)

22. 라이브 에이전트와 고객 간의 채팅을 시뮬레이션하여 어떻게 작동하는지
    확인한 후, 채팅을 종료합니다.

![A screenshot of a chat Description automatically
generated](./media/image80.png)

![A screenshot of a chat Description automatically
generated](./media/image81.png)

**요약**

이 실습에서는 다음을 배웠습니다:

- Copilot Studio에서 에이전트를 구축하고 Escalate 주제를 구성하는 방법

- 에이전트를 Dynamics 365 워크스페이스에 게시하고 이를 웹 페이지에 통합

- 라이브 에이전트로의 에스컬레이션을 구성하고 테스트하는 방법
