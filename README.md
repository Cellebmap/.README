# Cellebmap(임영웅 ver)

* **현재 웹 개발 목표**
    * 임영웅 언급/방문한 관광지 데이터들을 맵에 표시
    * 유저가 가려는 장소 기반, 관광지 데이터들을 추천
    * 선택한 순서 및 장소 정보들을 기반으로 여행

* **최종 목표**
    * 좋아하는 셀럽/여행자들의 위치 정보 선택
    * 그들이 방문/추천한 관광지 데이터 수집 및 분석
    * LLM 기반 개인화된 여행 추천 서비스 제공

* **사용방법**
    1. 사용자 로그인 및 가고자 하는 지역 정보 입력
    2. 지도 기반 관광지 정보 확인 및 리스트업된 개인화된 정보들 받기

* **서비스 URL 정보**
    * 배포 URL 정보 : 
    * 깃허브 링크(백엔드, 프론트 전체 코드 포함) : https://github.com/Cellebmap

* **앱 별 핵심 기능**
   * 인증된 사용자 기반 커뮤니티
      * 신뢰성 있는 여행 정보 공유
      * 실시간 현지 정보 업데이트

   * 맞춤형 여행지 추천
      * 지도 기반 임영웅 언급/방문 관광지 정보 표시
      * 관심 지역 기반 관광지 정보 표시

   * 지도 기반 인터페이스
     * 직관적인 위치 정보 제공
     * 경로 최적화 추천
     
* **ERD**
```mermaid
classDiagram
    class User {
        -Long userid
        -String email
        -String password
        -String preferredRegion
        +login()
        +logout()
        +getPreferences()
    }

    class Location {
        -Long locationid
        -String name
        -String address
        -String category
        +getDetails()
        +updateInfo()
    }

    class Celebrity {
        -Long celebrityid
        -String name
        -List<Location> visitedLocations
        +getVisitedPlaces()
        +addVisitedPlace()
        +getRecommendations()
    }

    class TravelPlan {
        -Long planid
        -User user
        -List<Location> locations
        +createPlan()
        +updatePlan()
        +expressRoute()
    }

    class MapService {
        +showLocationsOnMap(List<Location> locations)
        +expressRoute(List<Location> locations)
    }

    User "1" -- "*" TravelPlan
    Celebrity "1" -- "*" Location
    TravelPlan "*" -- "*" Location
    MapService -- Location
```

* **WBS**
```mermaid
gantt
    title Handmade_Pet_Food_Blog
    dateFormat  YYYY-MM-DD
    section 계획
    계획 수립(프로젝트 범위 수립, ERD 작성, API 명세서)        :       des1, 2025-02-20, 8d
    section 프론트엔드
    react JS         :         des2, after des1, 15d
    section 백엔드
    node JS                :         dev3, after des2, 31d
    section 배포
    파이어베이스       :         dev4, after dev3, 15d
```

* **화면 정의서**
    <table>
        <tr>
            <th>스플래쉬 화면</th>
            <th>설명</th>
        </tr>
        <tr>
            <td width="70%">
![셀럽맵 스플래쉬 화면](https://github.com/user-attachments/assets/378a4ea7-bb02-4dcb-85f8-66fb1d8d47b4)
            </td>
            <td>
                <ul>
                    <li>셀럽맵 로고 화면</li>
                    <li>셀럽맵 지도 화면으로 전환</li>
                    <li>웹 구동 시 가장 먼저 뜨는 화면</li>
                </ul>
            </td>
        </tr>
    </table>
    <table>
        <tr>
            <th>셀럽맵 지도 화면</th>
            <th>설명</th>
        </tr>
        <tr>
            <td width="70%">
![셀럽맵 지도 화면](https://github.com/user-attachments/assets/c2ee6919-f5c4-40fc-b565-5ddd0a82931e)
            </td>
            <td>
                <ul>
                    <li>임영웅 언급/방문 관광지 데이터 표시</li>
                    <li>돋보기 버튼을 누르면 관심 지역 입력</li>
                    <li>관심 지역 기반 관광지 정보들 표시(숙소, 카페, 식당 표기)</li>
                    <li>선택 정보들 리스트업</li>
                </ul>
            </td>
        </tr>
    </table>
    <table>
        <tr>
            <th>셀럽맵 내가 픽한 곳</th>
            <th>설명</th>
        </tr>
        <tr>
            <td width="70%">
![셀럽맵 내가 픽한 곳](https://github.com/user-attachments/assets/f9ce9981-7bac-429e-aac9-2915d32b86aa)
            </td>
            <td>
                <ul>
                    <li>리스트한 관광지 정보들 표시</li>
                    <li>네이버 지도 링크 공유</li>
                    <li>선택 장소들 기반 루트 경로 표시</li>
                </ul>
            </td>
        </tr>
    </table>

* **과업**
    * 와이어 프레임에 제시된 3개의 화면 구현 완료(스플래쉬 화면, 셀럽맵 지도 화면, 셀럽맵 내가 픽한 곳 화면)
    * user 정보 입력
        * default는 config
        * 다른 분들과 함께 집필할 때에는 호출하게 했음
    * CRUD 구현(저장-수정-삭제 기능 구현)
    * 회원가입 기능 구현
    * 로그인 기능 구현
    * 인증 구현

* **향후 액션플랜**
    * nodeJS로 백엔드 코드 작성
    * 파이어베이스 연동
    * 추가적인 셀럽 정보들 업로드
    * 예상 소요시간 및 비용 기능 업로드
    * 알림 기능(서비스 업데이트 사안 제공)
    * 유저 프로필 관리 기능

* **애러와 애러 해결(트러블슈팅 히스토리)**

* **활용한 언어 및 툴 정리**
    * 리액트 JS
    * 노드 JS
    * 파이어베이스
    * Git
    * Cursor
