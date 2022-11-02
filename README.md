# Spring Boot Toy Project
블로그 구현 프로젝트

## ⚙ 프로젝트 개발 환경
- 통합개발환경 : Eclipse
- JDK 버전 : JDK 17
- 스프링부트 버전 : 2.7.1
- 사용 DB : H2
- 빌드툴 : Maven
- 관리툴 : Git, Github

## ⚒ 기술 스택
- Backend
    - Spring Boot
    - Spring Security
    - Spring Devtools
    - Spring Data Jpa
    - Lombok


- Frontend
    - JSP
    - JSTL
    - Jasper
    - Bootstrap
    - Jquery
    - Spring Security Taglibs


- Database
    - H2

---

## 초반 구성
프로젝트를 시작하면 ADMIN 권한과 USER 권한을 가진 두 개의 아이디가 추가되도록 설정
>ADMIN 계정
ID   = test
PW = test

> USER 계정
ID   = aaa
PW = aaa


Spring Security를 이용해 로그인/로그아웃 및 페이지 권한 설정  
로그인을 하지 않은 유저는 블로그목록 조회/검색 및 블로그 조회, 블로그의 게시글 조회 및 카테고리별 검색 가능
> 게시글 수정/삭제 버튼은 뜨지만 클릭하면 로그인 화면으로 이동.

---

## 메인화면
- 블로그 검색을 클릭하면 대소문자 구분 없이 해당 문자열이 포함된 게시글 또는 태그 결과 출력(새로고침 눌러도 값 그대로 유지.)
- 상단 블로그 로고 이미지를 누르면 검색결과 및 블로그 리스트가 초기화된 메인화면 이동.
- 블로그 개수가 5개가 넘어가면 다음페이지 활성화.
- `ADMIN` 권한을 가진 아이디로 로그인하면 `삭제` 테이블 활성화.
- 상태가 `삭제요청` 인 블로그만 삭제 가능.
- 우측 삭제 이미지를 클릭하면 `삭제가 완료되었습니다` 출력 후 블로그 리스트 갱신
- `로그인`버튼을 누르면 로그인 페이지로 이동.
- `로그아웃` 버튼을 누르면 로그아웃 되고 메인페이지 이동.
- 로그인 완료 후 블로그를 소유하고 있지 않으면 `블로그등록` 버튼 활성화. 소유하고 있으면 `블로그바로가기` 버튼 활성화
- 블로그를 이미 보유중인데 블로그 등록을 하면 `이미 블로그를 보유하고 계십니다` 창 뜨고 메인화면 이동.
- `블로그바로가기` 버튼을 누르면 자신이 생성한 블로그로 이동.

---

## 블로그 화면
- 메인페이지
    - 우측 상단에 `블로그관리` 버튼을 누르면 블로그 관리 페이지로 이동.
    - `블로그메인`  버튼을 누르면 블로그 메인화면(게시글 목록)으로 이동.
    - `로그아웃` 버튼을 누르면 로그아웃 된 후 메인화면(블로그 목록)으로 이동
    - 우측 카테고리에 있는 카테고리들 중 하나를 선택하면 해당 태그에 해당하는 게시글만 출력
    - 우측 하단 블로그 로고를 누르면 메인화면(게시글 목록) 으로 이동.
    - 게시글이 3개이상 있으면 `다음페이지` 버튼 활성화
    - 게시글 보이기 유형이 `제목` 이면 제목만 보이게, `제목 + 내용` 이면 제목과 내용 둘 다 보이게 출력
    - 게시글 우측 `수정` 버튼을 누르면 게시글 수정 페이지로 이동
    - 게시글 수정 페이지에서 제목과 내용, 태그를 선택 후 `수정하기` 버튼 누르면 `수정에 성공하였습니다` 출력 후 블로그 메인화면(게시글 목록)으로 이동.
    - 게시글 우측 `삭제` 버튼을 누르면 `게시글 삭제가 완료되었습니다` 출력 후 게시글 목록 갱신
- 관리페이지
    - 기본설정
        - 블로그 제목과 태그에 현재 블로그 제목과 태그가 입력 된 채로 로딩
        - 원하는 블로그 제목과 태그를 입력 후 `수정하기` 버튼 누르면 블로그 제목과 태그가 변경됨.
    - 카테고리
        - 카테고리 번호 기준으로 내림차순 정렬된 채로 출력.
        - `미분류` 카테고리는 수정/삭제 불가능
        - 우측 삭제 이미지를 클릭하면 `카테고리 삭제가 완료되었습니다` 출력 후 해당 카테고리 삭제
        - 카테고리명 클릭하면 카테고리 수정 페이지로 이동.
        - `카테고리 추가` 버튼을 누르면 `카테고리 추가가 완료되었습니다.` 출력 후 카테고리 목록 갱신
        - `카테고리 수정` 버튼을 누르면 `카테고리 수정이 완료되었습니다.` 출력 후 카테고리 목록 갱신
        - 만약 카테고리 추가/수정을 할 때 이미 그 카테고리 명이 존재하면 `이미 존재하는 카테고리명입니다.` 출력
    - 글작성
        -  제목과 내용, 그리고 카테고리를 선택 후 `등록하기` 버튼 누르면 `글 작성이 완료되었습니다.` 출력 후 게시글 등록
    - 블로그삭제
        - `블로그삭제` 버튼을 누르면 블로그를 정말 삭제하는지 물어보는 팝업 창이 뜬 후 해당 팝업 창에서 `동의` 버튼 누르면 로그아웃 후 메인페이지로 이동.
        - 메인페이지에서 상태가 `운영` 에서 `삭제요청` 으로 변경 
