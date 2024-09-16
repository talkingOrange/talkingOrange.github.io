---
layout: post
title:  "[SpringBoot] CRUD REST API 작성하기"
date:   2024-09-16
categories: Java
---
# [SpringBoot] CRUD REST API 작성하기
--- 

```
# REST API: REST를 기반으로 만들어진 API
# REST: Representational State Transfer의 약자로, 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것
  - HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고,
  - HTTP Method(POST, GET, PUT, DELETE, PATCH)를 통해 
  - 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미
```

```
# HTTP 프로토콜과 CRUD의 관계

1. POST - Create
- 데이터를 생성하기 위해 사용 (INSERT)
- Body (o)
2. GET - READ
- 데이터를 조회하기 위해 사용 (SELECT)
- Body (x) - URL로 정보 요청
3. PUT - Update
- 데이터를 수정하기 위해 사용 (UPDATE)
- Body (o)
4. DELETE - Delete
- 데이터를 삭제하기 위해 사용 (DELETE)
- Body (x)
```

```
# PUT과 PATCH의 차이

- PUT: 리소스의 모든 것을 업데이트
보내지지 않은 정보에 대해서는 null값으로 업데이트
- PATCH: 리소스의 일부를 업데이트
보내지지 않은 정보에 대해 기존 데이터를 유지하는 방식으로 대응
```

1. Postman 
개발한 API를 테스트하고, 테스트 결과를 공유하여 API 개발의 생산성을 높여주는 플랫폼

2. CRUD 예제
/posts 경로로 접근하여 Post DB의 데이터를 CRUD 할 수 있도록 Rest API 작성

```
# GET
- /posts: Post 테이블의 모든 데이터 보여주기
- /posts/{id}: id(primary key)가 일치하는 Post 데이터 보여주기
- /posts?userId={userId}: userId가 일치하는 Post 데이터 보여주기
# POST
- /posts: 새로운 Post 데이터 생성
# PUT
- /posts/{id}: id가 일치하는 Post 데이터 수정
# DELETE
- /posts/{id}: id가 일치하는 Post 데이터 삭제
```


3. application.properties 추가
DB 정보와 Mapper.xml 파일 위치 설정해준다.

