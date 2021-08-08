## git-flow 사용법

## 1. init

git-flow를 사용하기 위해서는 git-flow에 맞게 초기화를 해야한다. 명령을 실행하면 브랜치들의 이름을 지정할 수 있다. 그냥 엔터키를 누르면 기본값으로 이름이 정해진다.

```
git flow init
```

기본값으로만 입력하고 싶다면 -d 옵션을 사용하면 된다.

```
git flow init -d
```



## 2. feature

### (1) feature start

기능 추가를 위해서 feature 브랜치를 생성한다. 해당 명령을 실행하면 develop 브랜치를 기반으로 새로운 feature 브랜치가 생성되고, 자동으로 feature 브랜치고 checkout 된다.

브랜치명은 `feature/feature name` 형태가 된다.

```
git flow feature start <feature name>
// ex) git flow feature start user
```



### (2) feature finsh

개발 작업이 끝나서 feature 브랜치를 마무리할 때 사용한다. 해당 명령을 실행하면 develop 브랜치로 checkout 한 뒤, feature 브랜치의 내용을 병합한다. 그리고 feature qmfosclfmf 삭제한다. 

```
git flow feature finish <feature name>
// ex) git flow feature finish user
```



### (3) feature publish

원격 저장소에 feature 브랜치를 push할 때 사용한다. 보통 PR 과정이 필요할 때 사용한다. 

```
git flow feature publish <feature name>
```



## 3. release

### (1) release start

release 브랜치를 생성한다. 해당 명령어를 실행하면 `release/<version>` 브랜치가 생성된다. release 과정에서 수정된 내용이 들어가게 된다.  

```
git flow release start <version>
```



### (2) publish

원격 저장소로 push 할 때 사용한다.

```
git flow release publish <version>
```



### (3) track

원격 저장소에서 변경 사항을 가져올 때 사용한다. pull이 아니라 `track`을 사용

```
git flow release track <version>
```



### (4) finish

릴리즈 준비가 끝났으면 finish를 통해 마무리한다. 해당 명령어를 수행하면 아래와 같이 동작하게 된다.

```
1. release 브랜치를 master 브랜치에 병합
2. release 버전을 태그로 생성
3. release 브랜치를 develop 브랜치에 병합
4. release 브랜치 삭제
```



