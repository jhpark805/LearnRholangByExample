# Sending 및 StandardOut

# Say Hello

!["Person Wawaying hello." (HelloWorld.pn)


프로그래밍에는 당신의 첫 프로그램이 "Hello World"라고 말해야 하는 오랜 전통이 있다. 여기 화면에 그 텍스트를 올릴 수 있는 가장 간단한 rholang 코드가 있다.

[Hello.rho] (Hello.rho)

### 연습
프로그램을 "Hello World" 대신에 "Rholang rockes!"라고 인쇄하십시오.


##stdout가 도대체 뭐인가?

![채널은 메시지 보내기 우편함과 같다](mailbox.png)

Rholang의 중심부는 채널로 의사소통하고 있다. 채널은 메시지를 보내고 받는 데 사용하는 통신 라인이다. 채널을 통해 메시지를 보내려면! 문자를 사용하십시오.

![이 도표 다시 쓰세요!](sendSyntax.png)

프로그램 첫 줄에 새로운 stdout으로 stdout 채널을 만들었다. 당신이 rholang을 배우면서 많은 채널을 만들 것이다. (rho:io:stdout)을 포함하여 우리채널에 특별한 힘을 주었다. 나중에 더 자세히 알게되겠지만, 지금은 텍스트가 화면에 실제로 나타나도록 하기 위해 괄호 안에 있어야 한다는 것을 알아야 한다.


##다른 채널 사용

여기서 "메시지 삭제"... JK, '튜플스페이스'라고 하는 우편함에서 메시지가 수신되기를 기다린다.png)

stdout뿐만 아니라 많은 채널에 메시지를 보낼 수 있다. 그러나 "stdout"과 달리 그들은 화면에 나타나지 않을 것이다. 왜냐하면 우리가 그들에게 특별한 힘을 가하지 않기 때문이다.

[TupleSpace.rho](TupleSpace.rho)

그럼 다른 채널들은 어디로 갈까? 아무데도 아니다! 아직은 아니다, 어차피. 메시지들은 그저 누군가(또는 어떤 과정) 그것들을 받을 수 있기를 기다리며 그곳에 앉아 있다. 우리는 다음 수업에서 메시지를 받는 방법을 배울 것이다. 그동안 메시지가 담겨있던 곳을 "튜플스페이스"라고 부른다.

메시지가 Tuple Space에 있는지 확인하시오. 사용하는 개발자 환경에 따라 이와 같은 텍스트를 봐야 한다.

```
저장소 내용:
@{"RandoChannel"}!("화면에 나타나지 않음)" | for (x0, x1 @{unforgeable(0x01) { Nil } | for (x0, x1, x2, x3 @{"secp256k1verify"}) ) {nil} |(x1 @{"256"} @(x1).feet(0x02)} ) { Nil } |(x0 @{Unforgeable(0x00)} ) { Nil } |(x0, x1 @{"keccak256Hash"} ) ) { Nil }
```



##한 번에 두 가지 작업 수행
순서만 따져도 모든 재료가 동시에 첨가된다png)

Rholang에서 우리는 컴퓨터에게 하나의 작업을 시키고, 그다음 작업, 그리고 그 다음 세 번째 작업을 하라고 말하지 않는다. 우리가 해야 할 모든 것을 한번에 말하고, 그것은 "동시에" 혹은 한번에 하도록 만든다.

[parallel.rho] (병렬).rho)

| 은 "parallel" 또는 짧게 "par"로 발음된다.


### 연습
"pizza shop"이라는 채널에 "1 large pepperoni please "라는 메시지를 보내세요.

### 연습
"Mom's phone" 채널에 "Mom"를 전송하십시오.

### 연습
화면에 한 프로그램에 "Rick"과 "Morty"라는 두 개의 메시지를 인쇄하십시오.



## 퀴즈

stdout!("Programming!")메시지는 어떻게 인쇄될것인가?
- [x] 프로그래밍!
- [ ] stdout!
- [ ] 없음


what!("Up")메세지에서는 어떤채널로 메세지가 보내지는가?
- [ ] '업'
- [x] '무엇'
- [ ] '무엇'
- [ ] 'stdout'


이메세지중에서 Rholang이 먼저 하는 작업은 무엇일까?
```
stdout!("Dogs")
|
stdout!("Cats")
```
- [ ] "Dogs" 인쇄
- [ ] "Cats" 인쇄
- [x] 둘 다. 그들은 동시적이다.


### 연습
Rho:io:stderr라는 특별 채널도 있다. 당신이 그것을 보낼 때 무슨 일이 일어나는지 살펴보시오. 차이가 무엇입니까? ](https://en.wikipedia.org/wiki/Standard_streams))
