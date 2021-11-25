## 상수를 관리하는 방법과 enum 등장 배경

프로그램에서 사용하는 공통 코드나, 자주 사용하는 문자 등을 따로 선언하지 않는다면 매번 값을 직접 입력하여 사용하면 하드 코딩을 하게된다. 이러한 문제를 해결하기 위해서 상수를 선언하여 사용한다.

상수란? 프로그램이 실행과 동시에 선언하고, 실행되는 동안 변하지 않는 값을 말한다. 아래와 같이 `final` 키워드를 통해 선언하여 사용한다.

```java
private static final int MAX_NUMBER = 9;
private static final int MIN_NUMBER = 1;
```



해당 방법에는 문제점이 존재한다.

1. 네이밍이 겹칠 수 있다.

```java
// 과일
private static final int APPLE = 1;
private static final int BANANA = 2;

// 회사
private static final int APPLE = 1;
private static final int SAMSUNG = 2;
```

2. 클래스에 상수가 불필요하게 많아질 수 있고, 상수들이 어떤 것에 관련된 것인지 한눈에 보기 힘들다.

```java
// 요일
private static final int MONDAY = 1;
private static final int TUESDAY = 2;
private static final int WEDNESDAY = 3;
private static final int THURSDAY = 4;

// '달'에 관련한 상수가 추가된다면, 상수가 너무 많아 진다. 
private static final int JANUARY = 1;
private static final int FEBRUARY = 2;
private static final int MARCH = 3;
private static final int APRIL = 4;

```



 `interface` 를 사용하여 위의 문제를 해결할 수 있다. 또한 '월', '요일' 각각 의미에 맞게 나누어 상수를 관리할 수 있다.

```java
interface DAY {
  int MONDAY = 1;
	int TUESDAY = 2;
	int WEDNESDAY = 3;
  int THURSDAY = 4;
}

interface MONTH {
  int JANUARY = 1;
	int FEBRUARY = 2;
	int MARCH = 3;
  int APRIL = 4;
}
```

그런데 이러한 방법에도 여전히 문제가 있다. DAY 와 MONTH 는 모두 int 타입이기 때문에 아래와 같은 비교가 가능하다. 

```java
if (DAY.MONDAY == MONTH.JANUARY) {
  System.out.println("두 상수는 같다");
}
```

하지만, DAY, MONTH 처럼 서로 다른 의미를 가진 집합을 비교한다는 것은 논리적으로 말이 안된다. 따라서 서로 다른 의미를 가진 상수는 비교조차 할 수 없도록 컴파일 단계에서 에러를 발생시켜야 한다.



이러한 문제들을 보완하여 나온 것이 `enum` 이다.

