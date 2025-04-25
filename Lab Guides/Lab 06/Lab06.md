# **Microsoft Copilot Studio에서 Teams로 Copilot 생성 및 배포하기**

**실습 소요 시간** – 30분

**목표:**

이 실습에서는 Microsoft Teams에 Copilot Studio 앱을 설치하고, 팀에서
새로운 Copilot을 생성한 후 테스트하는 방법을 배우게 됩니다.

## **연습 1: Microsoft Teams에 Copilot Studio 앱 설치**

1.  VM에서 **Start** 메뉴를 선택하고, +++teams+++ 를 검색한 후
    **Microsoft Teams app**을 선택하세요.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

2.  **Resources** 탭에서 제공된 자격 증명을 사용하여 로그인하세요.

![A screenshot of a sign in Description automatically
generated](./media/image2.png)

3.  **Apps**을 클릭한 후, +++**Copilot Studio**+++를 검색하고
    **Microsoft Copilot Studio**를 선택한 후 **Add**를 클릭하세요.

**참고:** Copilot Studio를 찾을 수 없다면, **Power Virtual Agent**를
검색하여 선택한 후 추가해야 합니다.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![](./media/image4.png)

4.  **Open**를 클릭하세요.

![A screenshot of a phone Description automatically
generated](./media/image5.png)

5.  **Start now**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

## **연습 2: Teams에서 새로운 Copilot 생성하기**

1.  **Office 365 tenant credentials**을 사용하여 **Teams**에
    로그인(**Sign in)**하세요.

> ![A screenshot of a sign in Description automatically
> generated](./media/image7.png)

2.  **Apps**를 클릭하세요. +++**Copilot Studio**+++를 검색하고
    **Microsoft Copilot Studio**를 선택한 후, **Add**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

![A screenshot of a phone Description automatically
generated](./media/image4.png)

**중요 사항:** If you are not able to find Copilot Studio를 찾을 수
없다면, +++**Power Virtual agent**+++를 검색하여 선택하고 추가해야
합니다.

![A screenshot of a search engine Description automatically
generated](./media/image8.png)

![A screenshot of a computer Description automatically
generated](./media/image9.png)

3.  **Start now**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

4.  **Contoso**를 선택하고 **Continue**를 클릭하세요.

![A screenshot of a chatbot Description automatically
generated](./media/image10.png)

![A screenshot of a chatbot Description automatically
generated](./media/image11.png)

**중요 사항:** 이 단계는 약 10분 정도 걸릴 수 있습니다. 너무 오래
걸린다면, 창을 닫고 왼쪽 패널의 Apps에서 Copilot Studio 또는 Power
Virtual Agents를 선택한 후 4단계를 다시 진행하세요.

5.  Create a copilot 창에서 Copilot의 이름을 +++**HR Support
    Copilot**+++으로 입력한 후 **Create**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

6.  **Your chatbot is provisioned**라는 성공 메시지가 표시됩니다.

![](./media/image13.png)

## **연습 3: 직원의 휴가 관련 일반적인 문의를 처리하는 휴가 주제 작성**

1.  왼쪽 창에서 **Topics**를 클릭하세요. **+ New topic -\> From
    blank**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image14.png)

2.  트리거 구문 창을 닫으세요(**close**).

![A screenshot of a computer screen Description automatically
generated](./media/image15.png)

3.  **Details** 아이콘을 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

4.  Details 창에서 이름(Name)에 +++**Employee time off**+++를
    입력하고,and Description 에 +++**Employee time off topic for common
    time-off queries**+++를 입력하세요.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

5.  Details 창을 닫으세요(**close)**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

6.  **Save**를 클릭하세요.

![A screenshot of a chat Description automatically
generated](./media/image19.png)

7.  **Trigger phases**를 클릭하세요;

![A screenshot of a computer Description automatically
generated](./media/image20.png)

8.  트리거 문구로 +++**I need help with time off**+++ 를 입력한 뒤, +
    아이콘을 클릭하세요.

![](./media/image21.png)

9.  아래 트리거 문구를 추가하세요.

- +++**Need information on time off**+++

- +++**How many days of paid vacation do I have**+++

- +++**What are the national holidays**+++

- +++**I need extended leave**+++

![A screenshot of a computer Description automatically
generated](./media/image22.png)

Trigger phrases 창을 닫으세요.

10. Message 노드를 추가하고, 텍스트 입력란에 +++I can help with
    questions related to time-off*+++*라고 입력하세요.

> ![A screenshot of a chat Description automatically
> generated](./media/image23.png)

11. 인사 직원으로서, 가장 흔한 휴가 관련 질문은 유급 휴가(**paid
    vacation** time)와 국경일(**national holidays**)에 관한 것입니다.
    사용자 응답 옵션이 있는 질문 노드를 추가하면, 주제는 자동으로 각
    응답에 대해 분기된 브랜치를 생성합니다.

12. 메시지 노드 아래에 있는 (+) 아이콘을 선택한 후, **Ask a question**를
    선택하여 질문 노드를 추가하세요. **Ask a question** 텍스트 박스에
    다음과 같이 입력하세요. Enter *What information are you looking
    for?* 

> ![A screenshot of a chat Description automatically
> generated](./media/image24.png)

13. **Options for user**에서 +++Paid vacation*+++* 및 +++National
    Holidays*+++*을 두 가지 옵션으로 추가하세요.

> ![A screenshot of a questionnaire Description automatically
> generated](./media/image25.png)

14. 사용자의 선택은 변수에 저장되며, 사용자가 선택한 옵션에 따라 주제가
    분기됩니다. 주제 흐름을 더 잘 추적할 수 있도록 변수를 이름 변경할 수
    있습니다.

15. 변수 영역에서 **Save response as** 아래에 있는 연필 아이콘 을
    클릭하여 변수 속성을 편집하세요.

16. The **Variable properties** 창이 열리면, 변수
    이름을 +++TimeoffType*+++*으로 변경하세요. **Variables properties**
    창을 닫으면, 작성 캔버스에서 변경 사항이 반영된 것을 확인할 수
    있습니다.

> ![A screenshot of a computer Description automatically
> generated](./media/image26.png)

17. 유급 휴가(Paid vacation) 분기(branch)에 메시지 노드를 추가하고,
    사용자에게 유급 휴가 신청을 위해 다음 메시지를 입력하세요: +++**For
    paid vacation time-off, go to www.contoso.com/HR/PaidTimeOff**+++

![A screenshot of a computer Description automatically
generated](./media/image27.png)

18. **National Holidays** 경로에 다음 텍스트가 있는 메시지 노드를
    추가하세요:

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

![](./media/image28.png)

19. **Save**를 클릭하세요.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

![A screenshot of a chat window Description automatically
generated](./media/image30.png)

## **연습 4: 예상 동작에 대해 Copilot 테스트하기**

1.  화면 상단에 있는 **Copilot/Power Virtual Agent** 아이콘을 선택하여
    테스트용 Copilot 캔버스를 실행하세요.

> ![A screenshot of a computer Description automatically
> generated](./media/image31.png)

2.  Copilot 채팅에 **I need time off information**을 입력하세요.

3.  **Paid vacation**을 선택하세요.

4.  설정한 구성에 따라 응답을 받게 됩니다.

> ![A screenshot of a chat Description automatically
> generated](./media/image32.png)
>
> ![A screenshot of a chat Description automatically
> generated](./media/image33.png)
>
> **요약:**
>
> 이번 실습에서는 Copilot Studio 앱을 Teams에 추가하고, Teams 내에서
> 클래식 봇(Classic bot)을 생성하는 방법을 배웠습니다.
