# DNS와 네임 서버

## DNS란?

- Domain Name System
- 도메인 주소를 IP 주소로 변환하는 시스템
- 인터넷의 전화번호부 역할을 한다.

---

## 도메인 (Domain)

- IP 주소를 사람이 기억하기 쉽게 만든 이름

### 예시

```text
www.naver.com
www.google.com
```
---

## Hosts 파일

- 도메인과 IP 주소를 저장하는 파일
- DNS 서버보다 먼저 확인한다.

### 예시

```text
127.0.0.1 localhost
```

---

## 네임 서버 (Name Server)

- DNS 기능을 수행하는 서버
- 도메인에 대한 IP 주소를 찾아준다.

---

## DNS 캐시

- 한번 조회한 IP 주소를 임시 저장하는 공간
- 같은 사이트에 다시 접속할 때 조회 속도를 높여준다.

---

# DNS 조회 과정

1. 사용자가 www.naver.com 입력
2. Hosts 파일 확인
3. DNS 캐시 확인
4. DNS 서버에 묻기
5. 루트 서버 조회
6. .com 서버 조회
7. naver.com 서버 조회
8. IP 주소 획득
9. 웹 서버 접속

---

# 핵심 정리

- DNS = 도메인을 IP 주소로 변환하는 시스템
- Hosts 파일을 먼저 확인한다.
- DNS 는 트리구조로 동작한다.
- 조회 결과는 캐시에 저장된다.