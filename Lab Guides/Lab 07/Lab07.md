# **실습 7_ Copilot(클래식)에서 Teams 채널로 메시지 전송**

**실습 소요 시간** – 30분

**목표:**

이번 실습에서는 Copilot에서 Power Automate 플로우를 호출하여 Teams
채널에 메시지를 전송하는 방법을 배워봅니다.

## **연습 1: Microsoft Teams에서 채널 및 팀 추가하기**

1.  VM에서 **Microsoft Teams**를 열고, 이미 종료한 경우에는 테넌트 자격
    증명으로 로그인하세요. 그 후 **Teams** 옵션을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  Team에서 **More options**을 선택한 후, **+ -\>** **Create team**를
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

3.  팀 이름을 +++**HR Team**+++으로, 채널을 +++**HR Experts**+++로
    지정하고 **Create**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

4.  ‘Add members to HR Team’ 창에 **Skip**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

5.  ‘Add members to the HR Experts channel’ 창에서 **Skip**을
    선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

## **연습 2: HR 전문가에게 에스컬레이션하여 복잡한 질문을 처리하도록 주제를 개선하기**

1.  Teams 앱에서 Copilot Studio 앱(Power Virtual Agents)을 선택하고,
    **Copilots** 탭을 클릭한 후 **HR Support Copilot**을 여세요.

> ![](./media/image6.png)
>
> **참고:** Copilot Studio 바로 가기를 찾을 수 없다면, **Copilot
> Studio/Power Virtual Agents under Apps**를 검색한 후 **Open** 을
> 선택하세요.![](./media/image7.png)

2.  왼쪽 창에서 **Topics**를 선택한 후, 이전에 생성한 **Employee time
    off** 주제로 돌아가서 작성 캔버스로 이동하세요.

> ![A screenshot of a chat Description automatically
> generated](./media/image8.png)

3.  **Ask a question node**에서 **Extended leave** 옵션을 추가하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image9.png)

4.  Extended leave의 Condition 노드 아래에 질문 노드를 추가하고, 다음
    텍스트를 입력하세요: +++**How would you describe the issue?***+++*

> ![](./media/image10.png)
>
> Identity에서 **User’s entire response**를 선택하고, 설명을
> +++Description+++이라는 변수에 저장하세요.![A screenshot of a computer
> screen Description automatically generated](./media/image11.png)

5.  **Save**를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

6.  질문 아래에 노드를 추가하고, **Call an action**을 선택하세요. 그 후,
    **Create a flow**를 선택하여 Copilot Studio in Teams 내에서 Power
    Automate 플로우를 실행하세요.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

7.  **Power Virtual Agents Flow** Template 옵션을 선택하세요.

![](./media/image14.png)

![A screenshot of a computer Description automatically
generated](./media/image15.png)

8.  첫 번째 단계에서 **+ Add an input**을 클릭하여 **text** 입력 필드를
    추가하세요. Input 필드를 Description으로 변경하세요.

![A computer screen shot of a computer error Description automatically
generated](./media/image16.png)

9.  **new step**을 삽입하고 **Add an action**을 선택하세요.

![](./media/image17.png)

10. **Choose an operation**에서 **Microsoft Teams**을 선택하세요.

![](./media/image18.png)

11. **Post message in a chat or channel**를 선택하세요.

![](./media/image19.png)

12. 다음 정보를 입력하세요:

- Post as – **User**

- Post in – **Channel**

- Team – **HR Team**

- Channel – **HR Experts**

- Message **– Description** from **Dynamic Content**

![A screenshot of a computer Description automatically
generated](./media/image20.png)

13. 프롤우의 이름을 +++**Send a message to HR team**+++으로 변경하고
    **Save**를 클릭하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image21.png)

14. **Close**를 클릭하여 Power Automate를 닫고 작성 캔버스(Authoring
    canvas)로 돌아가세요.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

15. Authoring canvas에서 노드를 추가하세요 – **call an action** -\>
    **Send a message to HR team**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

16. 입력을 **Description**으로 추가하세요.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

17. 메시지 노드에 다음 메시지를 추가하세요: +++**We notified the expert.
    They’ll reach out shortly**+++.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

18. 대화 종료 \> 설문 조사 종료

![A screenshot of a chat Description automatically
generated](./media/image26.png)

19. 주제를 저장하기 위해 **Save**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

20. **Topic saved** 라는 성공 메시지가 표시됩니다.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

## **연습 3: 챗봇 테스트하기**

1.  왼쪽 창에서 Test your chatbot를 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

2.  +++**I need help with time off**+++라는 메시지를 전송하고, 챗봇의
    답변으로 Extended leave를 선택하세요.

![A screenshot of a chat Description automatically
generated](./media/image30.png)

3.  휴가 연장의 사유를 설명하세요. 여기에서는 +++**I need extended leave
    of one month for travelling**+++이라고 입력해 주세요.

![A screenshot of a chat Description automatically
generated](./media/image31.png)

4.  봇은 “We notified an expert…..” 메시지로 응답합니다.

![A screenshot of a chatbot Description automatically
generated](./media/image32.png)

> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)

## **연습 4: Teams에서 메시지 확인.**

1.  MS Teams 앱의 왼쪽 메뉴에서 Teams를 클릭하세요.

![](./media/image34.png)

2.  **HR Team** 내의 **HR Experts** 채널을 선택하세요. 사용자가 봇에게
    보낸 메시지가 이 채널에 전송된 것을 확인하세요.

![A screenshot of a computer Description automatically
generated](./media/image35.png)

## **연습 5: Copilot 게시하기 – Teams**

1.  Microsoft Copilot Studio 앱으로 돌아가서 **HR Support Copilot**
    챗봇을 선택하세요

2.  왼쪽 창에서 Publish를 선택하세요.

![A screenshot of a chat Description automatically
generated](./media/image36.png)

3.  **Publish**를 클릭하세요.

![](./media/image37.png)

4.  **Publish latest content?**에서 Publish를 선택하세요.

![A close-up of a computer screen Description automatically
generated](./media/image38.png)

5.  아래 스크린샷처럼 성공 메시지가 표시됩니다. **Availability
    options**을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

6.  **Add to Contoso** 옵션은 봇을 특정 팀에 추가합니다.

7.  **Show to my teammates and shared users** 옵션은 봇을 Built by
    colleagues 섹션에 표시되도록 합니다.

8.  **Show to everyone in the org** 옵션은 봇을 **Built by org** 섹션에
    나열되도록 관리자에게 요청을 제출합니다.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

**요약:**

이번 실습에서는 봇을 통해 Teams 채널에 메시지를 게시하는 방법을
배웠습니다.
