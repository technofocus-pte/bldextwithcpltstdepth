
# 실습 06 - Copilot Studio에서 Azure AI Search를 활용하는 인사용 Knowledge Assistant 에이전트 만들기

## 목표

한 대기업에서는 SharePoint, PDF, 내부 위키 및 문서에 분산된 HR 관련
정보(정책, 복리후생, 휴가 지침 등)를 검색하는 데 소요되는 시간을
줄이고자 합니다.

이러한 문제를 해결하기 위해, 이 실습에서는 **Copilot Studio**에서
**Azure AI Search**를 사용하여 기업 HR 문서를 인덱싱하고 의미론적으로
검색하는 **Knowledge Assistant 에이전트**를 구축합니다.

## 연습 1: Azure AI Search 리소스 만들기

1.  Azure Portal의 홈페이지에서 **Azure AI Foundry**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image1.png)

2.  **AI Foundry page**에서 왼쪽 창에서 **AI Search**을 선택한 다음 **+
    Create**를 선택합니다.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image2.png)

3.  아래 세부 정보를 입력하고 **Review + create**을 선택합니다.

- Subscription – **할당된 구독을** 선택하세요

- Resource group – **할당된 리소스 그룹**(ResourceGroup1)을 선택하세요

- Storage account name – +++**searchleaves**+++

- Location –**할당된 지역**을 선택하세요

![A screenshot of a search service AI-generated content may be
incorrect.](./media/image3.png)

4.  검증이 통과되면 **Create**를 선택합니다.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image4.png)

5.  배포에는 몇 분 정도 소요됩니다. 검색 서비스가 생성되면 **Go to
    resource**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

6.  **Overview** 페이지에서 URL 값을 복사하여 메모장에 저장해 두었다가
    나중에 연습할 때 사용합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

7.  왼쪽 창의 **Settings**에서 **Keys**를 선택합니다. **Primary admin
    key**를 복사하여 메모장에 저장해 두었다가 다음 연습에서 사용합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

8.  왼쪽 창의 **Settings**에서 **Identity**를 선택합니다.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image8.png)

9.  **System assigned**에서 상태를 **on**으로 전환한 다음 **Save**을
    클릭합니다.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image9.png)

10. **Enable system assigned managed identity**대화 상자에서 **Yes**를
    선택합니다.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image10.png)

## 연습 2: 저장소 계정 만들기

1.  +++https://portal.azure.com/+++에서 Azure Portal에 로그인하고 자격
    증명을 사용하여 로그인합니다. 홈 화면에서 Storage accounts을
    선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image11.png)

2.  **+ Create**를 선택하여 새 저장소 계정을 만듭니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

3.  아래 세부 정보를 입력하고 다른 필드에서는 기본값을 그대로 사용한 후
    **Review + create**을 클릭합니다.

- Subscription – **할당된 구독**을 선택하세요

- Resource group – **할당된 리소스 그룹(ResourceGroup1)을** 선택하세요

- Region - **할당된 지역**을 선택하세요

- Storage account name – +++**leavepolicystorage**+++

- Primary service – **Azure Blob Storage or Azure Data Lake Storage Gen
  2**를 선택합니다.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image13.png)

4.  검증이 통과되면 **Create**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

5.  리소스 생성이 성공하면 **Go to resource**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

6.  **Data storage**아래에서 **Containers**를 선택합니다. **+
    Container**를 선택하고 이름을 +++**document**+++로 입력한 후,
    **Create**를 클릭하여 컨테이너를 생성합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

7.  생성된 컨테이너 **document**를 선택하여 휴가 정책 문서를
    업로드합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

8.  **Upload**를 클릭한 다음 **Browse for files**를 선택합니다.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image19.png)

9.  **C:\Labfiles**에서 **LeavePolicy.docx**를 선택한 다음 **Upload**를
    클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

10. **leavepolicystorage** 저장소 계정으로 이동합니다(Azure Portal
    **Home page**에서 **Storageaccounts**를 선택하고
    **leavepolicystorage**를 선택합니다). 왼쪽 창에서 **Access Control
    (IAM)**를 선택합니다. **Add -\> Add role assignment**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

11. +++**Storage Blob Data Reader**+++를 검색하여 선택한 후 **Next**를
    클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

12. **+Select members**을 클릭하고 **user id**를 검색하여 선택한 후,
    목록에 표시된 **user id**를 선택하고 **Select**을 클릭합니다. 이렇게
    하면 사용자 ID에 Storage Blob 데이터 리더 역할이 추가됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

13. **Managed identity**를 선택한 다음 **+ Select members**을
    선택합니다. **Managed identity**아래에서 **Search service**를
    선택하고 나열된 검색 서비스를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

14. **Select** 을 클릭하여 검색 서비스를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

15. 역할 할당 추가 화면으로 돌아가서 **Review + assign**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

16. 다음 화면에서 다시 **Review + assign**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

17. 역할이 추가되면 다음 단계로 진행하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

이 연습에서는 저장소 계정을 만들고 문서와 필요한 역할 권한을
추가했습니다.

## 연습 3: Azure OpenAI 서비스 만들기 및 모델 배포하기 

1.  Azure Portal 홈페이지에서 +++Azure OpenAI++를 검색하여 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

2.  **+ Create**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

3.  아래 세부 정보를 입력하고 Next을 선택하세요.

- Subscription – **할당된 구독을** 선택하세요

- Resource group – **할당된 리소스 그룹**(ResourceGroup1)을 선택하세요

- Region – **할당된 지역을** 선택하세요

- Name – +++**openaiservice52374668**+++

- Pricing tier – **Standard**를 선택합니다

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

