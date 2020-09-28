# HTTP



HTTP란 웹 표준데이터를 받아오는데 사용하는 프로토콜이다. (웹표준데이터란 HTML, CSS, JAVASCRIPT 등을 말한다.)

현재는 웹표준데이터 뿐만 아니라 이미미, 동영상 파일도 같이 받아온다.

특징은 ***요청*** - ***응답*** 으로 이루어졌다는 점.

클라이언트가 서버에 ***요청***하면 서버는 그에 대한 ***응답***을 준다.

## HTTP의 응답 프로토콜

HTTP의 응답프로토콜은 아래처럼 이루어져 있다.

| http 응답 프로토콜 계층구도 |                   |
| --------------------------- | ----------------- |
| RequestLine                 | 요청타입 + URI 등 |
| Headers                     |                   |
| 공백                        |                   |
| BODY                        |                   |



### RequestLine

[http/1.1:request](https://www.w3.org/Protocols/rfc2616/rfc2616-sec5.html)

리퀘스트라인에는 ``` GET/naver/com~~~ HTTP/1.1```  과 같은 메시지가 적힌다.

- `요청타입 | 공백 | URI | 공백 | HTTP버전`

- 첫 번째 GET은 요청타입이다. 이 요청타입의 종류는 많지만 대부분 쓰이지 않고 ```POST``` ```GET``` 이 두가지가 주로 쓰인다.
  - GET: 클라이언트가 서버로부터 문서를 읽어오려할 때 사용한다. 하지만 요청하는 동시에 데이터를 전송할 수 있다.
  - POST: 클라이언트가 서버로 데이터를 전송할 떄 주로 사용된다. 하지만 데이터를 요청할 때도 사용할 수 있다.
  - 즉, POST, GET 모두 데이터를 전송하고 요청할 수 있다. 그렇다면 차이가 무엇이냐?
    - `GET`은 데이터를 전송할 때 ```URI``` 에 붙여서 전송한다! 즉 우리가 전송하는 데이터가 URL에 모두 보인다는 것. 따라서 보안상에  큰 에러가 있다. 만약 우리가 네이버 웹툰을 본다고 생각해보자. 웹툰 목록에 들어가면 요일별로 많은 웹툰이 있는데 여기서 ```목요일``` 버튼을 누르면 우리는 서버에게 목요일 웹툰 페이지를 요청한다. 이 요청을 할 때 요청이라는 데이터를 전송하는데 이게 ```URL```을 베이스로 하게된다. 즉, 우리가 목요일 웹툰을 누르고 주소창을 보면 ``~~~/thu/~~~`` 라는 문구를 볼 수 있는데 이게 바로 우리가 `GET`로 전송한 데이터.
    - `POST`는 이와 다르게 전송되는 데이터가 패킷에 숨겨져서 보내진다.  따라서 보안적인 측면에서는 `GET`보다는 훨씬 낫다. 하지만 요즘에는 이 방법도 완벽한 보안이 안돼서 `SSL` 방식도 사용함.

- `URI (Uniform Resource Identifier)`

  - URI는 주소창에 있는 문자열 전체를 의미한다. URL과 다르다!
  - ***실제 의미는 인터넷 상에서 특정한 자원을 나타내는 유일한 주소다.***
  - 우리가 받고 싶어하는 HTML, 이미지, 영상등은 서버에 저장이 되어있다. 그걸 나타내는 주소라고 생각하면 된다. 굉장히 복잡한 주소로 이루어짐.
  - `scheme ://host[:port][/path][?query]`
    - `ftp ://IP주소 :포트 /파일이름`
    - `http ://IP주소 :포트 /폴더이름/파일이름`
    - `scheme`: 내가 요청하는 요청 형식. 보통 7계층 프로토톨
    - `IP주소, 포트번호` : 보통 여기에 도메인 주소를 씀. 하지만 내부적으로는 도메인주소를 IP주소로 바꿔준다. 포트번호는 지정하지 않으면 자동으로 `80` 또는 `443`을 웹브라우저가 자동으로 사용함.
    - `/파일이름, /폴더이름/파일이름`: 내가 원하는 특정 파일이 서버에 위치한 곳.

  - `https://comic.naver.com/webtoon/detail.nhn` 이라는 주소가 있으면 
    - `https: scheme`
    - `comic.naver.com` -> 도메인주소 = IP주소
    - `포트번호`는 생략
    - `webtoon` 폴더이름
    - `detail.nhn` 파일이름