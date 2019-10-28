---
title: "[Spring] GetMapping을 찾지 못할때"
layout: post
---

```java
    @DeleteMapping("member/remove/{id}")
    public String deleteMember(@PathVariable Long id){
        if(memberService.deleteMember(id)){
            return "삭제 성공";
        } else {
            return "데이터 없음";
        }
    }

```

위와 같은 코드를 작성했는데 나는 분명 DeleteMapping을 사용하는데 계속 Get Mapping을 찾지 못한다는 에러가 나왔다.


```java
@RestController
@RequestMapping(value = "/member" , method = {RequestMethod.GET, RequestMethod.POST, RequestMethod.DELETE})
public class MemberController {

    @DeleteMapping("/remove/{id}")
    public String deleteMember(@PathVariable Long id){
        if(memberService.deleteMember(id)){
            return "삭제 성공";
        } else {
            return "데이터 없음";
        }
    }
}
```

RequestMapping을 사용해서 묶어주고, method를 표시해주니까 해결되었다. 저번엔 분명 없이도 됬는데 이유를 모르겠다.
짐작하자면 /member/{name}을 받는 메소드가 있었는데 remove를 name으로 가져가서 충돌이 난게 아닐까?? 라는 추측이다.