4.  다음 두 화면에서 **Next**을 선택하고 **Review + submit**화면에서
    **Create**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

5.  서비스가 생성되면 **Go to resource**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

6.  왼쪽 창에서 **Access control (IAM)**를 선택하고 **Add -\> Add role
    assignment**를 선택합니다.

![](./media/image36.png)

7.  +++**Cognitive Services OpenAI User**+++를 검색하고 역할을 선택한 후
    **Next**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

8.  **+ Select members**을 선택하고, **user id**를 검색하여 선택한 후
    **Select**을 클릭합니다.

![](./media/image38.png)

9.  **Add role assignment**화면으로 돌아가서 **Managed identity**를
    선택합니다. 그런 다음 **+ Select members**을 선택합니다. **Select
    managed identities** 화면에서 **Managed identity**아래에 있는
    **seachleaves**를 선택하고 검색 서비스를 선택합니다.

![A screenshot of a computer screen AI-generated content may be
incorrect.](./media/image39.png)

10. 선택한 후 **Select**을 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

11. 다음 두 화면에서 Review + assign을 선택합니다.

![](./media/image41.png)

12. 역할 추가에 대한 **success** 메시지가 나타날 때까지 다음 작업을
    진행하세요.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

13. Azure OpenAI 서비스 리소스의 **Overview** 페이지에서 **Go to Azure
    AI Foundry portal**을 선택하여 해당 포털에서 Azure OpenAI 서비스를
    열고 모델을 배포합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

14. 왼쪽 창에서 **Deployments**를 선택합니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image44.png)

15. **+ Deploy model** -\> **From base models**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

16. +++**text-embedding**+++을 검색하고 **text-embedding-3-large**를
    선택한 다음 **Confirm**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

17. Deploy text-embedding-3-large에서 **Deploy**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

18. 모델이 배포되고 배포 세부 정보가 화면에 로드됩니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

## 연습 4: 벡터 인덱스 만들기

1.  **Searchleaves** AI 검색 서비스 리소스로 이동합니다. **Import and
    vectorize data**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

2.  **Azure Blob Storage** 옵션을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

3.  **What scenarios are you targeting?** 화면에서 **RAG** 옵션을
    선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

4.  아래 세부 정보를 입력하고 나머지 값은 기본값으로 두고 **Next**을
    클릭합니다.

- Subscription – **할당된 구독**을 선택하세요

- Storage account- **leavepolicystorage** 을 선택하세요

- Blob-container – **document**을 선택하세요

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

5.  Vectorize your text 화면에 구독 및 Azure OpenAI 리소스 세부 정보가
    미리 입력되어 있습니다. 아래 세부 정보를 입력하고 **Next**을
    클릭합니다.

- Model deployment – **text-embedding-3-large**를 선택합니다.

- Authentication type – **System assigned identity**를 선택합니다.

- Azure OpenAI의 비용 경고를 확인하려면 확인란을 선택합니다.

6.  여기서는 이미지를 다루지 않으므로 **Vectorize and enrich your
    images**화면에서 다음을 선택하고, **Advanced settings**화면에서도
    **Next**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

7.  **Review + create** 화면에서 **Create**을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

8.  성공 대화 상자에서 **Close**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

## 연습 5: 지식 지원 에이전트 만들기

1.  로그인 자격 증명을 사용하여
    +++https://copilotstudio.microsoft.com+++에 로그인합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

2.  왼쪽 창에서 **Create**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

3.  **+ New agent**를 선택하여 새 에이전트를 만듭니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

4.  +++를 입력하고 **Send**를 선택합니다. +++You are a Knowledge
    assistant agent for HR who will answer questions related to leaves
    and leave policies to the employees.+++

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image60.png)

5.  Copilot가 에이전트에게 이름을 제안합니다. **Create**를 클릭하여
    에이전트를 만듭니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

6.  에이전트가 생성되면 테스트 창에 +++How many days can I avail
    Maternity leaves?+++를 입력하고 **Send**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

7.  아래 스크린샷과 같이 일반적인 답변을 제공합니다.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image64.png)

## 연습 6: Azure AI Search를 지식 소스로 추가하기

1.  에이전트의 **Overview** 페이지에서 **Add knowledge**를 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

2.  사용 가능한 지식 소스 목록에서 Azure AI 검색을 선택합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

3.  다음 화면에서 Not connected옆에 있는 **드롭다운**을 클릭하고
    **Create new connection**를 선택합니다.

![A screenshot of a search engine AI-generated content may be
incorrect.](./media/image67.png)

4.  이전 연습에서 메모장에 저장해 두었던 **Endpoint URL**과 **Admin
    key** 값을 입력한 다음, **Create**를 클릭하여 연결을 만듭니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

5.  연결이 설정되면 사용 가능한 인덱스가 나열되고 이미 선택되어
    있습니다. **Add**를 클릭합니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

6.  AI 검색 서비스가 에이전트에 지식 소스로 추가되었으며 현재 **Ready**
    상태입니다.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

7.  이제 이전에 시도했던 것과 동일한 질문으로 에이전트를 테스트해
    보겠습니다.

8.  테스트 창에 +++How many days can I avail Maternity leaves?+++를
    입력하고 **Send**를 클릭합니다.

![A screenshot of a phone AI-generated content may be
incorrect.](./media/image71.png)

9.  이제 에이전트의 응답은 AI 검색 서비스에 업로드된 문서에서 나온
    것임을 확인할 수 있습니다.

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image72.png)

## 요약

이 실습에서는 지식 소스로 에이전트를 Azure AI Search 서비스에 연결하고
소스를 기반으로 에이전트를 테스트하는 방법을 학습했습니다.
