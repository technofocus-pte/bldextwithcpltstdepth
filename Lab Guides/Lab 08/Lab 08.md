# 실습 8 – Dataverse MCP 서버가 있는 Copilot Studio에서 에이전트를 생성하기

Dataverse MCP 서버 통합이 적용된 Copilot Studio에서 Copilot 에이전트를
생성하고 구성하여 비즈니스 워크플로우를 간소화합니다.

이 실습을 마친 후, 참가자들은 Copilot Studio에서 Copilot Agent를
생성하고 구성할 수 있으며, Dataverse MCP 서버를 통합하여 계정 및 연락처
테이블에서 계정 정보를 읽고 업데이트하고, 명확성과 비즈니스 가치를 위해
에이전트 응답을 구조화하며, 이러한 기술을 활용해 일반적인 비즈니스
문제를 해결할 수 있습니다.

## 작업 1: Copilot Agent를 생성 및 구성하기 

MCP 서버를 통해 Dataverse에 연결되는 Copilot Agent를 구축하여 원활한
데이터 접근을 가능하게 합니다.

이 섹션에서는 Copilot Studio에서 새로운 Copilot 에이전트를 생성하는
방법, 적절한 지침과 제안된 프롬프트로 설정하는 방법, 그리고 실시간
데이터 연결을 위한 Dataverse MCP 서버를 통합하는 방법을 배우게 됩니다

1.  아직 로그인하지 않았다면 로그인 자격증으로
    +++https://copilotstudio.microsoft.com+++ 에서 Copilot Studio에
    로그인하고, Dev One 환경에 있는지 확인하세요.

![](./media/image1.png)

2.  새 에이전트를 생성하려면 **Create an agent** 타일을 선택하세요.

![](./media/image2.png)

3.  에이전트 프로비저닝되면 **Details** 창에 Edit를 선택하세요.

![](./media/image3.png)

4.  다음 정보를 입력하고 **Save**를 선택하세요.

- Name - +++Contoso Agent+++

- Description - +++This agent will help Contoso sales reps update their
  accounts and contacts using the Dataverse MCP Server+++

> ![](./media/image4.png)

5.  Instruction을 **Edit**하고 아래 지침 세트를 입력한 후 **Save**를
    선택하세요.

This agent will: Read accounts and contact information from the Account
and Contact Tables in Dataverse using the Dataverse MCP Server. Update
accounts and contact information from the Account and Contact Tables in
Dataverse using the Dataverse MCP Server. Create new accounts and
contact information in the Account and Opportunity Tables in Dataverse
using the Dataverse MCP Server. Do not use outside knowledge. Only use
the Dataverse MCP Tool to create, read, update and delete.

![](./media/image5.png)

![](./media/image6.png)

6.  Suggested prompts 섹션에서 아래로 스크롤하고 **+ Add suggested
    prompts**를 선택하세요.

![](./media/image7.png)

7.  다음 프롬프트를 추가하고 **Save**를 클릭하세요.

- **Title**: +++Account Search+++ **Prompt**: +++List all accounts in
  Redmond+++

- **Title**: +++Contact Search+++ **Prompt**: +++List all contacts from
  Coho Winery+++

![](./media/image8.png)

8.  Tools 섹션에서 **+ Add tool**을 선택하세요.

![](./media/image9.png)

9.  **Model Context Protocol** 탭을 선택하고 +++Dataverse MCP
    Server+++를 검색하고 **Microsoft** **Dataverse MCP Server**를
    선택하세요.

참고: 미리보기에 없는 것을 선택하세요. **Microsoft** **Dataverse MCP
Server (Preview)**를 선택하지 마세요.

![](./media/image10.png)

10. **Add and configure**를 선택하세요.

![](./media/image11.png)

**참고:** Dataverse MCP 서버는 Dataverse 내 테이블에 자연어로 접근할 수
있게 해줍니다. 저희는 사용할 Accounts and Contacts 테이블에 샘플
데이터를 가지고 있습니다. 사용 가능한 도구로는 다음과 같습니다: 리스트
테이블, 테이블 설명, 데이터 읽기, 레코드 생성, 레코드 업데이트, 프롬프트
목록, 프롬프트 실행, 지식 소스 목록, 지식 검색

11. Dataverse MCP 서버용 도구를 검토하세요. 에이전트가 사용할 수 있는
    도구를 선택하거나 해제할 수 있습니다. 도구가 실행되면 목록이 MCP
    서버에서 동적으로 업데이트됩니다. 이 때문에 주제에서 MCP 서버를
    호출할 수 없습니다.

