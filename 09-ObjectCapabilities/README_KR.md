# Object Capabilities

최근에 우리는 용서할 수 없는 이름들이 그 이름을 아는 사람들에게 채널의 사용을 얼마나 제한할 수 있는지를 배웠다. 또한 상태 채널을 사용하여 데이터를 저장하고 캡슐화된 데이터를 수정하는 방법을 사용할 수 있는 방법도 확인하였다. 이 수업에서 우리는 용서할 수 없는 이름에 놓여진 방법들이 어떻게 "객체 능력"이라고 알려진 엄청나게 유용한 디자인 패턴으로 이어지게 되는지 볼 것이다.

![차량을 잃지 않아서 다행이야, 그 냉동고 안에 있는 차 열쇠 말이야] (키즈.png)

물체 능력의 일례는 집이나 자동차의 열쇠다. 물건을 소유하는 것은 당신에게 집에 들어가거나 차를 시동할 수 있는 능력을 준다. 당신은 또한 다른 사람에게 열쇠나 열쇠의 복사본을 줌으로써 위임할 수 있는 능력을 가지고 있다.

이 수업에서는 상태 채널과 객체 기능을 사용하는 몇 가지 예시 프로젝트를 만들 것이다. 우리는 데이터를 읽고 쓰는 것과 같은 권한을 부여하기 위해 번들보다 객체 기능이 더 일반적으로 사용될 수 있다는 것을 볼 수 있을 뿐만 아니라, 카운터를 재설정하거나 페이스북 계정을 삭제하는 것과 같은 더 추상적 기능도 사용할 수 있다는 것을 알게 될 것이다.

## ATC Revisited
4과목의 항공 교통 관제 예제를 다시 살펴보자. 이전에 관제사들은 반복적으로 송신함으로써 날씨와 활주로 정보를 방송할 수 있었다. 그러나 그들은 정보를 갱신할 수 없었다. 그리고 우리 모두는 날씨가 예측할 수 없이 변할 수 있다는 것을 안다. 따라서 이 예에서는 현재 정보를 상태 채널에 저장하고, 관제사에게 필요에 따라 업데이트를 할 수 있는 기능을 제공할 것이다.

[atc.rho](atc.rho)

역내 튜닝에 읽기 전용 번들을 사용하는 것은 당연해 보인다. 그러나, 만약 우리가 번들을 사용한다면, 그 메시지를 가장 먼저 듣는 사람이 그것을 주 채널로부터 소비할 것이다. 그것은 다른 조종사들이 받을 수 있도록 남겨두지 않을 것이다. 메시지가 우리가 원하는 대로 유지되도록 하기 위해, 우리는 주 채널에 대한 모든 접근을 우리 스스로 처리하고, 조종사에게 정확한 메시지를 질문할 수 있는 능력을 준다.

ATC는 어떻게 정보를 업데이트하는가?
- 셋!("강력한 역풍, 주의)""
- [ ] '("강력한 역풍, 주의)""
- [ ] "getInfo!"("강력한 역풍, 주의)""
- [ ] "stationFactory.setInfo!("강력한 역풍, 주의)""

### Exercise
ATC가 성공적으로 상태를 업데이트할 수 있고 조종사가 할 수 없는지를 확인하기 위해 보다 철저한 테스트를 작성하십시오.

## Savings Account
이 예에서 우리는 rholang에 있는 간단한 저축예금계좌를 모델링하는 코드를 쓸 것이다. 그것은 예금, 인출, 수속을 할 것이다.

우리 카운터와 달리 저축예금은 안전해야 한다. 우리는 우리의 균형을 아는 사람만, 더 나쁜 것은 그것을 철회하는 것을 원하지 않는다.

여기 고려해야 할 몇 가지 출발 코드가 있다.
[savingsStarter.rho] (SavingsStarter).rho)

### Exercise
계정에 남아 있는 방법을 입력하십시오.

어떤 계약이 공장으로서의 역할을 하는가?
- [ ] '체크'
- [ ] '끌기'
- [ ] '입금'
- [x] 'openAccount'

우리의 현재 저축 계좌는 마이너스 잔고를 허용하지만, 아마 그렇게 하지 않을 것이다. 네가 그 문제를 어떻게 풀려고 할지 생각해봐. 우리는 다음 수업에서 그것을 할 수 있는 적절한 방법을 배울 것이다.

## Stealing Funds
이브가 새라의 돈을 훔치기 위해 패러디해야 할 코드를 쓰도록 노력해라. 넌 아무 것도 생각할 수 없을 거야. 그것은 오직 사라만이 계정을 통제하는 용서할 수 없는 이름들에 접근할 수 있기 때문이다.


사라가 그녀의 친구 스테파니가 수표나 인출은 하지 않고 은행 계좌에 입금하기를 원한다면 어떤 코드를 실행해야 할까?
스테파니!(*sarahWithgraft)"
- [x] '(*사라입금)
- [ ] '사랑도 없이!("활성화", *스텝해니")
- [ ] '개방 계정'(10, *sarahDeposit, @"sarahWithtraw", @"sarahCheck")".


## Two Kinds of Factories
지금까지 우리의 모든 공장 방식은 계약을 맺기 위해 이름을 붙이도록 요구되어 왔다. 예컨대 저축예금 계좌에서 그 이름들은 체크 예금 인출이었다. 나는 이것을 "BYOC" 또는 "자신의 채널 확보" 공장이라고 부른다. BYOC 기술은 사용자가 다른 계약 또는 공용 이름에서 얻은 이름을 포함하여 자신이 좋아하는 이름을 제공할 수 있다는 장점이 있다.

또 다른 기법은 공장에 필요한 용서할 수 없는 이름을 만들어 발신자에게 다시 보내는 것이다. 나는 이것을 "완전한 서비스" 공장이라고 부른다. 만약 당신이 임의의 이름들을 전달하는 융통성을 필요로 하지 않는다면, 전체 서비스 공장은 종종 덜 번거롭다.

### Exercise
저축예금을 byoc factory에서 full service factory로 전환한다.

당신이 저축예금을 환전했으니 사라가 여전히 그녀의 예금 능력을 공개하는 것이 가능한가?
- [ ] 아니오. 더 이상 공적인 이름을 사용할 수 없음
- [ ] 아니, 그녀는 그렇게 할 수 없어.
- 네 - 새 기능을 직접 공개하기만 하면 돼
- [ ] 예; 예, 이전처럼


## Abortable Rocket Launch
우리가 처음 합류 운영자를 배웠을 때, 우리는 두 운영자가 로켓을 발사하기 위해 허가를 내야만 하는 시나리오를 고려했다. 우리는 그들이 허가를 철회할 수 있기를 원했다.

이 문제는 사용자가 실행 명령을 내릴 때 중단 버튼을 눌러 해결할 수 있다.

[AbortableLaunch.rho](AbortableLaunch.rho)

### Exercise
Bob의 출시 논리 및 통합 테스트를 통해 위의 코드를 완성하십시오.

## Design Patterns
많은 일반적인 객체 공정 능력 설계 패턴이 있다. 그 중 많은 부분이 [안전한 협력의 그림책](http://erights.org/talks/efun/SecurityPictureBook.pdf)에 설명되어 있다.

### Exercise
우리는 다음 예들을 통해 이러한 패턴들 중 많은 것을 접하게 될 것이다. 그러나 나는 당신이 한 두 가지 패턴을 지금 당장 홀랑에서 실행할 것을 권고한다.