# Bash 스크립트와 변수

## 셸 스크립트 작성과 실행

셸 스크립트는 셸 명령어를 파일에 작성해 순서대로 실행하는 프로그램입니다. Bash 스크립트의 첫 줄에는 실행할 인터프리터를 지정합니다.

```bash
#!/bin/bash

echo "Hello World!"
```

예를 들어 `hello.sh`로 저장한 뒤 실행 권한을 추가하고 실행합니다.

```bash
chmod 755 hello.sh
./hello.sh
```

실행 권한 없이 Bash로 직접 실행할 수도 있습니다.

```bash
bash hello.sh
```

## 변수 선언과 사용

Bash 변수는 자료형을 미리 선언하지 않습니다. 변수 대입에서 등호(`=`) 앞뒤에 공백을 넣지 않고, 변수 값을 사용할 때는 `$`를 붙입니다.

```bash
name="변동헌"
age=17
address="부산광역시"

echo "$name"
echo "$age"
echo "$address"
echo "이름: ${name}"
```

변수명은 대소문자를 구분합니다. 숫자를 포함할 수 있지만 숫자로 시작할 수는 없습니다. `${name}`처럼 중괄호를 사용하면 변수 이름의 범위를 명확하게 표시할 수 있습니다.

다음은 변수에 저장한 값을 이용해 정보를 출력하는 예시입니다.

```bash
#!/bin/bash

name="변동헌"
age=17
sex="남자"
address="부산광역시"

echo "이름 : $name"
echo "나이 : $age"
echo "성별 : $sex"
echo "거주지 : $address"
```

## 셸 변수와 환경 변수

일반적으로 스크립트에서 선언한 변수는 현재 셸에서 사용하는 셸 변수입니다. 자식 프로세스에도 값을 전달하려면 `export`로 환경 변수로 내보냅니다.

```bash
name="변동헌"
export name
```

`$USER`, `$HOME`처럼 셸에서 사용할 수 있는 환경 변수도 있습니다.

```bash
echo "$USER"
echo "$HOME"
```

## 읽기 전용 변수

`declare -r` 또는 `readonly`로 읽기 전용 변수를 선언할 수 있습니다. 선언한 뒤 값을 바꾸려고 하면 Bash가 오류를 출력하고 기존 값은 유지됩니다.

```bash
declare -r name="홍길동"
echo "${name}"

name="변동헌"
echo "${name}"
```

## 정수 속성 변수

`declare -i`는 변수에 정수 속성을 지정합니다.

```bash
declare -i number=17
echo "number: ${number}"
```
