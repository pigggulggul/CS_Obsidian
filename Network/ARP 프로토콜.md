#### ARP가 하는 일
옆 사람과 통신 할 때는 IP를 주소를 이용하여 통신한다. 실제로는 같은 네트워크 상에선 Ethernet 프로토콜 (MAC 주소)를 이용하여 통신한다. 그래서 IP 주소를 입력했을때 컴퓨터들끼리 상대방의 MAC 주소를 알아보게 되는데 이 때 ARP 프로토콜을 이용하여 상대방의 MAC주소를 알아온다. 그래서 IP주소만 입력하더라도 컴퓨터가 자동으로 상대방의 MAC주소를 알아와서 통신한다. ARP 프로토콜은 우리가 직접 무언가를 하지 않지만 컴퓨터에선 계속 사용한다. 

##### IP주소를 이용해 MAC주소를 알아오는 ARP 프로토콜.
|             |                                      |                               |                                          |     |
| ----------- | ------------------------------------ |:----------------------------- | ---------------------------------------- | --- |
| Byte Offset | 0                                    | 1                             | 2                                        | 3   |
| 0           | Hardware type (0 0 0 1)              | Protocol type (0 8 0 0)       | -                                        | -   |
| 4           | Hardware Address Length (0 6)        | Protocol Address Length (0 4) | Opcode (0 0 0 x)                         | -   |
| 8           | Source Hardware Address( Continued ) | -                             | -                                        | -   |
| 12          | Source Hardware Address              | -                             | Source Protocol Address (Continued)      | -   |
| 16          | Source Protocol Address              | -                             | Destination Hardware Address (Continued) | -   |
| 20          | Destination Hardware Address         | -                             | -                                        | -   |
| 24          | Destination Protocol Address         | -                             | -                                        | -   |

Hardware type : 2계층에서 사용하는 프로토콜 타입 (웬만하면 Ethernet 프로토콜만 옴)
Protocol type : 현재 계층에서 사용하는 프로토콜 어드레스 타입 (IPv4)
Opcode : 작동코드. 어떻게 동작하는지 나타내는 코드. (ARP 프로토콜로 상대방에게 MAC주소를 요청(1)을 하는지 응답(2)하는지로 나뉨.)
Source Hardware Address : 출발지에 물리적인 주소 (MAC주소 6바이트)
Source Protocol Address :  출발지 IP주소 (IPv4 4바이트)
Destination Hardware Address : 목적지에 물리적인 주소 (MAC주소 6바이트)
Destination Protocol Address : 목적지 IP주소 (IPv4 4바이트)

> [!NOTE]
> 보통은 Hardware type은 Ethernet 프로토콜만. Protocol Type은 IPv4만 오기 때문에 0바이트부터 7바이트까지의 값은 고정이다.

Ethernet 프로토콜의 경우 특이하게 먼저 오는게 목적지의 MAC 주소인데 나머지 프로토콜은 출발지가 먼저 온다.
#### ARP 프로토콜의 구조

#### 통신 과정

|       |        |       |
| ----- | ------ | ----- |
|       | 공유기 |       |
| Com A | 스위치 | Com C |
|       | Com B  |       |


- 하나의 네트워크 대역(같은 LAN 대역)에서 ARP 프로토콜로 상대방의 MAC주소를 알아 올 때 (Com A -> Com C)
A 컴퓨터가 ARP 요청을 프로토콜을 캡슐화하여 보낸다. ARP 프로토콜은 3계층이므로 2계층인 Ethernet 프로토콜을 붙인다. 하지만 Ethernet 프로토콜은 목적지 MAC주소가 필요하다. 그래서 ARP 요청 프로토콜을 만들 때 목적지 MAC 주소를 00 00 00 00으로 적고 보낸다. 이제 Ethernet 프로토콜을 캡슐화를 할 때 목적지의 맥 주소를 모르기 때문에 FF FF FF FF FF FF로 작성한다. 이렇게 뒤에 부분을 1로 가득 채우면 broadcast 주소가 되기 때문에 프로토콜을 같은 대역의 모두에게 보낸다. 그럼 스위치는 2계층 장비기 때문에 2계층 프로토콜 까지만 확인한다. 2계층까지 decapsulation을 하니까 ARP는 안 까고 모두에게 보낸다. 받은 기기들은 다시 decapsulation을 하여 2계층을 까고 3계층도 깐다. 목적지 IP 주소가 일치하지 않는 애들은 패킷을 버리고 일치하는 애는 응답 프로토콜을 만들어서 보낸다.  응답을 보낼 때는 이미 받는 사람의 MAC주소와 IP주소를 아니까 바로 보낸다.

#### ARP (캐시) 테이블
통신 했던 컴퓨터들의 주소는 ARP 테이블에 남는다.

#### ARP의 사용위치
ARP 프로토콜은 3계층인데 같은 네트워크 대역에서만 쓰인다. MAC 주소를 몰라서 Ethernet으로 브로드캐스트를 하는건데 3계층 장비는 broadcast가 오면 Internet 세상으로 보내지 않고 버린다.

[[3계층 데이터링크]]