![](./media/image12.png)

12. **Test** 창에서 +++List the accounts in the state of WA+++를
    입력하고 **Send**를 클릭하세요.

![](./media/image13.png)

13. 첫 번째 실행에서는 기본적으로 도구가 다음과 같기 때문에 동의
    대화상자가 뜨게 됩니다

" End user credentials"을 사용하도록 설정되었습니다. 계속하려면
**Allow**를 클릭하세요.

![](./media/image14.png)

13. 일련의 동작과 MCP 서버의 출력을 참고하세요,

![](./media/image15.png)

![](./media/image16.png)

14. 사용된 도구를 클릭하면 해당 도구의 Inputs 및 Outputs을 볼 수
    있습니다.

![](./media/image17.png)

## 작업 2: 맞춤형 프롬프트를 통한 구조화 에이전트 응답

맞춤형 프롬프트를 만들어 에이전트로부터 일관되고 구조화된 답변을 받으며
비즈니스 관련 정보를 제공하세요.

1.  Copilot에서 다른 테스트를 해보셨다면, 계정과 연락처에 다른 속성이
    나오는 것을 눈치채셨을 겁니다. 좀 더 체계적인 답변을 원한다면,
    **Tools**에서 **프롬프트**를 생성할 수 있습니다. **Tools** 탭에서
    **+ Add a tool** 을 클릭하고 **+ New tool**을 클릭하세요.

![](./media/image18.png)

![](./media/image19.png)

2.  Prompt를 선택하세요.

![](./media/image20.png)

3.  위 **prompt** **name**을 +++Show Account Details+++로 변경하세요.

**Instructions**에서 +++Find account which contains+++를 입력하고 **+
Add content**를 클릭해 우리가 찾는 계정 이름을 전달합니다. 입력의
**Text** 선택하고 **+++ Account Name+++** 라고 명명하세요. **Close**를
클릭하세요.

> ![](./media/image21.png)

![](./media/image22.png)

4.  이제 Dataverse에서 특정 필드를 가져와 채팅에서 최종 사용자에게
    보여줄 수 있습니다. 지시를+++ and find relevant details like:+++
    다시 클릭해 **+ Add content**를 클릭하세요. 이번에는 **Dataverse**와
    **Account** 테이블에서 최종 사용자들이 보고 싶어 할 만한 일부 필드를
    선택할 예정입니다.

![](./media/image23.png)

5.  드롭다운을 클릭하여 다음 항목을 선택해 봅시다: **Account Name**,
    **Account Number**, **Address 1**, **Annual Revenue**, **Email** 및
    **Main Phone**. **Add**를 클릭하고 **Save**를 선택하세요.

![](./media/image24.png)

![](./media/image25.png)

![](./media/image26.png)

6.  **Add and configure**를 선택하세요.

![](./media/image27.png)

7.  이제 우리의 프롬프트를 시험해볼 수 있겠네요. 우리 에이전트에게 다시
    가서 다시 테스트해 봅시다. 테스트 창으로 가세요.

8.  +++Show account Details for Fourth Coffee+++를 입력하고 **Send**를
    클릭하세요. 응답이 구조화된 응답과 맞춤 프롬프트 생성 안에 있다는
    것을 볼 수 있습니다.

![](./media/image28.png)

## 요약

이 실습에서는 Microsoft Copilot Studio에서 Copilot Agent를 구축하여
**Dataverse MCP Server**와 통합 하여 자연어를 사용해 비즈니스 데이터를
안전하게 접근하고 관리합니다. 에이전트를 설정하여 **Accounts,
Contacts,** 및**Opportunities** 등 Dataverse 테이블 전반에 걸쳐 레코드를
읽고, 생성하며, 업데이트할 수 있도록 외부 지식이나 맞춤형 API에 의존하지
않습니다.

또한 맞춤형 프롬프트를 활용해 **에이전트 응답을 구조화**하는 방법을
배워, 최종 사용자에게 가장 관련성 높은 데이터 필드를 일관되고 비즈니스
친화적인 결과물을 제공합니다. 실험실이 끝날 때쯤이면, 영업 및 계정 관리
워크플로우를 간소화하고, 명확하고 구조화된 인사이트를 제공하며, MCP 기반
에이전트가 실시간 기업 데이터로 실제 비즈니스 문제를 어떻게 해결할 수
있는지 시연하는 에이전트를 설계할 수 있습니다.
