## 덱(deque) 개념
- double-ended queue의 줄임말로, 큐의 앞과 뒤 모두에서 삽입 및 삭제가 가능한 큐를 말한다.
- 큐와 스택을 합친 형태로 생각할 수 있다.
- 큐나 스택보다 유연하다.
- 보통 두가지 중(스크롤/셀프) 하나로 사용하게 된다. (입력과 출력을 추가하는 방식으로 사용)

## 덱(deque) 종류
- 스크롤(Scroll) : 입력이 한쪽에서만 가능하고, 출력은 양쪽에서 모두 가능하도록 제한한 덱(입력 제한)
- 셀프(Shelf) : 출력이 한쪽에서만 가능하고, 입력이 양쪽에서 모두 가능하도록 제한한 덱(출력 제한)

## 덱(deque) 연산
- offerFirst() : 덱의 앞에 데이터를 삽입
- offerLast() : 덱의 뒤에 데이터를 삽입
- peekFirst() : 덱의 앞에 데이터를 리턴
- peekLast() : 덱의 뒤에 데이터를 리턴
- pollFirst() : 덱의 앞에 데이터를 리턴 및 삭제
- pollLast() : 덱의 뒤에 데이터를 리턴 및 삭제
- getSize() : 덱의 사이즈 리턴

## 덱(deque) 사용 사례
- 스케줄링
  - 스케줄링이 복잡해질수록 큐와 스택보다 덱이 더 효율이 잘 나오는 경우가 있음
- 우선순위를 조절하게 될 때
  - ex) 옛날에 있던걸 우선순위를 높이기 위해서는 앞에서 빼낼수 있어야 되는데 스택에서는 불가능함
  - ex) 최근에 들어온걸 우선순위를주고 싶은데 이 역시 큐의 구조에서는 불가능함
  - 결국 앞뒤로 다 인출이 가능한 덱(Deque)만이 이 조건을 충족시킴

## 덱(deque) 구현
- [연결 리스트로 덱 구현](https://github.com/hanull/DataStructures/blob/master/deque/LinkedList_Deque.java)
