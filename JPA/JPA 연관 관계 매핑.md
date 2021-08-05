## JPA 연관 관계 매핑

- 방향
  - 단방향 : 두 엔티티가 관계를 맺을 때, 한 쪽의 엔티티만 참조하고 있는 것을 의미
  - 양방향 : 두 엔티티가 관계를 맺을 때, 양 쪽이 서로 참조하고 있는 것을 의미
  - 엄밀히 말하면 양방향 관계는 없고, 두 객체가 단방향 참조를 각각 가져서 양방향 관계처럼 보이는 것이다.
- 다중성
  - 다대일(N : 1), 일대다(1 : N), 일대일(1 : 1), 다대다(N : M)
- 연관 관계의 주인
  - 연관 관계에서 관리 주체
  - 연관 관계를 갖는 두 테이블에 대해서 외래키를 갖는 테이블이 연관 관계의 주인이 된다.
  - 주인만이 외래키를 관리(등록, 수정, 삭제)할 수 있고, 주인이 아닌 엔티티는 읽기만 가능하다.



## 1. @ManyToOne

- 요구사항
  - 게시판(Boarad)과 게시글(Post)
  - 하나의 게시판(1)에는 여러 게시글(N)을 작성할 수 있다.

### 단방향

```java
public class Post {
  @Id
  @GenerateValue
  @Column()
  private Long id;
  
  @Column(name = "title")
  private String title;
  
  @ManyToOne
  @JoinColumn(name = "board_id")
  private Board board; 
  //... getter, setter
} 
  
@Entity
public class Board { 
  @Id 
  @GeneratedValue
  private Long id;
  private String title;
  //... getter, setter
}
```

### @ManyToOne

게시글 입장에서 게시판은 다대일 관계이므로 @ManyToOne이 된다. 연관 관계를 매핑할 때는 다중성을 나타내는 어노테이션을 필수로 사용해야하며, 엔티티 자신을 기준으로 다중성을 생각해야 한다.

### JoinColumn(name = "board_id")

외래키를 매핑할 때 사용하는 어노테이션이다. name 속성에는 매핑할 외래키 이름을 지정한다. Post 엔티티의 경우 Board 엔티티의 id 필드를 외래키로 가지므로 board_id로 설정하면 된다.



이후 hibernate가 테이블을 정의할 때,  post 테이블에 board_id 외래키를 갖는 SQL을 만들어 테이블을 생성하게 된다. 따라서 해당 외래키를 통해 Post에서 Board의 정보를 가져올 수 있다.

하지만 Board에서 Post의 정보를 가져올 수는 없다. Board에서 Post의 정보를 가져오고 싶다면?  @OenTomany를 추가하여 1 : N  관계를 설정해주면 된다.

## 2. @OneToMany

```java
@Entity
public class Board { 
  @Id 
  @GeneratedValue
  private Long id;
  private String title;
  
  @OneToMany(mappedBy = "board")
  List<Post> posts = new ArrayList<>();
}
```

MappedBy는 연관 관계의 주인을 지정해주는 역할을 한다. 값은 대상이 되는 변수명을 설정하면 된다. 

```java
// post 조회
Post findPost = entityManager.find(post.class, post.getId());
// board에서 모든 post 조회
List<Post> posts = findPost.getBoard().getPosts();
```



## 3. @OneToOne

일대일 관계는 양쪽이 서로 하나의 관계만 가진다. 예를 들어 회원은 하나의 사물함만 사용하고, 사물함도 하나의 회원에 의해서만 사용된다. 

일대일 관계는 주 테이블이나 대상 테이블 둘 중 어느곳이나 외래키를 가질 수 있다. 하지만 보통 주 테이블에 외래키를 갖는 방법으로 사용한다.

- 주 테이블에 외래 키

  - 주 테이블 : 많이 접근하는 테이블
  - 주 테이블에 외래 키가 존재
  - 장점
    - 주 테이블만 조회해도 대상 테이블에 데이터가 있는지 확인이 가능하다.
  - 단점
    - 값이 없으면 외래 키에 NULL을 허용해야 한다. DB입장에서는 치명적일 수 있다.

- 대상 테이블에 외래키

- - 대상 테이블에 외래 키가 존재

  - 전통적인 데이터베이스 개발자들이 선호하는 방식이다. NULL을 허용해야 하는 문제도 없다.

  - 장점

    - 주 테이블과 대상 테이블을 일대일에서 일대다 관계로 변경할 때 테이블 구조를 유지할 수 있다.(멤버가 락커를 여러개 가지도록 비즈니스 룰이 변경될 경우 테이블 구조 유지하면서 유지보수 가능)

  - 단점

  - - 코드상에서는 주로 멤버 엔티티에서 락커를 많이 엑세스 하는데, 어쩔 수 없이 양방향 매핑을 해야한다.
      - 일대일
        - 대상 테이블에 외래 키 단방향 매핑을 JPA에서 지원하지 않으므로, 단방향 매핑만 해서는 멤버 객체를 업데이트 했을 때 락커 테이블에 FK를 업데이트 할 방법이 없다. 따라서 양방향 매핑을 해야 한다.



## 4. @ManyToMany

결론부터 말하자면 실무에서 사용하지 않는 방법이다.

### 다대다 매핑의 한계

다대다로 자동 생성된 중간 테이블은 두 객체의 외래키만 저장되기 때문에 문제가 발생한다. 

예를들어, 회원과 상품 테이블이 있을 때, 단순히 주문한 회원 아이디와 상품 아이디만을 담고 끝나지 않고 주문수량, 주문 날짜 등 다양한 칼럼이 필요하기 때문이다.

![](https://github.com/hanull/TIL/blob/master/JPA/img/1.png)

이렇게 컬럼을 추가하면 더는 @ManyToMany를 사용할 수 없다. 왜냐하면 주문 엔티티나 상품 엔티티에는 추가한 컬럼들을 매핑할 수 없기 때문이다. 이를 해결하기 위해서, 중간 테이블을 추가하여 다대일, 일대다로 풀어서 사용한다. 

![](https://github.com/hanull/TIL/blob/master/JPA/img/2.png)



## 참고

- https://ict-nroo.tistory.com/126?category=826875
- https://jeong-pro.tistory.com/231