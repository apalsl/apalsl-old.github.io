---
title: "[Spring] Repository Null"
layout: post
---


코드에서 create()를 테스트하는데 자꾸 Repository에서 NullPointException이 발생한다.

```java
class MemberRepositoryTest {

    @Autowired
    private  MemberRepository memberRepository;

    @Test
    public void create(){
        Member member = new Member();
        member.setId(4L);
        member.setName("테스트1");

        Member newMember = memberRepository.save(member);

        Assert.assertNotNull(newMember);

    }
}
```


  
열심히 알아봤더니 다음과 같은 annotation을 입력하지 않았다.
내가 이걸 까먹은 이유는 두가지다. 하나는 기존에 듣던 강의에서는 Test 메인 클래스를 상속받아서
annotation을 추가하지 않았다.

두번째 강의는 Mvc강의로만 진행을 해서 그런지 저런 annotation을 추가한적이 없다. (그래도 잘 동작했다)
이 실수의 가장 큰 문젠느 그냥 NullPointException이 뜬다는점이다. 뭘 잘못했는지 알 방법이 없다.
(테스트 해봤는데 사실 RunWith(SpringRunner.class는 없어도 지금 테스트에서는 상관없다)

```java
@RunWith(SpringRunner.class)
@SpringBootTest
class MemberRepositoryTest {

}
```

추가로 기존에 들었던 강의처럼 extends를 사용해봤는데 똑같이 NullPointException이 난다. 아직은 잘 모르겠다.
