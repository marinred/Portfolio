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


## 4. Architecture

![mova_art](https://user-images.githubusercontent.com/113073174/210240826-dd23a2bf-212c-4128-9bfa-062a1600c7e5.png)



## 5. ERD 설계


   ![mova_erd](https://user-images.githubusercontent.com/113073174/210240686-8703f3df-64b8-4de7-94d9-28b57e5c18a8.jpg)



## 6. API 설계

  - Postman 활용하여 만든 api 명세서

    https://documenter.getpostman.com/view/24027867/2s8Z6x2Z38
    
  
## 7. 핵심 트러블 슈팅 및 

[Wiki로 이동](https://github.com/marinred/MOVA_BACKEND/wiki/%ED%8A%B8%EB%9F%AC%EB%B8%94-%EC%8A%88%ED%8C%85-%EB%B0%8F-%ED%94%BC%EB%93%9C%EB%B0%B1)

 
 
 ## 9. 회고 및 느낀점
 
> [프로젝트 개발 회고 게시물](https://velog.io/@marinred/%EB%82%B4%EC%9D%BC%EB%B0%B0%EC%9B%80%EC%BA%A0%ED%94%84-%EC%B5%9C%EC%A2%85%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C-K.P.T)
