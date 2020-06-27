## 스택(stack)의 개념
한 쪽 끝에서만 자료를 넣고 뺄 수 있는 LIFO(Last In First out) 형식의 자료구조이다.

## 스택(stack)의 연산
- push() : 스택의 가장 위에 데이터를 넣는다.
- pop() : 스택의 가장 위에 있는 데이터를 뺀다.
- isEmty() : 스택이 비어 있을 경우 true를 반환한다.
- peek() : 스택의 가장 위에 있는 데이터를 반환한다.

## 스택(stack)의 사용 사례
- 재귀 알고리즘
- 문자열 역순 출력
- 웹 브라우저 방문 기록(뒤로가기)
- 실행 취소
- 수식의 괄호 검사 (연산자 우선순위 표현을 위한 괄호 검사)
  - Ex) 올바른 괄호 문자열(VPS, Valid Parenthesis String) 판단하기
- 후위 표기법 계산 [구현 코드 보기](https://github.com/hanull/DataStructures/blob/master/stack/postfix_notation/Solution.java)

## 스택(stack) 구현
먼저 인터페이스를 생성한 뒤 메소드를 구현하였다.

```java
public interface Stack {
  void push(Object data);
  Object pop();
  Object peek();
  boolean isEmpty();
}
```

[1. 배열로 구현하기](https://github.com/hanull/DataStructures/blob/master/stack/Array_Stack.java)

[2. 연결 리스트로 구현하기](https://github.com/hanull/DataStructures/blob/master/stack/LinkedList_Stack.java)

[3. 스택으로 후위 계산기 구현하기](https://hanul-dev.netlify.app/DataStructure/%EC%8A%A4%ED%83%9D(stack)%EC%9D%84-%ED%99%9C%EC%9A%A9%ED%95%98%EC%97%AC-%ED%9B%84%EC%9C%84%EC%97%B0%EC%82%B0-%EA%B3%84%EC%82%B0%EA%B8%B0-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0/)
