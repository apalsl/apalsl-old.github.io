---
title: "[Spring] H2 Database 연동 실패"
layout: post
comments : true
---

현재 사용하는 org.springframework.boot 2.1.10 와
h2 database = 1.4.200을 사용 중이다.

```yml
spring:
    datasource:
        url: jdbc:h2:tcp://localhost/~/jpashop;MVCC=TRUE
        username: sa
        password:
    driver-class-name: org.h2.Driver
```


위와 같이 yml파일을 설정하였을때 연결이 되지 않는다. 에러는 여러 가지 형태로 나오는듯 함(다른사람과 다르게 에러문구가 떠서 사진 버림)

이유는 MVCC=TRUE를 h2 db 1.4.200 version부터 제거하기를 권장하기 때문이다.

다만 특이한 점은 springframework version과도 연관이 있는 것 같아서 기록을 남긴다.

직접 테스트 해보진 않았지만 직장동료는 2.2.0과 1.4.200으로 MVCC=TRUE를 하였는데 설공

댓글을 보면 2.1.10과 1.4.199로 하여도 실패가 발생한다

---
결론  

MVCC=TRUE는 무조건 제거할 것. (DB를 이전 version을 쓸 이유가 없음, h2는 나에겐 테스트 전용 DB라서)


MVCC란 Multi Version Concurrency Content의 약자로 사용자 별로 스냅샷을 제공하는 것이다.       
기존에는 내가 update를 하고 commit을 까먹은 경우, 다른 사용자가 DB를 조회하려면 에러가 발생한다.     
mvcc 경우에는 commit하기 이전 작업을 다 무시하고 그냥 보여준다.  


 
 
사족을 붙이자면 처음 회사에서 일할때 주로 오라클DB Tool을 사용했는데 update만 하고 commit을 안했었다. 그 이후 db를 또 수정하려고 하니까 에러가 발생해서  한참찾았는데 문제는 commit을 안해서 발생...


밑에 yml 권장

```yml
spring:
    datasource:
        url: jdbc:h2:tcp://localhost/~/jpashop
        username: sa
        password:
    driver-class-name: org.h2.Driver
```
