# 주제 : 전체 기능 정의
### 태그
* #MyInstagram

#### 인스타 그램 프로젝트 진행 
* 인스타 그램을 클론 코딩합니다.
* 구현은 버전별로 프로젝트의 기능을 정의합니다.

## 프로젝트 구성
#### V1 MyInstagram
* 로그인, 회원가입, 관리자, 소셜 로그인, 소개 페이지

#### V2 MyInstagram
* 팔로우, 검색

#### V3 MyInstagram
* 댓글, 게시판, 좋아요

## V1 MyInstagram

##### 회원가입
* 이메일, 주소, 사용자 이름, 비밀번호를 입력해 회원가입을 합니다.
	* 각 상태값들을 유효성 검증합니다.
* 로그인 페이지로 돌아갑니다.
* 회원이 변경되면 회원 인증도 함께 변경된다. 

##### 로그인
* 아이디와 비밀번호를 입력하여 로그인합니다.
	* 아이디, 비밀번호 유효성 검증을 합니다.
* 회원가입을 합니다. 

##### 비밀번호 찾기
* 회원은 비밀번호 찾기 페이지를 방문합니다.
* 비밀번호 찾기 페이지에서 메일을 보냅니다. 
* 회원은 메일함에서 비밀번호 변경 페이지로 이동합니다.
* 비밀번호 변경페이지에서 비밀번호를 변경합니다. 

##### 소셜 로그인
* 구글을 통해 회원가입과 로그인을 진행합니다. 

##### 소개 페이지
* **프로필 편집**
	* 내 프로필 사진을 변경합니다.
	* 인스타그램 소개글을 수정합니다.

## V2 MyInstagram

##### 팔로우
* 회원은 상대 회원을 팔로우합니다.
* 회원은 상대 회원을 팔로우 했는지 확인합니다. 
* 회원은 잘못 팔로우한 회원을 삭제합니다.
* 상대 회원은 자신을 팔로우한 목록을 확인할 수 있습니다. 
* 상대 회원은 원하는 대상을 팔로잉합니다.

##### 검색
* 회원 연관관계를 검색합니다.
* 검색된 회원을 클릭시 회원의 소개페이지로 이동합니다.
  * 타인의 소개페이지로 이동했을 때 프로필 수정 버튼이 보이지 않게 구현합니다.


## V3 MyInstagram

##### 게시판
* 회원은 게시글을 CRUD 작업을 진행합니다.
	*  게시판 등록
		* 게시판에 사진을 적용한 뒤 필터를 적용합니다.
		* 게시판에 내용을 입력합니다.
	* 게시판 수정
		* 등록한 게시물의 사진을 삭제할 수 있습니다.
		* 등록한 게시물의 내용을 수정할 수 있습니다.
	* 게시판 삭제
		* 게시판의 내용을 삭제합니다.
	* 게시판 조회
		* 게시판의 정렬 순서를 적용합니다.
			1. 최신 게시글
			2. 친구
			3. 팔로우
			4. 팔로워
	* 회원은 게시판의 좋아요를 누를 수 있습니다.
	
##### 댓글
* 등록된 게시판에 댓글을 입력할 수 있습니다. 
* 입력된 댓글에 답글을 달 수 있습니다.
* 회원은 좋아요를 클릭할 수 있습니다.



