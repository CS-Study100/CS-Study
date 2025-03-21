## 4-5. 트리

> 계층적인 구조를 표현하기 위한 자료구조
> 

| 용어 | 설명 |
| --- | --- |
| 노드 | 트리 자료구조에서 데이터를 저장하는 구성 요소 |
| 간선 | 트리 자료구조에서 노드를 연결하는 구성 요소 |
| 부모 노드 | 어떤 노드의 상위에 연결된 노드 |
| 자식 노드 | 어떤 노드의 하위에 연결된 노드 |
| 루트 노드 | 트리의 최상위 노드, 부모 노드가 없는 노드 |
| 리프 노드 | 트리의 최하위 노드, 자식 노드가 없는 노드 |
| 차수 | 어떤 노드가 가지고 있는 자식 노드의 수 |
| 레벨 | 루트 노드에서 시작해 특정 노드에 이르기까지 거치게 되는 간선의 수 |
| 서브 트리 | 트리에 포함되어 있는 부분 트리 |

<img width="372" alt="Image" src="https://github.com/user-attachments/assets/adb6e6e9-f714-4082-9bab-e3526d7b9097" />

- 하나의 노드를 데이터를 저장할 공간과 자식 노드의 위치 정보를 저장할 공간의 모음으로 간주

### 1️⃣ 트리의 순회

1. **전위 순회(preorder traverse)**: 루트 → 왼쪽 → 오른쪽
    
    ```cpp
    전위 순회(노드):
    	if 노드가 존재하지 않으면 return
    	노드값 출력
    	전위 순회(노드의 왼쪽 자식)
    	전위 순회(노드의 오른쪽 자식)
    ```
    
2. **중위 순회(inorder traverse)**: 왼쪽 → 루트 → 오른쪽
    
    ```cpp
    중위 순회(노드):
    	if 노드가 존재하지 않으면 return
    	중위 순회(노드의 왼쪽 자식)
    	노드값 출력
    	중위 순회(노드의 오른쪽 자식)
    ```
    
3. **후위 순회(postorder traverse)**: 왼쪽 → 오른쪽 → 루트
    
    ```cpp
    후위 순회(노드):
    	if 노드가 존재하지 않으면 return
    	후위 순회(노드의 왼쪽 노드)
    	후위 순회(노드의 오른쪽 노드)
    	노드값 출력
    ```
    
- **레벨 순서 순회(level-order traverse)**: 레벨의 순서대로 노드를 순회하는 방법

### 2️⃣ 트리의 종류

1. **이진 트리(binary tree)**: 자식 노드의 개수가 2개 이하인 트리
    - 편향된 이진 트리(skewed binary tree): 모든 자식 노드가 한 쪽으로 치우친 경우
    - **정 이진 트리(full binary tree)**: 자식 노드의 개수가 1개가 아닌 이진 트리(0 개 or 2개)
    - **포화 이진 트리(perfect binary tree)**: 리프 노드를 제외한 모든 노드들이 자식 노드를 2개씩 가지고 있고, 모든 리프 노드의 레벨이 동일한 이진 트리
    - **완전 이진 트리(complete binary tree)**: 마지막 레벨을 제외한 모든 레벨이 2개의 자식 노드를 가지고 있으며, 마지막 레벨의 모든 노드들이 왼쪽부터 존재하는 이진 트리
2. 탐색에 활용되는 트리: 이진 탐색 트리와 힙
    - **이진 탐색 트리(BST, Binary Search Tree)**: 특정 노드의 왼쪽 서브트리에는 해당 노드보다 작은 값을 지닌 노드/ 오른쪽 서브트리에는 해당 노드보다 큰 값을 지닌 노드들이 있는 구조 → $O(logn)$ / 최악의 상황: $O(n)$ (한 쪽으로 편향된 경우)
    - **힙(heap)**: 완전 이진 트리의 종류 중 하나, 최댓값과 최솟값을 찾기 위해 사용
        - 우선순위 큐는 최대 힙으로 구현
3. 균형을 맞추는 트리: RB 트리
    - **자가 균형 이진 탐색 트리(self-balancing binary search tree)** → AVL 트리, RB 트리 등
4. 대용량 입출력을 위한 트리: B 트리
    - 다진 탐색 트리의 한 종류(한 노드가 여러 자식 노드를 가질 수 있는 트리)
    - 한 노드가 가질 수 있는 자식 노드의 최소, 최대 개수가 정해져 있음
    - 최대 자식 노드의 개수가 M개인 B 트리 → M차 B 트리
    - 최소 자식 노드의 개수 → $\lceil M/2 \rceil$ 개
    - 하나 이상의 키 값이 존재하고,각 키들이 오름차순으로 저장되어 있음
    - 모든 리프 노드의 깊이가 같음
    - 파일 시스템, 데이터베이스와 같이 대량의 데이터를 기반으로 탐색, 접근, 저장을 수행할 때 활용
    - 트라이, 세그먼트 트리, 펜윅 트리 등