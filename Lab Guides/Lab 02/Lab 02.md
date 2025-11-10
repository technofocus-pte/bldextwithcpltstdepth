# 실습 02 - Dynamics 365 Customer Service 구성

## 목표

이 실습에서는 Azure에서 보안 그룹을 만들어 Copilot Studio에서 설정을
업데이트한 다음, **Dynamics 365 Customer Service 체험판을**
활성화합니다.

## 작업 1: Entra ID에서 보안 그룹 생성 및 Copilot Studio Authors 구성

1.  +++https://portal.azure.com/+++ Azure 포털로 이동하여 로그인 자격
    증명으로 로그인합니다.

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image1.jpeg)

![A screenshot of a computer login AI-generated content may be
incorrect.](./media/image2.jpeg)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image3.png)

2\. 계정을 안전하게 유지 창에서 **Next를** 선택하고 **지시에** 따릅니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  휴대폰에 Authenticator 앱이 아직 없다면 다운로드합니다.![A
    screenshot of a computer screen AI-generated content may be
    incorrect.](./media/image5.png)

&nbsp;

4.  지시에 따라 설정을 완료합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

5.  Azure 시작 화면에서 **Get Started**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image10.png)

6.  +++Microsoft EntraID+++를 검색하여 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

7.  왼쪽 창에서 **Manage** -\> **Groups**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

8.  새 보안 그룹을 생성하려면 **New group**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

9.  다음 세부 정보를 입력합니다.

- 그룹 유형 – **Security**를 선택합니다.

- 그룹 이름 – +++**copilotagentsecurity**+++를 입력합니다.

- Microsoft Entra 역할을 그룹에 할당할 수 있음 – **Yes**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

10. **No owners selected**를 선택한 다음, **Add owners** 페이지에서
    **MOD Administrator**를 선택하고 **Select**를 클릭합니다.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

11. 동일하게 **No members selected**를 선택한 후, 목록에서 **MOD
    Administrator**를 추가하고 **Select**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

12. **No roles selected**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

13. +++**Global admin**+++을 검색하여 선택하고 **Select**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

14. 모든 세부 정보를 추가한 후 **Create**를 선택하고, 확인 대화 상자에서
    **Yes**를 선택합니다.

![A screenshot of a group AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

15. **성공** 메시지가 표시되는지 확인합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

16. 새 탭에서 +++https://powerplatform.microsoft.com+++으로 이동합니다.
    왼쪽 창에서 **Manage**를 선택한 다음 **Tenant Settings** 옵션을
    선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

17. 사용 가능한 목록에서 **Copilot Studio Authors**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

18. 설정을 편집하려면 **Edit** 아이콘을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

19. 이전에 생성한 **copilotagentsecurity** 그룹을 검색하여 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

20. 설정을 저장하려면 **Save**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

작업 2: Dynamics 365 Customer Service 체험판에 가입

1.  +++<https://dynamics.microsoft.com/en-us/customer-service/overview/+++>에
    로그인합니다

2.  메시지가 표시되면 **Home** 탭에서 **Office 365 Tenant 세부 정보를**
    사용하여 로그인합니다

3.  **Try for free**를 클릭합니다

![](./media/image28.png)

4.  **Resources** 탭에서 **Office 365 Administrative Username**을
    입력하고, 확인란을 선택한 다음 **Start your free trial**을
    클릭합니다..

![](./media/image29.png)

5.  지역을 **United States**로 입력하고, **Phone number**를 입력한 후
    **Submit**을 클릭합니다.

![](./media/image30.png)

6.  Engage 고객용 Launch Trial 옵션이 표시되면 **Launch Trial**을
    클릭합니다.

![](./media/image31.png)

7.  활성화되면 Customer Service workspace가 열립니다.

![](./media/image32.png)

## 요약

이 실습에서는 Dynamics 365 Customer Service를 활성화했으며, 이 서비스는
**실습 04 - Dynamics 365 Customer Service 앱과 에이전트를 통합하고 자동
사례 에스컬레이션을 라이브 에이전트에게 구현하기**에서 사용됩니다.
