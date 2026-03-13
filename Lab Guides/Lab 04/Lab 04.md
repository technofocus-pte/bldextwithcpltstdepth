# 실습 1: 인재 확보를 위한 지능적인 채용 에이전트 생성하기

이 실습에서는 채용 자동화 시스템의 기초를 수립할 것입니다. 먼저 지원자,
직무, 채용 워크플로우 관리를 위한 필요한 Dataverse 테이블과 데이터
구조를 포함한 사전 구성 솔루션을 가져오게 됩니다. 다음으로, 이 표들에
샘플 데이터를 채워 모듈 학습을 지원하고 시험에 현실적인 시나리오를
제공합니다. 마지막으로 Copilot Studio에서 Hiring Agent를 생성하여 향후
미션에서 추가할 모든 기능의 초석이 될 기본 대화 인터페이스를 구축하게
됩니다.

## 연습 1: 솔루션을 가져오기

이 연습에서는 기존의 솔루션을 가져올 것입니다.

1.  +++https://copilotstudio.microsoft.com+++에 Copilot Studio로
    이동하세요

2.  왼쪽 탐색의 **...**에서 **Solutions**을 선택하세요.

![](./media/image1.png)

3.  **Import solution**을 선택하세요. **Browse**를 클릭하고
    **Operative** form **C:\LabFiles**로 시작하는 **zip** 파일을
    선택하고 **Open**을 선택하세요.

![](./media/image2.png)

![](./media/image3.png)

![](./media/image4.png)

4.  선택되면 **Next**를 선택하고 **Import**를 선택하세요.

![](./media/image5.png)

![](./media/image6.png)

5.  이 과정은 약 3분에서 5분 정도 걸릴 것입니다. 성공 시 녹색 알림 바와
    다음 메시지가 표시됩니다: "Solution "Operative" imported
    successfully."

![](./media/image7.png)

6.  "imported successfully" 메시지가 표시되면 솔루션 목록에서 솔루션의
    표시명 (**Operative**)을 선택해 가져온 내용을 확인하세요.

![](./media/image8.png)

7.  솔루션을 검토하고 다음 구성 요소가 수업되었는지 확인하세요.

![](./media/image9.png)

8.  페이지 상단의 Publish all customizations 버튼을 선택하세요.

![](./media/image10.png)

## 연습 2 – 샘플 데이터 가져오기

이 연습에서는 이전 연습에서 가져온 표에 샘플 데이터를 추가하세 됩니다.

1.  이전 연습에서 가져온 솔루션에서 행 앞에 체크 표시하고 상단의
    **Play** 버튼을 놀러 **Hiring Hub** 모델 기반 앱을 선택하세요.

> ![](./media/image11.png)

2.  왼쪽 탐색에서 **Job Roles**을 선택하세요. **More** 아이콘 (서로 아래
    세 개의 점)을 선택한 후 **Import from Excel** 옆에 있는 **right
    arrow**를 선택하세요**.**

![](./media/image12.png)

3.  **Import from CSV**를 선택하세요.

![](./media/image13.png)

4.  **Choose File** 버튼을 선택하고 **C:\LabFiles**에서
    **job-roles.csv**을 선택하고 **Open**을 선택하세요.

![](./media/image14.png)

5.  **Next**를 선택하세요. 다음 단계는 그대로 두고 **Review Mapping**을
    선택하세요

![](./media/image15.png)

![](./media/image16.png)

6.  매핑이 맞는지 확인하고 **Finish Import**를 선택하세요.

![](./media/image17.png)

7.  **Done**을 선택하세요. 이 과정은 시간이 좀 걸릴 수 있지만,
    **Refresh** 버튼을 눌러 가져오기가 성공했는지 확인할 수 있습니다.

![](./media/image18.png)

![](./media/image19.png)

8.  이제 **Evaluation Criteria sample data**를 가져올 것입니다.

9.  왼쪽 탐새에서 **Evaluation Criteria**를 선택하세요.

10. 이전에 한 것처럼 **Import from CSV**를 선택하세요. **Choose
    File** 버튼을 선택하고 **C:\LabFile**에서
    **evaluation-criteria.csv**를 선택하세요.

![](./media/image20.png)

11. **Next**를 선택하세요. 다음 단계를 그대로 두고 **Review Mapping**을
    선택하세요.

![](./media/image21.png)

![](./media/image22.png)

12. 이제 매핑 작업을 좀 더 해야합니다. **Job Role** 필드 옆에
    있는**magnifying glass icon**을 선택하세요.

![](./media/image23.png)

13. 여기서 **Job Title**이 선택되었는지 확하고 없으면 추가하고 **OK**를
    선택하세요.

![](./media/image24.png)

14. 나머지 매핑이 맞는지도 확인하고 **Finish Import**를 선택하고
    **Done**을 선택하세요.

![](./media/image25.png)

15. 이 과정은 시간이 좀 걸릴 수 있지만, **Refresh** 버튼을 눌러
    가져오기가 성공했는지 확인할 수 있습니다.

![](./media/image26.png)

## 연습 3 – 채용 에이전트를 생성하기

이제 선수과목 준비를 마쳤으니, 이제 본격적인 작업을 시작할 차례입니다!
먼저 채용 에이전트를 추가합시다!

1.  Copilot Studio의 왼쪽 창에서 Agents를 선택하세요. + Create blank
    agent 옆의 드롭다운을 선택하고 Advanced create를 선택하세요.

![](./media/image27.png)

2.  Agent 설정에서 Solution을 **Operative**로 선택하고 **Confirm and
    create**를 선택하세요.

![](./media/image28.png)

3.  생성된 에이전트의 정보에 **Edit**를 선택하세요.

![](./media/image29.png)

4.  Name을 +++**Hiring Agent**+++로 입력하고 Description을 +++**Central
    orchestrator for all hiring activities**+++로 입력하고 **Save**를
    선택하세요.

> ![](./media/image30.png)

## 요약

> 이 실습에서는 다음을 완료했습니다.

- **시나리오 이해**: 채용 자동화 과제와 구축할 솔루션에 대한 포괄적인
  지식

- **솔루션 배포**: 채용 관리 시스템의 기본 구성 요소를 성공적으로
  가져오고 구성

- **에이전트 생성**: Agent Academy Operative로서 구축할 시나리오의
  시작점인 채용 에이전트를 구축
