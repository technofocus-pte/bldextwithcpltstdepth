# 실습 7 – Computer-Using Agents (CUA) 를 이용한 자율 금융 데이터 검색 에이전트를 구축하기

**소개**

API가 없는 레거시 시스템은 자동화에 큰 장애물을 생성합니다. 전통적인
RPA는 종종 취약한 화면 스크레이핑이나 수동 우회 방법에 의존하는데, 이는
의사결정을 느리게 하고 오류가 증가하며 생산성을 저하시킵니다. 이
연구실에서는 Microsoft Copilot Studio 및 Computer Using Agents(CUA)를 더
스마트한 솔루션으로 소개합니다. 내부 시스템과의 인간 상호작용을
시뮬레이션함으로써 CUA는 API 통합 없이도 데이터를 안전하게 접근하고
처리할 수 있습니다. 더 빠른 응답을 제공하고, 수작업 부담을 줄이며,
실시간으로 정보에 기반한 의사결정을 가능하게 하는 자율 에이전트를
생성하는 법을 배우게 됩니다.

목표

이 실습에서는 Microsoft Copilot Studio를 사용해 자율 에이전트를 생성하는
방법을 배울 것입니다. 이 에이전트는 직접 API 접근 없이도 레거시 내부
시스템과의 인간 상호작용을 시뮬레이션하여 금융 포트폴리오 데이터를
조회할 것입니다.

## 작업 1: 자율적인 에이전트를 생성 및 구성하기

이 작업에서는 Microsoft Copilot Studio에서 새로운 자율 에이전트를
생성하고, 그 ID를 설정하며, Microsoft 365 Outlook 커넥터를 사용해 이메일
트리거를 설정해야 합니다.

포트폴리오 조회를 자동화하려면 에이전트가 들어오는 이메일 요청을
감지하고 제목 필터링을 기반으로 적절한 자동화 흐름을 시작할 수 있어야
합니다.

1.  자격 증명을 사용하여 +++https://copilotstudio.microsoft.com+++로
    Copilot Studio에 로그안하세요.

2.  오른쪽 상단에서 Dev One 환경을 선택하세요.

![](./media/image1.png)

3.  **Create an agent**를 선택하세요.

![](./media/image2.png)

4.  에이전트가 생성되면 **Details**에 **Edit** 를 선택하세요.

![](./media/image3.png)

5.  Name을 +++Portfolio Lookup Agent+++로 입력하고 에이전트의 기본
    이름을 변경하려면 Save를 선택하세요.

![](./media/image4.png)

6.  트리거 섹션으로 스크롤하여 **+Add trigger**를 선택하세요.

![](./media/image5.png)

