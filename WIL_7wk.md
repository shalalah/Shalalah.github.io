#### Web Sockets
![image](https://user-images.githubusercontent.com/105087933/179432374-04183aa5-d7ac-4d8c-b38f-4113962126e9.png)

#### ๐ผ์๋ฒ์ ํด๋ผ์ด์ธํธ ํต์  ( HTTP์ AJAX ์ฐจ์ด )
- HTTP๋ ํด๋ผ์ด์ธํธ์ชฝ(์น๋ธ๋ผ์ฐ์ )์์ Request๋ฅผ ๋ณด๋ด๊ณ  Server์ชฝ์์ Response๋ฅผ ๋ฐ์ผ๋ฉด ์ด์ด์ก๋ ์ฐ๊ฒฐ์ด ๋๊ธฐ๊ฒ ๋์ด์๋ค. ๊ทธ๋์ ํ๋ฉด์ ๋ด์ฉ์ ๊ฐฑ์ ํ๊ธฐ ์ํด์๋ ๋ค์ Request๋ฅผ ํ๊ณ  Response๋ฅผ ํ๋ฉด์ ํ์ด์ง ์ ์ฒด๋ฅผ ๊ฐฑ์ ํ๊ฒ ๋๋ค.
- AJAX๋ html ํ์ด์ง ์ ์ฒด๊ฐ ์๋ ์ผ๋ถ๋ถ๋ง ๊ฐฑ์ ํ ์ ์๋๋ก XMLHttpRequest๊ฐ์ฒด๋ฅผ ํตํด ์๋ฒ์ request ํ๋ค. XMLHttpRequest๋ ์๋ฒ์์ ์ฐ๊ฒฐ์ ์ก์๋๋ค. Json์ด๋ xmlํํ๋ก ํ์ํ ๋ฐ์ดํฐ๋ง ์ฃผ๊ณ  ๋ฐ์ผ๋ฉฐ DOM์ ๊ฐฑ์ ํ๊ธฐ ๋๋ฌธ์ ๊ทธ๋งํผ์ ์์๊ณผ ์๊ฐ์ ์๋ ์ ์๋ค.

 ##### *HTTP ํ๋กํ ์ฝ* : ํด๋ผ์ด์ธํธ๊ฐ ์๋ฒ์ ์์ฒญ์ ๋ณด๋ด๋ฉด ์๋ฒ๋ ๊ทธ์ ๋ํ ์๋ต์ ๋ณด๋ด๋ ํด๋ผ์ด์ธํธ ์๋ฒ ๊ตฌ์กฐ๋ก ์ด๋ฃจ์ด์ ธ ์๋ค.
  ##### โ ์์ฒญ์ ๋ธ๋ผ์ฐ์  url์์ ์ง์  ์์ฒญ ๊ฐ๋ฅํ๋, ์๋ก๊ณ ์นจ ๋๋ ๋จ์ ์ด ์๋ค.  
       ํด๋ผ์ด์ธํธ โ ๋ฉ์ธ์ง โ> ์๋ฒ๋ฅผ ์์ฒญ(request)์ด๋ผ ํ๊ณ ,  
       ์๋ฒ โ ๋ฉ์ธ์ง โ> ํด๋ผ์ด์ธํธ๋ฅผ ์๋ต(response)๋ผ๊ณ  ํ๋ค.                               
  ###### โ๏ธ ์์ฒญ์ ์ข๋ฅ
        โข GET : ์๋ฃ๋ฅผ ์์ฒญํ  ๋ ์ฌ์ฉ
        โข POST : ์๋ฃ์ ์์ฑ์ ์์ฒญํ  ๋ ์ฌ์ฉ
        โข PUT : ์๋ฃ์ ์์ ์ ์์ฒญํ  ๋ ์ฌ์ฉ
        โข DELETE : ์๋ฃ์ ์ญ์ ๋ฅผ ์์ฒญํ  ๋ ์ฌ์ฉ  
  ###### ๋ฌด์ํ ํ๋กํ ์ฝ(Stateless)  
        http๋ ํ๋ฒ์ request์ response๋ก ์ด๋ฃจ์ด์ ธ ์๊ณ  Back-End๋ ์ด ํ๋ฒ์ ๊ณผ์ ์ด ๋๋๋ฉด User๋ฅผ ์์ด๋ฒ๋ฆฐ๋ค.  
        HTTP -> ์๋ฒ๊ฐ ํด๋ผ์ด์ธํธ์ ์ํ๋ฅผ ๋ณด์กดํ์ง ์๋ ๋ฌด์ํ ํ๋กํ ์ฝ์ด๋ค. ์๋ฒ๊ฐ ํด๋ผ์ด์ธํธ ์ํ๋ฅผ ๋ณด์กดํ์ง ์๋๋ค.  
  
  *โป(http ํต์  ์ฐธ๊ณ ) https://inpa.tistory.com/108*  
  
  ##### *AJAX*: ์๋ฒ์ ๋ฐ์ดํฐ ์์ฒญ ์ ์๋ก๊ณ ์นจ ์์ด ๋ฐ์ดํฐ ์ฃผ๊ณ ๋ฐ์ ์ ์๊ฒ ํ๋ ๋ธ๋ผ์ฐ์  ๊ธฐ๋ฅ์ด๋ค.
  ##### โ ์๋ก์ด ์นํ์ด์ง๋ก ์ด๋ํ๋ ๊ฒ์ด ์๋, ๋์ผํ ์นํ์ด์ง ๋ด์์ DOM์ ๋ณ๊ฒฝํ๊ฒ ๋๋ค.
  
  **Ajax๋ ํด๋ผ์ด์ธํธ์์ ์๋ฒ๋ก๋ฐ์ ์์ฒญ์ ๋ชปํ๋ ๋จ๋ฐฉํฅ ํต์ 
  WebSocket์ ์ด๋ ์ชฝ์์๋  ์์ฒญ์ ๋ณด๋ผ ์ ์๋ ์๋ฐฉํฅ ํต์ **
  
   #### *WebSocket* : ์น ์๋ฒ์ ์น ๋ธ๋ผ์ฐ์ ๊ฐ ์ง์์ ์ผ๋ก ์ฐ๊ฒฐ๋ TCP ๋ผ์ธ์ ํตํด ์ค์๊ฐ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ  ๋ฐ์ ์ ์๋๋ก ํ๋ HTML5์ ์๋ก์ด ์ฌ์์ด๋ค.  
  ##### WebSocket์ ์ด์ฉํ๋ฉด ์ผ๋ฐ์ ์ธ TCP์์ผ๊ณผ ๊ฐ์ดย ์ฐ๊ฒฐ์งํฅ ์๋ฐฉํฅ ์ ์ด์ค ํต์ ์ด ๊ฐ๋ฅํ๋ค.์๋ฒ์๊ฒ ์ฒ์ request๋ฅผ ๋ณด๋ด์ด ์ฐ๊ฒฐํ๋ ์์ฒญ์ ํ๊ณ  ์๋ฒ๋ Acceptํ๊ฒ ๋๋ฉด ์ฐ๊ฒฐ์ด ์ฑ๋ฆฝ(establish)๋๋ค๊ณ  ํ๋ค.
  ##### ์ฐ๊ฒฐ๋ ์ํ์์๋ ์๋ฐฉํฅ ํต์ (br-directional)์ด๊ธฐ ๋๋ฌธ์ ์๋ฒ๋ ์ ์ ๊ฐ ๋๊ตฌ์ธ์ง ์๊ณ  ์๊ณ  ๋จผ์  ํต์ ์ ๋ณด๋ผ ์๋ ์๊ฒ ๋๋ค.  
  ##### โ ํด๋ผ์ด์ธํธ์ ์๋ฒ๊ฐ ์ฐ๊ฒฐ๋์ด ์๊ธฐ ๋๋ฌธ์ ์ค์๊ฐ ํต์ ์ด ๊ฐ๋ฅ(Real Time-Networking)ํ๋ค.   
 
    Real-time web application๊ตฌํ์ ์ํด ๋๋ฆฌ ์ฌ์ฉ๋์ด์ง๊ณ  ์๋ค.  
    ๋ณดํต ์ฑํ์ด๋ LoL๊ฐ์ ๋ฉํฐํ๋ ์ด์ด ๊ฒ์, ๊ตฌ๊ธ Doc, ์ฆ๊ถ ๊ฑฐ๋, ์ค์๊ฐ ์ฃผ์ ์ฐจํธ์ ๊ฐ์ ์ค์๊ฐ์ด ์๊ตฌ๋๋ ์์ฉํ๋ก๊ทธ๋จ์ ๊ฐ๋ฐ์ ํ์ธต ํจ๊ณผ์ ์ผ๋ก ๊ตฌํํ  ์ ์๋ค.
   
