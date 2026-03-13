# 실습 2- 템플릿 기반 엔터프라이즈 어시스턴트를 구축하고 개선하기

**목표**

**Agent templates**은 **custom agent**와 시작하는 데 도움을 주가 위해
설계되었습니다. 에이전트 템플릿 사용에 따른 모든 안전 및 법적 영향을
평가하고 비즈니스에 맞게 맞춤화할 책임이 있습니다.

An agent built from the **Safe Travels agent template**을 기반으로 한
에이전트는 회사 직원들에게 **travel assistance**을 제공하기 위해 설계된
Business-to-Employee (B2E) 에이전트입니다. 이 에이전트는 직원들이 다음
출장에 대해 잘 준비하고 정보를 충분히 갖추도록 돕습니다. 이 에이전트는
자연어 처리를 통해 대화형 인터페이스를 제공하여 직원들이 필요한 정보를
쉽고 직관적으로 접근할 수 있도록 합니다. 하지만 현재 에이전트가 사용하는
기본 웹사이트는 미국 여행지만 다루고 있습니다. 기본 웹사이트를 자신의
지식 출처로 대체할 수 있습니다.

이 실습에서는 **Safe Travels template**에서 에이전트를 생성하고 실습
05에서 이를 개선할 것입니다.

## 연습 0 - Entra ID에서 보안 그룹을 생성하고 Copilot Studio Authors를 구성하기

이 과정은 Copilot Studio 내에서 에이전트들과 원활하게 작업라고 게시할 수
있도록 돕기 위한 필수 작업입니다.

1.  +++<https://portal.azure.com/+++> 에서 Azure 포털로 이동하고
    **Resources** 탭에 있는 테넌트 자격 증명으로 로그인하세요.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2.  Keep your account secure 창에서 **Next**를 선택하고 **prompts**를
    따르세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  아직 사용하지 않았다면 휴대폰에 Authenticator 앱을 다운로드하세요.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image5.png)

4.  안내를 따라 설정을 완료하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  Azure welcome 화면에서 **Get Started**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  +++Microsoft EntraID+++를 검색하고 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  왼쪽 창에서 **Manage** -\> **Groups**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  새 보안 그룹을 생성하려면 **New group**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  다음 정보를 입력하세요

    - Group type – **Security**를 선택하세요

    - Group name – +++**copilotagentsecurity**+++를 입력하세요

    - Microsoft Entra roles can be assigned to the group – **Yes**를
      선택하세요 (이 옵션이 보이지 않는다면 이 단계를 무시하세요)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. **No owners selected**를 선택하고 **Add owners** 패이지에서 **MOD
    Administrator**를 선택하고 **Select**를 클릭하세요.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. 마찬가지로 **No members selected**를 선택하고 목록에서 **MOD
    Administrator**를 선택하고 **Select**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. **No roles selected**를 선택하세요. 이 옵션이 보이지 않으면 무시하고
    다음 단계로 넘어가세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. +++**Global admin**+++를 검색하고 선택하고 **Select**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. 모든 세부 정보가 추가되면 **Create**를 선택하고 확인 대화상자에서
    **Yes**를 선택하세요.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. **success** 메시지가 받는지 확인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. 왼쪽 상단에서 Contoso|Groups을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. 왼쪽 창의 **Manage**에서 **Properties**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. **can manage access to all Azure subscriptions and management groups
    in this tenant** 옵션에서 Yes를 토글하고 **Save**를 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. 왼쪽 창의 **Manage**에서 **Roles and administrators**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. +++privileged role admin+++를 검색하고 **Privileged Role
    Administrator** 역할을 클릭하세요 (**체크박스를 선택하지 마시고**
    이름을 클릭하세요).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

21. **+ Add assignments**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

22. **No members selected**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

23. **MOD Admin id**를 선택하고 **Next**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

24. **Assign**을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

25. 역할 할당이 성공적인지 확인하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

26. 새 탭에서 +++<https://admin.powerplatform.microsoft.com/+++>로
    이동하세요. 왼쪽 창에서 **Manage**를 선택하고 **Tenant
    Settings** 옵션을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

27. 사용 가능한 목록에서 **Copilot Studio Authors**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

28. 설정을 편집하려면 **Edit** 아이콘을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

29. 이전에 생성한 **+++copilotagentsecurity+++** 그룹을 검색해서
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

30. 설정을 저장하려면 **Save**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

## 연습 1: 템플릿에서 Safe Travels 에이전트를 생성하기

이 연습에서는 Safe Travels 에이전트 템플릿을 사용해 Copilot Studio에서
에이전트를 생성할 것입니다.

1.  브라우저에서
    +++[https://copilotstudio.microsoft.com+++](https://copilotstudio.microsoft.com+++/)로
    로그인하세요. Start free trial 페이지가 열립니다. 나라를 선택하고
    **Start free trial**을 클릭하세요.

![](./media/image39.png)

2.  **Dev One** 환경을 선택하세요.

> ![](./media/image40.png)
>
> \[!경고\] **중요** 아래 스크린샷처럼 Copilot Studio에서
> **Environment**  선택 옵션이 나타나지 않는다면, 아래 단계를 따르세요.
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image41.png)
>
> +++<https://admin.powerplatform.microsoft.com/+++>를 여세요.
> Select **Manage** -\> **Environments -\> Dev One**을 선택하고
> **Environment ID**의 값을 선택하세요. ![A screenshot of a computer
> AI-generated content may be incorrect.](./media/image42.png)
>
> Copilot Studio 탭으로 이동하고
> +++<https://copilotstudio.microsoft.com/environments/>**\<
> EnvironmentID \>**+++를 여세요 (**\<EnvironmentID \>** 위에 불러온
> 값으로 대체하기 )