7.  **When a new email arrives (V3) (Office 365 Outlook**을 검색하고
    선택하고 **Next**를 클릭하세요.

![](./media/image6.png)

8.  트리거 이름을 +++When a portfolio lookup email arrives+++로
    변경하세요. Copilot Studio 및 Outlook에 대한 연결이 확립되었늕지
    확인한 후 **Next**를 클릭하세요.

![](./media/image7.png)

9.  **Subject Filter (Optional)** 필드에서 제목 줄에 +++Portfolio+++를
    입력하세요.

![](./media/image8.png)

10. 트리거가 생성되면 트리거 대화 테스트를 위한 시간을 **닫으세요.**

![](./media/image9.png)

## 작업 2: Computer use tool을 추가하기 

이 작업에서는 컴퓨터에 로그인하고, 웹사이트를 탐색하며, 금융 포트폴리오
데이터를 검색하고 가져오는 컴퓨터 사용 도구를 구성해야 합니다. 그 다음
Office 365 Outlook 커넥터를 사용해 요청한 데이터를 답장으로 보내세요.

1.  위 메뉴에서 **Tools**로 이동하세요.

![](./media/image10.png)

2.  **+ Add a tool**을 선택하세요.

![](./media/image11.png)

3.  **+ New tool**을 선택하세요.

![](./media/image12.png)

4.  **Computer use (preview)**를 선택하세요.

![](./media/image13.png)

5.  다음 지침을 추가한 후 **Add and configure**를 선택하세요.

&nbsp;

1.  <https://computerusedemos.blob.core.windows.net/web/Portfolio/index.html>로
    이동하세요.

2.  "Enter Portfolio ID" 검색 필드에 Portfolio ID를 입력하고 "Search"
    버튼을 클릭하세요.

3.  표시된 대로 "Client Name", "Portfolio Value" 및 "Manager"값을 정확히
    확인하세요.

4.  이 세 값을 최종 출력으로 반환합니다. 포트폴리오 데이터가 없다면,
    지정된 ID를 가진 포트폴리오를 찾을 수 없었다고 답장하세요.

![](./media/image14.png)

6.  Computer use tool의 **Name**을 +++Look up portfolio data+++로
    업데이터하세요.

7.  **Description**을 +++Search and retrieve financial portfolio
    data+++로 업데이터하세요

![](./media/image15.png)

8.  Inputs 섹션에서 **+ Add input**를 선택하세요.

![](./media/image16.png)

9.  Name을 +++Portfolio ID+++로 입력하고 description을 +++The ID of the
    portfolio+++로 입력하고 **Done**을 선택하세요.

![](./media/image17.png)

10. **Save**를 선택하세요.

![](./media/image18.png)

## 작업 3: Computer use tool을 테스트하기

1.  **Instructions** 섹션에서 오른쪽의 **Test** 버튼을 선택하세요.

![](./media/image19.png)

2.  Sample value를 +++44123BCD+++로 추가하고 **Test now**를 선택하세요.

![](./media/image20.png)

3.  Computer use tool로 로그인하고 요청된 작업을 수행하는 것을
    관찰하세요:

    - 왼쪽 패널에는 사용 설명서와 도구의 추론 및 행동에 대한 단계별
      로그가 표시됩니다.

    - 오른쪽 패널에는 컴퓨터용으로 설정한 기계의 동작 미리보기가
      표시됩니다.

![](./media/image21.png)

> ![](./media/image22.png)

![](./media/image23.png)

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

4.  **Finish testing**을 선택하세요.

![](./media/image27.png)

## 작업 4: 이메일 응답 기능 설정하기

이 작업에서는 이메일 기능을 설정해야 합니다.

1.  **Tools** 탭으로 돌아가고 **+ Add a tool**을 선택하세요.

![](./media/image28.png)

2.  +++**Send an email (V2) (Office 365 Outlook)**+++를 검색하고
    선택하세요.

![](./media/image29.png)

3.  **Add and configure**를 선택하세요.

![](./media/image30.png)

4.  **Name**을 +++Reply to email+++로 업데이트하고 **Description**을
    +++Use this operation to reply to the email received+++로
    업데이터하고 **Additional details**을 선택하세요.

![](./media/image31.png)

5.  **Additional details**에서 **Credentials to use**를 **Maker-provided
    credentials**로 설정하세요.

![](./media/image32.png)

6.  **Inputs** 섹션에서 **To** 입력의 **customize**를 클릭하고
    **Description**을 +++Use the "from" email of the triggering received
    email+++로 설정하세요.

![](./media/image33.png)

![](./media/image34.png)

7.  **Subject** 입력을 **Customize**하고 **Description**을 +++Write the
    email subject+++로 설정하세요.

![](./media/image35.png)

8.  **Body** 입력을 **Customize**하고 **Description**을 to +++Write the
    email body using HTML and highlight the requested data+++로
    설정하세요.

![](./media/image36.png)

9.  도구 구성을 마무리하려면 **Save**를 클릭하세요.

![](./media/image37.png)

10. **Overview** 탭으로 이동하고 지침을 **Edit**하세요.

![](./media/image38.png)

11. 다음 지침을 붙여넣으세요.

When a financial portfolio related request is received, identify the
Portfolio ID and search for the requested data using \< Look up
portfolio data \>. Once you have gathered the financial portfolio
information, use the \< Reply to email \> tool to reply to the original
email you received. Do not respond with data beyond what was requested.

![](./media/image39.png)

12. Select \< Look up portfolio data \>를 선택하고 Look up portfolio
    data를 /을 입력하고 선택하세요.

![](./media/image40.png)

![](./media/image41.png)

13. 마찬가지로, \< Reply to email \>를 **Reply to email** 도구로
    교체하세요.

14. 아래 스크린샷처럼 교체가 완료되면, **Save**를 선택하세요.

![](./media/image42.png)

15. 오른쪽 상단의 **Settings**을 선택하세요.

![](./media/image43.png)

16. **Knowledge** 섹션의 **Use general knowledge option**을
    **Disable**하고 **Save**를 선택하세요.

![](./media/image44.png)

17. **Settings** 창을 닫으세요.

![](./media/image45.png)

## 작업 5: 전체 에이전트 테스트하기

이 에이전트에서는 당신이 만든 에이전트의 완전한 동작을 테스트하게
됩니다.

1.  원하는 이메일 주소에서 교육 사용자의 이메일 계정으로 테스트 이메일을
    보내세요.

Subject: +++Portfolio data request+++

Body:

Hi!

I hope you're doing well!

I'm looking for the portfolio manager and value of portfolio \#44123BCD.
Much appreciated.

Thanks!

![](./media/image46.png)

2.  교육 사용자의 이메일이 받은편지함에 꼭 도착하도록 하세요.

3.  **Overview** 탭에서 **Triggers** 섹션으로 이동하고 **Test
    trigger**를 선택하세요.

![](./media/image47.png)

4.  **trigger instance**를 선택하고 **Start testing**을 선택하세요.

![](./media/image48.png)

5.  실행이 이루어지고, 테스트 창에서 업데이트와 흐름을 확인할 수
    있습니다.

![](./media/image49.png)

![](./media/image50.png)

6.  실행 완료 후에는 에이전트의 답변을 이메일로 확인하세요.

![](./media/image51.png)

## 요약

이 실습ㅂ에서는 Microsoft Copilot Studio와 Computer-Using Agents(CUA)를
사용해 자율 금융 데이터 검색 에이전트를 생성했습니다. 이메일 요청에
자동으로 응답하고, 레거시 시스템과의 인간 상호작용을 시뮬레이션하여
포트폴리오 데이터를 가져오며, API에 의존하지 않고 정확한 결과를 반환하는
이벤트 기반 에이전트를 설정했습니다.

다음을 배웠습니다:

- 직접적인 사용자 상호작용 없이 작동하는 자율 에이전트를 설계하기

- 이메일 기반 트리거를 사용해 자동화된 워크플로우를 시작하기

- Computer-Using Agents를 구성하여 레거시 웹 애플리케이션에서 데이터를
  안전하게 탐색하고 추출하기

- 결과를 이메일로 보내기 위한 실행 도구를 통합하기

- AI 기반 컴퓨터 상호작용을 활용해 취약한 RPA 패턴에 대한 의존도를
  줄이기

이 실습은 CUA를 활용한 자율 에이전트가 기존 시스템 접근을 현대화하고,
운영 워크플로우를 간소화하며, API가 없는 환경에서 더 빠르고 신뢰할 수
있는 의사결정을 가능하게 하는 방법을 보여줍니다.
