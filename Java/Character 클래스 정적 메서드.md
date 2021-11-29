## Character 클래스

char를 int로 변환할 때는 항상  `'0'` 또는 `48`  을 빼서 숫자 형태로 변환해왔다.  그런데 Character 래퍼 클래스에 문자를 숫자로 변환하는 기능을 하는 `getNumericValue` 정적 메서드가 존재하는 것을 알게되었다. 

이를 활용하면 좀 더 명확한 의미를 가진 코드를 작성할 수 있다고 생각한다. 따라서 몇몇 쓸만한 정적 메서드를 함께 정리하려고 한다.

```java
for (char number : enterPlayerNumber.toCharArray()) {
  // playerNumbers.add(number - '0');
  playerNumbers.add(Character.getNumericValue(number));
}
```



### isLowerCase

- 소문자인지 확인

```java
System.out.println(Character.isLowerCase('a'));	// true
System.out.println(Character.isLowerCase('A'));	// false
```

### isUpperCase

- 대문자인지 확인

```java
System.out.println(Character.isLowerCase('a'));	// false
System.out.println(Character.isLowerCase('A'));	// true
```

### isDigit

- 숫자인지 확인

```java
System.out.println(Character.isDigit('1'));	// true
System.out.println(Character.isDigit('a'));	// false
```

### isLetter

- 문자인지 확인

```java
System.out.println(Character.isLetter('1'));	// false
System.out.println(Character.isLetter('a'));	// true
```

### isLetterOrDigit

- 문자 or 숫자인지 확인

```java
System.out.println(Character.isLetterOrDigit('a'));	// true
```

### isAlphabetic

- 알파벳인지 확인

```java
System.out.println(Character.isAlphabetic('a'));	// true
System.out.println(Character.isAlphabetic('1'));	// false
```

#### getNumericValue

- Char 의 int값을 return 해준다.
- 매개변수가 char 값일 경우, 코드포인트로 리턴

```java
System.out.println(Character.getNumericValue('1'));	// 1
System.out.println(Character.getNumericValue('A'));	// 10
```

### isSpaceChar, isWhitespace

- 공백인지 확인해준다.
- 두 메서드의 차이점
  - isSpaceChar는 단지 unicode 공백 문자만 체크, isWhitespace는 탭이나 개행 등의 공백까지 체크해준다.

```java
System.out.println(Character.isSpaceChar(' '));	// true
System.out.println(Character.isWhitespace(' '));	// true

System.out.println(Character.isSpaceChar('\n'));	// false
System.out.println(Character.isWhitespace('\n'));	// true
```

### compare

- 두 문자를 비교한다. (char x, char y)
- x == y, 0을 리턴
- x < y, 음수 리턴
- x > y, 양수 리턴

```java
System.out.println(Character.compare('a', 'a'));	// 0
System.out.println(Character.compare('a', 'b'));	// -1
System.out.println(Character.compare('c', 'a'));	// 2
```