![image](https://velog.velcdn.com/images/wooryung/post/d6644616-9a56-4467-a455-ea3ac8458a12/image.png)

5. VO 작성
DB의 데이터에 접근할 수 있도록 PostVo.java를 작성한다.

- Post 테이블 구조


![image](https://github.com/user-attachments/assets/7e88c585-759d-4e7f-ace0-3381991b16ee)


- 테이블 구조에 맞게 데이터 타입과 컬럼명을 작성한다.

![image](https://velog.velcdn.com/images/wooryung/post/b2ba3ee3-2c4f-4158-9b32-8188d5d6f7d8/image.png)


5. GET 요청 처리하기
1) mapper.xml 작성
PostMapper.xml에 Post 테이블의 전체 데이터를 가져오는 SQL문과 userId 또는 id가 일치하는 데이터를 가져오는 SQL문을 작성한다.
![image](https://github.com/user-attachments/assets/87562ef9-07c1-4d27-85a1-eb993d71af0e)


2) Mapper 인터페이스 작성
PostMapper.java에 getPostList와 getPostListByUserId, getPostById 메서드를 선언한다.

- getPostList는 Post 테이블의 전체 데이터를 가져오는 메서드이므로 매개변수가 필요없으며, PostVo 타입의 데이터들을 List에 담아 반환한다.
  + 테이블이 비어있을 때는 null이 아니라 빈 리스트가 반환된다. → null 값으로 데이터 체크 금지! (null은 나올 수가 없는 값)

- getPostListByUserId는 userId(Post 테이블이 User 테이블에서 참조하고 있는 Foreign Key) 값에 따라 데이터를 가져오는 메서드이므로 매개변수로 userId가 필요하며, PostVo 타입의 데이터를 List에 담아 반환한다.

- getPostById는 id(Post 테이블의 Primary Key) 값에 따라 데이터를 가져오는 메서드이므로 매개변수로 id가 필요하며, id에 따른 Post 데이터는 1개씩 존재하므로 PostVo 타입의 데이터를 반환한다.
  + 데이터가 존재하지 않으면 null을 반환

![image](https://github.com/user-attachments/assets/cdf0c540-d824-4400-880e-5bcc553673af)


3) Service 작성
PostService.java에 PostMapper의 getPostList와 getPostListByUserId, getPostById 메서드를 호출하여 로직을 수행하는 메서드를 작성한다.

![image](https://github.com/user-attachments/assets/ef903bd0-6bad-43d9-9c0e-35385e5c643f)


4) Controller 작성
PostController.java에 GET 요청을 처리하는 controller를 작성한다.

![image](https://github.com/user-attachments/assets/675bda18-63f1-4997-8151-ca71dbcf0a65)

```
# @Controller와 @RestController의 차이

- @Controller: view를 반환
- @RestController: JSON과 같은 데이터를 반환
- 현재 프로젝트에서는 JSON 형식의 데이터를 처리하므로 @RestController annotation을 사용한다.
```

6. POST 요청 처리하기
1) mapper.xml 작성
PostMapper.xml에 새로운 Post 데이터를 추가하는 SQL문을 작성한다.

![image](https://github.com/user-attachments/assets/e2a6c7e8-1253-4249-99a2-c969700b9dec)


2) Mapper 인터페이스 작성
PostMapper.java에 insertPost 메서드를 선언한다.

- insertPost는 Post 테이블에 새로운 데이터를 추가하는 메서드이므로 PostVo 타입의 데이터가 매개변수로 필요하며, 테이블에 insert 된 행의 개수를 int로 반환한다.

![image](https://github.com/user-attachments/assets/e2816536-1365-42ce-a85f-13f6c65aecce)

```
# int 타입의 insert, update, delete 메서드

- SQL의 영향을 받은 행의 개수를 반환
→ 0을 반환한다면 sql문은 성공적으로 실행됐으나 테이블에서 영향을 받은 행이 없다는 의미. 실패했다는 의미가 아니다!
- insert는 데이터를 추가하는 것이므로 0을 반환할 수 없다.
→ 0으로 테스트 금지!
```

```
# MyBatis Query return 값

- Select
성공: Select문에 해당하는 결과
실패: 에러

- Insert
성공: 1 (여러개인 경우도 1)
실패: 에러

- Update
성공: Update된 행의 개수 (없으면 0)
실패: 0

- Delete
성공: Delete된 행의 개수 (없으면 0)
실패: 에러
```

3) Service 작성
PostService.java에 PostMapper의 insertPost 메서드를 호출하여 로직을 수행하는 메서드를 작성한다.
![image](https://github.com/user-attachments/assets/96b81c0b-c56f-4f6c-8c32-be1ed12dc535)


4) Controller 작성
PostController.java에 POST 요청을 처리하는 controller를 작성한다.

- POST request가 올 때 Body에 담겨온 데이터를 PostVo 타입의 객체에 담아 postService의 createPost 메서드에 넘겨주어 새로운 Post를 생성하는 로직을 수행한다.

![image](https://github.com/user-attachments/assets/409d066d-9c03-429e-b8e6-3ae16ed11bdf)


7. PUT 요청 처리하기
1) mapper.xml 작성
PostMapper.xml에 id가 일치하는 Post 데이터를 수정하는 SQL문을 작성한다.

![image](https://github.com/user-attachments/assets/57910154-6bcd-430e-b138-cc9bc771f59d)


2) Mapper 인터페이스 작성
PostMapper.java에 updatePost 메서드를 선언한다.

- updatePost는 Post 테이블에서 id가 일치하는 데이터를 수정하는 메서드이므로 PostVo 타입의 데이터가 매개변수로 필요하며, 테이블에서 update 된 행의 개수를 int로 반환한다.

![image](https://github.com/user-attachments/assets/2781f936-485a-4e52-a098-aed340d45781)


3) Service 작성
PostService.java에 PostMapper의 updatePost 메서드를 호출하여 로직을 수행하는 메서드를 작성한다.

![image](https://github.com/user-attachments/assets/c070fd5c-e3d8-44e7-badd-f7881dd909c7)


4) Controller 작성
PostController.java에 PUT 요청을 처리하는 controller를 작성한다.

- path variable로 넘어온 id를 PostVo 타입의 객체의 id로 설정해준다.

- PUT request가 올 때 Body에 담겨온 데이터를 PostVo 타입의 객체에 담아 postService의 updatePost 메서드에 넘겨주어 id로 검색한 Post 데이터를 수정하는 로직을 수행한다.

![image](https://github.com/user-attachments/assets/1ec56175-0e18-46a7-b001-fb6c046db5dc)



8. DELETE 요청 처리하기
1) mapper.xml 작성
PostMapper.xml에 id가 일치하는 Post 데이터를 삭제하는 SQL문을 작성한다.

![image](https://github.com/user-attachments/assets/02773920-b3a9-4ccf-a95f-5f05f93b0b90)


2) Mapper 인터페이스 작성
PostMapper.java에 deletePost 메서드를 선언한다.

- deletePost는 Post 테이블에서 id가 일치하는 데이터를 삭제하는 메서드이므로 id가 매개변수로 필요하며, 테이블에서 delete 된 행의 개수를 int로 반환한다.

![image](https://github.com/user-attachments/assets/e2b40ccf-3b54-47d3-83ea-d013d84d0824)


3) Service 작성
PostService.java에 PostMapper의 deletePost 메서드를 호출하여 로직을 수행하는 메서드를 작성한다.

![image](https://github.com/user-attachments/assets/80bef62c-9320-48f9-9be5-679fab67cf45)


4) Controller 작성
PostController.java에 DELETE 요청을 처리하는 controller를 작성한다.

- path variable로 넘어온 id를 postService의 deletePost 메서드에 넘겨주어 id로 검색한 Post 데이터를 삭제하는 로직을 수행한다.

![image](https://github.com/user-attachments/assets/90647c30-230f-49fa-922a-7e686e208271)


9. 실행 화면

![image](https://github.com/user-attachments/assets/71fc630f-8bbb-4dcd-9cb1-6594c54316be)


![image](https://github.com/user-attachments/assets/17a1872b-bbfc-4888-bf6c-e28aa5f5e27b)

![image](https://github.com/user-attachments/assets/36a0991e-213b-4e42-9472-9fb22f6753c7)




