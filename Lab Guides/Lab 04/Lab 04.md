# 실습 04 - 에이전트를 Dynamics 365 Customer Service 앱에 통합하고 실시간 에이전트에게 자동 사례 에스컬레이션 구현하기

## 목표

이 실습에서는 에이전트가 실시간 에이전트에게 대화를 에스컬레이션하는
단계를 자세히 설명합니다.

\[!알림\] **중요**: 이 실습은 실습 02 - **Dynamics 365 Customer Service
구성**에 따라 Dynamics 365 평가판이 활성화된 경우에만 실행할 수
있습니다.

## 연습 1: Dynamics 365 Customer Service 작업 영역 구성하기

### Task 1: Configure Omnichannel Power Virtual Agent Extension

1.  다음 링크를 엽니다.
    +++<https://appsource.microsoft.com/en-cy/product/dynamics-365/mscrm.omnichannelpvaextension?tab=Overview&ref=dynamicsforcrm.com+++>
    그리고 Omnichannel Power Virtual Agent 확장 프로그램 페이지에서
    **Get it now** 를 클릭합니다.

![](./media/image1.png)

2.  **Resources** 탭에서 테넌트 자격 증명으로 로그인합니다.

![](./media/image2.png)

3.  **Get it now**를 클릭합니다.

![](./media/image3.png)

4.  **Select an environment**에서 **CustomerService Trial** 선택하고
    확인란을 선택한 후 **Install**을 클릭합니다.

![](./media/image4.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

## 작업 2: Power Platform 관리 센터에서 검색 설정 구성하기

1.  테넌트 정보를 사용하여
    +++<https://admin.powerplatform.microsoft.com/+++>에 로그인합니다.
    왼쪽 창에서 **Manage**를 선택한 다음 환경 목록에서 **CustomerService
    Trial** 환경을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

2.  상단 창에서 **Settings**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

3.  **Product** -\> **Features**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

4.  **Dataverse Search** 및 **Single table search**  옵션을 **ON**으로
    전환하고 **Save**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

## 연습 2: 에이전트 만들기

1.  Copilot Studio 홈페이지
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/)에서
    오른쪽 상단의 **CustomerService Trial** 환경을 선택합니다.

![](./media/image10.png)

2.  왼쪽 창에서 **Agents**를 선택합니다. **+ New Agent** 를 클릭하여 새
    에이전트를 생성합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

3.  메시지 입력란에 +++**You are a customer service agent who helps in
    identifying stores nearby.**+++를 입력하고 **send**를 누릅니다.

![](./media/image12.png)

4.  에이전트가 생성되는 에이전트의 **이름**을 제안할 수 있습니다. 제안된
    이름을 수락하거나 새 이름을 제안합니다.

5.  다음으로 +++ **Maintain a polite tone** +++라는 메시지를 입력하고
    **send**를 누릅니다.

![](./media/image13.png)

6.  **Create**를 클릭합니다.

![](./media/image14.png)

7.  생성된 에이전트가 열리면 **Your agent is ready**라는 메시지가
    표시됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## 연습 3: 부조종사를 Dynamics 365 Customer Service에 연결하고 Escalate주제 구성하기

### 작업 1: Escalate 주제 구성하기

여기서는 실시간 에이전트에게 에스컬레이션하는 개념을 소개하는 데 중점을
두고 있습니다. 따라서 다른 새로운 주제를 만들지 않고 바로 에스컬레이션을
진행해 보겠습니다.

1.  **Topics** 탭을 선택한 다음 **System** 탭을 선택합니다.
    **Escalate**  주제를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

2.  주제의 메시지 노드를 선택하고 기존 내용을 다음으로 바꾸세요. +++You
    will be transferred to a live agent shortly+++

![](./media/image17.png)

3.  \+ 기호를 클릭하여 메시지 노드 옆에 노드를 추가합니다.

4.  **Topic management** -\> **Transfer conversation**.을 선택합니다.

![](./media/image18.png)

5.  Transfer conversation 노드에서 +++The customer wants to talk to a
    live agent+++메시지 보냅니다.

