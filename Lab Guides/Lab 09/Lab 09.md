# 실습 09 - 퀴즈 생성 에이전트 주제에 대한 프롬프트 액션 구현

## 연습 1: 자연어로 에이전트 생성하기

1.  브라우저를 열고 +++https://copilotstudio.microsoft.com/+++에
    로그인하세요. Resources 탭에서 제공된 자격 증명을 사용하여
    로그인하세요.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  이미 Copilot Studio 페이지에 있다면, **Home**을 클릭하여 홈 페이지로
    이동하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

3.  홈 페이지에서 Describe your agent to create it 텍스트 입력란에서
    +++I want you to be a question and answering assistant that can
    answer common questions from users using the content of a website+++
    라고 입력하고 **Send**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  에이전트의 이름을 제안할 수 있습니다. 제안을 수락하거나 원하는
    이름을 제공할 수 있습니다.

5.  에이전트의 기능에 대한 추가 정보를 아래와 같이 입력하세요.

+++help answer common product and support questions using the content of
a website, and help answer HR questions from an uploaded file+++

6.  지식 소스로 사용할 웹사이트로 +++www.microsoft.com+++ 을 제공하세요.

![A screenshot of a chat Description automatically
generated](./media/image4.png)

7.  지시 사항을 모두 입력한 후, **Create** 를 클릭하여 에이전트를
    생성하세요.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image5.png)

8.  에이전트가 생성되면, 설정된 내용과 함께 열립니다. 페이지를
    스크롤하여 에이전트가 제대로 생성되었는지 확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

9.  **Test** 아이콘을 클릭하여 에이전트를 테스트하세요. +++What is
    Copilot Studio+++를 입력하고 **Enter** 키를 누르세요.

![A screenshot of a phone Description automatically
generated](./media/image8.png)

10. +++What is the latest xbox model?+++를 입력하세요.

![A screenshot of a chat Description automatically
generated](./media/image9.png)

위 두 단계에 대해 에이전트는 일반적인 지식을 바탕으로 제공되는 답변을
받을 수 있습니다.

## **연습 2: 생성적인(generative) 답변을 위한 주제(Topic)에 프롬프트 액션 생성**

액션은 에이전트의 기능을 확장하는 데 사용될 수 있습니다. Microsoft
Copilot Studio에서 다양한 에이전트에 유형의 액션을 추가할 수 있습니다:

- **미리 구축된 커넥터 액션:** Power Platform 커넥터를 사용하여
  Salesforce, Zendesk, MailChimp, GitHub과 같은 인기 있는 기업 제품의
  데이터를 액세스합니다.

- **사용자 정의 커넥터 액션:** 공개 또는 비공개 API에서 데이터를
  액세스하기 위해 커넥터를 구축할 수 있습니다.

- **Power Automate 클라우드 플로우:** Power Automate 클라우드 플로우를
  사용하여 작업을 수행하고, 데이터를 검색하고 처리합니다.

- **AI Builder 프롬프트:** AI Builder와 자연어 이해를 사용하여 비즈니스
  내의 특정 시나리오 및 워크플로우를 처리합니다.

- **Bot Framework skill**: Skill manifest를 사용하여 스킬이 수행할 수
  있는 작업, 입력 및 출력 매개변수, 스킬의 엔드포인트 및 디스패치 모델을
  정의합니다.

이번 실습에서는 주제(topic) 노드에 프롬프트에서 액션으로(prompt to
action)를 추가하는 방법을 배우게 됩니다.

1.  에이전트에서 **Topics** 탭을 선택하고, **+ Add a topic**을 클릭한 후
    **From blank**를 선택하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

2.  Topic 이름을 +++Generate questions for a quiz+++로 입력하세요.
    트리거 아래의 **Edit** Edit 하이퍼링크를 선택한 후, 최소 5개의
    트리거 문구를 입력해야 합니다.

아래 문구들을 하나씩 추가하세요. 각 문구를 추가한 후, + 옵션을 선택하여
트리거를 추가하세요.

> +++create a number of questions for a quiz based on a topic and format
> the quiz based on the instruction provided+++
>
> +++creates a quiz with a number of questions based on the topic
> provided and formats the quiz+++
>
> +++generate a quiz with a number of questions using the topic provide
> and format the questions+++
>
> +++creates questions for a quiz on a specific topic and format+++
>
> +++format a quiz by a number of questions based on the topic
> provided+++

오른쪽 위에서 **Save**을 선택하여 주제를 저장하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image11.png)

3.  트리거 노드 아래에 있는 + 기호를 클릭하세요. Add an action 옵션을
    선택한 후, 해당 옵션 아래에서 New prompt(default AI model) 옵션을
    선택하세요.

