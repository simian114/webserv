#  HTTP헤더

- 헤더는 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송할 수 있도록 해준다.
- HTTP 헤더는 대소문자를 구분하지 않는 이름과 콜론 '`:`'  다음에 오는 값으로 이루어져 있다.
- 값 앞에 붙은 빈 문자열은 무시된다.

-----

## 서브젝트에서 요구하는 헤더

#### [`일반 헤더`](https://developer.mozilla.org/ko/docs/Glossary/General_header)

> 요청과 응답 모두에서 사용되지만 컨텐트 자체에는 적용되지 않는 헤더.
>
> 일반 헤더는 응답 또는 요청 헤더다(?) 엔티티 헤더가 될 수는 없다.

- [Date](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Date)
  - 메시지가 만들어진 날짜와 시간을 포함한다.
- [Transfer-Encoding](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Transfer-Encoding)
  - 사용자에게 [entity](https://developer.mozilla.org/ko/docs/Glossary/Entity_header)를 안전하게 전송하기 위해 사용하는 인코딩 형식을 지정한다.

-----


#### [`엔티티 헤더`](https://developer.mozilla.org/ko/docs/Glossary/Entity_header)

> 메시지 **바디 컨텐츠**를 나타내는 HTTP헤더이다. 엔티티 헤더는 **<u>*HTTP 요청 및 응답 모두*</u>**에서 사용이 된다. 

##### 응답 컨텍스트

- [Allow](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Allow)
  - 리소스가 지원하는 메소드 집합을 나열한다.
  - 어떤 요청 메소드를 사용할 수 있는지 알리기 위해 서버가 [405](https://developer.mozilla.org/ko/docs/Web/HTTP/Status/405) `Method Not Allowed` 상태코드로 응답할 경우에 이 헤더를 반드시 보내야한다. 비어있는 `Allow` 헤더는 리소스가 어떤 요청 메소드도 허용하지 않음을 나타낸다. 예를 들어, 특정 리소스에 대해 일시적으로 발생할 수도 있는 요청 메소드조차 허용하지 않음을 나타낸다.

##### 컨텐츠 헤더

- [`Content-Language`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Content-Language)
  - 해당 개체와 가장 잘 어울리는 사용자 언어.
  - 청중을 위한 언어를 설명하기 위해 사용되는데, 사용자가 선호하는 언어에 따라 사용자를 구분하도록 해준다.
  - 잘 모르겠다... 계속 알아보자.
- [`Content-Length`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Content-Length)
  - 수신자에게 보내지는, 바이트 단위를 가지는 개체 본문의 크기를 나타낸다.

- [`Content-Location`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Content-Location)
  - 반환된 데이터에 대한 대체 위치를 가리킨다. 주되 사용 케이스는 [`컨텐츠 협상`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation) 의 결과로써 전달되는 리소스의 URL을 가리키는 것.
  - [`Location`]() 이 `Page Redirection` 이라면 `Content-Location` 은 리소스 위치가 변경되었을 경우에 대한 `Entity Redirection` 이다.
  - 해당 개체의 실제 위치를 알려준다.

- [`Content-Type`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Content-Type)
  - 리소스의 [`media type`](https://developer.mozilla.org/ko/docs/Glossary/MIME_type)을 나타내기 위해 사용된다
  - 응답 내에 있는 `Content-Type` 헤더는 클라이언트에게 반환된 컨텐츠의 유형이 실제로 무엇인지를 알려준다.


-----

#### [`요청 헤더`](https://developer.mozilla.org/ko/docs/Glossary/Request_header)

> HTTP 요청에서 사용되지만 메시지의 컨텐츠와는 관련이 없는 헤더다.

##### 요청 컨텍스트

- [`Host`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Host)
  - (가상 호스팅을 위해) 서버의 도메인명과 서버가 리스닝하는 (부가적인) TCP 포트를 특정한다.
  - 포트가 주어지지 않으면, 요청된 서버의 기본 포트를 의미한다.
  - `Host` 헤더의 필드는 모든 `HTTP/1.1` 요청 메시지 내에 포함되어 전송되어야 한다. `Host` 헤더 필드가 없거나 한 개 이상의 필드를 포함하는 `HTTP/1.1` 요청 메시지에 대해서는 [`400`](https://developer.mozilla.org/ko/docs/Web/HTTP/Status/400) (Bad Request) 상태 코드가 전송 된다.
- [`Referer`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Host)
  - 현재 페이지로 연결되는 링크가 있던 이전 웹 페이지의 주소다.
  - 사람들이 어디로부터 와서 방문 중인지를 인식할 수 있도록 해준다.
  - 해당 데이터는 분석, 로깅, 혹은 캐싱 최적화에 사용될 수 있다.

- [`User-Agent`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/User-Agent)
  - 클라이언트의 소프트웨어(브라우저, OS) 명칭 및 버전 정보

##### [컨텐츠 협상](https://developer.mozilla.org/ko/docs/Web/HTTP/Content_negotiation)

- [`Accept-Charset`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Accept-Charset)
  - 클라이언트가 이해할 수 있는 캐릭터셋이 무엇인지를 알려준다.
  - [`컨텐츠 협상`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation) 을 사용하여, 서버는 제안된 것 중 하나를 선택하고 사용하며 [`Content-Type`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Content-Type) 응답 헤더를 통해 서택된 캐릭터셋을 클라이언트에게 알려준다.

- [`Accept-Language`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Accept-Language)
  - 어떤 언어를 클랑언트가 이해할 수 있는지, 그리고 지역 설정 중 어떤 것이 더 선호되는지를 알려준다.

##### 보안 헤더

- [`Authorization`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Authorization)
  - 인증토큰을 서버로 보낼 때 사용하는 헤더.
  - `토큰의 종류 + 실제 토큰 문자` 를 전송
  - 서버의 사용자 에이전트임을 증명하는 자격을 포함하여, 보통 서버에서 `401` `unautorized` 상태를 [`www-Authenticate`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/WWW-Authenticate) 헤더로 알려준 이후에 나온다.


-----

#### [`응답 헤더`](https://developer.mozilla.org/ko/docs/Glossary/Request_header)

> 위치 또는 서버 자체에 대한 정보와 같이 응답에 대한 부가적인 정보를 갖는 헤더다.

##### 응답 컨텍스트

- [`Server`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Server)
  - 요청을 처리하는 서버의 이름과 버전을 표시한다.
  - 너무 길고 상세한 서버의 정보는 공격을 받을 수 있기 때문에 피해야 한다.

##### 리다이렉트

- [`Location`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Location)
  - 리다이렉트 될 `URL` 을 나타낸다.
  - `3xx (redirection)` 또는 `201 (created)` 응답일 때 어느 페이지로 이동할지를 알려준다.
    - 새로 생성된 리소스의 경우 `201 Created` 가 반환된다.
    - `HTTP/1.1 302 Found Location: /xxx` 이런 응답이 왔다면 브라우저는 `/xxx` 주소로 리다이렉트 된다.

##### 보안 헤더

- [`WWW-Authenticate`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/WWW-Authenticate)

  - 서버가 클라이언트를 인증볻는 과정에 사용하는 방법.

  - [`401`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/401) `Unauthorized` 와 같이 보내진다.

##### 조건부

- [`Last-Modified`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Last-Modified)
  - 가장 마지막 수정된 날짜와 시각을 담고 있다. 
  - 캐싱을 위한 정보다.
  - 저장된 리소스가 이전과 같은지 유혀성 검사자로 사용된다.

##### 그 외

- [`Retry-After`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Retry-After)
  - 다음에 올 요청이 이루어지기 전에 사용자 에이전트가 대기해야 하는 시간을 가르킨다.
  - 현재 서버가 정상적인 응답이 어려울 때 정상적인 접속이 가능한 시각을 전달한다. 세 가지 경우에서 주로 사용된다.
    - 유지보수나 과부하로 인한 중단(`503 Service Unavailable`) ->`Date` 형식으로 정상적인 서비스가 가능해지는 시각을 전달한다.
    - `429(Too Many Requests)나 301(Moved Permanently)` 에서는 클라이언트가 기다려야 할 최소한의 시간을 음수가 아닌 초의 값으로 전달한다.



## 참고 사이트

- [`MDN`](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers)
- [`블로그`](https://gmlwjd9405.github.io/2019/01/28/http-header-types.html)
- [`GIT`](https://github.com/eunhyulkim/webserv/wiki/D.-HTTP-Headers)
