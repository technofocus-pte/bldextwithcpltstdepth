# 실습 02 – OneDrive에 새로 생성된 파일을 모니터링하는 자율 에이전트 구축

**소개**

조직의 OneDrive For Business에 여러 파일이 생성되고 있어, 관리자가 이를
관리하는 데 어려움을 겪고 있습니다.

**목표**

새로 추가된 파일의 세부 정보를 Files Details(파일 정보) 추적기에
자동으로 입력하는 자율 에이전트를 구축하는 것입니다. 이를 통해 파일
추가를 효율적으로 관리할 수 있게 되고, 파일 정보 추적기에는 새로 생성된
모든 파일의 세부 정보가 저장됩니다.

## 연습 1: 환경 설정

1.  Resources 탭의 비밀번호를 사용하여 VM에 로그인하세요.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

### 작업 1: OneDrive 설정

1.  브라우저를 열고 +++https://office.com+++로 이동하세요. **Resources**
    탭의 자격 증명을 사용하여 로그인(**Sign in)**하세요.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

2.  왼쪽 메뉴에서 **OneDrive**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

3.  왼쪽 상단의 + 기호를 클릭하고 Files Upload를 선택하세요**.**

![A screenshot of a computer Description automatically
generated](./media/image4.png)

4.  C:\LabFiles에서 **File details**파일을 선택하고 **Open**을
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

5.  파일이 성공적으로 업로드되면 성공 메시지 창이 나타납니다.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

6.  왼쪽 메뉴에서 **My files**을 클릭하면, 새 파일이 추가된 것을 확인할
    수 있습니다.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

### 작업 2 : 개발 환경 생성하기

1.  Resources 탭의 테넌트 정보를 사용해
    +++<https://admin.powerplatform.microsoft.com/>+++에 로그인하세요.

2.  왼쪽 탐색 창에서 **Environments**을 선택하고 **+ New**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

3.  열린 New environment 창에서 아래 정보를 입력한 후, **Next**를
    클릭하세요.

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image9.png)

![A screenshot of a computer Description automatically
generated](./media/image10.png)

4.  **Add Dataverse** 창에서 기본값을 수락하고 **Save**을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

5.  새로 생성된 환경은 Admin center의 Environments 창에 상태와 함께
    표시됩니다.

6.  **Status**가 **Ready**로 표시되면, 해당 환경을 사용할 수 있습니다.
    이 환경은 다음 실습에서 사용하게 될 예정입니다.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

### 작업 3: Copilot Studio 체험판 활성화

1.  새 탭에서 +++**https://copilotstudio.microsoft.com/**+++를 여세요.

2.  Lab VM의 **Resources** 탭에 제공된 **Credentials**으로 로그인하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image13.png)

3.  로그인 후, **Welcome to Microsoft Copilot Studio** 페이지에서 국가를
    **United States**로 그대로 두고, **Get Started**를 클릭하세요.

![A person sitting at a computer Description automatically
generated](./media/image14.png)

4.  **Welcome** 화면에서 **Skip**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

## 연습 2: 자율 에이전트 구축 및 테스트

### 작업 1: Copilot Studio에서 에이전트 생성하기

1.  열리는 Agent creation 페이지에서 Skip to configure 옵션을
    클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

2.  Agent creation 창에 다음 정보를 입력하고**Create**을 클릭하세요.

- **Name** - +++New file tracker agent+++

- **Description** - +++This agent will update the File details tracker
  placed in the OneDrive, each time a new file is created in the
  OneDrive

![A screenshot of a computer Description automatically
generated](./media/image17.png)

### 작업 2: 에이전트에 트리거 추가

1.  에이전트가 생성되면, 아래로 스크롤하여 **Trigger** 섹션을 찾고, **+
    Add trigger**를 선택하세요**.**

![A screenshot of a computer Description automatically
generated](./media/image18.png)

2.  **Turn on generative orchestration to continue** 대화 상자에서 Turn
    it on를 선택하세요. 트리거를 추가하려면 이 옵션을 on으로 설정해야
    합니다.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

3.  Add trigger 메뉴에서 **When a file is created** 트리거를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

4.  **Add trigger** 화면에서 Continue를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

다음 화면에서 **Trigger name**이 자동으로 채워진 것을 확인하세요.
**Microsoft Copilot Studio**와 **OneDrive for Business**에 대한
연결(**connections)**이 설정될 때까지 기다리세요 (각 커넥터 옆에 녹색
체크 표시됨). 그 후, **Next**를 클릭하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image22.png)

5.  다음 정보를 입력하세요.

- **Folder** – Root

- **Include subfolders** – Yes

> 다른 필드는 기본값으로 두고, **Create trigger**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

![A screenshot of a computer Description automatically
generated](./media/image24.png)

6.  트리거가 생성되면 **Time to test your trigger** 메시지가 표시됩니다.
    이를 **close** 하세요. 트리거의 기본 흐름을 조금 수정하여 기능을
    구현한 후, 테스트를 진행할 것입니다.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

### 작업 3: 트리거에 로직 추가

1.  New file track agent 페이지에서 트리거 섹션까지 아래로 스크롤하세요.

2.  **When a file is created** 트리거 옆의 3개의 점을 클릭하고, **Edit
    in Power Automate**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

3.  **When the file is created**와 **Sends a prompt** 액션 사이에 있는 +
    아이콘을 선택하고, **Add an action**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

4.  +++add a row+++를 검색하고 **Add a row into the table**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

5.  각 행에 대해 아래 값을 선택하고 **save**을 클릭하세요.

[TABLE]

![A screenshot of a computer Description automatically
generated](./media/image30.png)

![A screenshot of a computer Description automatically
generated](./media/image31.png)

6.  이제 플로우가 아래 스크린샷과 같이 표시됩니다.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

7.  플로우를 저장하고 **publish** 하세요.

### 작업 4: 트리거 게시

1.  Copilot Studio로 돌아가서 **Settings**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

2.  **Security** -\> **Authentication** -\> **No authentication**
    선택하고**Save**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image34.png)

3.  확인(confirmation) 대화상자에서 **Save**을 선택하세요.

![A screenshot of a computer error Description automatically
generated](./media/image35.png)

4.  이제 **Publish**를 선택하여 에이전트를 게시하세요.

![](./media/image36.png)

5.  확인 대화상자에서 **Publish**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

### 작업 5: 트리거를 테스트하기

1.  브라우저에서 OneDrive로 다시 이동하세요 . **+** 를 클릭하고 **Word
    document**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

2.  문서에 **name**을 지정하고 **Create**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

3.  **Close**을 클릭하여 개인 정보 보호(privacy) 옵션을 닫으세요.

![A screenshot of a computer screen Description automatically
generated](./media/image40.png)

4.  이와 비슷하게 몇 개의 파일을 더 추가하세요.

5.  이제 OneDrive에서 파일 details.xlsx 열고 생성된 파일의 세부 정보가
    추적기에 추가되었는지 확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image41.png)

6.  OneDrive에 파일이 생성되면 트리거가 실행되어 **When a file is
    added**흐름을 실행하고 추적기를 업데이트합니다.

7.  또한, Copilot Studio의 Activity탭에서 자율 에이전트의 세부 사항을
    확인할 수 있습니다.

**요약**

이 실습에서는 Copilot Studio에서 자율 에이전트를 생성, 게시 및
테스트하는 방법을 배웠습니다.
