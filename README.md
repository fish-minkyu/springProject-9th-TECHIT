## 기초 설명
#### 실행하기에 앞서...
JPA-Hibernate를 통해 SQLite를 DB로 사용했습니다. 

본 프로젝트는 ddl-auto가 update로 초기 설정이 되어있습니다.
참고 바랍니다.
```yaml
  jpa:
    hibernate:
    ddl-auto: update
```

또한, 8080 포트가 아닌 3000포트를 사용하였습니다.
랜딩 페이지의 주소는 ```http://localhost:3000/boards``` 이므로 여기서부터 시작하면 됩니다.  

### 사용 라이브러리
- Spring Web
- Lombok
- JPA
- SQLite
- Thymeleaf

## 진행 중 발생한 어려움

### 1. 게시글 작성 페이지로 가는 버튼을 명확히 명시되어 있지 않아 혼란스러웠다.
명세 페이지를 잘 찾아봐도 게시글 작성 페이지로 갈 수 있는 버튼 위치가 명시되어 있지 않아 혼란스러웠다.  

### 2. password를 확인하는 로직이 헷갈렸다.
게시글 상세페이지에서 바로 비밀번호를 확인할지 아님 따로 페이지를 만들어서 할지 고민이 되었다.

### 3. password를 확인하는 페이지 로직 중복
하나의 password 페이지를 만들어서 Method에 따라 분기처리하여 페이지를 반환하고 싶었지만
정확히 방법을 몰라서 같은 페이지를 출력하는 코드 로직이 중복이 되었다.

### 4. Entitly가 아닌 Dto를 사용하고 싶었다.
수업에선 데이터를 왔다갔다 할 때, Entity를 바로 사용해주었지만 Dto를 쓰고 싶었다.
하지만, thymeleaf에서 Dto를 활용하는 방법이 워낙 복잡하고, 복습이 부족해 기존 배웠던 로직도 구현하기 힘들어 포기하였다.

### 5. redirect를 왜 하는지, 또한 새로 고침 시, 양식 재제출을 막는 것이 redirect인 걸로 알고 있는데 잘 안되었다.

### 6. ```th:ref@{/경로/{id}/(id=${id})/path}```과 ```th:ref@{/경로/{id}/path/(id=${id})}```은 같은데 될 때가 있고 안될 때가 있어서 힘들었다.

### 7. 수정 페이지에서 이미 있는 content 내용이 나오지 않아 해결 방법을 찾지 못하였다.

## 프로젝트 실행방법

##### 게시판 둘러보기, 게시글 생성, 댓글 생성
1. 프로젝트 실행
2. ```localhost:3000/boards```에 접속합니다.
3. 자유 게시판, 개발 게시판, 일상 게시판, 사건사고 게시판 중 원하는 게시판에 접속합니다.
4. 게시판별 페이지 접속 후, 게시글 작성을 할 수 있습니다. (게시글 작성 시, 비밀번호는 필수값입니다.)
5. 상세 게시글을 들어가면 수정버튼(Edit)과 삭제버튼(Delete)을 확인할 수 있습니다.
6. 댓글 쓰기부터 게시글별 댓글을 확인할 수 있고, 댓글 생성을 할 수 있습니다. (게시글 작성 시, 비밀번호는 필수값입니다.)

##### 게시글 수정
1. 게시글 상세페이지에서 ```Edit```버튼을 클릭합니다.
2. 비밀번호를 확인하는 페이지로 이동하여 작성 시 입력했던 비밀번호를 넣어줍니다.
3. 비밀번호가 맞으면 update-view로 이동, 틀리면 틀렸다는 경고창이 뜹니다.
4. 수정 페이지에서 전부 수정 후, 제출 버튼을 눌러주십시오

##### 게시글 삭제, 댓글 삭제
1. 게시글 상세페이지에서 ```Delete``` 버튼을 누릅니다.
2. 비밀번호를 확인하는 페이지로 이동하여 작성 시 입력했던 비밀번호를 넣어줍니다.
3. 비밀번호가 맞으면 바로 삭제된 후, 전체 게시글 리스트로 이동합니다.
4. 댓글 삭제는 게시글 상세페이지에서 ```댓글 삭제``` 버튼을 눌러줍니다.
5. 비밀번호를 확인하는 페이지로 이동하여 작성 시 입력했던 비밀번호를 넣어줍니다.
6. 비밀번호가 맞으면 게시글 상세 페이지로 다시 돌아옵니다.
7. 비밀번호가 틀리면 경고창이 뜹니다.