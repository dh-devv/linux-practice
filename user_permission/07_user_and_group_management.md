# 사용자와 그룹 관리 (User and Group Management)

## 사용자와 그룹이란?

리눅스는 **다중 사용자(Multi User) 운영체제**로, 여러 사용자가 하나의 시스템을 함께 사용할 수 있다.

모든 사용자는 **하나 이상의 그룹(Group)** 에 소속되며, 사용자와 그룹을 이용하여 파일 및 시스템의 접근 권한을 관리한다.

---

# 사용자 관련 파일

## `/etc/passwd`

사용자의 기본 정보가 저장되는 파일이다.

### 저장 정보 예시

```text
ubuntu:x:1000:1000:ubuntu:/home/ubuntu:/bin/bash
```

| 항목 | 설명 |
|------|------|
| 사용자 이름 | ubuntu |
| 비밀번호 | x (실제 비밀번호는 `/etc/shadow`에 저장) |
| UID | 사용자 ID |
| GID | 기본 그룹 ID |
| 홈 디렉터리 | `/home/ubuntu` |
| 기본 셸 | `/bin/bash` |

---

## `/etc/shadow`

사용자의 **암호화된 비밀번호**와 비밀번호 정책이 저장되는 파일이다.

일반 사용자는 내용을 확인할 수 없으며, 관리자(root)만 접근할 수 있다.

---

## `/etc/group`

시스템에 존재하는 그룹 정보가 저장되는 파일이다.

그룹 이름, 그룹 ID(GID), 그룹에 속한 사용자 정보를 확인할 수 있다.

---

# 사용자 관리 명령어

| 명령어 | 설명 |
|--------|------|
| `adduser` | 새로운 사용자 생성 |
| `passwd` | 사용자 비밀번호 설정 및 변경 |
| `usermod` | 사용자 정보 변경 |
| `userdel` | 사용자 삭제 |

---

## 사용자 생성 옵션

| 옵션 | 설명 |
|------|------|
| `--uid` | 사용자 ID 지정 |
| `--gid` | 기본 그룹 지정 |
| `--home` | 홈 디렉터리 지정 |
| `--shell` | 기본 셸 지정 |

---

## 사용자 관리 실습

```bash
adduser newuser1
passwd newuser1

usermod --group ubuntu newuser1

userdel newuser1
```

---

# 그룹 관리 명령어

| 명령어 | 설명 |
|--------|------|
| `groups` | 현재 사용자가 속한 그룹 확인 |
| `groupadd` | 새로운 그룹 생성 |
| `groupmod` | 그룹 정보 변경 |
| `groupdel` | 그룹 삭제 |
| `gpasswd` | 그룹 비밀번호 설정 및 그룹 관리 |
| `chage` | 사용자 비밀번호 변경 주기 설정 |

---

## 그룹 관리 실습

```bash
chage -m 2 newuser2

groups

groupadd newgroup1

groupmod --new-name mygroup1 newgroup1

groupdel newgroup1

gpasswd mygroup1
```

---

# 종합 실습

## 1. 사용자 생성

```bash
adduser user1
```

비밀번호를 두 번 입력한다.

```text
1234
1234
```

---

## 2. 사용자 정보 확인

```bash
tail -5 /etc/passwd
```

---

## 3. 그룹 정보 확인

```bash
tail -5 /etc/group
```

---

## 4. 사용자 삭제

```bash
userdel -r user1
```

`-r` 옵션은 홈 디렉터리까지 함께 삭제한다.

---

## 5. 그룹 생성

```bash
groupadd ubuntuGroup
```

생성 여부 확인

```bash
tail -5 /etc/group
```

---

## 6. 특정 그룹으로 사용자 생성

```bash
adduser --gid 1001 user1

adduser --gid 1001 user2
```

---

## 7. 사용자 정보 확인

```bash
tail -5 /etc/passwd
```

---

## 8. 비밀번호 정보 확인

```bash
tail -5 /etc/shadow
```

---

## 9. 홈 디렉터리 확인

```bash
ls -l /home/

ls -a /home/user1
```

---

## 10. 기본 사용자 환경 확인

```bash
ls -a /etc/skel
```

`/etc/skel`은 새로운 사용자가 생성될 때 기본으로 복사되는 파일들이 저장된 디렉터리이다.

---

## 11. 시스템 종료

```bash
init 0
```

---

# 핵심 정리

- 리눅스는 다중 사용자 운영체제이다.
- 사용자 정보는 `/etc/passwd`에 저장된다.
- 비밀번호는 `/etc/shadow`에 암호화되어 저장된다.
- 그룹 정보는 `/etc/group`에 저장된다.
- `adduser`, `passwd`, `usermod`, `userdel` 명령으로 사용자를 관리할 수 있다.
- `groupadd`, `groupmod`, `groupdel`, `gpasswd` 명령으로 그룹을 관리할 수 있다.
- `/etc/skel`은 새 사용자 생성 시 기본 파일을 제공하는 디렉터리이다.