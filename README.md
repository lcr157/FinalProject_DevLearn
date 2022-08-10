# FinalProject_DevLearn
> 쌍용교육센터에서 파이널프로젝트로 진행했던 프론트/백엔드 기반 웹 프로젝트입니다.

## 목차
- [기획](#기획)
  - [프로젝트 소개](#1-프로젝트-소개)
  - [프로젝트 특징](#2-프로젝트-특징)
  - [개발 기간 및 기술 스택](#3-개발-기간-및-기술-스택)
  - [시스템 흐름도 및 ERD 다이어그램](#4-시스템-흐름도-및-erd-다이어그램)
  - [주요기능](#5-주요기능)
- [개발내용](#개발내용)
  - [로그인 관련기능](#1-로그인-관련기능)
  - [커뮤니티 질문과답변](#2-커뮤니티-질문과답변)
  - [커뮤니티 스터디](#3-커뮤니티-스터디)
- [프로젝트 마치며](#프로젝트-마치며)
<br>


## 기획
### 1. 프로젝트 소개

![image](https://user-images.githubusercontent.com/44182633/183571505-dddd27d1-e9fc-4907-936e-0442b2e710b6.png)

<br><br>


### 2. 프로젝트 특징
- Spring의 DI(Dependency Injection)패턴을 적용하여 불필요한 의존관계 줄임
- JSTL을 사용한 코드의 가독성 향상
- Tiles로 반복적으로 사용되는 코드를 분리 후 한 곳에서 관리, 높은 재사용성과 확장성 제공
- MyBatis Framework를 이용하여 별도의 XML 문서에 매핑된 프로시저와 SQL 구문을 연동헤 데이터베이스와 연동할 수 있도록 도와 DB개발, JDBC 연동 코드나 트랜잭션 코드를 간소화 시킬 수 있어 소스코드의 유지보수를 용이하게 함
- AJAX의 비동기 방식을 사용하여 웹에서 데이터 조회 시 페이지 전체를 새로고침 하지 않아 불필요한 데이터 요청을 최소화
- 관리자 영역과 클라이언트의 영역을 분리 개발하여 개발의 효율성 및 유지 보수의 편의성을 제공
- jQuery(JavaScript Library)를 사용하여 HTML document traversing, 이벤트 처리, 애니메이션, Ajax를 단순화하여 빠른 웹 개발
- Maven 을 이용한 의존성 관리
- HTML, CSS, BootStrap, jQuery, JavaScript 를 이용한 반응형 웹 구현
<br><br>


### 3. 개발 기간 및 기술 스택
<b>개발기간</b> : 2022.06.01 ~ 2022.06.30 
<br><br>

<b>기술 스택</b>

![image](https://user-images.githubusercontent.com/44182633/183572393-6bb34e15-2494-4518-8c74-11dbf701934b.png)

<br><br>


### 4. 시스템 흐름도 및 ERD 다이어그램
<b>시스템 흐름도</b>

![image](https://user-images.githubusercontent.com/44182633/183574558-d7cc81b0-47fd-448c-b675-a64ec5a89eea.png)

<br><br>

<b>ERD 다이어그램</b>

![image](https://user-images.githubusercontent.com/44182633/183573905-ce72c335-be0b-40ae-a31f-9cdd88d2d7d6.png)

<br>


### 5. 주요기능
기능은 크게 3개의 분류로 나뉩니다.<br>
- **로그인** - 회원 가입 시 이메일 인증 및 유효성 검사를 통한 가입 및 로그인 시 각종 제약부여 구현
- **커뮤니티_질문과 답변** - 부트스트랩 모달과 JSP를 이용한 페이지 작성 및 CRUD기능, 페이징 및 검색 구현
- **커뮤니티_스터디** - 질문과 답변 기능 + 카카오지도 api를 이용한 위치정보가져오기 구현
<br><br>


## 개발내용
### 1. 로그인 관련기능
<details>
  <summary><h3>사이트 헤더부분</h3></summary>
  
  <b>회원</b>

  ![로그인_회원](https://user-images.githubusercontent.com/44182633/183581067-50299a72-7faa-429f-810e-b149b666a308.gif)

  <b>관리자</b>

  ![로그인_관리자](https://user-images.githubusercontent.com/44182633/183581011-89a2eedb-c8ef-4cdb-b59d-f3560b785a08.gif)

  ![image](https://user-images.githubusercontent.com/44182633/183582145-5992bd64-d730-49c7-92f5-202934e76ce9.png)

  <br>

  - 로그인 등급이 <b>회원 / 관리자</b>인지에 따라 메뉴창이 변경
  - EL문의 <b><c:choose>에서 <c:when test="회원 일때">와 <c:when test="관리자 일때">의 조건</b>을 넣어서 구현
</details>


<details>
  <summary><h3>로그인 실패 시</h3></summary>
  
  <b>아이디 잘못입력시</b>

  ![로그인_아이디틀릴시](https://user-images.githubusercontent.com/44182633/183585828-2a9d6fa6-2c62-466c-8d56-aab03d8a13b5.gif)

  - "등록된 아이디가 아닙니다" 문구 띄워줌<br>

  <b>코드</b>

  ![image](https://user-images.githubusercontent.com/44182633/183586410-477554b9-a779-4ffb-8744-f3395544c62d.png)

  - 이메일이 존재하지않으면 -> <b>RedirectAttributes클래스의 addFlashAttribute(파라미터, 메시지내용)</b>를 이용하여 <b>메시지 내용을 메인페이지로 redirect하면서 넘겨줌</b>
  - 이메일이 존재하면 -> 로그인 완료
  <br>


  <b>비밀번호 잘못입력시(5회 미만)</b>

  ![로그인_비밀번호틀릴시](https://user-images.githubusercontent.com/44182633/183585682-487af7cc-b05a-4ea5-ab3e-bb7ad8ac48e6.gif)

  - "패스워드가 일치하지않습니다" 문구 띄워줌
  <br>

  <b>비밀번호 잘못입력시(5회 틀릴 시)</b>

  ![로그인_비밀번호5회이상틀릴시](https://user-images.githubusercontent.com/44182633/183588738-0c93c4b3-1dc8-473a-97f8-a0d4ab964f30.gif)

  - 해당 계정 비활성화로 변환되었다는 문구 띄워줌
  <br>

  <b>비밀번호 잘못입력시(5회 이상)</b>

  ![로그인_비활성화계정로그인시](https://user-images.githubusercontent.com/44182633/183589222-5aab9e9e-dbe3-4af7-b335-cfa92526566b.gif)

  - 비활성화된 계정이란 문구 띄워줌
  <br>

  <b>코드</b>

  ![image](https://user-images.githubusercontent.com/44182633/183586180-8fc3541d-841d-4248-ae8d-c5a7571cc823.png)

  ![image](https://user-images.githubusercontent.com/44182633/183589735-28a04c5c-da31-4745-89b1-c772ff2e82aa.png)

  - dto의 getPwdFail()값을 조건문을 통해 비교하여 상황에 맞게 코드 실행
  - 위의 조건들을 충족하면 <b>세션에 로그인 정보가 저장되어 30분간 로그인 유지</b>
</details>


<details>
  <summary><h3>회원가입</h3></summary>

  ![image](https://user-images.githubusercontent.com/44182633/183590145-5382349b-b08c-4123-b423-911de795da8a.png)

  - 회원 가입 시 <b>이메일 인증 및 유효성 검사</b>를 거쳐야 회원 가입이 가능
  <br>

  <b>이메일 인증</b>

  <b>이메일 유효성검사 실패 시</b>

  ![회원가입_이메일유효성검사실패](https://user-images.githubusercontent.com/44182633/183598007-ea09e123-4cf1-48b6-9eb1-6520291cb4a0.gif)

  <b>이메일 유효성검사 성공 시</b>

  ![회원가입_이메일유효성검사성공](https://user-images.githubusercontent.com/44182633/183598021-7f27dd36-4156-41f8-9af3-56b2669d83e9.gif)

  ![회원가입_이메일인증](https://user-images.githubusercontent.com/44182633/183598148-26511b32-6d59-4216-8fe3-23f3cdf5e4f1.gif)

  - 인증단계로 넘어가서 입력한 메일로 인증번호 전송

  <b>위 과정 정리</b>

  ![image](https://user-images.githubusercontent.com/44182633/183598565-c12cc61c-ab65-46cf-b4f5-ae02abf41f5d.png)

  <b>코드</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183612711-863a54c5-d460-46e7-8980-62de7979a97f.png)

  - 정규식을 이용하여 이메일 조건을 구성
  - Ajax를 이용하여 아이디 중복여부를 체크
  <br>


  <b>이메일 인증번호 입력 과정</b>

  ![image](https://user-images.githubusercontent.com/44182633/183598958-a03ea37f-45fe-4fec-9fc5-0078cf778471.png)

  - 이메일로 받은 인증번호를 회원가입창에 입력하여 회원가입 진행
  - 인증번호 실패 시

  ![회원가입_이메일인증실패](https://user-images.githubusercontent.com/44182633/183600533-87a6acdf-cfc4-428c-9b1f-93253ff22837.gif)

  - 인증번호 성공 시

  ![회원가입_이메일인증성공](https://user-images.githubusercontent.com/44182633/183600545-36cd855c-4821-4213-b818-0d5c46c1c5c0.gif)

  <br>
  
  <b>코드</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183615710-0a595b47-cd0c-4a35-ba3f-a8ae7ba09f5c.png)

  - SMTP 권한을 추가
  
  ![image](https://user-images.githubusercontent.com/44182633/183616208-a5d652f8-8388-4d6a-be48-d05b71d6ba2a.png)

  - Naver계정과 연결해주고, 패스워드 찾기인지 이메일인증인지 <b>용도에 맞게 메일의 제목과 내용</b>을 보내는 사람의 정보와 받는사람 정보 입력로 보내줌
  
  <br>
  - 이메일 인증번호를 완료하면 아이디와 패스워드도 유효성검사를 거쳐 회원가입을 완료

  ![image](https://user-images.githubusercontent.com/44182633/183600868-4a5e971c-bd43-4e91-a73b-28beb9117572.png)

  ![image](https://user-images.githubusercontent.com/44182633/183600915-e48fd328-4753-4433-8760-8b72d95e3045.png)

  <br>
  - 회원가입 완료 시, 로그인하면 정상 로그인 완료

  ![image](https://user-images.githubusercontent.com/44182633/183600970-0be451ef-5081-4e27-828d-eee0bf903471.png)
</details>


<details>
  <summary><h3>패스워드 찾기</h3></summary>

  ![패스워드찾기](https://user-images.githubusercontent.com/44182633/183609544-284d0589-37f7-4fed-b9fe-a939475f4fbe.gif)

  - 패스워드를 잊어버렸다면 찾고자하는 이메일로 임시 패스워드 전송하여 패스워드 변경가능
  <br>
  
  <b>코드</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183617487-023e14a5-f798-4926-93f8-6634c004c33a.png)

  - 존재하는 이메일 체크하고, Mail dto에 보내는 사람과 받는사람 정보 저장하고 generatePwd()함수로 임시 패스워드 생성
  <br>
  
  - <b>generatePwd()함수</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183618133-fb1f055a-2358-4f2a-a02e-f5bf76e5a6f2.png)

  - <b>영문자, 숫자 조합하여 랜덤하게 10자리</b> 생성
  
</details>
<br>


### 2. 커뮤니티 질문과답변
<details>
  <summary><h3>커뮤니티 질문과답변</h3></summary>
  
  <b>질문과답변 메인페이지</b>
  ![image](https://user-images.githubusercontent.com/44182633/183623723-2b2baa16-a046-4ecc-9514-14119666feb3.png)
  
  ![질답_네비게이션바](https://user-images.githubusercontent.com/44182633/183621174-a1785336-a88d-4bf8-bdc9-2fb494cebb5d.gif)

  - 네비게이션 바를 이용하여 전체/미해결/해결에 해당하는 리스트를 Ajax를 이용하여 가져옴
  
  <b>코드</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183625382-696d27f6-e4cd-405d-9034-b89a2b485168.png)

  - 네비게이션 바 클릭 시 검색값도 유지하면서 리스트의 결과를 nav-all이란 리스트 보여주는 클래스에 덮어씌워줌
  <br><br>
  
  ![질답_검색기능](https://user-images.githubusercontent.com/44182633/183621060-8b695940-bfb6-4d46-b2e5-ca97d6550d76.gif)
  
  - 검색한 값이 제목과 내용이 포함된 게시글들의 리스트를 가져옴
  <br><br>
  
  ![질답_게시글작성](https://user-images.githubusercontent.com/44182633/183624756-e5d987bd-a8d3-4936-9660-c70c2f4d283c.gif)
  
  - 게시글은 모달창을 이용해 작성하고, 게시글 상세는 게시글 수정, 삭제, 답변이 가능
  
  <b>코드</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183627788-32adb7aa-afa6-44d1-a55a-b8cc181e47ee.png)

  - <b>문자뿐 아니라 이미지도 첨부가능한 ckEditor</b>를 이용하여 내용을 작성할 수 있도록 구현
  - <b>window.editor.getData().trime()을 이용해서 내용을 HTML코드로 DB에 저장</b>
</details>


<details>
  <summary><h3>커뮤니티 질문과답변 게시글상세</h3></summary>
  
  ![질답_게시글수정](https://user-images.githubusercontent.com/44182633/183627003-a00461bb-dca9-48c0-9c27-3c9a3042904f.gif)

  - 게시글 수정은 글쓴이만 가능
  <br>
  
  ![질답_게시글삭제](https://user-images.githubusercontent.com/44182633/183627018-23424abf-706f-480e-b138-07853c251ee4.gif)

  - 게시글 삭제는 글쓴이와 관리자만 가능
  <br>  
   
  ![질답_답변하기](https://user-images.githubusercontent.com/44182633/183630599-d81f09a6-96b1-4f69-90fd-87c7f78a8d3f.gif)

  - 질문자의 질문이 내가 아는 내용이라면 자유롭게 게시글에 대한 답변을 달 수 있음
  <br>
  
  ![질답_해결로변경](https://user-images.githubusercontent.com/44182633/183629690-e2cc294f-e9e8-4a89-877a-938a1c2f9b00.gif)

  - 답변이 달린 게시글이라면 해결 버튼을 통해 게시글의 상태를 "해결"로 변경가능
  <br>
  
  ![질답_신고하기](https://user-images.githubusercontent.com/44182633/183629973-7df638e0-af9a-49b1-a739-964262e6fbb7.gif)

  - 게시글이 적합하지 않다고 판단되면 "신고하기"버튼을 통해 신고하여 관리자 판단하에 게시글 삭제 여부가 결정
</details>
<br>


### 3. 커뮤니티 스터디
<details>
  <summary><h3>커뮤니티 스터디</h3></summary>

  <b>커뮤니티 스터디 메인페이지</b>
  
  ![스터디_네비게이션탭](https://user-images.githubusercontent.com/44182633/183922517-983a23f0-9541-4199-8851-ccc989372ec9.gif)

  - 네비게이션 바 클릭 시 검색값도 유지하면서 리스트의 결과를 nav-all라는 리스트 보여주는 클래스에 덮어씌워줌
  
  ![스터디_중간탭](https://user-images.githubusercontent.com/44182633/183923830-f70f3449-9c71-435c-9305-7f8849540dda.gif)

  - 중간탭을 클릭 시 최신순/댓글많은순으로 리스트의 결과를 nav-all이란 리스트 보여주는 클래스에 덮어씌워줌
  - 둘 다 AJAX를 이용한 파라미터값 변화로 리스트의 결과를 가져옴
  <br>
  
  ![스터디_카카오api](https://user-images.githubusercontent.com/44182633/183922259-a7a12035-228f-4b60-a931-b298fff9919c.gif)

  - 카카오 지도api를 이용하여 현재위치/서울(홍대입구역)/경기(일산역)/인천(굴포천역) 중심으로 주변의 카페와 학교도서관을 마커로 표시해주고 마커 클릭 시 오버레이되어 해당 장소의 정보를 보여줌
  <b>코드</b>
  
  ![image](https://user-images.githubusercontent.com/44182633/183925017-28b93e71-0ee8-4ae8-903a-96bad198b584.png)

  - 카카오지도 api document를 참고하여 .LatLng(위도, 경도)를 이용하여 원하는 지역을 중심으로 설정해주었음
  
  ![image](https://user-images.githubusercontent.com/44182633/183925319-4af046dd-69d4-4bd0-bf7c-fdd2a7a950e7.png)

  - 설정해준 함수는 JQuery를 이용하여 클릭 시 지도에 해당 위치를 중심으로 이동
</details>


<details>
  <summary><h3>커뮤니티 스터디 상세</h3></summary>

  ![image](https://user-images.githubusercontent.com/44182633/183926176-dd5d58fa-d7b7-418d-bf85-56e055842ee2.png)

  - 커뮤니티의 질문과 답변과 마찬가지로 수정 삭제 가능하고, 글쓴이가 아니라면 스터디신청을 통해 스터디 신청이 가능
  - 스터디 인원이 꽉 찼다면 더 이상 스터디 신청 불가능하고, 게시글 상태가 모집완료로 변경
  - 스터디에 대한 질문은 답변을 통해서 질문할 수 있음
</details>
<br>


## 프로젝트 마치며
파이널프로젝트로 만든 사이트는 "인프런"이라는 사이트를 모티브로 만든 강의 판매사이트입니다. <br>
그래서 저는 <b>기능구현을 할 때 실제 고객이 사용한다는 가정하에 구현을 했기에 디테일한 부분</b>(스터디인원 모두 찼다면 모집중에서 모집완료로 게시글 상태 변경 등)을 신경을 많이 썼었습니다. 그 과정에서 파라미터나 Ajax, redirect등과 같이 코드적으로나 Http통신과정, MVC패턴 등 <b>이론적인 개념들과 프로그래밍적인 실력도 많이 향상됨을 몸소 느꼈습니다.</b> 그리고 <b>개발이라는것에 재미와 원하는대로 코드구현했다는 뿌듯함</b>도 느낄 수 있었습니다.<br><br>
<b>아쉬웠던 점</b>은 <b>OAuth 2.0을 이용해 간편로그인 기능을 구현해보지 못한것</b>과 <b>카카오지도api를 원하는대로 제어하지못한게</b> 아쉬웠습니다.
