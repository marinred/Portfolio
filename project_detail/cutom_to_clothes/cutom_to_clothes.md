# 👕 Custom to Clothes

#### 딥러닝을 이용하여 옷들을 커스텀하여 옷을 주문하는 쇼핑몰 서비


<br/>

## 1. 제작 기간, 참여 인원 & 맡은 역할

- 기간: 2022년 11월 22일 ~ 11월 28일 (1주)
- 팀 프로젝트 (팀장 담당)

- 역할

  - User 회원가입
  - access token을 이용한 로그인 기능 구현
  - SIMPLE JWT를 이용한 User Custom
  - AWS EC2를 이용한 Backend 배포
  - 위 항목의 API 구축을 바탕으로 프론트 연동 진행

  
## 2. 사용 기술
  
  > Backend
  
    - Python
    - Django
    - DjangoRestFramework
    - Django simple JWT
     
        
    
  > Infra
  
    - AWS EC2
      
    
  > Frontend
    
    - Vanilla JS
    - html
    - css
        
    
  > Management
  
    - Git/Github
    - Notion
    - Slack
    
  
    
 ## 3. 핵심 기능
 
Cutom To Clothes의 핵심 기능은 아래와 같습니다.
  
1. [Style-transfer-pytorch](https://github.com/crowsonkb/style-transfer-pytorch)를 이용한 옷 제작 딥러
2. 커스텀 옷 주문 후 사이즈, 수량 선택 기능 구현
3. 커스텀 주문 클릭 시 장바구니, 주문목록 카테고리로 진행하여 상태 표시


## 4. 와이어프레임

https://www.figma.com/file/2wXsZhQlOURcWATyJzz2he/Untitled?node-id=0%3A1&t=1Sm22iCgAOGjt3Sy-0
![clc피그마](https://user-images.githubusercontent.com/113073174/210203800-a61d5423-ebac-4aee-aef4-0dbadad49f8a.png)


## 5. ERD 설계

![CTC](https://user-images.githubusercontent.com/113073174/210205145-a160275e-f7b1-4ffa-9060-83a6e7c48e01.jpg)



## 6. API 설계


| App | 기능 | URL | Method | Request | Response |
| --- | --- | --- | --- | --- | --- |
| User |  |  |  |  |  |
|  | 회원가입 | /user/signup/ | POST | {“email”,“username”,“password”,”password2”} | status:200<br>"result": "ok" |
|  | 로그인 | /user/api/token/ | POST | {“email”, “password”} |  |
|  | 로그아웃 | /user/logout/ |  |  |  |
|  | 프로필 | /user/<int:user_id>/ | GET |  | {"id", "article_image"} |
|  | 메인페이지 | / | GET |  | {"id", "article_image", "likes_count"} |
| Article |  |  |  |  |  |
|  | Base 정보 | /article/| GET |  | {“draft”, "style"} |
|  | 커스텀 제작 | /article/ | POST | {"draft_id", "style_image", "style_id"} | {“article”} |
|  | 커스텀 제적 수정 | /article/ | PUT | {"article_id", "draft_id", "style_image", "style_id"} | {“article”} |
|  | 게시글 좋아요 | /<int:article:id>/like/| POST | {"article_id"} | {"좋아요 등록(취소) 완료"} |
| Order |  |  |  |  |  |
|  | 장바구니 조회 | /order/ | GET |  | {"id", "article_user", "mount", "size", "price"} |
|  | 주문하기 | /order/<int:article_id>/ | POST | {"size", "mount", "status"} | {"order"} |
|  | 주문목록 | /order/ | GET |  | {"id", "article_user", "mount", "size", "price"} |  |

    
  
## 7. 💣 트러블 슈팅

[Wiki 이동](https://github.com/marinred/Custom_To_Clothes_DLC_Backend/wiki/TroubleShooting)



## 8. 프로젝트 시연영상
[![A4팀 프로젝트 시연영상](https://user-images.githubusercontent.com/113073174/204188971-949176c9-1b0e-471b-90e2-c257f54d5ac9.png)](https://www.youtube.com/watch?v=dH_CHanu6E4)
 
 ## 9. 회고 및 느낀점
 
> [프로젝트 개발 회고 게시물](https://velog.io/@marinred/%EB%82%B4%EC%9D%BC%EB%B0%B0%EC%9B%80%EC%BA%A0%ED%94%84-%EC%B5%9C%EC%A2%85%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C-K.P.T)


## 10. 딥러닝 모델
[style-transfer-pytorch](https://github.com/crowsonkb/style-transfer-pytorch)
