# ๐ Custom to Clothes

#### ๋ฅ๋ฌ๋์ ์ด์ฉํ์ฌ ์ท๋ค์ ์ปค์คํํ์ฌ ์ท์ ์ฃผ๋ฌธํ๋ ์ผํ๋ชฐ ์๋น์ค


<br/>

## 1. ์ ์ ๊ธฐ๊ฐ, ๋งก์ ์ญํ 

- ๊ธฐ๊ฐ: 2022๋ 11์ 22์ผ ~ 11์ 28์ผ (1์ฃผ)
- ํ ํ๋ก์ ํธ (ํ์ฅ ๋ด๋น)

- ์ญํ 

  - User ํ์๊ฐ์
  - access token์ ์ด์ฉํ ๋ก๊ทธ์ธ ๊ธฐ๋ฅ ๊ตฌํ
  - SIMPLE JWT๋ฅผ ์ด์ฉํ User Custom
  - ๋ฐฐํฌ ๋ฐ ์ด์(AWS EC2)
  - ์ ํญ๋ชฉ์ API ๊ตฌ์ถ์ ๋ฐํ์ผ๋ก ํ๋ก ํธ ์ฐ๋ ์งํ

  
## 2. ์ฌ์ฉ ๊ธฐ์ 
  
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
    
  
    
 ## 3. ์ฃผ์ ๊ธฐ๋ฅ
 
Cutom To Clothes์ ์ฃผ์ ๊ธฐ๋ฅ์ ์๋์ ๊ฐ์ต๋๋ค.
  
1. [Style-transfer-pytorch](https://github.com/crowsonkb/style-transfer-pytorch)๋ฅผ ์ด์ฉํ ์ท ์ ์ ๋ฅ๋ฌ๋ (ํํฐ๋ฅผ ์ด์ฉํ์ฌ ์ท Custom)
2. ์ปค์คํ ์ท ์ฃผ๋ฌธ ํ ์ฌ์ด์ฆ, ์๋ ์ ํ ๊ธฐ๋ฅ ๊ตฌํ
3. ์ปค์คํ ์ฃผ๋ฌธ ํด๋ฆญ ์ ์ฅ๋ฐ๊ตฌ๋, ์ฃผ๋ฌธ๋ชฉ๋ก ์นดํ๊ณ ๋ฆฌ๋ก ์งํํ์ฌ ์ํ ํ์


## 4. ์์ด์ดํ๋ ์

https://www.figma.com/file/2wXsZhQlOURcWATyJzz2he/Untitled?node-id=0%3A1&t=1Sm22iCgAOGjt3Sy-0
![clcํผ๊ทธ๋ง](https://user-images.githubusercontent.com/113073174/210203800-a61d5423-ebac-4aee-aef4-0dbadad49f8a.png)


## 5. ERD ์ค๊ณ

![CTC](https://user-images.githubusercontent.com/113073174/210205145-a160275e-f7b1-4ffa-9060-83a6e7c48e01.jpg)



## 6. API ์ค๊ณ


[API ๋ช์ธ์](https://documenter.getpostman.com/view/23810621/2s8Z72VXUr)

    
  
## 7. ๐ฃ ํธ๋ฌ๋ธ ์ํ

- Django.db.utils.OperationalError (์์ ๋ก๊ทธ์ธ ๊ธฐ๋ฅ ๊ตฌํ ์ค no such table)
- UserModel ์ปค์คํ ์งํ ์ค Login ์ค๋ฅ (์๋ฐ์คํฌ๋ฆฝํธ ์ฐ๋ ๋์ค ๋ก๊ทธ์ธ ์ค๋ฅ)
- ํ๋ก ํธ์๋ ์ฐ๋ ๋์ค TypeError
- ์ฅ๋น๊ตฌ๋ ๊ธฐ๋ฅ ๊ตฌํ ์ค ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ ธ์ค์ง ๋ชปํ๋ ์ค๋ฅ
- ๋ฐฑ์๋ ๋ฐ์ดํฐ๋ฅผ ํ๋ก ํธ ๋ฐ์ดํฐ๋ก ๊ฐ์ ธ์ค๋ ๊ณผ์  ์ค ๊ถํ์ด ์๋ค๊ณ  

[Wiki ์ด๋](https://github.com/marinred/Custom_To_Clothes_DLC_Backend/wiki/TroubleShooting)



## 8. ํ๋ก์ ํธ ์์ฐ์์

- ์์ฐ์์ ์ดฌ์์: ์๋๊ทผ


[![A4ํ ํ๋ก์ ํธ ์์ฐ์์](https://user-images.githubusercontent.com/113073174/204188971-949176c9-1b0e-471b-90e2-c257f54d5ac9.png)](https://www.youtube.com/watch?v=dH_CHanu6E4)
 
 ## 9. ํ๊ณ  ๋ฐ ๋๋์ 
 - ์ฒ์ ๊ธฐํ์ ํ๋ฉด์, ํ๋ก์ ํธ ๊ธฐ๊ฐ์ ๋ง๊ฒ ๊ธฐํํ๋ ๊ฒ์ ๋ชฉํ๋ก ๊ฐ์ก์ต๋๋ค.
 - ๊ธฐํ์ ์งํํ๋ฉฐ, ๊ธฐํ์ ์ธ์ธํ๊ณ  ํ์คํ๊ฒ ํด์ผํ๋ ๊ฒ์ ๊นจ๋ฌ์์ต๋๋ค.
 - DRF๊ฐ ์ ๋ณด๋ค๋ ์ต์ํด์ ธ ๊ธฐํ ์๋๋๋ก ํ๋ก์ ํธ ์งํ์ ํ  ์ ์์๊ณ , ํ๋ก ํธ ์ฐ๋๊น์ง ์ฑ๊ณตํ  ์ ์์ด ๋ฟ๋ฏํ์ต๋๋ค.
 
 
> [ํ๋ก์ ํธ ๊ฐ๋ฐ ํ๊ณ  ๊ฒ์๋ฌผ](https://velog.io/@marinred/%EB%82%B4%EC%9D%BC%EB%B0%B0%EC%9B%80%EC%BA%A0%ED%94%84-%EC%B5%9C%EC%A2%85%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C-K.P.T)


## 10. ๋ฅ๋ฌ๋ ๋ชจ๋ธ
[style-transfer-pytorch](https://github.com/crowsonkb/style-transfer-pytorch)
