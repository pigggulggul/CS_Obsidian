#### ARP가 하는 일
옆 사람과 통신 할 때는 IP를 주소를 이용하여 통신한다. 실제로는 같은 네트워크 상에선 Ethernet 프로토콜 (MAC 주소)를 이용하여 통신한다. 그래서 IP 주소를 입력했을때 컴퓨터들끼리 상대방의 MAC 주소를 알아보게 되는데 이 때 ARP 프로토콜을 이용하여 상대방의 MAC주소를 알아온다. 그래서 IP주소만 입력하더라도 컴퓨터가 자동으로 상대방의 MAC주소를 알아와서 통신한다. ARP 프로토콜은 우리가 직접 무언가를 하지 않지만 컴퓨터에선 계속 사용한다. 

##### IP주소를 이용해 MAC주소를 알아오는 ARP 프로토콜.
![![Network/#^Table1]]
Hardware type : 2계층에서 사용하는 프로토콜 타입 (웬만하면 Ethernet 프로토콜만 옴)
Protocol type : 현재 계층에서 사용하는 프로토콜 어드레스 타입 (IPv4)
Opcode : 작동코드. 어떻게 동작하는지 나타내는 코드. (ARP 프로토콜로 상대방에게 MAC주소를 요청(1)을 하는지 응답(2)하는지로 나뉨.)
Source Hardware Address : 출발지에 물리적인 주소 (MAC주소 6바이트)
Source Protocol Address :  출발지 IP주소 (IPv4 4바이트)
Destination Hardware Address : 목적지에 물리적인 주소 (MAC주소 6바이트)
Destination Protocol Address : 목적지 IP주소 (IPv4 4바이트)

> [!NOTE]
> 보통은 Hardware type은 Ethernet 프로토콜만. Protocol Type은 IPv4만 오기 때문에 

Ethernet 프로토콜의 경우 특이하게 먼저 오는게 목적지의 MAC 주소인데 나머지 프로토콜은 출발지가 먼저 온다.
#### ARP 프로토콜의 구조

#### 통신 과정

ARP 테이블
