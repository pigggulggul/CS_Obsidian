##### URL
브라우저에는 여러 기능이 있고 그에따라 URL도 여러 종류가 있다.
URL은 http: file: matilto: 등등 여러가지가 있다. 결국 브라우저는 몇 개의 클라이언트 기능을 겸비한 복합적인 클라이언트 소프트웨어. 
액세스 대상이 웹 서버라면 HTTP 프로토콜을 사용하고 FTP 서버라면 FTP 프로토콜을 사용한다.
www . naver . com/ 의 경우 네이버 아래의 / 디렉토리가 지정되고 파일명은 생략. 이 때는 보통 index.html이나 default.html.
www . naver . com인 경우 루트 디렉토리의 아래에 있는 미리 설정된 파일을 (보통 index, default)를 엑세스. 하위 주소가 파일로 존재하면 하위 주소를 파일명으로 보고. 하위 주소가 디렉토리로 존재하면 하위 주소를 디렉토리명으로 본다.
##### URI
HTTP 프로토콜은 서버가 주고받는 메시지의 내용, 순서를 정하지만 쉽게 생각해서 "무엇을, 어떻게 해서" 하겠다는 내용이 쓰여있음. "무엇을"에 해당하는것이 URI고 보통 파일 이름이나 CGI 프로그램(웹 서버 소프트웨어에서 프로그램을 호출 할 때 규칙을 정한 것.)의 파일 명이다. 'dir1/file.html', 'dir1/program1.cgi' 등. 또한 URL을 그대로 쓸 수 있음. "어떻게 해서"는 메소드로 URI로 나타낸 데이터를 읽고싶다, URI로 나타낸 프로그램에 전달하고 싶다는 식의 동작이 대표적.

#### HTTP 프로토콜
HTTP은 HyperText Transfer Protocol이다.
HTTP의 속성으로는 GET __ __ /index.html
이것 말고도 HTTP 프로토콜 상의 메소드는 PUST, POST, DELETE 등이 있다.
우리는 이것들을 주고 받으면서 인터넷을 사용한다.
html은 hyper text markup language. 하이퍼텍스트를 표현하기 위한 언어.
html 파일을 주고 받을 수 있는 파일.

##### HTTPS 프로토콜
HTTP에 SSL(Secure Socket Layer)보안 장치를 이용하여 보안을 강화한 것. HTTP를 통하여 데이터를 전송하거나 전송될 때 제 3자가 감청하고 조작하거나 속일 수 있다. 이런것을 방지하기 위하여 보안적인 약점을 막고 보강한 것이다. HTTPS를 이용하면 통신하는 데이터들이 암호화되기 때문에 상대가 몰래 도청 할 수 없다. 
기본 화면은 https가 없다가도 로그인 페이지로 가면 https로 프로토콜이 변경된다. 아이디와 비밀번호를 입력 할 때 아이디와 비밀번호는 매우 중요한 정보이기 때문이다. 여기서 아이디와 패스워드를 입력하고 로그인을 하면 서버로 https 프로토콜로 암호화된 데이터가 보내지기 때문에 그 정보는 제3자에 의해서 변조되거나 감청 될 수 없다. 

##### HTTPS와 SSL
SSL(더 포괄적) 위에서 HTTPS가 동작한다. HTTP가 SSL을 이용하면 HTTPS가 되는것이다. SSL은 전송계층과 응용 계층 사이에 있는 독립적인 프로토콜이다. 

[[SSL]] 

#### url, uri
url에서 l은 locator. 인터넷 주소를 말함.
uri에서 i는 identifier 그 주소의 끝에 .png, .html같은 리소스를 식별하는 것. 
http:// 주소를 치면 찾아가는데 이 주소를 url이라고 한다.

#### RESTful
Rest 방식
Representational State Transfer :  표현 상태 전송. 상태의 표현을 전송한다.
DB의 데이터들이 CRUD로 App에서 하는데 웹 상에서도 통신을 통해서 url 적으로 처리를 해주기 위해 리소스를 제어하는 것. 
REST를 구성한다 : Client와 Server에서 리소스를 GET, PUT, POST 할 수 있도록 제어하는 API인 RestfulAPI를 구성한다.

[[DNS]] [[SSL]]