## 문제

gitignore에 추가했는데, 해당 파일을 계속 추적하는 경우

즉, gitignore가 적용이 안될 때

## 발생 원인

.gitignore에 파일을 추가하기 전에 stage 올라간 파일들은 캐시처리가 되어 기록이 남아있기 때문

## 해결방법

캐시를 제거

```bash
git rm -r --cached .
git add .
git commit -m "clear git cache"
```