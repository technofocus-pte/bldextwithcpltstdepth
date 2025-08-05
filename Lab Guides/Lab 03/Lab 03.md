# 실습 03 – 템플릿에서 안전 여행 에이전트 만들기

**목표**

에이전트 템플릿은 사용자 지정 에이전트를 시작하는 데 도움이 되도록 설계되었습니다. 에이전트 템플릿 사용의 모든 안전 및 법적 영향을 평가하고 비즈니스에 맞게 사용자 지정할 책임이 있습니다. 

Safe Travels 에이전트 템플릿에서 구축된 에이전트는 회사 직원에게 출장 지원을 제공하도록 설계된 Business-to-Employee (B2E) 에이전트입니다. 이 에이전트는 직원들이 다음 출장을 위해 잘 준비하고 정보를 얻을 수 있도록 도와줍니다. 이 에이전트는 자연어 처리를 사용하여 대화형 인터페이스를 제공하므로 직원이 필요한 정보에 쉽고 직관적으로 액세스할 수 있습니다. 그러나 에이전트가 사용하는 기본 웹사이트는 현재 미국 여행지에만 적용됩니다. 기본 웹사이트를 자신의 지식 소스로 바꿀 수 있습니다. 

이 실습에서는 Safe Travels 템플릿에서 에이전트를 생성하고 실습 05에서 개선합니다.               

## 연습 1: 템플릿을 사용하여 Safe Travels 에이전트 만들기

이 연습에서는 Safe Travels 에이전트 템플릿을 사용하여 Copilot Studio에서 에이전트를 생성합니다. 

1.  브라우저에서 +++https://copilotstudio.microsoft.com+++에
    로그인합니다. 무료 평가판 시작 페이지가 열립니다. 국가를 선택하고
    **Start free trial**을 클릭합니다.

    ![](./media/image1.png)

2.  **Dev One** 환경을 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  왼쪽 창에서 **+ Create**를 선택하여 새 에이전트를 만듭니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

4.  **Start with an agent template Safe Travels**을 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

5.  Safe Travels 템플릿은 회사 직원에게 여행 지원을 제공하도록 설계된
    새로운 에이전트를 만듭니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  설정 페이지를 탐색하세요. **Knowledge** 아래에 that **US Travel
    Website**가 이미 Knowledge source로 추가되어 있는 것을 확인할 수
    있습니다. 필요한 경우 편집할 수 있습니다. 여기서는 동일한 웹사이트를
    사용합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  **Create**를 선택하여 Safe Travels에이전트를 생성합니다. 여기서는
    아무것도 변경하지 않고 기존 템플릿을 그대로 사용합니다. 사용자 요구
    사항에 따라 언제든지 에이전트를 업그레이드할 수 있습니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  **에이전트**가 **생성되고** 자동으로 열리면서 **Overview** 페이지가
    표시됩니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

    테스트 창에 +++How to apply for passport?+++을 입력하고 보내기를
클릭하세요.

테스트 창은 기본적으로 열려 있습니다. 열려 있지 않으면 오른쪽 상단의
테스트 아이콘을 클릭합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

9.  해당 여행사가 자체 지식 소스를 통해 여권 신청 방법에 대한 정보를
    제공하는 것을 볼 수 있습니다.

    ![A screenshot of a phone AI-generated content may be
incorrect.](./media/image10.png)

## 연습 2: Teams 및 Microsoft 365 Copilot에 에이전트 게시하기

이 연습에서는 Copilot Studio에서 생성한 에이전트를 Microsoft Teams 및 Microsoft 365 Copilot 채널에 게시합니다.

1.  에이전트 페이지 오른쪽 상단에서 **Publish**를 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  확인 대화 상자에서 **Publish**를 선택합니다.

    ![](./media/image12.png)

3.  상단 탐색 모음에서 **Channels**을 선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

4.  사용 가능한 채널 목록에서 **Teams**와 **Microsoft 365 Copilot**을
    선택합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  **Add channel**을 성택합니다.

    ![](./media/image15.png)

6.  **See agent in Teams**옵션을 클릭하여 에이전트를 Teams에 추가합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

7.  Microsoft Teams에서 에이전트가 열립니다. **Add**를 선택하여
    에이전트를 추가합니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  에이전트를 추가하면 해당 에이전트를 열 수 있는 옵션이 나타납니다.
    **Open**를 선택합니다.

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image19.png)

9.  Teams에서 에이전트를 테스트합니다.

![](./media/image20.png)

10. Copilot Studio로 돌아와서 Teams 및 Microsoft 365 Copilot 채널 창을
    닫습니다.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)


