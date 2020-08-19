## equals()
두 객체의 `내용이 같은지` 검사하는 메소드

## hashCode()
두 객체가 `같은 객체인지` 검사하는 메소드



```java
class Member{
    int id;
    String name;

    public Member(int id, String name) {
        this.id = id;
        this.name = name;
    }
}
```

```java
public static void main(String[] args) {
    Map<Member, Integer> map = new HashMap<>();
    Member s1 = new Member(1, "hanul");
    Member s2 = new Member(1, "hanul");
    map.put(s1, 1);
    map.put(s2, 1);
    System.out.println(s1==s2);
    System.out.println(s1.equals(s2));
}
```

```
false
false
```

결과는 위와 같이 모두 `false`가 나온다. 먼저 `==`로 비교할 때는 두 객체의 주소값으로 비교하게 된다. 이 때 두 객체의 메모리 주소값은 다르고, false를 리턴하게 된다. 그런데 `equals`는 왜?? 왜냐하면 equals는 내부적으로 ==로 비교한 값을 리턴하기 때문이다. 

## 어떻게 두 객체의 내용을 비교할까?  
equals 메소드를 `@Override`한다.

```java
@Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Member member = (Member) o;
        return id == member.id &&
                Objects.equals(name, member.name);
    }
```

```java
System.out.println(s1.equals(s2));  // true
```

두 객체의 내용이 같은지를 equals 오버라이드를 통해 해결했다. 그러면 이제 같은 것일까?? 

```java
System.out.println(map.size());    // 2
```

맵의 사이즈를 확인해봤는데 `2` 가 나왔다. 내용이 같은데 왜 하나가 아닐까??  Hash를 사용한 Collection 들은 key를 결정할때 hashCode()를 사용하기 때문이다. 즉, hashcode 값이 다르기 때문이다.

```java
System.out.println(s1.hashCode());  //  1528902577
System.out.println(s2.hashCode());  //  1927950199
```

## 어떻게 같은 내용읜 두 객체를 같은 hashcode값을 갖도록 할 수 있지??  
`hashCode()` 메소드를 오버라이드하면 된다.

```java
@Override
public int hashCode() {
    return Objects.hash(id, name);
}
```

```java
System.out.println(s1.hashCode());  //  99046348
System.out.println(s2.hashCode());  //  99046348
```


## String

```java
String str1 = "hello";
String str2 = "hello";
System.out.println(str1 == str2);   // true,   리터럴로 생성한 객체로 heap에 생성된 "hello"를 같이 가리키고 있는 것이다.

String str3 = new String("hello");
String str4 = new String("hello");
System.out.println(str3.hashCode() == str4.hashCode()); // true
```

`String`은 내부적으로 파라미터로 hashcode를 생성한다. 따라서 같은 파라미터를 이용한 str1, str2, str3, str4 모두 같은 hashcode가 생성된다.


## hashCode가 같으면, equals는 반드시 true 인가??
`NO!` 
서로 다른 문자열이지만 같은 hashCode를 리턴하는 경우가 생긴다.(충돌)
`hashCode의 값은 객체마다 유일한 값이 아니다.`

 
### 그럼 hashCode는 왜 필요해?
먼저 hashCode를 이용하여 같은 객체가 있는지 비교하고, 그 다음 equals로 비교한다.  
이렇게 비교하는 이유는 , 수만가지의 String 데이터중에 hashcode로 먼저 비교하여 경우의 수를 줄이고 그 다음 "Hello world"를 찾는것이 더 효과적이기 때문.


## 자바에서 정의하고 있는 hashCode 규약
- equals() 메소드가 true 이면 , 두 객체의 hashCode값은 같아야한다.
- equals() 메소드가 false 이면 , 두 객체의  hashCode값이 꼭 다를 필요는 없다.



## 참조
- https://nesoy.github.io/articles/2018-06/Java-equals-hashcode
- https://beomseok95.tistory.com/248