![ ](./media/image19.png)

6.  주제를 저장합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

7.  에이전트를 **게시합니다.**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

### 작업 2: Dynamics 365 Customer Service에 Copilot 연결하기

1.  게시가 완료되면 Copilot 페이지 오른쪽 상단에서 **Settings**을
    클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

2.  **Security**를 선택하고 보안 아래의 **Authentication**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

3.  **No authentication** 옵션을 선택한 다음 **Save**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

4.  확인 대화 상자에서 **Save** 을 선택합니다.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image25.png)

5.  **Settings** 창을 닫습니다.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image26.png)

6.  **Channels**을 클릭합니다(채널이 보이지 않으면 +1을 클릭하여
    **Channels** 옵션을 확인하세요)

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image27.png)

7.  Customer engagement hub창에서 **Dynamics 365 Customer Service**를
    선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  Dynamics 365 Customer Service 페이지에서 **Connect**을 클릭합니다.

![A screenshot of a message AI-generated content may be
incorrect.](./media/image29.png)

9.  **successfully connected** 라는 메시지가 나타나면 **Close**를
    클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

## 연습 4: Dynamics 365 관리 센터에서 워크스트림 및 채널 만들기

### 작업 1: 고객 서비스용 옴니채널에서 사용자 관리하기

1.  관리자 테넌트 자격 증명을 사용하여
    +++[https://admin.powerplatform.microsoft.com+++](https://admin.powerplatform.microsoft.com+++/)에
    로그인합니다. 왼쪽 창에서 **Manage**를 선택합니다. **Environments**
    아래에서 **CustomerService** **trial**환경"을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

2.  **Environment URL** 아래의 **URL value**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

3.  헤더 바에서 **Customer Service workspace**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  **Apps** 페이지가 열립니다. 여기서 **Customer Service admin
    center**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  **Dynamics 365 Customer Service admin center**페이지가 열립니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

### 작업 2: 워크스트림 구성하기

1.  관리 센터 페이지 왼쪽 창의 **Customer support** 에서
    **Workstreams**을 선택한 후 **+ New workstream** 옵션을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

2.  Inbound를 선택합니다.

![](./media/image37.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

3.  아래 세부 정보를 입력하고 아래로 스크롤하여 **Create**를 클릭합니다.

    - Name - +++**New Workstream**+++

    - Owner – **MOD Administrator** (Selected by default)

    - Type – **Messaging**

    - Channel – **Chat**

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image39.png)

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image40.png)

4.  workstream이 생성되면 **Set up chat**을 클릭하여 채팅 채널을
    설정합니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

5.  **Live chat setup – Channel details**  화면에서 아래 세부 정보를
    입력합니다.

    - Name - +++**Chat Channel**+++

    - Language – **English - United States**

![A screenshot of a chat channel AI-generated content may be
incorrect.](./media/image42.png)

6.  아래로 스크롤하여 **Next**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

7.  다음 두 페이지에서 채팅 위젯 화면이 나올 때까지 기본값을 그대로
    사용합니다. 라이브 채팅 설정 - 채팅 위젯 화면에서 이름을 +++ **Store
    Locator Assistant** +++로 입력하고, 나머지 기본값은 그대로 둔 후
    **Next**을 클릭합니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

8.  **Live chat setup – Behaviors** 화면에서 기본값을 그대로 두고
    **Next**을 클릭합니다.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image45.png)

9.  **Live chat setup – User features** 화면에서 **File attachment** 및
    **Voice and video calls** 옵션을 끄고 **Next**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

10. 알림 화면에서 기본값을 수락하고 **Next**을 클릭합니다.

11. **Live chat setup – Review and finish** 화면에서 **Create
    channel**를 선택합니다.

![](./media/image47.png)

12. **Live chat setup – Success**  화면에 나타나는 위젯 값을 복사하여
    메모장에 저장하고, 이후 연습에서 웹 페이지에 추가합니다. 그런 다음
    **Done**를 클릭하여 구성을 완료합니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image48.png)

### 작업 3: 워크스트림에 에이전트 추가하기

