---

copyright:
  years: 2017
lastupdated: "2017-04-13"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# API 관리
{: #manage_apis}

API 관리 시스템에서 관리하고 모니터할 수 있도록 API를 통합한 이후, 사용자는 API 설정을 보고 수정할 수 있습니다. API를 통합하지 않은 경우에는 [{{site.data.keyword.openwhisk_short}} 조치에서 API 작성](manage_openwhisk_apis.html)의 프로시저를 완료하여 이를 통합해야 합니다.  

API에 대한 설정을 관리하려면 다음 단계를 완료하십시오. 

새 API가 작성되었으며 이 API가 인터페이스에서 이미 열려 있으면 처음 세 단계를 건너뛸 수 있습니다. 

1. 아직 API에 대한 정보가 표시되지 않으면 {{site.data.keyword.openwhisk_short}} 서비스 대시보드에서 조치를 선택하여 관리하고자 하는 API를 선택하십시오. 
2. 필요하면 **API** 탭을 선택하십시오. 
3. 필요하면 관리하고자 하는 API를 선택하십시오. 연결이 설정되면 다음과 같은 선택사항을 보고 이를 업데이트할 수 있습니다. 
    * 요약
    * 정의
    * 공유
    * API 탐색기
4. 관리되는 API 노출 슬라이더를 선택하여 이를 활성화하고 API를 노출하십시오. 참고: API가 노출되지 않으면 일부 설정을 지정할 수 없습니다.   

## API에 대한 설정의 요약
{: #overview_api}

요약 탭은 API를 선택할 때 기본적으로 선택되며 이는 두 개의 섹션으로 구분되어 있습니다. 
* 특성 - 특성 섹션에서는 다음 정보를 볼 수 있습니다. 
    * API에 대한 기본 정보
	* 보안 정책
	* 속도 제한 정보
    * 공유 세부사항
* 분석 및 로깅 섹션 - 분석 및 로깅 섹션에서는 다음 통계를 볼 수 있습니다. 
	* 마지막 지정된 기간 중의 응답 수와 평균 응답 시간
    * 분당 API 호출 수(그래프 형식)
    * 응답 로그 테이블의 마지막 100개 응답
	
*응답* 그래프는 API가 수신한 응답의 수와 응답 상태의 분석을 바로 보여줍니다. 이는 다수의 오류 응답을 수신 중인지 여부를 판별하는 데 도움이 됩니다. 다수의 오류 응답은 속도 설정에서 허용한 것보다 많은 트래픽이 있음을 표시할 수 있습니다. 사용자는 정보 아이콘 위에 마우스 커서를 올려놓아서 응답 코드별로 응답의 수치 분석을 볼 수 있습니다. 일반적인 응답 코드는 다음과 같습니다. 
* 200  확인
* 201  작성됨
* 302  찾음
* 304  수정되지 않음
* 400  잘못된 요청
* 401  권한 없음
* 403  금지됨
* 500  내부 서버 오류
* 503  사용 불가능한 서비스

응답 로그 테이블에는 마지막 100개 응답의 개별 세부사항이 포함되어 있습니다. 열 표제를 선택하여 열의 항목에 따라 정보를 정렬할 수 있습니다. *응답 검색* 막대를 사용하여 응답 로그 테이블의 특정 항목을 검색할 수 있습니다. 이를 선택하거나 항목 옆에 있는 옵션 메뉴(3개의 수직 점)의 목록에서 **세부사항 보기**를 선택하면 이벤트에 대한 자세한 정보를 볼 수 있습니다. 


## API 설정 편집
{: #settings_api}

**정의** 탭에서 API에 대한 기본 정보를 업데이트할 수 있습니다. 이 정보에는 문서, 이름 및 기본 URL이 포함됩니다. 보안 및 속도 제한 섹션을 사용하면 호출 및 기간 제한을 지정하여 특정 양의 호출만 초, 분 또는 시간당 작성되도록 보장할 수 있습니다. 데이터의 원하지 않는 사용을 방지하거나 API에 대한 통계를 수집할 수 있도록 API 호출 작성에 대한 인증을 요구할 수도 있습니다. 

API에 대한 설정을 변경하려면 다음 단계를 완료하십시오. 

1. API 관리 대시보드에서 **정의** 탭을 클릭하십시오. 
2. API의 이름을 지정하거나 이를 업데이트할 수 있으며 API 정보 섹션의 API 정의를 가져올 수 있습니다. 
3. 보안 및 속도 제한 섹션에서 다음 정책을 업데이트할 수 있습니다. 
    * API 키 요구 - 올바른 API 키가 제공될 때만 API 호출이 처리될 수 있는지 여부를 지정합니다. 기본 설정은 추가 키를 요구하지 않습니다. 
    * 보안 메소드 - API 키 옵션이 선택될 때 API 처리에서 API 키만 요구하는지 또는 API 키와 API 시크릿을 둘 다 요구하는지 여부를 지정합니다. 
    * API 키와 시크릿의 위치 - 메소드에 대한 설정에 따라, API 보안 정보가 호출에 포함되는지 여부를 지정합니다. 호출 이름은 보안 정보가 식별되는 방법을 지정합니다. 
    * API 호출 속도 제한 - 지정된 기간 중에 허용되는 API 호출의 수를 설정합니다(각 키마다 이를 설정하는 옵션 포함). 참고로 버스트 유형의 속도 제한 방법이 사용됩니다. API 호출의 평균 속도는 사용자가 속도에서 지정한 총 기간에 따라 계산됩니다. 기간 중에 API 호출의 속도가 API 호출의 평균 속도를 초과하는 경우에는 사용자가 속도에서 지정된 시간 제한까지 호출이 거부된 기간이 있을 수 있습니다.    
    * OAuth 제공자 - 올바른 보안 매개변수가 있는 사용자가 Google, Facebook, IBM 및 GitHub 등과 같은 제공자의 소셜 로그인 신임 정보를 통해 OAuth를 적용하여 API에 액세스할 수 있는지 확인하십시오. 
4. CORS 사용 - CORS(Cross-Origin Requests)는 다른 도메인에서 일부 제한된 요청을 사용합니다. 
5. **저장**을 클릭하십시오. 

## API 공유
{: #share_api}

{{site.data.keyword.Bluemix_notm}} 조직 내부나 외부에서 기타 사용자와 API를 공유할 수 있습니다. 

{{site.data.keyword.Bluemix_notm}} 조직의 내부나 외부에서 API를 기타 사용자와 공유하는 경우에는 API에 대한 키를 작성할 수 있습니다. 관리되는 각 API는 해당 API의 작성 및 지정이 가능한 5개의 키를 지원합니다. 고유 키를 개인 또는 회사에 전송하여 사용자는 해당 API가 사용되는 방법에 대한 일부 통계를 추적할 수 있습니다. 예를 들어, 해당 개인 또는 회사별로 API에 대한 호출 또는 수를 추적할 수 있습니다. 

키를 사용하지 않거나 키에서 호출을 제한할 수도 있습니다. 이는 테스트, 워크로드 밸런싱, 금액 환산 중에 또는 일부 보안 상황을 처리하는 데 유용할 수 있습니다.   

1. API 관리 대시보드에서 **공유** 탭을 클릭하십시오. 
2. {{site.data.keyword.Bluemix_notm}} 조직에 대한 액세스 권한이 있는 기타 사용자가 API를 사용할 수 있도록 하려면 "{{site.data.keyword.Bluemix_notm}} 조직 내에서 공유" 영역 내에서 **내 Bluemix 조직의 모든 사용자와 API 공유**를 선택하십시오. 키를 생성하려면 이를 반드시 선택해야 합니다. 
3. API에 대한 고유 키를 작성하려면 **API 키 작성**을 클릭하십시오. API 키 작성 대화 상자가 표시됩니다. API 키는 자동으로 생성됩니다. 
4. 사용자에게 고유 키를 보내서 API에 액세스 중인 사용자를 판별하려면 API 키를 사용하십시오. 게이트웨이는 호출을 생성하는 키(및 고객)를 판별할 수 있습니다. 
5. 키 옆의 **메뉴** 아이콘(3개의 수직 점)을 클릭하여 해당 API 키를 편집 또는 삭제할 수 있습니다. 

"{{site.data.keyword.Bluemix_notm}} 조직 외부에서 공유" 섹션에서 사용자는 {{site.data.keyword.Bluemix_notm}} 계정이 없는 사용자와 API를 공유할 수 있습니다. 이 공유 방법은 API 탐색기에서 API 관련 정보를 보기 위한 직접 링크를 제공합니다. API에는 API 탐색기 보기에서 API를 실행하기 위한 단추가 포함되어 있습니다. API에 대한 링크를 요청하려면 다음 단계를 완료하십시오. 

1. "{{site.data.keyword.Bluemix_notm}} 조직 외부에서 공유" 섹션 내에서 **API 키 작성**을 클릭하십시오. API 키 작성 대화 상자가 표시됩니다.
제어가 불가능한 시크릿을 사용자가 보유 중인지 확인하십시오. 
2. API 키에 대한 고유 이름을 제공하십시오. 
3. **키 작성**을 선택하십시오.  
4. {{site.data.keyword.Bluemix_notm}} 계정이 없는 고객에게 API 포털 링크를 전송하십시오. API 키와 시크릿(사용되는 경우)이 링크에 포함되므로, 링크를 생성한 키를 여전히 판별할 수 있습니다. 
  
API 문서 링크가 **API 탐색기** 탭에서 API를 엽니다. 

## API 탐색기로 보기 및 테스트
{: #explore_api}

Swagger 문서에서 생성된 html을 보려면 API 탐색기 탭을 선택하십시오.  

API 탐색기는 API에 적용되는 모든 API 조치 및 문서를 표시합니다. 조작 및 조치, 해당 설명을 보고 UI에서 API를 테스트할 수 있습니다. 또한 Swagger 문서를 다운로드하여 해당 컨텐츠를 재사용할 수도 있습니다. 

API를 테스트하려면 다음 단계를 완료하십시오. 
1. *예제*가 기본적으로 선택됩니다. 이는 선택된 API에 대한 코드의 예제를 보여줍니다. 
2. 필요하면 지정된 언어 옆의 메뉴에서 언어를 선택하여 예제 형식을 변경하십시오.  
3. **시도하기**를 선택하십시오. 
4. **호출 조작**을 선택하십시오.  

요청에 대한 응답이 표시됩니다.    
