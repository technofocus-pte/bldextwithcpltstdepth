# 실습 1 - Copilot Studio Agent Builder를 사용한 AI 비서 설계하기

**목표**

이 실습에서는 **Copilot Studio Agent Builder**를 사용해 에이전트의 목적,
행동 어조를 자연어로 설명하여 맞춤형 대화형 에이전트를 생성하는 방법을
배울 것입니다. You will design a사용자는 식물 관리, 모범 사례,
일상생활에서 자연의 중요성에 집중한 가정 원예 전문가 지도를 제공하는
**Gardening Assistant**를 설계하게 됩니다. 실습이 끝날 때쯤이면 에이전트
지침을 반복적으로 다듬고 기능적이고 도메인 특화 어시스턴트를 구현하는
방법을 이해하게 될 것입니다.

## 연습 1: 에이전트를 생성하기

1.  브라우저에서 +++<https://m365.cloud.microsoft/chat+++> 링크를 열고
    자격 증명으로 로그인하세요.

    - 사용자 이름 - <+++@lab.CloudPortalCredential>(User1).Username+++

    - 비밀번호 - <+++@lab.CloudPortalCredential>(User1).Password+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image1.png)

2.  **왼쪽** 창에서 **New agent**를 선택하세요. **New agent** 옵션이
    보이지 않으면 **브라우저**를 **새로고**침하고 몇 분 후에 다시
    시도하세요. 때로는 완전히 로드되는 데 몇 분이 걸리기도 합니다.

![](./media/image2.png)

3.  **Describe** 탭을 선택하세요.

![](./media/image3.png)

4.  커스텀 에이전트를 정의하기 시작할 수 있습니다. 시작할 템플릿을
    선택할 수도 있고, 자연어로 에이전트를 *설명*할 수도 있습니다. 다음과
    같은 초기 설명을 제공해 보겠습니다.

> +++You are an expert gardener, and you help users to maintain and
> improve their home garden providing detailed instructions and advice
> about the best practices for home gardening.+++

![](./media/image4.png)

5.  지침을 제공하면 초기 정보가 채워집니다.

6.  필요하면 에이전트 이름을 변경할 수 있습니다. 다음과 같은 +++ Name it
    as “Gardening assistant”+++ 프롬프트를 제공하세요.
    ![](./media/image5.png)

7.  더 세정한 지침에 대해 질문받으면 다음 문장을 제공하세요.

+++Focus on suggesting ways to keep plants and flowers shining and
gorgeous+++

![](./media/image6.png)

8.  에이전트 빌더와 계속 상호작용하여 에이전트를 생성하는 데 필요한 모든
    정보를 갖추게 됩니다. 다음 문장을 작성하세요.

> +++Focus on highlighting the importance of nature and plants/flowers
> to be present in every house!+++
>
> ![](./media/image7.png)
>
> ![](./media/image8.png)

9.  그 다음 에이전트 톤에 대해 아래와 같이 지시를 제공하세요.

+++Use a professional, yet friendly, tone.+++

> ![](./media/image9.png)

11. 에이전트를 생성하려면 오른쪽 상단에서 **Create**를 클릭하세요.

![](./media/image10.png)

![](./media/image11.png)

12. 에이전트가 생성되면 **Go to agent**를 선택하세요.

![](./media/image12.png)

13. 생성된 에이전트가 열립니다.

![](./media/image13.png)

> \[!경고\] **경고:** 에이전트가 자동으로 열리지 않는다면, 페이지를
> **새로고**침하고 왼쪽 창에서 **created gardening agent**를 선택하세요.
>
> ![](./media/image14.png)

14. 아래와 같은 안내문을 제공해 에이전트와 대화하세요.

> +++Give me tips to keep Rose plants fresh+++

![](./media/image15.png)

## 요약:

이 실습에서는 Copilot Studio Agent Builder 경험을 활용해 **Gardening
Assistant agent**를 생성했습니다. 간단한 자연어 설명에서 시작해,
에이전트의 역할을 전문가 정원사로 정의하고, 인터랙티브 프롬프트를 통해
점차 집중력, 어조, 개성을 다듬어갔습니다. 당신은 에이전트를
전문적이면서도 친근한 원예 조언을 제공하도록 맞춤화했으며, 식물을
건강하고 생기 넘치며 시각적으로 매력적으로 유지하는 데 중점을 두었고,
모든 가정에서 식물과 꽃의 가치를 강조했습니다.

에이전트를 생성하고 실행한 후, 장미 식물을 신선하게 유지하기 위한 팁
요청과 같은 실제 사용자 프롬프트를 사용해 에이전트의 행동을
검증했습니다. 이 실습에서는 대화형 설계와 반복적인 명령어 다듬기를
활용해 코드 작성 없이도 Copilot Studio를 얼마나 빠르고 직관적으로 목적
지향적인 에이전트를 구축할 수 있는지 보여주었습니다.
