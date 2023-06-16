### 날짜 : 2023-06-11
### 주제 : API 설계 수정
---
### 태그
* #API설계

### API 설계 수정
* 기존 API 설계에 문제점을 발견하게 되어 URL을 수정하게 되었습니다.
* 문제를 발견하게 된 건 V2 회의를 진행하면서입니다.
* API GET요청을 Body를 통해 보내고 있다는 것이었습니다.
* 이 내용을 토대로 REST API 스펙을 다시 확인하고 내용을 수정하려 합니다.

#### GET 요청 파라미터 문제
```java 
@GetMapping("/api/accounts/profile")  
public ApiResponse<ProfileSearchResponse> searchProfile(@Valid @RequestBody ProfileSearchRequest profileSearchRequest){  
    ProfileSearchResponse accountsLoginResponse = accountService.searchProfile
    (profileSearchRequest);  
    return new ApiResponse<>(HttpStatus.OK, accountsLoginResponse);  
}
```
* 기존 GET 요청시 @RequestBody로 body의 데이터의 요청을 전송합니다.  
* 하지만 GET 요청을 @RequestBody로 받는 것은 문제가 있어, @PathVariable로 특정 데이터를 받으려 합니다. 

<br/>

* @PathVariable로 받은 URL에 ProfileName을 받아 처리할 수 있도록 변경하려 합니다. 
```java 
@GetMapping("/api/accounts/{profileName}/profile")  
public ApiResponse<ProfileSearchResponse> searchProfile(@PathVariable("profileName") String profileName){  
    ProfileSearchResponse accountsLoginResponse = accountService.searchProfile
    (profileName);  
    return new ApiResponse<>(HttpStatus.OK, accountsLoginResponse);  
}
```
* REST API의 규칙에선 메시지의 내용을 통해 명확히 내용을 이해할 수 있어야 한다고 합니다
* 그래서 GET /api/accounts/profile > GET /api/accounts/{profileName}/profile로 변경하였습니다.
* 프로젝트에선 HTTP Method인 GET은 조회를 의미합니다. 
* 그리고 나머지 메시지를 읽으면 **회원의 프로필 명을 통해 프로필을 조회**한다는 것을 명확히 알 수 있게 됩니다.
* 이때, 프로필 명으로 프로필을 조회하는 것임으로 프로필 명에 대한 중복성 검사를 추가했으면 합니다. 
---

<br/>

```java
@GetMapping("/api/follow")  
public ApiResponse<List<FollowSearchResponse>> searchFollow(@Valid @RequestBody FollowSearchRequest followSearchRequest) throws IOException {  
    return new ApiResponse<>(HttpStatus.OK, followService.searchFollow(followSearchRequest));  
}
```
* 이 메서드 역시 @RequestBody로 GET 요청을 받습니다. 
* 또한 Get URL 메시지가 모호합니다. 또한 URL에 포함된 Resource가 단수로 되어 다음과 같이 수정하려 합니다.

<br/>

```java
@GetMapping("/api/follows/{profileName}")  
public ApiResponse<List<FollowSearchResponse>> searchFollow(@PathVariable("profileName") String profileName) throws IOException {
    return new ApiResponse<>(HttpStatus.OK, followService.searchFollow(profileName));  
}
```
* 메서드 내용을 해석하면 프로필 명에 해당하는 팔로우를 조회하겠다는 내용입니다. 
* 또한 follow는 복수형으로 follows로 등록하는 것이 좋습니다. 
* 외에도 위에서 설명한 대로 @RequestBody로 파라미터를 받는 것이 아니라 @PathVariable로 데이터를 받아야 합니다. 
* 이외에도 GET에 적용된 메서드들 중 위와 같은 내용으로 잘못 적용된 내용은 API 설계에 재적용하여 올려두었습니다. 

#### REST API 설계
* REST API 스펙에 대한 내용을 다시 파악하며 이전에 잘못 이해했던 내용을 돌아볼 수 있던 시간이었습니다.
* 물론 제가 적용한 설계가 100% REST API라고 할 수 는 없을 것 같습니다. 
* 하지만 REST API 표준 스펙에 최대한 만족할 수 있도록 설계를 진행했습니다. 
* 아직 많이 부족하지만 이후에도 수정이 필요한 부분이 있다면 다시 한번 작업을 진행하도록 하겠습니다.