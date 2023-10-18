# Oracle Live SQL

- Oracle Live SQL은 Oracle 데이터베이스가 빌트인되어있는 웹기반 SQL editor 다.
- Live SQL은 Oracle 데이터베이스 19c Enterprise Edition 버전을 실행시킨다.
- [https://livesql.oracle.com](https://livesql.oracle.com)



## 사용 방법
1. 위 링크로 들어가 오라클 계정 로그인을 한다. <br/>
    <img src="../img/oracle_live_sql_1.png" width="70%"></img>
    <br>

2. **"start coding"** 버튼을 눌러 시작한다. <br/>
    <img src="../img/oracle_live_sql_2.png" width="80%"></img>
    <br>

3. SQL worksheet에 쿼리를 입력하면 실행할 수 있다. 실행하기 위해서는 우측 상단 **"Run"** 버튼을 누른다. SQL worksheet는 세션이 유지되고 있는 한 이전 정보/쿼리들을 저장한다. <br/>
    <img src="../img/oracle_live_sql_3.png" width="80%"></img>



## Oracle 기본 제공 스키마 사용법 1 (Read Only)
- SQL Worksheet 페이지에서 왼쪽 상단 메뉴 버튼을 누르면, "Schema" 항목이 있다.
- 원하는 스키마를 선택하면 해당 스키마에 대해  READ-ONLY ACCESS를 가지게 된다. <br/>
<img src="../img/oracle_live_sql_4.png" width="100%"></img> <br/>


## Oracle 기본 제공 스키마 사용법 2 (For Manipulating)
- 위 방법은 READ-ONLY 접근을 가지기 때문에 테이블 데이터를 수정할 수 없다.
- 따라서, 실습을 위해 데이터를 수정할때는 worksheet에서 직접 원하는 스키마의 테이블 생성 및 데이터 삽입을 해야한다.
- schema list
    | schema | link |
    | --- | --- |
    | Scott | [scott.sql](./scott.sql) |
