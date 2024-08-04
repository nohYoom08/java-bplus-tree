# 데이터베이스 과제 중 B+Tree 구현
* 대학 전공수업 중 데이터베이스 과목에서 m-way의 B+Tree를 구현하는 과제이다.
* m의 값과 삽입 및 삭제할 데이터를 모두 임의로 설정할 수 있다.
<br><br><br><br>

## 파일 구성 설명

### App.java
실제 과제 수행 여부를 검사할 테스트 코드가 형식에 맞게 구현되어 있다.
<br><br>

### MyBPlusTree.java
B+Tree의 탐색, 삽입, 삭제 등의 기능들이 MyBPlusTree 클래스 내에서 오버라이드된 여러 메소드들을 통해서 구현되어있다.
<br><br>

### MyBPlusTreeNode.java
루트노드를 포함한 단일 B+Tree의 노드가 구현되어있다.
<br><br><br><br>

## 삽입 및 삭제시 주의사항
아래에는 실제 구현방식마다 다를 수 있는 상황과 그에 따른 해당 리포지토리의 구현방식 기준에 대한 내용이다.
<br><br>

### m이 홀수이며 잎새노드가 아닌 노드에서 max_key를 넘을 시
* 인덱스 [m/2]\(가우스기호)의 key가 부모노드에 삽입된다.
<br><br>

### min-key property 조사에 따른 삭제 우선순위 :
1. 왼쪽 형제노드 존재함 + min-key property 만족 > 왼쪽 형제노드에서 키값 가져오기 > 트리 유지
2. 1번의 케이스를 만족 못할 시 : 오른쪽 형제노드 존재함 + min-key property 만족 > 오른쪽 형제노드에서 키값 가져오기 > 트리 유지
3. 1,2번의 케이스를 만족 못할 시 : 왼쪽 형제노드 존재함 > 왼쪽 형제노드 기준으로 부모노드와 합병 > 트리 유지
4. 1,2,3번의 케이스도 만족 못할 시 : 오른쪽 형제노드 존재함 > 오른쪽 형제노드 기준으로 부모노드와 합병 > 트리 유지
