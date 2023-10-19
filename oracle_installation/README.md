# Oracle Installation

Lecture 1에서는 oracle을 설치하고, scott/tiger 계정을 활성화하는 것을 목표로 합니다.


로컬에서 oracle을 설치하고 실습을 하기 위해서는 다음과 같은 방법들이 있습니다. 

1. **Oracle19c 설치** ([설치 방법 가이드](./oracle19c_installation.md))
2. **Oracle Live SQL** ([사용 방법 가이드](./oracle_live_sql.md)])


실습을 모두 따라가기 위해서는 로컬에 직접 oracle 19c를 설치하는 것을 추천드리지만, oracle19c 설치가 쉽지 않기 때문에 Live SQL을 사용하셔도 됩니다. <br/>

### Summary
- `Windows`: Oracle 19c 쉽게 설치 가능
- `Mac (Intel Chip)`: Oracle에서 제공하는 가상 환경으로 비교적 쉽게 설치 가능
- `Mac (Apple Chip)`: 가상 환경 벤더 자체가 mac apple chip 환경을 잘 제공하지 않음. 따라서, 부수적인 환경 설정이 많이 필요. 해당 경우에는 Oracle Live SQL을 추천드립니다.

### Oracle 19c vs. Oracle Live SQL
|Oracle 19c (Local) | Oracle Live SQL | 
| --- | --- |
| - Hard to Install, Complex environment settings. <br/> - All of the functions are supported. <br/> - Has a space limit depending on the environment.  | - Easy to Install<br/> - Do not require any complex environment settings. <br/> - User-frendly, Good visibility <br/> - Some of the functions related to sysdba are unsupported.<br/> &ensp; (i.e GRANT, CONNECT, SET AUTOTRACE) <br/> - Has a space limit. |
