# Call by Reference와 Call by Value 차이
결론부터 말하면 자바는 `Call by Value` 이다.


함수의 인자로 전달되는 타입이 기본형(원시 자료형)인 경우 값을 넘기게 되어있다. 이 경우 메모리에는 함수를 위한 별도의 공간이 생성되고 이는 함수 종료 시 사라진다. 따라서 함수 안에서 해당 인자의 값을 변경하더라도 원본 값은 바뀌지 않는 특징이 있다.

```java
public static void main(String[] args) {
    int a = 10;
    int b = 20;
    swap(a, b);
    System.out.println("a = " + a + ", " +  "b = " + b);
}

private static void swap(int a, int b) {
    int tmp = b;
    b = a;
    a = tmp;
}
```

```
a = 10, b = 20
```

참조형(참조 타입)인 경우, 변수가 가지는 값이 주소 값이므로 Call by Value에 의해 주소 값이 전달된다. 따라서 함수 안에서 해당 인자의 값을 변경하게 되면 원본 값도 바뀌게 되는 특징이 있다.

```java
public static void main(String[] args) {
    int[] array = {10, 20};
    multiply(array, 10);
    for (int num : array) {
        System.out.println(num);
    }
}

private static void multiply(int[] array, int num) {
    for (int i = 0; i < array.length; i++) {
        array[i] *= num;
    }
}
```

```
100
200
```