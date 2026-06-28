# 리눅스 텍스트 파일 다루기

---

## 명령어

- `cat` : 파일 내용 출력
- `head` : 파일의 앞부분 내용 출력
- `tail` : 파일의 뒷부분 내용 출력
- `more` : 페이지 단위로 출력
- `less` : 파일 내용 탐색

---

## 실습

```bash
echo "Hello Linux" > test.txt
cat test.txt
head test.txt
tail test.txt

cat test.txt | more
cat test.txt | less
```