![A screenshot of a quiz AI-generated content may be
incorrect.](./media/image12.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

4.  프롬프트 대화 상자가 나타나며, 프롬프트를 만드는 방법을 안내하는
    플라이아웃이 표시될 수 있습니다. **Next**를 선택하여 가이드를 계속
    진행하세요.

5.  퀴즈용 질문을 생성하는 프롬프트를 만들겠습니다. 프롬프트 이름을
    +++Quiz Generator+++로 입력하세요.

6.  아래 내용을 Prompt 입력란에 붙여넣으세요.

+++Generate a quiz with \[number\] questions to cover this \[topic\].
Decide on the format, such as multiple-choice questions or true/false
statements. Use this \[format\]. Designate the correct answer within
parentheses.+++

**Input** 섹션을 확장하고 **+ Add input**를 선택하세요.

**참고:** 입력(Input) 섹션이 보이지 않는 경우, 아래로 스크롤하여
확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

7.  **Add input** 옵션에서 **Text**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

8.  이름란에 +++number+++를 입력하고, 샘플 데이터로 +++5+++를
    입력하세요. **+ Add input** -\> **Text**를 선택하여 다음 입력 항목을
    추가하세요.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

9.  이름을 +++topic+++로 입력하고 샘플 데이터(예: +++Science+++)를
    입력한 다음, + Add input -\> Text를 선택하여 다음 입력을 추가하세요.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

10. 이름을 +++format+++로 입력하고 샘플 데이터(예: +++bullet
    points+++)를 입력하세요.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

11. 이제 입력 이름과 예시 데이터를 모두 추가했으므로, 다음으로 입력값을
    프롬프트에 삽입해야 합니다. Prompt 필드에서 **\[number\]** 부분을
    강조 표시한 뒤, + Add를 선택하고 **In your prompt** 탭 아래에서
    **number**를 선택하세요. 이제 숫자 입력이 프롬프트에 입력으로
    추가되었습니다.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image20.png)

12. 나머지 입력값들에 대해서도 동일한 단계를 반복하세요.

13. 모든 입력값을 프롬프트에 추가한 후, **Test prompt**를 클릭하고 응답
    결과를 확인하세요.

![A screenshot of a quiz generator Description automatically
generated](./media/image21.png)

14. **Save** 를 선택하여 프롬프트를 저장하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

15. 이제 프롬프트 액션 노드가 해당 주제의 작성 캔버스(Authoring
    canvas)에 표시됩니다. 다음 단계로, 에이전트가 입력 값을 자동으로
    채울 수 있도록 입력 매개변수의 값을 정의해야 합니다. \> 아이콘을
    선택하세요.

![A screenshot of a quiz Description automatically
generated](./media/image24.png)

16. **System** 탭을 선택하고, **Activity.Text**를 선택하여 액션이
    사용자의 전체 응답을 입력 값으로 사용하고 형식 값을 식별하도록
    설정하세요.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

17. 프롬프트 액션의 나머지 입력 매개변수에 대해서도 동일한 작업을
    반복하세요.

![A screenshot of a quiz Description automatically
generated](./media/image26.png)

18. 다음으로, 프롬프트 액션의 출력 변수를 정의해야 합니다. 이렇게 해야
    응답을 주제의 다운스트림으로 참조될 수 있습니다. \> 아이콘을
    선택하고 Custom 탭에서 Create new를 선택한 후 변수 이름을
    +++**VarQuizQuestionsResponse+++**로 지정하세요.

![A screenshot of a quiz AI-generated content may be
incorrect.](./media/image27.png)

> ![A screenshot of a browser window Description automatically
> generated](./media/image28.png)

19. Prompt action 아래에서 **+** 아이콘을 선택하여 새 노드를 추가하고
    **Send a message**를 선택하세요. **{x}** 변수 아이콘을 선택하세요.

![A screenshot of a quiz Description automatically
generated](./media/image29.png)

20. **VarQuizQuestionsResponse.text** 변수를 선택하세요. 이렇게 하면
    프롬프트 액션 응답의 텍스트 속성이 메시지 전송 노드에 추가됩니다.
    **Save**을 선택하여 주제를 저장하세요.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

21. 다음으로 주제 정보를 업데이트해야 합니다. 이는 Generative 모드가
    활성화된 상태에서 사용자의 의도와 주제를 연결하는 데 사용됩니다.
    **Details**를 선택하고 다음 정보를 입력하세요**.**

- Display name - +++ generate questions for a quiz+++

- Description - +++ This topic creates questions for a quiz based on the
  number of questions, the topic and format provided by the user+++

**Save**을 선택하여 주제를 저장하세요.

> ![A screenshot of a quiz Description automatically
> generated](./media/image31.png)

22. 이제 **Generative mode** 설정을 활성화해야 합니다. 이렇게 하면
    에이전트가 프롬프트 액션이 포함된 주제를 호출할 수 있습니다.
    에이전트의 **Settings**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image32.png)

23. **Generative AI** 설정을 선택하고 **Generate (preview)**를 선택한
    후, **Save** 버튼을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image33.png)

24. 이제 에이전트를 테스트할 준비가 되었습니다. **Settings** 창을
    닫고(**close**), 테스트 창에서 **refresh** 아이콘을 선택하세요. 그런
    다음 다음 질문을 입력하고 출력을 확인하세요**.**

+++Create 5 questions for a quiz based on geography and format the quiz
as multi choice+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

> ![A screenshot of a cell phone Description automatically
> generated](./media/image35.png)

요약

이번 실습에서는 사용자 지정 프롬프트를 생성하고 이를 테스트하여 토픽에
대한 프롬프트 액션을 만드는 방법을 배웠습니다.
