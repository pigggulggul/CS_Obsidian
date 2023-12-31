
#### DNS
문자열로 된 도메인 이름에서 IP주소로 정보를 알려주는 전화번호를 함.
www,naver.com이라는 이름을 가진 주소가 있다.
www : Host name
naver : www는 naver에 속한다
com : naver는 com에 속한다.
naver.com이라는 도메인이라 한다.

##### 도메인 사용 이유
숫자는 외우기 힘드므로 사람이 좋은 이름을 사용한다. 실제 접속은 IP주소로 해야하기 때문에 IP로 바꿔야한다.

##### 주소창에 도메인 주소를 쳤을 때 발생 순서.
1. PC에서 DNS에게 물어보기 전에 자기 PC메모리의 DNS 캐쉬를 뒤진다. 없으면 hosts file을 뒤진다.
2. 없으면 DNS에게 물어본다
3. 이 과정에서 대부분 공유기를 사용한다. 공유기는 DNS 포워딩 기능을 제공하여 자기가 응답을 대신 해주기도한다. 공유기가 응답하지 않으면 인터넷 서비스(KT 등)이 제공하는 DNS가 응답해준다.
4. 한 번 물어보면 DNS 캐쉬에 저장하여 자기가 캐쉬를보고 네이버에 접속을 한다.
5. 만약에 DNS가 도메인 주소를 알면 바로 응답하지만 모르면 또 다른 DNS(root dns)에게 물어보고 Root DNS는 \*.com으로 되어있는 DNS 목록을 알려준다. 처음에는 .jr, .jp, .cn, .net, .com, .biz 등등 여러가지 최상위 도메인 중 .com에게 naver를 묻고 .co, .go, .or, (domain.kr 등 희망문자열)등에서 naver가 있으면 naver에게 www가 있는지 묻는다. 그 후에 있으면 IP주소를 알려주고 PC에게 전달한다.
6. 모든 응답에는 유효기간이 있어 유효기간이 지나면 다시 물어야한다.


![](https://i.imgur.com/gOURpLY.jpg)

