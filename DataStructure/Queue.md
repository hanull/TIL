## 큐(Queue) 개념
- 삽입은 한쪽 끝에서, 삭제는 반대쪽 끝에서만 일어난다.
- FIFO(First In First Out, 선입선출) : 가장 먼저 들어온 것이 가장 먼저 나오는 형식.
- 큐의 가장 첫 원소를 front, 끝 원소를 rear라고 부름.
- 데이터는 큐의 rear쪽으로 들어오고, front 부터 빠지게 된다.

## 큐(Queue) 연산
- enqueue(data) : 데이터를 리스트의 끝 부분에 추가한다.
- dequeue()	: 리스트의 첫 번째 데이터를 삭제한다.
- peek()	: 큐의 첫 번째 데이터를 반환한다.
- isEmpty()	: 큐가 	비어있을 경우 true를 반환한다.

## 큐(Queue) 사용 사례
***데이터가 입력된 시간 순서대로 처리해야 할 필요가 있는 상황에서 사용.***
- cpu 스케줄링	: 멀티테스킹 환경에서 프로세스들은 큐에서 cpu가 할당되기를 기다린다.
- 버퍼			: 네트워크를 통해 전송되는 패킷들은 도착 순서대로 버퍼에 저장되어 처리되기를 기다린다.
- bfs			: 처리할 리스트를 저장하는 용도로 사용. 노드를 하나 처리할 때마다 해당 노드와 인접한 노드를 다시 큐에 저장.
- 프린터의 출력
- 티켓 카운터


## 큐(Queue) 구현

```java
public interface Queue {
  void enqueue(T data);
  T dequeue();
  T peek();
  boolean isEmpty();
}
```

- [배열로 큐 구현하기](https://github.com/hanull/DataStructures/blob/master/queue/Array_Queue.java)
- [스택으로 큐 구현하기](https://github.com/hanull/DataStructures/blob/master/queue/Stack_Queue.java)
- [연결 리스트로 큐 구현하기](https://github.com/hanull/DataStructures/blob/master/queue/LinkedList_Queue.java)
