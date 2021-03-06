## 추상 클래스(abstract class)
`추상 클래스란?` 실체 클래스의 공통적인 부분을 추출하여 어느정도 규격을 잡아놓은 클래스를 말한다. 예를 들어 '동물'이라는 클래스가 있을 때 강아지는 멍멍멍, 고양이는 야옹, 호랑이는 어흥 소리는 낸다. 여기서 동물들은 소리를 낸다라는 액션에 공통점이 있다. 즉, 메서드가 공통적이며 이 메서드를 추출하여 추상 클래스 안에 두면 된다.


### 추상 클래스의 목적
- 공통된 필드와 메서드를 통일
  - 이를 통해 유지보수성을 높일 수 있고 통일성을 유지할 수 있다.
- 실체 클래스 구현시 시간 절약
  - 자식 클래스에게 구현이 강제화되며, 이렇게 주어진 필드와 메서드를 가지고 나만의 스타일로 구현만 하면 된다.
- 규칙성을 갖는 실체 클래스 구현
  - 개발은 혼자 하는게 아니다. 따라서 어느정도의 규격이 있어야한다. 소스 수정시 다른 소스의 영향도를 낮추고 해당 규격에 대한 구현부만 수정하며 유지보수성을 높일 수 있다.


### 추상 클래스의 특징
- 선언부만 작성하고 구현부는 작성하지 않는 메소드이며, 앞에 abstract 키워드를 붙인다.
- 구현부를 작성하지 않는 이유는 메소드의 내용이 상속받은 클래스에 따라 달라질 수 있기 때문이다.
- 추상 클래스를 상속받은 자식 클래스는 오버라이딩을 통해 추상 메소드를 모두 구현해야 한다.
- 추상 메소드를 하나라도 포함하고 있다면 추상 클래스로 선언해야 한다. 하지만 추상 클래스는 추상 메소드가 아닌 일반 메소드, 멤버도 포함할 수 있다.
- 추상 클래스는 인스턴스를 생성할 수 없다. 동작이 정의되지 않은 추상 메소드(실체성이 없고 구제적이지 않은)를 포함하고 있기 때문이다.


### 추상 클래스 사용법
- 클래스 앞에 `abstract`를 붙인다.

```java
public abstract class Animal {
  public String kind;

  public abstract void bark();
}
```

```java
public class Dog extends Animal{
  public Dog()
  {
    this.kind = "멍멍이";
  }

  @Override
  public void bark() {
    System.out.println("멍멍멍멍멍머엄멍");
  }
}

```

```java
public class Cat extends Animal{
  public Cat()
  {
    this.kind = "고양이이";
  }

  @Override
  public void bark() {
    System.out.println("야옹야옹");
  }

}
```

```java
public class Test {

  public static void main(String[] args) {
    // Animal animal = new Animal();
    // 추상 클래스는 자체적으로 인스턴스를 생성할 수 없다. 불완전하기 때문

    Dog dog = new Dog();
    Cat cat = new Cat();

    dog.bark();
    cat.bark();

    Animal animal = new Dog(); // 자동으로 캐스팅된다.
	// 추상클래스 변수에, 추상클래스를 상속받아 구현한 실체클래스 인스턴스를 주입하면 해당 추상클래스 변수는 자동 타입변환을 발생시켜 실체클래스 인스턴스처럼 사용할 수 있다. 이를 타입의 다형성이라고 한다.
	animal.bark();
  }
}
```
추상 클래스인 Animal은 추상 메소드인 bark()를 가지고 있으며, Animal 클래스를 상속받는 자식 클래스인 Dog, Cat 클래스는 bark() 메소드를 오버라이딩해야만 인스턴스를 생성할 수 있다.


### 참조
> [limky](https://limkydev.tistory.com/188)

> [WooVictory](https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Java/%5BJava%5D%20%EC%B6%94%EC%83%81%20%ED%81%B4%EB%9E%98%EC%8A%A4.md)
