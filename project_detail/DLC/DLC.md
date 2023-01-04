# 🎵 DLC

#### 음악을 좋야요 했을 떄 좋아요 한 음악 리스트 기반으로 음악 추천을 해주는 서비스입니다.

<br/>

## 1. 제작 기간, 참여 인원 & 맡은 역할

- 기간: 2022년 11월 02일 ~ 11월 08일 (1주)
- 팀 프로젝트 (팀장 담당)

- 역할

  - 음악 리스트 조회 기능 구현
  - 음악 상세 조회 기능 구현
  - 음악 좋아요 기능 구현
  - 음악 노래 추천 시스템현기능 구현
  - 위 항목의 API 구축을 바탕으로 프론트 연동 진행

## 2. 사용 기술

> Backend

- Python
- Django
- DjangoRestFramework
- Django simple JWT

> Frontend

- Vanilla JS
- html
- css

> Management

- Git/Github
- Notion
- Slack

## 3. 주요 기능

DLC의 주요 기능은 아래와 같습니다.

- [Spotify Dataset](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset)을 이용한 음악 추천 시스템
- 음악 순위별 리스트 크롤링 및 곡명으로 Spotify API 검색 후 DB 저장
- 좋아요 누른 음악 기반으로 음악 추천 및 추천

## 4. 와이어프레임

- 로그인 / 회원가입 페이지
![](https://velog.velcdn.com/images/marinred/post/55c08bf6-7d02-4d98-acad-bff8556b8200/image.png)
- 메인 페이지
![](https://velog.velcdn.com/images/marinred/post/0a49bd42-f3af-4b5b-b69a-31bbd63d8e0b/image.png)
- 노래 상세 페이지
![](https://velog.velcdn.com/images/marinred/post/e60387fc-d50c-4896-8b1b-42080d5f6432/image.png)
- 프로필 상세 페이지
![](https://velog.velcdn.com/images/marinred/post/98e341cb-d392-4afa-931c-522093679073/image.png)

## 5. ERD 설계

![](https://velog.velcdn.com/images/marinred/post/3c1665f6-fd99-4732-b4e7-cc506e7d446f/image.jpg)

## 6. API 설계


| App | 기능 | URL | Method | Request | Response |
| --- | --- | --- | --- | --- | --- |
| User |  |  |  |  |  |
|  | 회원가입 | /user/signup/ | POST | {“username”,“email”,“password”,”password2”} |  |
|  | 로그인 | /user/api/token/ | POST | {“username”, “password”} |  |
|  | 프로필 | /user/<int:user_id>/ | GET |  | {“user_id”, "username”, “email”, "bio”} |
|  | 프로필 수정 | /user/<int:user_id>/ | PUT | {“username”, “email”, “bio”} | {“user_id”, “username”, “email”, “bio”} |
| Music |  |  |  |  |  |
|  | 노래 목록 조회 | / | GET |  | {“music_id”, “name”, “year”, “artist”, “aalbum”, “music_image”, “like”} |
|  | 노래 상세 조회 | /<int:music_id>/ | GET |  | {“music_id”, “name”, “year”, “artist”, “aalbum”, “music_image”, “like”} |
|  | 노래 좋아요 | /<int:music_id>/like/ | POST | {“user_id”} |  |
| Review |  |  |  |  |  |
|  | 리뷰 작성 | /<int:music_id>/review/ | POST | {“content”} |  |

## 8. 프로젝트 시연영상

- 시연영상 촬영자: 임동근




[![프로젝트 시연영상](https://velog.velcdn.com/images/marinred/post/0a49bd42-f3af-4b5b-b69a-31bbd63d8e0b/image.png)](https://www.youtube.com/watch?v=dH_CHanu6E4)
## 9. 회고 및 느낀점
- DRF를 이용한 첫 프로젝트였는데, 이전까지 Django로만 이용하다가 DRF를 사용하니 이전보다 좀 더 편리하게 작성할 수 있었다.
- 머신러닝이 생각보다 어려웠지만, 추천 시스템이 되고나니 만족스러웠다.
- Python에 대한 이해가 아직 부족했던 것 같다. Python과 Django에 대하여 좀 더 공부할 수 있도록 해야겠다.

> [프로젝트 개발 회고 게시물](https://velog.io/@marinred/%EB%82%B4%EC%9D%BC%EB%B0%B0%EC%9B%80%EC%BA%A0%ED%94%84-%EC%B5%9C%EC%A2%85%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C-K.P.T)

## 10. 머신러닝 데이터셋

[Spotify Dataset](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset)
