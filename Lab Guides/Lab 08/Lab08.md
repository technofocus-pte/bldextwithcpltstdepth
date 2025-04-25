**실습 08 - Microsoft Copilot을 위한 대화형 액션 만들기**

**실습 소요 시간** – 20분

**목표**

Microsoft Copilot은 조직 내 다양한 콘텐츠와 리소스를 활용할 수 있는 즉시
사용 가능한 환경을 제공합니다. 경우에 따라 외부 시스템과의 상호 작용이나
추가적인 답변이 필요할 수 있습니다. Microsoft Copilot Studio를 사용하면
대화형 주제를 작성하여 Copilot 플러그인으로 게시할 수 있습니다. 테넌트
관리자의 승인을 받은 플러그인은 조직의 M365 Chat 환경에 추가될 수
있습니다.

해당 기능은 조직에 유효한 라이선스가 있을 경우, 실제 운영 환경의
Microsoft Copilot에서 사용 가능합니다.

이 실습에서는 대화형 액션(Coverational Action)을 생성하는 방법을 학습할
것입니다.

## **연습 1: 대화형 액션 만들기**

1.  아직 로그인하지
    않았다면,+++**https://copilotstudio.microsoft.com/**+++에 테넌트
    자격 증명을 사용해 로그인하세요.

2.  오른쪽 상단에서 환경을 **Dev one**으로 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

3.  왼쪽 창에서 **Agents**를 선택하세요.

4.  **Copilot for Microsoft 365**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

5.  **Actions**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

6.  **Add an action**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

7.  **New action** 창에서 **Conversational**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

8.  액션 이름을 !!**Conversational action**!! 으로 입력하고,
    **Create**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

9.  준비가 되면, 생성된 액션이 Authoring canvas에서 열립니다.
    **Topics**을 선택하세요.

10. 열리지 않는 경우, 페이지를 새로 고침하고 **Library -\>
    Conversational** 아래에 나열되어 있는지 확인하세요.

![A screenshot of a chat box AI-generated content may be
incorrect.](./media/image7.png)

11. **Conversational action**를 여세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

12. 주제 이름을 다음과 같이 지정하세요: !!Holidaylist!!

![A screenshot of a computer Description automatically
generated](./media/image9.png)

13. 트리거 노드 설명에 이 대화형 플러그인이 사용자에게 어떤 도움을 줄 수
    있고 어떤 기능을 하는지 명확히 설명하세요. 이 항목은 사용자가 2025년
    공휴일 목록을 찾을 수 있도록 도와주는 기능입니다.

트리거 노드의 설명란에 +++**This plugin helps to retrieve the list of
holidays for the year 2025.**+++ 을 입력하세요.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

이 설명은 기능적 목적을 가지고 있으며 Microsoft Copilot에서 플러그인을
호출할지 여부를 결정하는 데 사용됩니다.

14. 공휴일 목록이 포함된 메시지 노드를 추가하세요.

National holidays for 2025:

- New Year’s Day: Jan 1

- Martin Luther King Jr. Day: Jan 20

- Washington’s Birthday (Presidents’ Day): Feb 17

- Memorial Day: May 26

- Juneteenth National Independence Day: June 19

- Independence Day: July 4

- Labor Day: Sep 1

- Columbus Day / Indigenous Peoples’ Day: Oct 13

- Veterans Day: Nov 11

- Thanksgiving Day: Nov 27

- Christmas Day: Dec 25

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

15. **Save**를 클릭하여 플러그인을 저정하세요.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

![A screenshot of a chat box Description automatically
generated](./media/image13.png)

## **연습 2: 대화형 액션을 Microsoft Copilot에 게시하기**

1.  대화형 플러그인을 게시하면 해당 테넌트의 Dataverse 레지스트리에
    새로운 플러그인이 생성됩니다. 플러그인이 레지스트리에 등록되면,
    테넌트 관리자가 이를 승인해야 Microsoft Copilot 플러그인
    카탈로그에서 사용자가 사용할 수 있습니다.

2.  **Publish**를 클릭하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image14.png)

3.  **Publish**를 선택하세요.

![A screenshot of a computer program Description automatically
generated](./media/image15.png)

4.  **Publish latest content** 대화 상자에서 **Publish**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

5.  게시 상태가 화면에 표시됩니다.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

참고: 게시 과정은 빠르게 완료되지만, Microsoft Admin Cnter에 실제로
반영되어 사용 가능해지기까지는 최대 4시간이 소요될 수 있습니다.

**중요 사항:** Admin center에 플러그인이 표시되도록 하려면, 회사에서
유효한 Copilot 라이선스를 보유하고 있어야 합니다.

6.  관리자(Admin)는 **Dataverse and Microsoft Copilot Studio** 통합 앱을
    Microsoft Admin Center의 **Settings** 아래에 **Integrations to be
    reviewed and approved** 에서 찾을 수 있습니다.

7.  관리자(Tenant Admin)가 Dataverse and Microsoft Copilot Studio 통합
    앱을 승인하면, 해당 앱은 사용자의 Microsoft Copilot UI에 있는
    플러그인 목록에 나타납니다.

**요약:**

이번 실습에서는 대화형 액션(Conversational action)을 생성하고 게시하는
방법을 배웠습니다.
