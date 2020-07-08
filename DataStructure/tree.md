## 트리(tree) 개념
- 비선형 자료구조로 계층적(망) 관계를 표현한다. ex) 디렉터리 구조, 조직도
- 노드로 이루어진 자료구조이다.
- 오직 하나의 루트 노드를 갖는다.
- 루트 노드는 0개 이상의 자식 노드를 갖고 있다.
- 각 노드는 어떤 자료형으로도 표현할 수 있다.
- 노드들과 노드들을 연결하는 간선(edge)들로 구성되어 있다.
- 사이클이 존재할 수 없다.
- 노드가 N개인 트리는 항상 N-1개의 간선을 가진다.
- 임의의 노드에서 다른 노드로 가는 경로(path)는 유일하다.

![](https://github.com/hanull/TIL/blob/master/DataStructure/img/tree.png)

- 루트 노드(root node): 부모가 없는 노드, 트리는 오직 하나의 루트 노드만을 가진다.
- 단말 노드(leaf node): 자식이 없는 노드, ‘말단 노드’ 또는 ‘잎 노드’라고도 부른다.
- 내부(internal) 노드: 단말 노드가 아닌 노드
- 간선(edge): 노드를 연결하는 선 (link, branch 라고도 부름)
- 형제(sibling): 같은 부모를 가지는 노드
- 노드의 크기(size): 자신을 포함한 모든 자손 노드의 개수
- 노드의 깊이(depth): 루트에서 어떤 노드에 도달하기 위해 거쳐야 하는 간선의 수
- 노드의 레벨(level): 트리의 특정 깊이를 가지는 노드의 집합
- 노드의 차수(degree): 하위 트리 개수 / 간선 수 (degree) = 각 노드가 지닌 가지의 수
- 트리의 차수(degree of tree): 트리의 최대 차수
- 트리의 높이(height): 루트 노드에서 가장 깊숙히 있는 노드의 깊이


## 트리(tree) 종류
- 이진 트리, 이진 탐색 트리, 균형 트리(AVL tree, red-black tree), 이진 힙(최대힙, 최소힙) 등이 있다.

### 이진 트리(Binary Tree)
각 노드가 최대 두 개의 자식을 갖는 트리를 말한다.

- Balanced Tree
  - O(logN) 시간에 insert와 find를 할 수 있을 정도로 균형이 잘 잡혀 있는 경우
  - ex) AVL Tree, Red-Black Tree
- Full Binary Tree
  - 모든 노드가 0개 또는 2개의 child를 갖는 이진트리
- Complete Binary Tree
  - 마지막 레벨을 제외하고 모든 레벨이 완전히 채워져 있다.
  - 마지막 레벨의 노드는 왼쪽 부터 차있어야 한다.
- Perfect Binary Tree
  - 모든 레벨에서 노드가 꽉 차 있는 트리
  - 노드의 개수 = 2^(k-1) , (k : 트리의 높이)

## 트리(tree) 순회

![](https://github.com/hanull/TIL/blob/master/DataStructure/img/traversal.png)

- 중위 순회(Inorder) : Left - Root - Right
  - 4,2,5,1,3
- 전위 순회(Preorder) : Root - Left - Right
  - 1,2,4,5,3
- 후위 순회(Postorder) : Left - Right - Root
  - 4,5,2,3,1

## 트리(tree) 구현
배열이나 연결 리스트를 이용하여 구현할 수 있다. 배열을 이용한 방법은 구현이 쉽고, 인덱스 규칙에 따라 쉽게 노드를 찾을 수 있다. 하지만, 배열로 구현할 때 큰 문제가 있다. 트리의 길게 한쪽으로 기울어져 있다면, 배열에는 빈 공간이 많이 발생하게 되어 `메모리를 낭비`하게 된다. 또한, 삽입/삭제 시 비효율적이기 때문에 연결 리스트 방법을 주로 사용한다.

- [이진 트리(Binary Tree) 및 순회 알고리즘 구현](https://github.com/hanull/DataStructures/blob/master/tree/BinaryTree.java)


## 참고자료
- [Heee's Development Blog](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)
- [ratsgo's blog](https://ratsgo.github.io/data%20structure&algorithm/2017/10/21/tree/)
- [엔지니어대한민국 youtube](https://www.youtube.com/watch?v=LnxEBW29DOw&list=PLjSkJdbr_gFY8VgactUs6_Jc9Ke8cPzZP)
