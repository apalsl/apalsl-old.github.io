---
title: "[Spring] RequiredArgsConstructor"
layout: post
comments : true
---

Spring boot에서 @RequiredArgsConstructor는 @NotNull과 final로 지정된 필드 변수에 자동으로 의존성 주입을 해준다.

```java
@RestController
@RequiredArgsConstructor
public class EventController {

    private final EventService eventService;
    @NotNull
    private MemberService memberService;

```

위 코드는 밑 코드와 같다.    
```java
@RestController
public class EventController {

    @Autowired
    private EventService eventService;
    @Autowired
    private MemberService memberService;

```

기존에는 생성자를 호출, 또는 모든 경우의 생성자를 만들어주는 어노테이션을 이용한 @Autowired를 생성 등 여러가지 방법이 있었는데

요즘에는 final, 또는 @NotNull을 이용한 주입을 한다고 한다. (NotNull과 final 두 개의 정확한 차이점을 모르겠다. 기능의 차이점보다 어느코드가 이득인지)

이것은 기존의 Spring에서 Interface와 구현 클래스에 의존성 주입하는것과 같은 역할을 한다.  


---


개인적으로 SpringBoot로 넘어와서 특이한 점은 EventService라는 인터페이스를 그대로 사용한다는 점이다. 

SpringBoot는 하나의 Interface와 하나의 구현체가 있다면 자동으로 찾아서 의존성 주입을 해준다.

```java
EventService event = new EventServiceImpl(); 
```
쉽게 말하면 위 코드에서 EventServiceImpl을 자동으로 찾는것이다. 
  
SpringBoot를 제대로 하려면 Spring에 대한 이해도가 높아야 좀 더 깊이 파고들 수 있을 것 같다.
