# TCP

> **완벽한 보안과 안정성을 갖춘 프로토콜**

OSI 계층의 전송 계층에 해당되는 프로토콜로, TCP/IP라는 명칭으로도 불린다.

## 역할

- #### 호스트가 연결 가능한 상태인지 확인 및 연결 수립
- #### 전송을 제어하는 정보를 패킷에 추가해주는 역할

## 3-Way Handshake

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNHdDC%2Fbtq4qzFhnaG%2FpVZVWLM8S7ROCZvhaaiBDk%2Fimg.png)
노드의 활성 상태를 확인하기 위해 3-Way Handshake를 통해 노드와 통신한다.

총 세 단게로 SYN, SYN-ACK, ACK 단계로 나뉜다.

### SYN

어플리케이션이 서버에 통신을 위한 연결을 요청하는 단계이다.

### SYN-ACK

서버가 어플리케이션에 자신이 활성 상태임을 알리고 어플리케이션에서도 포트를 열어 연결을 활성화하라는 요청 메세지를 전송한다.

### ACK

어플리케이션이 서버의 요청 메세지를 수락하여 연결이 수립된다.
