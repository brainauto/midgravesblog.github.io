---
title: "정보처리기사 필기 2과목 소프트웨어개발 2"
last_modified_at: 2023-01-17 14:00:00 + 09:00
categories:
  - Certificate
tags:
  - Engineer Information Processing
---

데이터 입출력 구현 B 자료구조
===

트리의 순회 방법 
---

트리의 순회 방법 


* 전위 순회
  * 중간 노드 -왼쪽 서브트리 - 오른쪽 서브트리

* 중위 순회
  * 왼쪽 서브트리 - 중간 노드 - 오른쪽 서브트리 

* 후위 순회
  * 왼쪽 서브트리 - 오른쪽 서브트리 - 중간 노드


<img src="/assets/images/full_binary_tree.png" width="80%" height="80%" title="포화이진트리" alt="이미지 보여줄 수 없을때 보일 텍스트"/>

위 포화이진트리 그림을 예시로 각 순회 방법을 설명하면 아래처럼 그릴 수 있다.


전위 순회
<img src="/assets/images/Preorder_Traversal.png" width="80%" height="80%" title="전위 순회" alt="이미지 보여줄 수 없을때 보일 텍스트"/>


중위 순회
<img src="/assets/images/Inorder_Traversal.png" width="80%" height="80%" title="중위 순회" alt="이미지 보여줄 수 없을때 보일 텍스트"/>


후위 순회
<img src="/assets/images/Postorder_Traversal.png" width="80%" height="80%" title="후위 순회" alt="이미지 보여줄 수 없을때 보일 텍스트"/>


추가 트리 용어 정리

* 루트 노드(root node) : 부모가 없는 노드. 트리는 하나의 루트 노드만을 가진다.
* 단말 노드(leaf node) : 자식이 없는 노드이다.
* 내부(internal) 노드  : 리프 노드가 아닌 노드.
* 링크(link)           : 노드를 연결하는 선 (edge, branch 라고도 부름).
* 형제(sibling)        : 같은 부모를 가지는 노드.

* 노드의 크기(size) : 자신을 포함한 모든 자손 노드의 개수.
 * A의 크기 : 7
 * B의 크기 : 3
* 노드의 깊이(depth) : 루트에서 어떤 노드에 도달하기 위해 거쳐야 하는 간선의 수
 * B의 깊이 : 1
 * C의 깊이 : 2
* 노드의 레벨(level) : 트리의 특정 깊이를 가지는 노드의 집합
 * A의 레벨 : 1
 * B, E의 레벨 : 2
 * C, D, F, G의 레벨 : 3
* 노드의 차수(degree) : 부(하위) 트리 갯수/간선수 (degree) = 각 노드가 지닌 가지의 수
 * A의 차수 = 2
 * B의 차수 = 2
 * C의 차수 = 0
* 트리의 차수(degree of tree) : 트리의 최대 차수
 * A, B, E가 최대 차수를 가짐 => 2
* 트리의 높이(height) : 루트 노드에서 가장 깊숙히 있는 노드의 깊이
 * 3

***


그래프
---

그래프는 객체간의 관계를 표현할 수 있는 자료구조

종류
* 무방향 그래프 : 화살표 없음
* 방향 그래프 : 화살표 있음

특징
* 네트워크 모델이며 2개 이상의 경로가 가능하다. 자기 자신을 향하는 간선은 없으며 중복 간선은 허용하지 않음


그래프는 아래와 같이 행렬로 변환 할 수 있다.

그래프 to 행렬
<img src="/assets/images/gragh_Matrix.png" width="80%" height="80%" title="그래프와 행렬" alt="이미지 보여줄 수 없을때 보일 텍스트"/>



추가로 최소비용 신장트리도 있음 아래 그림처럼  어디하나 끊어져서 순환 구조가 없는 그림

* 신장트리 최대 간선 수 = n-1 개

그래프 to 행렬
<img src="/assets/images/minimun_Spanning_ Tree.png" width="80%" height="80%" title="최소비용신장트리" alt="이미지 보여줄 수 없을때 보일 텍스트"/>

