# ✒ MOVA

#### 웹툰 커뮤니티, 팬아트 서비스
#### 링크: https://mo-va.site/

<br/>

## 1. 제작 기간, 참여 인원 & 맡은 역할

- 기간: 2022년 11월 30일 ~ 12월 28일
- 팀 프로젝트 (팀장 담당)

- 역할

  - 게시글 CRUD(공지사항, 팬 게시판)
  - ListAPIView를 이용한 공지사항, 팬 게시판 작성 페이지 내 웹툰 검색
  - 게시글 카테고리 기능 구현
  - Docker, AWS 배포
  - 이용자의 피드백 반영 (웹툰 검색 내 작가로 검색 요청건 피드백 반영)
  - 위 항목의 API 구축을 바탕으로 프론트 연동 진행

  
## 2. 사용 기술
  
  > Backend
  
    - Python
    - Django
    - DjangoRestFramework
    - Django simple JWT
    - Dj-rest-auth
    - django-allauth
     
    
  > Database
      
    
  
    - PostgreSQL
        
    
  > Infra
  
    - AWS EC2
    - AWS Route 53
    - AWS CloudFront
    - AWS S3
    - Docker
    - Docker compose
    - Nginx
    - Gunicorn
      
    
  > Frontend
    
    - Vanilla JS
    - html
    - css
    - toast UI
        
    
  > Management
  
    - Git/Github
    - Notion
    - Slack
    
  
    
 ## 3. 핵심 기능
 
MOVA의 핵심 기능은 게시글과 팬아트 기능 입니다.
  
