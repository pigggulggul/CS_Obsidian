- 프로그램이 네트워크에서 데이터를 주고받을 수 있도록 네트워크 환경에 연결할 수 있게 만들어진 연결부
- 소켓은 파일이다. 소켓은 OS 커널에 구현되어 있는 프로토콜 요소에 대한 추상화된 인터페이스.
- 장치 파일의 일종
- 일반 파일에 대한 개념
- 파일을 깠을때 블루투스면 블루투스 소켓, IRDA면 IRDA 소켓
- 파일 입출력 행위의 주체 : Process. 대상체 파일이 TCP 스택에 대한 추상화된 인터페이스를 제공하면 파일을 파일이라 하지 않고 TCP 소켓이라 한다. 파일에 대한 또다른 이름이 TCP 소켓

#### TCP 소켓
소켓도 파일이랑 똑같다. 소켓 함수로 파일열기(R,W,X), 파일닫기. TCP 프로토콜의 특징으로 특정 함수로 부르지만 그거 말고는 똑같다. 다시 한 번 소켓은 파일이다.

User mode에서 Kerner mode로 바뀌면 데이터 단위가 바뀌는데 L4: Segment, L3: Packet이다. 세그먼트나 ,패킷단위로 데이터가 잘라져서 나가는데
직소퍼즐 하나가 세그먼트, 패킷 하나라고 생각하면 된다. 직소 퍼즐이 연속되어서 쭉 이어져있으면 이것을 스트림이라고 한다. Stream은 기본적으로 조립이 되어서 연속돼서 한 줄로 이어진거고 패킷은 조각난 단편 하나이다. 길쭉한 데이터를 일정 단위로 자르는 것을 세그멘테이션이라고 하고 잘려진 조각 하나를 세그먼트라고한다. 세그먼트를 인터넷이라는 네트워크에서 유통 가능한 형태로 만들기 위해 뽁뽁이로 싸서 택배박스에 담아서 배송을 가능하게 하는 것이 패킷. 소켓 파일의 경우 파일의 크기는 Stream이라고 본다. Stream은 시작이 있고 언제 끝날지 모른다. TCP에서 다루는 데이터의 단위는 Segment, IP는 Packet, NIC는 Frame.

![](https://i.imgur.com/j052nEG.png)


어플리케이션 프로세스가 파일에 대고 스트림 데이터를 write한다. 네트워크로 보낼때는 커널로 내려가서 TCP를 만나면 Stream 데이터가 Segment화된다 (세그멘테이션). 분해(자르기)라고 이해하면 쉽다. Segment를 인터넷 환경에서 전송 가능한 형태로 포장한 것을 Pack이라한다. 패킷의 길이의 최대 크기(MTU)는 1500bytes. Segment의 길이의 최대 길이는 MSS (Maximum Segment Size). 이것은 패킷의 최대 크기에 영향을 받는다.(MTU). MSS는 MTU보다 더 작다. Pack을 실어 넣을때는 Frame데이터에 넣는다.

![](https://i.imgur.com/Xww4zBd.png)

