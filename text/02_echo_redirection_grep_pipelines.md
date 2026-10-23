# echo, 리다이렉션, grep과 파이프라인

## `echo`와 이스케이프 문자

`echo -e`는 문자열 안의 이스케이프 문자를 해석해 출력합니다. 아래 예시는 Bash 기준입니다.

| 이스케이프 문자 | 의미 |
| --- | --- |
| `\n` | 줄바꿈 |
| `\t` | 수평 탭 |
| `\b` | 백스페이스 |
| `\\` | 역슬래시(`\`) |

```bash
echo -e "이름: 변동헌\n나이: 17살"
```

출력:

```text
이름: 변동헌
나이: 17살
```

## 표준 입출력과 리다이렉션

리다이렉션은 명령어의 표준 입력이나 표준 출력을 키보드·화면 대신 파일에 연결하는 기능입니다.

### 출력 덮어쓰기: `>`

`>`는 표준 출력을 파일에 저장합니다. 파일이 없으면 새로 만들고, 이미 있으면 기존 내용을 덮어씁니다.

```bash
ls -l > result.txt
cat result.txt
```

파일 내용을 복사하거나 여러 파일의 내용을 합칠 때도 사용할 수 있습니다.

```bash
cat result.txt > backup.txt
cat result.txt backup.txt > combined.txt
```

### 덮어쓰기 방지: `noclobber`

실수로 기존 파일을 덮어쓰지 않도록 Bash의 `noclobber` 옵션을 켤 수 있습니다.

```bash
set -o noclobber   # 기존 파일을 >로 덮어쓰지 않음
set +o noclobber   # noclobber 해제
```

`noclobber`가 켜져 있어도 `>|`를 사용하면 해당 명령에서 덮어쓰기를 명시적으로 허용할 수 있습니다.

### 출력 추가: `>>`

`>>`는 기존 파일의 끝에 표준 출력을 추가합니다. 파일이 없으면 새로 만듭니다.

```bash
echo "Hello World" > hello.txt
echo "Hello Linux" >> hello.txt
cat hello.txt
```

출력:

```text
Hello World
Hello Linux
```

### 입력 가져오기: `<`

`<`는 파일의 내용을 명령어 표준 입력으로 전달합니다.

```bash
wc -l < result.txt
sort < hello.txt
```

## `grep`으로 문자열 검색하기

`grep`은 파일에서 패턴과 일치하는 **줄**을 출력합니다. `-r` 옵션을 사용하면 지정한 디렉터리와 하위 디렉터리를 재귀적으로 검색합니다.

```bash
grep "Hello" hello.txt
grep -r "ubuntu" /etc
```

| 옵션 | 설명 |
| --- | --- |
| `-r` | 하위 디렉터리까지 재귀적으로 검색 |
| `-i` | 대소문자를 구분하지 않음 |
| `-w` | 패턴이 단어 경계에 맞는 경우에만 검색 |
| `-n` | 일치한 줄과 줄 번호를 함께 출력 |
| `-c` | 패턴과 일치하는 줄의 수를 출력 |

```bash
grep -n "Hello" hello.txt
grep -i "hello" hello.txt
grep -w "Linux" hello.txt
grep -c "Hello" hello.txt
```

## 파이프라인: `|`

파이프라인은 앞 명령어의 표준 출력을 뒤 명령어의 표준 입력으로 전달합니다.

```bash
명령어1 | 명령어2
```

예를 들어 프로세스 목록에서 `ssh`가 포함된 줄을 찾을 수 있습니다.

```bash
ps -ef | grep "ssh"
```

파이프라인의 결과를 파일에 저장할 수도 있습니다.

```bash
ls -l | cat -n > listing.txt
```

이 명령은 `ls -l` 결과에 `cat -n`으로 줄 번호를 붙인 뒤 `listing.txt`에 저장합니다. `>`를 사용하므로 같은 이름의 파일이 이미 있으면 덮어씁니다.
