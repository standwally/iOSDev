# **Memory Management**

>메모리 누수(leak)란?
>
>메모리를 점유하고 있지만 이를 참조하거나 참조를 얻으려는 오브젝트가 없는 경우를 말한다.

>댕글링 포인터란(dangling pointer)?
>
>메모리 해제된 오브젝트를 가진 포인터를 말한다.

Swift와 Objective-C 양쪽 모두 클래스 인스턴스는 레퍼런스 타입이다. 내부적으로 Swift와 Objective-C 레퍼런스 타입의 메모리 관리는 동일한 방식으로 동작한다.

Swift는 ARC(Auto Reference Counting)를 사용하기 때문에 매 참조 타입의 오브젝트를 명시적, 개별적으로 메모리 관리하지 않아도 된다.

하지만 ARC를 사용하더라도 여전히 메모리 관리에 오류가 발생할 수도 있다.


## 코코아 메모리 관리 법칙

>리테인 카운트(retain count)란?
>
>모든 레퍼런스 타입 오브젝트를 관리하는 숫자에 기반한 메모리 관리 정책을 말하며, 리테인 카운트가 0인 오브젝트는 자동으로 해제된다.

오브젝트를 소유한 객체만이 리테인 카운트의 증감을 관리하는 소유권(ownership)을 발휘할 수 있다.


## ARC와 ARC가 하는 일

예전에 프로그래밍을 할 때 프로그래머들은 retain과 release 메세지를 보내어 오브젝트를 얻고 릴리즈를 직업했었다. ARC에서는 우리가 직접 retain과 release를 호출하지 않는다. ARC가 이 메소드를 직접 호출하기 때문이다.


ARC는 컴파일러의 일부로 구현되어 있다. 컴파일러는 컴파일 과정에서 우리의 코드에 retain과 release 호출을 삽입한다.

## autorelease

오브젝트에 release 메시지를 보내면, 리테인 카운트가 하나 감소합니다.

autorelease는 리테인 카운터의 감소를 지연시킵니다.

autorelease라는 이름때문에 ARC와 비슷한 것으로 생각할 수 있다. 하지만 아니다. 이것은 C언어에서의 "자동 변수"와 좀 더 비슷하다.

> 자동변수란 문법적으로 범위가 설정된 변수이다. 따라서 프로그램 실행이 이 범위를 벗어나면 자동으로 소멸된다.

autorelease로 객체들을 가종 변수와 같은 방식으로 이용할 수 있다. 프로그램 실행이 코드 블록을 벗어나면 그 객체에 대해 자동으로 release 메서드가 호출되는 것을 의미한다.

## 리테인 사이클과 Property

메모리 누수가 발생하는 가장 대표적인 상황은 두 개의 클래스 인스턴스가 서로를 참조하려는 리테인 사이클이 만들어진 경우에 발생한다.

deinit 함수를 통해서 메모리 누수를 확인, 관찰할 수 있다.

```swift
func testRetainCycle() {

	class Dog {
    
    	var cat : Cat? = nil
        deinit {
        	print("good-bye from Dog")
        }
    
    }
    
    class Cat {
    
    	var dog : Dog? = nil
        deinit {
       		print("good-bye from Cat")
        }
    
    }
    
    let d = Dog()
    let c = Cat()
    d.cat = c
    c.dog = d

}

testRetainCycle()
```

* Property
	* strong
	* copy(@NSCopying)
	* weak
	* assign(unowned(unsafe))

* 위 코드에서 두 오브젝트간에 리테인 사이클이 발생하고 있는 상황을 해결해보세요.

