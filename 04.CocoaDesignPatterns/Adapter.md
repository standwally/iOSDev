# **Adapter**


두 개의 서로 다른 타입의 객체들을 끼워 맞춰서 서로 아무 문제 없이 잘 돌아가도록 하기 위함. 여기서 Adapter는 재사용하고자 하는 기존 클래스이며, 클라이언트는 Adapter를 사용하고자 하는 클래스임.

> 어떤 클래스의 인터페이스를 클라이언트가 원하는 다른 인터페이스로 변환함. 인터페이스가 호환되지 않아서 함께 사용할 수 없는 클래스들을 Adapter가 사용할 수 있게 해줌.

## Adapter 패턴은 언제 사용하면 좋을까?

* 기존 클래스의 인터페이스가 우리가 필요한 것과 일치하지 않을 때
* 인터페이스가 호환되지 않는 다른 클래스들과 함께 사용할 수 있는 재사용 가능한 클래스를 원할 때

## Cocoa Touch Framework에서의 Adapter 패턴

Cocoa Touch Framework의 많은 클래스들은 Adapter 패턴인 Protocol에 정의된 Delegation 형태를 사용해서 구현되어 있는 것을 봤을 것이다.

* Protocol을 이용한 방법
* block을 이용한 방법

> Q. Protocol과 block을 이용한 방법에 대해서 알아보세요.