# ๐ 43 - Ajax
## Ajax
JS๋ฅผ ์ฌ์ฉํด ์๋ฒ์ ๋น๋๊ธฐ ๋ฐ์ดํฐ๋ฅผ ์์ฒญํ๊ณ  ์์ ํ์ฌ web์ ๋์ ์ผ๋ก ๊ฐฑ์ ํ๋ ํ๋ก๊ทธ๋๋ฐ ๋ฐฉ์

๊ธฐ์กด: ๋ณ๊ฒฝ์ด ํ์ํ  ๋ ์์ ํ html ํ์ผ์ ๋ค์ ์์ฒญํ๋ ๋ฐฉ์
๋ณ๊ฒฝ: ๋ณ๊ฒฝ์ด ํ์ํ ๋ถ๋ถ์ ์ธ ๋ฐ์ดํฐ๋ง ์์ฒญํ ๋ฐ๋ ๋ฐฉ์

## JSON
HTTP ํต์ ์ ์ํ ํ์คํธ ๋ฐ์ดํฐ ํฌ๋งท
- ๊ฐ์ฒด literal๊ณผ ์ ์ฌํ `key`,`value`๋ก ์ด๋ฃจ์ด์ง
- key๋ ""๋ก ๋ฌต์ฌ์ผ ํจ
- ์๋ฒ๋ก ๊ฐ์ฒด ์ ์ก ์ ์ง๋ ฌํ ๊ณผ์ ์ด ํ์์ ์ (JSON.Stringfy)
- ์ญ์ง๋ ฌํ (๋ฌธ์์ด -> ๊ฐ์ฒด) JSON.parse
    
## XMLHttpRequest
`form` , `a` ๋ก HTTP ์์ฒญ ๊ธฐ๋ฅ ์ ๊ณต
Wep API ์ค ํ๋ 

1. HTTP ์์ฒญ ์ด๊ธฐํ
2. (์ ํ)HTTP ์์ฒญ ํค๋๊ฐ ์ค์ 
3. HTTP ์์ฒญ ๋ฉ์๋๋ก ์ ์ก

### HTTP ์์ฒญ ๋ฉ์๋
GET, POST, PUT, PATCH, DELETE
GET: ์ฟผ๋ฆฌ ๋ฌธ์์ด๋ก ์ ์ก (`body`=null)
POST: ๋ฐ์ดํฐ`payload`๋ฅผ `body`๋ก ์ ์ก 

### Content-type
MIME ํ์์ ์ ๋ณด ํํ
text, application, multipart
