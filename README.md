# sns-login

설정 방법은 마지막에.

![절차 최종](https://github.com/user-attachments/assets/c8db83bf-6278-4733-9982-46cc8f62e31a)

   
## 1. sns 로그인 (인가코드 요청)
   쇼셜 로그인 버튼 클릭시 (예시 / 카카오)
   ![카카오 예시1](https://github.com/user-attachments/assets/24d546bc-ed78-4a4d-b542-7c930372774d)
   
   출처: kakao developers
   
   카카오톡 로그인이 되어있다면 바로 동의 화면이 출력됨.
   
   동의하고 계속하기.


## 2. 설정해둔 redirect uri로 인가코드가 발급됨.(설정은 아래 참고)

----

## 3. 토큰 요청
   https://kauth.kakao.com/oauth/token - [ POST ]

   ### 헤더
   
   Content-type: application/x-www-form-urlencoded;charset=utf-8
   
   ### 바디
   
   ${ grant_type } - authorization_code [ 고정 ]
   
   ${ client_id } - 앱 REST API 키
   
   ${ redirect_uri } - 설정한  redirect uri
   
   ${ code } - 1. 에서 발급받은 인가코드
   
   ${ client_secret } - 선택사항.
   
## 4. 응답

   ### 바디
   
   ${ token_type } - bearer[ 고정 ]

   ${ access_token } - 엑세스 토큰

   ${ id_token } - id 토큰 / 조건에 따라 발급

   ${ expires_in } - 엑세스 토큰 , id 토큰 만료시간(초)
   
   ${ refresh_token } - 리프레시 토큰

   ${ refresh_token_expires_in } - 리프레시 토큰 만료시간(초)

   ${ scope } - 엑세스 토큰으로 조회할 수 있는 정보의 권한 범위 / 조건에 따라 발급

----