1.  **New Workstream** 페이지로 돌아가 아래로 스크롤하여 봇 섹션에서 **+
    Add bot** 를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  Add bot 화면의 조종사 목록에서 **Store Locator Assistant**
    에이전트를 선택하고 **Connect**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  아래 스크린샷과 같이 봇이 workstream에 추가되었는지 확인합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  왼쪽 창에서 **AI Agents**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  **Store locator**  에이전트가 연결되었는지 확인합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## 연습 5: 웹 페이지를 만들고 에이전트로 에스컬레이션을 테스트하기

1.  테넌트 관리자 자격 증명을 사용하여
    +++<https://make.powerpages.microsoft.com/+++>에 로그인합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  **CustomerService Trial** 환경에 있는지 확인합니다.

3.  **Get started**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

4.  **Tell us about yourself**  페이지에서 Skip를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  다음 페이지에서 아래로 스크롤하여 **Start with a template** 옵션을
    클릭하면 템플릿을 사용하여 사이트를 만들 수 있습니다.

![A screenshot of a web page AI-generated content may be
incorrect.](./media/image57.png)

6.  템플릿을 선택하고 이 **Choose this template**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  Give your site a name 텍스트 상자에 이름을 **+++Contoso Store
    assistant+++**로 입력하고 나머지는 기본값으로 설정한 후 **Done**를
    클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

8.  사이트가 생성되면 **Edit**을 클릭합니다.

> ![](./media/image60.png)

9.  **Company name** 제목에서 **Edit site header** 을 클릭합니다.

![](./media/image61.png)

10. **Edit site header** 창에서 **Site title** 을 +++**Contoso Store
    assistant**+++로 입력하고 대화 상자를 닫습니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

11. 페이지 오른쪽 상단에 있는 **Edit code**을 클릭합니다.

![](./media/image63.png)

12. **Open Visual Studio Code**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

1.  **Allow**을 클릭합니다. 필요한 경우 테넌트 자격 증명을 사용하여
    **로그인**합니다.

![A black screen with white text AI-generated content may be
incorrect.](./media/image65.png)

13. 웹 페이지의 홈페이지가 Visual Studio Code에서 열립니다.

![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image66.png)

14. 파일 끝까지 스크롤합니다. workstream을 생성할 때 복사한 **script**를
    이 파일의 마지막 줄 뒤에 추가합니다.

![A screen shot of a computer screen AI-generated content may be
incorrect.](./media/image67.png)

15. 파일을 저장하고 Visual Studio Code 탭을 닫은 후 Power 페이지로
    돌아갑니다. **Sync**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

16. 동기화가 완료되면 **Preview** -\> **Desktop**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

17. 웹 페이지가 새 탭에서 열립니다. 웹 페이지 오른쪽 하단에서 페이지에
    내장된 **Store Locator Assistant** 를 찾아 **클릭합니다.**

![A screenshot of a website AI-generated content may be
incorrect.](./media/image70.png)

18. +++Talk to agent+++를 입력합니다.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

19. 고객 서비스 관리 페이지에서 **Customer Service admin center** 를
    클릭하고 해당 센터에서 앱 **Customer Service workspace** 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

20. Customer Service workspace 페이지에서 **chat request**을 받게
    됩니다. **Accept**합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

21. 수락되면 채팅 화면이 열리고 Escalate 제목에서 입력한 메시지가
    표시됩니다. 사용자가 입력한 다른 정보는 실시간 에이전트에게 추가할
    수 있습니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image75.png)

22. 실시간 상담원과 고객 간의 채팅을 시뮬레이션하여 채팅이 어떻게
    진행되고 끝나는지 확인합니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image76.png)

> ![A screenshot of a chat AI-generated content may be
> incorrect.](./media/image77.png)

## 요약

이 실험실에서 우리는 다음을 배웠습니다:

- Copilot Studio에서 에이전트를 생성하고 에스컬레이션 주제를 구성합니다.

- 에이전트를 Dynamics 365 작업 영역에 게시하고 웹 페이지에 통합합니다.
