# 3-way Handshake

- TCP 연결을 설정할 때 사용하는 세 단계의 통신 절차. 
- 클라이언트와 서버가 서로 연결을 신뢰성 있게 준비하는 과정.


### 📌 순서 요약
	1.	SYN: 클라이언트 → 서버       : “연결하자!”
	2.	SYN + ACK: 서버 → 클라이언트 : “그래, 나도 준비됐어!”
	3.	ACK: 클라이언트 → 서버       : “좋아, 그럼 시작하자!”


### 📌 플래그 용어 의미
| 플래그     | 의미           | 역할                                |
|------------|----------------|-------------------------------------|
| SYN        | Synchronize    | 연결 시작 요청                      |
| ACK        | Acknowledge    | 응답/확인 표시                      |
| SYN-ACK    | 둘 다 포함     | 요청 수락과 응답을 동시에 전달     |


### 🧭 실제 흐름도
```text
클라이언트                        서버
    | --- SYN(seq=x) -------->   |   → 연결 요청
    |                            |
    | <-- SYN(seq=y), ACK(x+1) --|   → 수락 + 응답
    | --- ACK(y+1) ----------->  |   → 확인 응답
    |                            |
   연결 완료                    연결 완료
```

### SYN과 SCK
- SYN과 ACK는 컴퓨터 네트워크, 특히 TCP (Transmission Control Protocol) 통신에서 사용하는 **제어 플래그(flag)**. 
- 이들은 주로 TCP 연결을 설정하거나 종료할 때 사용됨.


### TCP 연결 설정 과정: 3-way Handshake 
1. 클라이언트 → 서버: SYN
  - 클라이언트가 서버에 “연결을 시작하고 싶어요!“라고 요청함.
  - 이때 SYN (synchronize) 플래그를 설정한 패킷을 보냄.
2. 서버 → 클라이언트: SYN-ACK
  - 서버가 “좋아요, 저도 준비됐어요!“라고 응답함.
  - SYN + ACK (acknowledgment) 플래그를 동시에 설정한 패킷을 보냄.
3. 클라이언트 → 서버: ACK
  - 클라이언트가 “그럼 연결할게요!“라고 마지막 확인을 보냄.
  - ACK 플래그만 설정한 패킷을 보냄.