1. 게시글 작성/수정/삭제 및 검색 기능
2. 게시글 작성/수정 시 웹툰, 게시글 카테고리 기능
3. [Colorization_tool_on_web](https://github.com/yangco-le/Colorization_Tool_on_Web)을 활용한 팬아트 기능


## 4. ERD 설계


    [IMGAE]


## 5. API 설계

  - Postman 활용하여 만든 api 명세서

    https://documenter.getpostman.com/view/24027867/2s8Z6x2Z38
    
## 6. Architecture

  [IMGAE]
  
## 7. 핵심 트러블 슈팅

[Wiki로 이동](https://github.com/marinred/MOVA_BACKEND/wiki/%ED%8A%B8%EB%9F%AC%EB%B8%94-%EC%8A%88%ED%8C%85-%EB%B0%8F-%ED%94%BC%EB%93%9C%EB%B0%B1)

## 8. 피드백 반영
 <details>
  <summary >소셜 로그인</summary>
  <div markdown="1">
1. 소셜 로그인

KakaoLoginView를 통해 콜백 URL를 리턴해주고 KakaoCallbackView에  통해 카카오에서 제공하는

access 토큰을 받을 수 있었다.

access 토큰 발급 후 mova에 적용하기 위해 카카오 이메일을 통해 이미 가입된 정보가 있는지 확인을 하였으며,
확인 후 OAuth를 사용하여 JWT 토큰 방식으로 발급하여 사용할 수 있었다.

```python
class KakaoLoginView(APIView):
    def get(self, request):
        client_id = os.environ.get("SOCIAL_AUTH_KAKAO_CLIENT_ID","")
        return Response(f"https://kauth.kakao.com/oauth/authorize?client_id={client_id}&redirect_uri={KAKAO_CALLBACK_URI}&response_type=code&scope=account_email")
    
class KakaoCallbackView(APIView):
    def get(self, request):
        client_id = os.environ.get("SOCIAL_AUTH_KAKAO_CLIENT_ID", "")
        print(client_id)
        code = request.GET.get("code")

        # code로 access token 요청
        token_request = requests.get(f"https://kauth.kakao.com/oauth/token?grant_type=authorization_code&client_id={client_id}&redirect_uri={KAKAO_CALLBACK_URI}&code={code}")
        token_response_json = token_request.json()

        # 에러 발생 시 중단
        error = token_response_json.get("error", None)
        if error is not None:
            raise Response(error)
        
        access_token = token_response_json.get("access_token")
        
        profile_request = requests.post(
            "https://kapi.kakao.com/v2/user/me",
            headers={"Authorization": f"Bearer {access_token}"},
        )
        profile_json = profile_request.json()

        kakao_account = profile_json.get("kakao_account")
        email = kakao_account.get("email", None) # 이메일!
        
        try:
            # 전달받은 이메일로 등록된 유저가 있는지 탐색
            user = User.objects.get(email=email)

            # FK로 연결되어 있는 socialaccount 테이블에서 해당 이메일의 유저가 있는지 확인
            social_user = SocialAccount.objects.get(user=user)

            # 있는데 카카오계정이 아니어도 에러
            if social_user.provider != 'kakao':
                return Response({'err_msg': 'no matching social type'}, status=status.HTTP_400_BAD_REQUEST)

            # 이미 카카오로 제대로 가입된 유저 => 로그인 & 해당 유저의 jwt 발급
            data = {'access_token': access_token, 'code': code}
            accept = requests.post(f"{BASE_URL}user/kakao/login/finish/", data=data)
            accept_status = accept.status_code

            # 뭔가 중간에 문제가 생기면 에러
            if accept_status != 200:
                return Response({'err_msg': 'failed to signin'}, status=accept_status)

            accept_json = accept.json()
            accept_json.pop('user', None)
            return Response(accept_json, status=status.HTTP_200_OK)

        except User.DoesNotExist:
            # 전달받은 이메일로 기존에 가입된 유저가 아예 없으면 => 새로 회원가입 & 해당 유저의 jwt 발급
            data = {'access_token': access_token, 'code': code}
            accept = requests.post(f"{BASE_URL}user/kakao/login/finish/", data=data)
            accept_status = accept.status_code

            # 뭔가 중간에 문제가 생기면 에러
            if accept_status != 200:
                return Response({'err_msg': 'failed to signup'}, status=accept_status)

            accept_json = accept.json()
            accept_json.pop('user', None)
            return Response(accept_json)
    
class KakaoLogin(SocialLoginView):
    adapter_class = kakao_view.KakaoOAuth2Adapter
    callback_url = KAKAO_CALLBACK_URI
    client_class = OAuth2Client
```

프론트에서는 handleKakao를 통해 백엔드에서 넘겨주는
return Response(f"[https://kauth.kakao.com/oauth/authorize?client_id={client_id}&redirect_uri={KAKAO_CALLBACK_URI}&response_type=code&scope=account_email](https://kauth.kakao.com/oauth/authorize?client_id=%7Bclient_id%7D&redirect_uri=%7BKAKAO_CALLBACK_URI%7D&response_type=code&scope=account_email)") 를 받아와 해당 주소로

이동 하였으며,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/58289094-8d6a-423d-ae39-515ba8d3f827/Untitled.png)

카카오 로그인 완료시 위 사진과 같이 url에 code 값이 담겨오는데 해당 code값을 사용하여 백엔드 쪽에 넘겨 보내주면 KakaoCallbackView가 실행되어 reponse로 JWT토큰을 받아올 수 있었다.

```jsx
async function handleKakao(){
  const response = await fetch(`${backend_base_url}/user/kakao/login`, {
  })
  const response_json = await response.json()
  location.href = response_json
}

async function handleSigninKakao(){
  let code = new URL(window.location.href).searchParams.get("code")
  if (code != null){
    const response = await fetch(`${backend_base_url}/user/kakao/callback/?code=${code}`)
    const response_json = await response.json()
    localStorage.setItem("access", "Bearer "+response_json.access_token);
    localStorage.setItem("refresh", response_json.refresh_token);
    const base64Url = response_json.access_token.split('.')[1];
    const base64 = base64Url.replace(/-/g, '+').replace(/_/g, '/');
    const jsonPayload = decodeURIComponent(atob(base64).split('').map(function(c) {
        return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
    }).join(''));
    localStorage.setItem("payload", jsonPayload);
    alert("MOVA에 오신걸 환영 합니다.")
    location.href = "main.html";
  }
}
```


  </div>
  </details>
 
 
 ## 9. 회고 및 느낀점
 
> [프로젝트 개발 회고 게시물](https://velog.io/@marinred/%EB%82%B4%EC%9D%BC%EB%B0%B0%EC%9B%80%EC%BA%A0%ED%94%84-%EC%B5%9C%EC%A2%85%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C-K.P.T)
