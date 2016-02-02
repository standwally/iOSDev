# **Classes and Structures**


클래스와 구조체는 우리의 프로그램 코드 블럭을 유연하게 설계하게끔 하는데 사용하기 위한 목적임. 프로퍼티와 메소드는 클래스와 구조체에 상수, 변수, 함수로서 동일한 syntax를 정확하게 사용하여 기능을 추가하도록 정의함.

다른 프로그래밍 언어와는 달리, Swift는 custom 클래스와 구조체를 위한 interface와 implementation 파일을 따로 나눌 필요가 없음. 다른 코드에 사용하기 위한 클래스, 구조체의 외부인터페이스는 자동으로 만들어짐.

## Comparing Classes and Structure

Swift에서는 클래스와 구조체가 서로 많은 공통점들을 가지고 있음.
* 값을 저장하는 프로퍼티를 정의
* 기능을 제공하는 메소드를 정의
* 서브스크립트 syntax를 이용하여 값을 접근할 수 있는 서브스크립트 정의
* 초기 상태를 설정할 수 있는 초기화를 정의
* 기본 구현외에 기능을 확장할 수 있는 확장이 가능
* 특정 종류의 표준 기능을 제공하는 프로토콜을 따름

더 많은 정보는 아래 내용을 참고
* Properties
* Methods
* Subscripts
* Initialication
* Extension
* Protocols

클래스는 구조체가 할 수 없는 추가적인 능력들이 있음
* Inheritance
* Type Casting
* Deinitializers
* Reference counting

> 구조체는 전달될 때, 항상 복사되며, reference counting을 사용하지 않음

### Definition Syntax

	
	class SomeClass {
    	// class definition goes here
	}
    
	struct SomeStructure {
    	// structure definition goes here
	}
	

### Class and Structure Instance
클래스와 구조체는 객체를 생성하는 syntax가 매우 비슷함.

	
    let someResolution = Resolution()
	let someVideoMode = VideoMode()
	

### Accessing Properties

. syntax를 이용하여 객체의 프로퍼티에 접근할 수 있음.

    print("The width of someResolution is \(someResolution.width)")

> Objective-C와는 다르게 Swift는 직접 구조체의 프로퍼티에 내부 프로퍼티를 설정하는 것이 가능함


### Memberwise Initializers for Structure Types
모든 구조체는 자동 생성된 멤버 초기화를 가지며, 새로은 구조체 객체의 멤버 프로퍼티를 초기화 하도록 사용할 수 있음.

    let vga = Resolution(width: 640, height: 480)

>Q. **값 타입의 구조체와 열거형과 참조 타입의 클래스에 대해 알아보세요.**