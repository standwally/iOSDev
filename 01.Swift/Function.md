# **Function**


## 일급 객체로서의 함수

Swift는 객체지향 언어이자 동시에 함수형 언어입니다. 함수형 언어를 학습하게 되면 반드시 일급 객체(First-Class Object)라는 용어를 접하게 되는데요. 이것은 영국의 컴퓨터 과학자가 1960년대에 처음 사용한 개념으로서, 프로그램 언어 안에서 특정 종류의 객체가 일급의 지위를 가지는가에 대한 의미입니다.

객체가 다음의 조건을 만족하는 경우 이 객체를 일급 객체로 간주한다.

* 객체가 런타임에도 생성이 가능해야 한다.
* 인자값으로 객체를 전달할 수 있어야 한다.
* 반환값으로 객체를 사용할 수 있어야 한다.
* 변수나 데이터 구조 안에 저장할 수 있어야 한다.
* 할당에 사용된 이름과 관계없이 고유한 구별이 가능해야 한다.

함수가 위 조건에 만족하면 이를 일급 함수(First-Class Function)라고 하고 그 언어를 함수형 언어로 분류합니다.

>**Q. 함수 타입이란 무엇인가요?**

* 함수의 반환 타입으로 함수를 사용할 수 있음. 
```swift 
func foo() -> String {
	return "this is foo()"
}

func boo() -> (Void -> String) {
	return foo
}

let b = boo()
b()
```
* 함수의 인자값으로 함수를 사용할 수 있음.
```swift 
func boo(param : Int) -> Int {
	return param + 1
}

func foo(base : Int, function f : Int -> Int) -> Int {
	return f(base)
}

foo(3, function:boo)
```

* 함수의 중첩
```swift
func basic(param : Int) -> (Int) -> Int {

	let value = param + 20
    
    func append(add : Int) -> Int {
    
    	return value + add
    
    }
    
    return append

}

let b = basic(10)
b(10)
```

>**Q. 위 코드의 결과값을 예측해보세요.**

* 클로저란 내부 함수와 내부 함수에 영향을 미치는 주변 환경(Context)을 모두 포함한 객체이다.
	* 두 가지로 이루어진 객체입니다. 하나는 내부 함수이며, 또 다른 하나는 내부 함수가 만들어진 주변 환경입니다.
	* 외부 함수 내에서 내부 함수를 반환하고, 내부 함수가 외부 함수의 지역변수나 상수를 참조할 때 만들어집니다.
	* 정확히는 지역변수의 값이 저장된다. 이를 '값이 캡쳐되었다'고 표현한다.

>**Q. 위 코드에서 클로저의 범위를 정의해보세요.**

