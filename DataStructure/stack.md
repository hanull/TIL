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
- 후위 표기법 계산

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

1. 배열로 구현하기

```java
public class Array_Stack implements Stack{
  private int maxSize;
  private int index;
  private Object[] stackArray;

  public Array_Stack(int maxSize) {
    this.maxSize = maxSize;
    this.index = 0;
    stackArray = new Object[maxSize];
  }

  @Override
  public void push(Object data) {
    if (index < maxSize) {
      stackArray[index] = data;
      index++;
    }else {
      throw new IndexOutOfBoundsException("Stack is FULL!!!");
    }
  }

  @Override
  public Object pop() {
    if (isEmpty()) {
      throw new IndexOutOfBoundsException("Empty stack");
    }else {
      Object res = peek();
      stackArray[index-1] = null;
      index--;
      return (res);
    }
  }

  @Override
  public Object peek() {
    if (isEmpty()) {
      throw new IndexOutOfBoundsException("Empty stack");
    }else {
      Object res = stackArray[index - 1];
      return (res);
    }
  }

  @Override
  public boolean isEmpty() {
    return (index == 0);
  }

  public void empty() {
    if (isEmpty()) {
      throw new IndexOutOfBoundsException("Stack is already empty");
    }else {
      stackArray = new Object[100];
    }
  }

  public void printStack() {
    if (isEmpty()) {
      System.out.println("Stack is empty");
    }else {
      int i=0;
      while(stackArray[i] != null) {
        System.out.println(stackArray[i]);
        i++;
      }
    }
  }

  public int size() {
    if (isEmpty()) {
      return 0;
    }else {
      return (index);
    }
  }
}

```

2. 연결 리스트로 구현하기

```java
class Node{
  private Object data;
  public Node next;

  public Node(Object data) {
    this.data = data;
    this.next = null;
  }

  public Object getData() {
    return (this.data);
  }
}

public class LinkedList_Stack implements Stack{
  private Node top;
  private Node bottom;
  private int stackSize;

  public LinkedList_Stack() {
    top = null;
    bottom = null;
    stackSize = 0;
  }

  @Override
  public void push(Object data) {
    Node newNode = new Node(data);
    if (isEmpty()) {
      top = newNode;
      bottom = top;
    }else {
      newNode.next = top;
      top = newNode;
    }
    stackSize++;
  }

  @Override
  public Object pop() {
    if (isEmpty()) {
      throw new EmptyStackException();
    }else {
      Object data = peek();
      top = top.next;
      stackSize--;
      return (data);
    }
  }

  @Override
  public Object peek() {
    if (isEmpty()) {
      throw new IndexOutOfBoundsException("Stack is Empty!");
    }else {
      return (top.getData());
    }
  }

  @Override
  public boolean isEmpty() {
    return (stackSize == 0);
  }

  public int getSize() {
    return (stackSize);
  }
}
```
