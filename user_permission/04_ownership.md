# 파일 소유자와 그룹 변경

## 1. chown이란?

`chown`은 파일이나 디렉터리의 소유자를 변경하는 명령어입니다.

`chown`은 change owner의 줄임말입니다.

```bash
chown 사용자명 파일명
```

소유자가 변경되면 이전 소유자는 더 이상 해당 파일의 소유자가 아닙니다.

## 2. 파일 소유자 변경

```bash
chown dh test.txt
```

`test.txt` 파일의 소유자를 `dh` 사용자로 변경합니다.

파일의 소유자가 변경되었는지는 다음 명령어로 확인할 수 있습니다.

```bash
ls -l test.txt
```

## 3. 디렉터리와 하위 항목의 소유자 변경

`-R` 옵션을 사용하면 지정한 디렉터리와 그 안에 있는 모든 파일 및 하위 디렉터리의 소유자를 함께 변경할 수 있습니다.

```bash
chown -R dh copy
```

`copy` 디렉터리와 그 하위 항목의 소유자를 모두 `dh` 사용자로 변경합니다.

## 4. chgrp이란?

`chgrp`는 파일이나 디렉터리가 속한 그룹을 변경하는 명령어입니다.

`chgrp`는 change group의 줄임말입니다.

```bash
chgrp 그룹명 파일명
```

예를 들어 다음 명령어는 `test.txt` 파일의 그룹을 `dh`로 변경합니다.

```bash
chgrp dh test.txt
```

디렉터리와 하위 항목의 그룹을 함께 변경하려면 `-R` 옵션을 사용합니다.

```bash
chgrp -R dh copy
```

## 5. 소유자와 그룹을 동시에 변경하기

`chown` 명령어에서 소유자와 그룹을 콜론(`:`)으로 구분하면 두 가지를 동시에 변경할 수 있습니다.

```bash
chown root:root test.txt
```

`test.txt` 파일의 소유자를 `root`, 그룹을 `root`로 변경합니다.

디렉터리와 하위 항목까지 함께 변경하려면 다음과 같이 합니다.

```bash
chown -R root:root copy
```

## 6. 소유자와 그룹 변경 시 주의할 점

일반 사용자는 보통 자신이 소유한 파일의 그룹을 자신이 속한 다른 그룹으로만 변경할 수 있습니다.

다른 사용자의 파일 소유자를 변경하거나 root 소유의 파일을 변경하려면 root 권한이 필요할 수 있습니다.

```bash
sudo chown root:root test.txt
```

권한이 부족하면 다음과 같은 오류가 발생할 수 있습니다.

```text
Permission denied
```

## 7. 종합 실습

### 실습 목표

1. `/` 디렉터리에 `quiz` 디렉터리를 생성합니다.
2. `quiz` 디렉터리 안에 `file1.txt` 파일을 생성합니다.
3. `vi` 편집기로 `Linux quiz` 문구를 작성합니다.
4. `file1.txt`의 권한을 모든 사용자가 읽기, 쓰기, 실행할 수 있도록 변경합니다.
5. `file2.txt` 파일을 생성합니다.
6. `file2.txt`는 소유자와 그룹이 읽기와 쓰기를 할 수 있고, 기타 사용자는 읽기만 할 수 있도록 변경합니다.

### 디렉터리 생성 및 이동

```bash
cd /
sudo mkdir quiz
cd quiz
```

일반 사용자가 `/` 디렉터리에 디렉터리를 생성하려면 권한이 부족할 수 있으므로 `sudo`를 사용할 수 있습니다.

### file1.txt 생성

```bash
touch file1.txt
```

### vi로 파일 편집

```bash
vi file1.txt
```

`vi`에서 입력 모드로 전환하려면 `i`를 누릅니다.

다음 문장을 입력합니다.

```text
Linux quiz
```

입력을 마친 뒤 `Esc` 키를 누르고 다음 명령어를 입력합니다.

```text
:wq
```

`:wq`는 저장 후 종료를 의미합니다.

### file1.txt 내용 확인

```bash
cat file1.txt
```

화면을 정리하려면 다음 명령어를 사용합니다.

```bash
clear
```

### file1.txt 권한 변경

```bash
chmod 777 file1.txt
```

`file1.txt`의 권한을 다음과 같이 변경합니다.

- 소유자: 읽기, 쓰기, 실행
- 그룹: 읽기, 쓰기, 실행
- 기타 사용자: 읽기, 쓰기, 실행

### file2.txt 생성

```bash
touch file2.txt
```

### file2.txt 권한 변경

```bash
chmod 664 file2.txt
```

`file2.txt`의 권한은 다음과 같습니다.

- 소유자: 읽기, 쓰기
- 그룹: 읽기, 쓰기
- 기타 사용자: 읽기

### 최종 결과 확인

```bash
ls -l file1.txt file2.txt
```

예상되는 권한은 다음과 같습니다.

```text
-rwxrwxrwx file1.txt
-rw-rw-r-- file2.txt
```

## 핵심 정리

- `chown`은 파일의 소유자를 변경합니다.
- `chgrp`는 파일이 속한 그룹을 변경합니다.
- `chown 사용자:그룹 파일명` 형식으로 소유자와 그룹을 동시에 변경할 수 있습니다.
- `-R` 옵션은 디렉터리와 하위 항목에 변경 내용을 재귀적으로 적용합니다.
- 다른 사용자의 파일이나 root 소유 파일을 변경할 때는 `sudo`가 필요할 수 있습니다.
- 권한 변경 후에는 `ls -l`로 결과를 확인하는 습관이 중요합니다.