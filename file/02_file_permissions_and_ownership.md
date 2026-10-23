# 파일 허가권과 소유권 (File Permissions and Ownership)

## 파일 정보 확인

`ls -l` 명령어를 사용하면 파일의 허가권, 소유자, 그룹 등의 정보를 확인할 수 있다.

### 예시

```text
-rw-r--r-- 1 root root 0 Jul 11 11:06 sample.txt
```

| 항목 | 설명 |
|------|------|
| `-` | 파일 유형 |
| `rw-r--r--` | 파일 허가권(Permission) |
| `1` | 하드 링크 수 |
| `root` | 파일 소유자(User) |
| `root` | 파일 소유 그룹(Group) |
| `0` | 파일 크기(Byte) |
| `Jul 11 11:06` | 마지막 수정 시간 |
| `sample.txt` | 파일 이름 |

---

# 파일 유형

| 기호 | 의미 |
|------|------|
| `-` | 일반 파일 |
| `d` | 디렉터리 |
| `l` | 심볼릭 링크 |

---

# 파일 허가권 (Permission)

파일 허가권은 **3개씩 끊어서 읽는다.**

예시

```text
rw- r-- r--
```

| 권한 | 의미 | 값 |
|------|------|----|
| `r` | Read (읽기) | 4 |
| `w` | Write (쓰기) | 2 |
| `x` | Execute (실행) | 1 |
| `-` | 권한 없음 | 0 |

---

## 허가권 구성

| 권한 | 대상 |
|------|------|
| `rw-` | 소유자(User) 권한 |
| `r--` | 그룹(Group) 권한 |
| `r--` | 기타 사용자(Other) 권한 |

예를 들어

```text
755
```

은

```text
rwx r-x r-x
```

를 의미한다.

---

# 파일 허가권 및 소유권 변경 명령어

| 명령어 | 설명 |
|--------|------|
| `chmod` | 파일 허가권 변경 |
| `chown` | 파일 소유자 변경 |
| `chgrp` | 파일 소유 그룹 변경 |

---

## 사용 예시

```bash
chmod 777 sample.txt

chown ubuntu:ubuntu sample.txt

chgrp ubuntu sample.txt
```

---

# 실습

## 1. 파일 생성

```bash
nano test_file
```

파일 내용을 입력한다.

```text
안녕하세요
```

---

## 2. 파일 정보 확인

```bash
ls -l test_file
```

---

## 3. 현재 사용자 확인

```bash
whoami
```

---

## 4. 실행 권한 확인

```bash
./test_file
```

실행 권한이 없으면 실행되지 않는다.

---

## 5. 실행 권한 추가

```bash
chmod 777 test_file
```

권한 변경 후 다시 확인한다.

```bash
ls -l test_file

./test_file
```

---

## 6. 화면 정리

```bash
clear
```

---

## 7. 파일 소유자 변경

```bash
chown ubuntu test_file

ls -l test_file
```

---

## 8. 파일 그룹 변경

```bash
chgrp ubuntu test_file

ls -l test_file
```

---

## 9. 사용자 변경

```bash
su - ubuntu

whoami

pwd
```

---

## 10. 접근 권한 확인

```bash
ls -l /root/test_file

ls -ld /root
```

루트 디렉터리의 권한 때문에 일반 사용자는 파일에 접근할 수 없다.

---

## 11. root 사용자로 복귀

```bash
exit
```

---

## 12. 파일 이동

```bash
ls -l

mv test_file ~ubuntu
```

---

## 13. ubuntu 사용자로 로그인

```bash
su - ubuntu
```

파일 확인

```bash
ls -l test_file
```

---

## 14. 소유권 변경 시도

```bash
chown root:root test_file
```

일반 사용자는 다른 사용자의 파일 소유권을 변경할 수 없으며, 일반적으로 root 권한이 필요하다.

---

# 핵심 정리

- `ls -l` 명령으로 파일의 허가권과 소유자를 확인할 수 있다.
- 파일 허가권은 **소유자(User), 그룹(Group), 기타 사용자(Other)** 순서로 표시된다.
- 권한 값은 **r=4, w=2, x=1**이다.
- `chmod`는 파일 허가권을 변경한다.
- `chown`은 파일 소유자를 변경한다.
- `chgrp`는 파일 소유 그룹을 변경한다.
- 파일의 소유권 변경은 일반적으로 root 권한이 필요하다.