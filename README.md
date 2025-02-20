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

* **WBS**
```mermaid
gantt
    title Handmade_Pet_Food_Blog
    dateFormat  YYYY-MM-DD
    section 계획
    계획 수립(프로젝트 범위 수립, ERD 작성, API 명세서)        :done,    des1, 2025-02-20, 8d
    section 설계
    와이어프레임 작성         :         des3, after des2, 1d
    데이터베이스 스키마 설계  :         des4, after des2, 1d
    section 개발
    기능 개발                :         dev2, after des2, 2d
    section 테스트
    테스트 케이스 작성       :         tes1, after dev2, 1d
    테스트                  :         tes2, after dev2, 1d
    section 배포
    배포 준비               :         dep1, after tes2, 1d
    출시                    :         dep2, after dep1, 1d
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

* **API 명세서**

[Swagger](localhost:8000)  

|app: accounts|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'login/'|POST|유저 로그인|||
|'logout/'|POST|유저 로그아웃|✅||
|'register-admin/'|POST|관리자 계정 생성|||✅|
|'register/'|POST|일반 사용자 계정 생성|||
|'user/'|GET|현재 로그인한 사용자 정보 조회|✅||
|'users/'|GET|전체 사용자 목록 조회|||✅|
|'<int:pk>/'|GET|특정 사용자 정보 조회|||✅|
|'<int:pk>/'|PUT|특정 사용자 정보 수정||✅|✅|
|'<int:pk>/'|PATCH|특정 사용자 정보 부분 수정||✅|✅|
|'<int:pk>/'|DELETE|특정 사용자 삭제|||✅|
|'<int:pk>/delete/'|DELETE|특정 사용자 삭제|||✅|
|'<int:pk>/tokens/generate/'|POST|특정 사용자 토큰 생성|||✅|
<br>

|app: alarm|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'alarms/'|GET|전체 알람 목록 조회|✅||
|'alarms/'|POST|새로운 알람 생성|✅||
|'alarms/<int:pk>/'|GET|특정 알람 조회|✅||
|'alarms/<int:pk>/'|PUT|특정 알람 수정|✅|✅|
|'alarms/<int:pk>/'|PATCH|특정 알람 부분 수정|✅|✅|
|'alarms/<int:pk>/'|DELETE|특정 알람 삭제|✅|✅|
|'risks/'|GET|전체 위험 목록 조회|✅||
|'risks/'|POST|새로운 위험 생성|✅||
|'risks/<int:pk>/'|GET|특정 위험 조회|✅||
|'risks/<int:pk>/'|PUT|특정 위험 수정|✅|✅|
|'risks/<int:pk>/'|PATCH|특정 위험 부분 수정|✅|✅|
|'risks/<int:pk>/'|DELETE|특정 위험 삭제|✅|✅|
|'alarm-types/'|GET|전체 알람 유형 목록 조회|✅||
|'alarm-types/'|POST|새로운 알람 유형 생성|✅||✅|
|'alarm-types/<int:pk>/'|GET|특정 알람 유형 조회|✅||
|'alarm-types/<int:pk>/'|PUT|특정 알람 유형 수정|✅||✅|
|'alarm-types/<int:pk>/'|PATCH|특정 알람 유형 부분 수정|✅||✅|
|'alarm-types/<int:pk>/'|DELETE|특정 알람 유형 삭제|✅||✅|
|'receive-alarm-data/'|POST|알람 데이터 수신|||✅|
<br>

|app: chat|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'rooms/'|GET|전체 채팅방 목록 조회|✅|||
|'rooms/'|POST|새로운 채팅방 생성|✅|||
|'rooms/<int:pk>/'|GET|특정 채팅방 조회|✅|||
|'rooms/<int:pk>/'|PUT|특정 채팅방 수정|✅|✅||
|'rooms/<int:pk>/'|PATCH|특정 채팅방 부분 수정|✅|✅||
|'rooms/<int:pk>/'|DELETE|특정 채팅방 삭제|✅|✅||
|'rooms/<int:room_pk>/messages/'|GET|특정 채팅방 메시지 목록 조회|✅|||
|'rooms/<int:room_pk>/messages/'|POST|특정 채팅방에 새로운 메시지 생성|✅|||
|'rooms/<int:room_pk>/messages/<int:pk>/'|GET|특정 채팅방의 특정 메시지 조회|✅|||
|'rooms/<int:room_pk>/messages/<int:pk>/'|PUT|특정 채팅방의 특정 메시지 수정|✅|✅||
|'rooms/<int:room_pk>/messages/<int:pk>/'|PATCH|특정 채팅방의 특정 메시지 부분 수정|✅|✅||
|'rooms/<int:room_pk>/messages/<int:pk>/'|DELETE|특정 채팅방의 특정 메시지 삭제|✅|✅||
<br>

|app: media|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|'files/'|GET|전체 미디어 파일 목록 조회|✅|||
|'files/'|POST|새로운 미디어 파일 업로드|✅|||
|'files/<int:pk>/'|GET|특정 미디어 파일 조회|✅|||
|'files/<int:pk>/'|PUT|특정 미디어 파일 수정|✅|✅||
|'files/<int:pk>/'|PATCH|특정 미디어 파일 부분 수정|✅|✅||
|'files/<int:pk>/'|DELETE|특정 미디어 파일 삭제|✅|✅||
|'files/<int:pk>/predict/'|POST|특정 미디어 파일 예측|✅|||
<br>

|app: notice|HTTP Method|설명|로그인 권한 필요|작성자 권한 필요|Admin 권한|
|:-|:-|:-|:-:|:-:|:-:|
|''|GET|전체 공지사항 목록 조회||||
|''|POST|새로운 공지사항 생성|||✅|
|'<int:pk>/'|GET|특정 공지사항 조회||||
|'<int:pk>/'|PUT|특정 공지사항 수정|||✅|
|'<int:pk>/'|PATCH|특정 공지사항 부분 수정|||✅|
|'<int:pk>/'|DELETE|특정 공지사항 삭제|||✅|
<br>

* **활용한 언어 및 툴 정리**
    * 리액트 JS
    * 노드 JS
    * 파이어베이스
    * Git
    * Cursor
