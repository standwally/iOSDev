# **Observer**


옵저버 패턴은 Publish-Subscribe(발행-구독) 패턴이라고도 함.
> 객체들 간에 일대다(one-to-many)의 종속 관계를 정의함. 그럼으러써 한 객체의 상태가 변경될 때 그것의 모든 종속 객체들이 통보를 받고 자동으로 변경될 수 있음.

## Observer 패턴은 언제 사용하면 좋을까?

* 상호 의존적인 두 개의 추상 타입이 있을 때다. 별도의 객체에 그 두 가지를 캡슐화하면 그것들을 독립적으로 변경하거나 재사용할 수 있음.
* 한 객체가 변경되면 다른 객체들도 변경될 필요가 있되, 변경될 필요가 있는 객체의 개수가 다양하고 많을 수 있을 때.
* 어떤 한 객체가 다른 여러 객체들에게 통보할 필요가 있을 때(그것들이 어떤 객체인지 알지 못해도)

## Cocoa Touch Framework에서의 Observer 패턴

* Notification
* Key-Value Observing

### Notification

NotificationCenter와 NSNotification 객체를 사용해서 일대다(one-to-many)의 Publish-Subscribe(발행-구독) 모델을 표현함. 그리고 Observer 패턴의 Subject와 그것의 Observer들이 약한 결합도로 상호 접속하게 해줌. 그리고 상호 접속은 상대방을 잘 알 필요 없이 이루어질 수 있음.

* 통보 센터에 통보 게시
```swift
NSNotificationCenter.defaultCenter().postNotificationName("Identifier", object: nil)
```

* 구독 객체 등록
```swift
NSNotificationCenter.defaultCenter().addObserver(self, selector: "selector:", name:"Identifier", object: nil)
```

* 통보 삭제
```swift
NSNotificationCenter.defaultCenter().removeObserver(self, name: "Identifier", object: nil)
NSNotificationCenter.defaultCenter().removeObserver(self) // 현재 등록되어 있는 모든 통보 삭제
```

### Key-Value Observing

이 메커니즘은 NSKeyValueObserving 프로토콜을 기반으로 함.

> 참고자료 : https://developer.apple.com/library/prerelease/mac/documentation/Cocoa/Reference/Foundation/Protocols/NSKeyValueObserving_Protocol/index.html 

### Notification과 Key-Value Observing의 주요 차이점

* Notification
	* 중심이 되는 객체가 모든 Observer들에게 변경 통보를 제공함.
	* 주로 프로그램 이벤트들과 관련됨.
* Key-Value Observing
	* 관찰되는 객체가 Observer 객체들에게 직접 통보를 보냄.
	* 특정 객체의 속성 값과 결부됨.