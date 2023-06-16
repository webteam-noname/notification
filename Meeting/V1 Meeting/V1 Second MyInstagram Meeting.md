### 날짜 : 2023-05-19
### 주제 : MyInstagram 기능 회의
---
### 태그
* #MyInstagram

## MyInstagram 회의 진행
1.  Http 통신 기초 및 로그인
2.  Vue JWT 및 firebase 사용법 전달
3.  이관 및 추가된 프로젝트 구성

## Http 통신 기초 및 로그인

**http 통신되는 방법**
-   기본적으로 stateless하게 통신하고 있습니다.
-   그래서 매번 새로운 요청이 필요합니다.
<img style="width:100%" src="https://github.com/webteam-noname/notification/assets/53805469/aa828c80-7cfc-4b0f-a6f0-a6c999b3b9ac" />

**로그인**
-   기본적인 http 통신과는 달리 로그인은 계정의 상태를 유지해야 합니다.
-   이에 따라 session이나 cookie를 이용한 로그인 검증을 진행합니다.
<img style="width:100%" src="https://github.com/webteam-noname/notification/assets/53805469/c64ac0ac-ba7e-4a46-bcf0-bcbc757eca95" />

* 로그인 된 이후 게시판을 조회할 때는 검증된 session의 내용을 토대로 조회할지말지 결정합니다. 
<img style="width:100%" src="https://github.com/webteam-noname/notification/assets/53805469/c2b51fdc-ec07-4910-bd4b-f4c536df07c4" />

**cookie, session 방식의 문제점**
-   하지만 cookie나 session으로 로그인을 처리할 경우 보안적인 문제가 있을 수 있습니다.
<img style="width:100%" src="https://github.com/webteam-noname/notification/assets/53805469/b53e8244-e82b-49e7-9b1d-af35ad8fcb53" />
-   한편으로는 계속해서 연속성을 가진채로 데이터를 가지고 있다보니 다수의 계정이 접속 할때는 서버 부하가 생길 수 있습니다.
    
**jwt(json web token) & refresh token**
- 그래서 서버 부하를 줄이기 위해 state한 방식이 아닌 stateless한 방식으로 통신을 합니다.
- stateless한 통신 방식 중 하나가 jwt 방식입니다.
- jwt는 쉽게 티켓이라 생각하면 됩니다.
- Client가 가지고 있는 토큰을 해킹당하면 서버는 검증할 방법이 없음으로 유효기간을 짧게 설정합니다.
- 하지만 너무 짧게 설정하면 이전 cookie, session과 다를게 없기에 refresh token을 발급합니다.
- refresh token을 사용하는 이유는 토큰의 유효기간이 끝나도 갱신을 할 수 있도록 도움을 주는 토큰입니다.
-  token 사용은 OAuth 버전에 따라 차이가 있습니다. 차이가 있는 부분은 백엔드 기능에 정의하도록 합니다.

## Vue JWT 및 firebase 사용법 전달
-   뷰 공식 사이트: [](https://v2.ko.vuejs.org/v2/guide)[https://v2.ko.vuejs.org/v2/guide](https://v2.ko.vuejs.org/v2/guide)?
-   뷰 관련 코드 모음: [https://github.com/vuejs/awesome-vue](https://github.com/vuejs/awesome-vue)
-   뷰 JWT 구현: [](https://www.youtube.com/watch?v=JR0jSscNNd4)[https://www.youtube.com/watch?v=JR0jSscNNd4](https://www.youtube.com/watch?v=JR0jSscNNd4)
    -   만약 vue 공식사이트의 내용이 어렵다면 다른 블로그나 영상을 보고 감을 익힌 뒤 공식사이트를 참고하는 것도 좋은 방법일 것 같습니다.
-   뷰 파이어베이스: [](https://www.youtube.com/watch?v=we4zuQIXmnw)[https://www.youtube.com/watch?v=we4zuQIXmnw](https://www.youtube.com/watch?v=we4zuQIXmnw)
    -   파이어베이스도 따라 하는 방식이 너무 어렵다면 찾아보셔도 좋아요ㅎㅎ

## 이관 및 추가된 프로젝트 구성
#### V1 MyInstagram 목차
* 로그인, 회원가입, 관리자, 소셜 로그인

#### V1 MyInstagram 회의 진행 
* V1에서는 회원과 관련된 기능을 추가하고자 기존에 있던 검색은 V2로 옮겼습니다.
* 현재 추가될 기능은 비밀번호 찾기와 관리자 유저 관리, 소셜 로그인 기능입니다. 
* 비밀번호 찾기 기능은 기존의 인스타그램과 같은 방법으로 email 인증을 통해 본인 email일 경우 비밀번호 변경 페이지로 이동해 변경할 수 있도록 유도합니다. 
* 관리자 유저 관리 기능은 추후 있을 프로젝트를 대비해 추가해봤습니다. 
* 이후 관리자와 연관된 기능은 더 추가될 수도 추가되지 않을 수도 있습니다. 
* 관리자 관련된 UI는 회의를 통해 정리할 필요가 있어보입니다.
* 소셜 로그인 또한 이후 있을 프로젝트의 사용을 염두해 만들었습니다. 
* 현재는 구글 인증만을 구현한다고 적었지만 추후에 페이스북 인증을 추가할 수도 있습니다.

## V2로 이관한 기능
##### 검색
-   회원 연관관계를 검색합니다.
-   검색된 회원을 클릭시 회원의 소개페이지로 이동합니다.


## V1 추가된 기능 
##### 비밀번호 찾기
* 회원은 비밀번호 찾기 페이지를 방문합니다.
* 비밀번호 찾기 페이지에서 메일을 보냅니다. 
* 회원은 메일함에서 비밀번호 변경 페이지로 이동합니다.
* 비밀번호 변경페이지에서 비밀번호를 변경합니다. 

##### 관리자
* 관리자는 권한을 추가합니다. 
* 관리자는 회원을 만듭니다. 
* 관리자는 회원과 회원의 권한을 매칭시킵니다.

##### 소셜 로그인
* 구글을 통해 회원가입과 로그인을 진행합니다. 