3.  Welcome 화면에서 Skip를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

4.  왼쪽 창에서 **Agents**를 선택하고 **Start with an agent
    template**에서 **Safe Travels** 템플릿을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

5.  Safe Travels 템플릿은 회사 직원들에게 여행 지원을 제공하기 위해
    설계된 새로운 에이전트를 생성합니다. 

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

6.  설정 페이지를 둘러보세요. **Knowledge** 항목 아래에는 이미 **US
    Travel Website**가 지식 출처로 추가되어 있습니다. 필요하다면 편집할
    수 있습니다. 여기서는 같은 웹사이트를 사용하고 있습니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

7.  Select **Create** to create the Safe Travels agent. We are not
    changing anything here and using the template as such. At any point,
    the agent can be upgraded as per the user requirements.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

8.  **Agent**가 **생성**되면 자동으로 **Overview**  페이지가 나타납니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

9.  Test 창에서 +++How to apply for passport?+++를 입력하고 **Send**를
    누르세요.

테스트 창은 기본적으로 열려 있습니다. 아니라면 오른쪽 상단의 테스트
아이콘을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

10. 대리인이 지식 출처에서 여권 신청 방법에 대한 정보를 제공하는 것을 볼
    수 있습니다.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image50.png)

## 연습 2: Teams 및 Microsoft 365 Copilot로 에이전트를 게시하기

이 연습에서는 Copilot Studio에서 생성된 에이전트를 **Microsoft Teams**와
**Microsoft 365 Copilot** 채널에 게시합니다.

1.  +++<https://teams.microsoft.com/v2/+++> 브라우저에서 **MS Teams**를
    열고 **Resources** 탭에서 테넌트 자격 증명으로 **로그인하세요**.

2.  Copilot Studio로 돌아가 에이전트 페이지 오른쪽
    상단에서 **Publish**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

3.  **Force newest version** 체크박스를 확인하고 확인 상자에서
    **Publish**를 선택하세요.

![](./media/image52.png)

![](./media/image53.png)

4.  상단 탐색 바에서 **Channels**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

5.  사용 가능한 체널 목록에서 **Teams and Microsoft 365 Copilot**을
    선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

6.  **Add channel**을 선택하세요.

![](./media/image56.png)

7.  **See agent in Teams** 옵션을 클릭하고 Teams에 에이전트를
    추가하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

8.  이렇게 하면 Microsoft Teams에서 에이전트가 열립니다. **This site is
    trying to open Microsoft Teams** 팝업에서 **Cancel**을 선택하고
    **Use the Web App instead** 옵션을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

9.  에이전트를 추가하려면 **Add**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

10. 추가되면 에이전트를 열 수 있는 옵션이 생깁니다. **Open**을
    선택하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image61.png)

11. Teams에서 에이전트를 테스트하세요.

![](./media/image62.png)

12. Copilot Studio로 돌아가 Teams와 Microsoft 365 Copilot 채널 창을
    닫으세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

## 연습 3 – 기존 Safe Travels 에이전트를 테스트하기

이번 연습에서는 **Safe Travels** 에이전트가 여행 승인에 대해 질문받았을
때 어떻게 반응하는지 테스트할 것입니다.

1.  Copilot Studio -\> Safe Travels 에이전트로 돌아가서 에이전트를
    테스트하려면 **Test** 아이콘을 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image64.png)

2.  Test 창에서 +++Need travel approval+++를 입력하고 **Enter**를
    클릭하세요.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image65.png)

3.  에이전트가 여행 승인을 받기 위해 따라야 할 일반적인 지침 세트를
    안내하는 것을 볼 수 있습니다.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image66.png)

## 연습 4 – 회사별 지식 자산으로 에이전트를 강화하기

이번 작업에서는 Contoso에 특화된 지식 자산 - **Travel Policy**를 추가할
예정입니다.

1.  에이전트의 Overview 페이지에서 아래로 스크롤하고 **+ Add
    knowledge**를 선택하세요

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

2.  **select to browse** 옵션을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

3.  **C:\Labfiles\Lab Files** 폴더에서 **Travel Policy.docx**를 선택하고
    **Open**을 클릭하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

4.  파일을 추가하려면 **Add to agent**를 클릭하세요.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image70.png)

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image71.png)

5.  파일이 추가되었는지 확인하세요. **In progress**에서 **Ready**로 바뀔
    때까지 기다리세요. 준비 상태로 전환되는 동안 다음 단계를 계속할 수
    있습니다. 몇 분 이상 걸리면 됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image73.png)

6.  이제 같은 질문으로 에이전트를 테스트해보면, 에이전트가 추가된 지식
    자산에서 회사 특유의 정책으로 답변하는지 확인하세요.

## 요약

이 실습에서는 Microsoft Copilot Studio의 **Safe Travels agent
template** 을 사용해 **Business-to-Employee (B2E) travel assistance**
에이전트를 생성했습니다. 에이전트 템플릿이 대화 기능과 지식 소스를 미리
설정하여 빠른 출발점을 제공하면서도, 조직 및 법적 요구사항을 충족하기
위한 미래 맞춤화를 가능하게 하는 방법을 탐구하셨습니다. 내장된 **US
travel website** 를 **knowledge source**로 활용하여, 직원의 여행 관련
질문에 자연어로 답변하는 능력을 테스트하셨습니다. 마지막으로,
**Microsoft Teams와 Microsoft 365 Copilot**에 에이전트를 **게시**하고,
Teams에서 가용성을 검증했으며, 직원들이 일상 협업 도구 내에서 Safe
Travels 에이전트에 직접 접근하고 상호작용할 수 있음을 확인하셨습니다.
