
해당 문서는 liveSQL에서 SQL script 를 실행하기 위한 가이드를 제공한다. <br/>

1. 먼저 들어가기 앞서서, `my_schema`(기본 창)에서 scott schema 내의 데이터를 모두 로드한다.

    ```SQL
    DROP TABLE DEPT;
    CREATE TABLE DEPT (
        DEPTNO NUMBER(2) CONSTRAINT PK_DEPT PRIMARY KEY,
    DNAME VARCHAR2(14) ,
    LOC VARCHAR2(13) ) ;

    DROP TABLE EMP;
    CREATE TABLE EMP(
        EMPNO NUMBER(4) CONSTRAINT PK_EMP PRIMARY KEY,
    ENAME VARCHAR2(10),
    JOB VARCHAR2(9),
    MGR NUMBER(4),
    HIREDATE DATE,
    SAL NUMBER(7,2),
    COMM NUMBER(7,2),
    DEPTNO NUMBER(2) CONSTRAINT FK_DEPTNO REFERENCES DEPT);
    INSERT INTO DEPT VALUES (10,'ACCOUNTING','NEW YORK');
    INSERT INTO DEPT VALUES (20,'RESEARCH','DALLAS');
    INSERT INTO DEPT VALUES (30,'SALES','CHICAGO');
    INSERT INTO DEPT VALUES (40,'OPERATIONS','BOSTON');
    INSERT INTO EMP VALUES (7369,'SMITH','CLERK',7902,to_date('17-12-1980','dd-mm-yyyy'),800,NULL,20);
    INSERT INTO EMP VALUES (7499,'ALLEN','SALESMAN',7698,to_date('20-2-1981','dd-mm-yyyy'),1600,300,30);
    INSERT INTO EMP VALUES (7521,'WARD','SALESMAN',7698,to_date('22-2-1981','dd-mm-yyyy'),1250,500,30);
    INSERT INTO EMP VALUES (7566,'JONES','MANAGER',7839,to_date('2-4-1981','dd-mm-yyyy'),2975,NULL,20);
    INSERT INTO EMP VALUES (7654,'MARTIN','SALESMAN',7698,to_date('28-9-1981','dd-mm-yyyy'),1250,1400,30);
    INSERT INTO EMP VALUES (7698,'BLAKE','MANAGER',7839,to_date('1-5-1981','dd-mm-yyyy'),2850,NULL,30);
    INSERT INTO EMP VALUES (7782,'CLARK','MANAGER',7839,to_date('9-6-1981','dd-mm-yyyy'),2450,NULL,10);
    INSERT INTO EMP VALUES (7788,'SCOTT','ANALYST',7566,to_date('13-JUL-87')-85,3000,NULL,20);
    INSERT INTO EMP VALUES (7839,'KING','PRESIDENT',NULL,to_date('17-11-1981','dd-mm-yyyy'),5000,NULL,10);
    INSERT INTO EMP VALUES (7844,'TURNER','SALESMAN',7698,to_date('8-9-1981','dd-mm-yyyy'),1500,0,30);
    INSERT INTO EMP VALUES (7876,'ADAMS','CLERK',7788,to_date('13-JUL-87')-51,1100,NULL,20);
    INSERT INTO EMP VALUES (7900,'JAMES','CLERK',7698,to_date('3-12-1981','dd-mm-yyyy'),950,NULL,30);
    INSERT INTO EMP VALUES (7902,'FORD','ANALYST',7566,to_date('3-12-1981','dd-mm-yyyy'),3000,NULL,20);
    INSERT INTO EMP VALUES (7934,'MILLER','CLERK',7782,to_date('23-1-1982','dd-mm-yyyy'),1300,NULL,10);

    DROP TABLE BONUS;
    CREATE TABLE BONUS (
    ENAME VARCHAR2(10) ,
    JOB VARCHAR2(9)  ,
    SAL NUMBER,
    COMM NUMBER
    ) ;

    DROP TABLE SALGRADE;
    CREATE TABLE SALGRADE (
        GRADE NUMBER,
    LOSAL NUMBER,
    HISAL NUMBER
    );
    INSERT INTO SALGRADE VALUES (1,700,1200);
    INSERT INTO SALGRADE VALUES (2,1201,1400);
    INSERT INTO SALGRADE VALUES (3,1401,2000);
    INSERT INTO SALGRADE VALUES (4,2001,3000);
    INSERT INTO SALGRADE VALUES (5,3001,9999);
    ```
    <br/>
- 위 sql문들을 실행한 후에 select문으로 데이터가 제대로 들어갔는지 확인한다. <br/>
    ```
    SELECT * FROM EMP
    ```

<br/><br/>

2. 교안에 있는 sql 파일을 열어 한 쿼리씩 실행한다. 아래는 sql 파일을 실행할 때 참고하면 좋을 항목들이다.


- script 내의 `@$ORACLE_HOME/rdbms/admin/utlsampl.sql`는 scott 데이터를 삽입하는 sql파일로, oracle에서 scott schema가 기본적으로 제공되지 않을때 실행시키는 sql 파일이다. LiveSQL에서는 scott schema가 있으나 조작을 해봐야하는 실습 의도와는 맞지 않기 때문에 직접 default schema에서 scott의 테이블과 데이터를 삽입한다. 데이터 삽입 방법은 1번에 나와있다.
- 간혹 `rollback;` 이라는 명령어가 스크립트 내에 있다. 이는 커밋하지 않은 데이터를 모두 반영하지 않겠다는 의미인데, LiveSQL의 경우 "RUN" 버튼을 실행하는 순간 자동으로 커밋까지 완료되어 `rollback` 명령어가 실행되지 않는다. 따라서, 만약 데이터를 돌리고 싶다면 추가한 데이터를 직접 삭제해주어야 한다.
예를 들어서,
    ```SQL
    INSERT INTO DEPT VALUES (50, 'VLDB', 'SUWON');
    ```
    위와 같은 SQL문이 실행되었다가 rollback된 sql query가 있다면, LiveSQL에서는 직접 추가된 데이터를 DELETE해주어야 한다.
    ```SQL
    DELETE FROM DEPT WHERE deptno=50;
    ```
- LiveSQL은 autotrace 기능이 없다.

- LiveSQL은 conn 기능도 없다. 따라서, `conn / as sysdba;`, `conn hr/hr;`, `conn scott/tiger;` 등의 명령어는 모두 실행시키지 않아도 된다.



