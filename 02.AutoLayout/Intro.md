# **AutoLayout**

AutoLayout은 '제약사항(Constraints) 기반의 서술형 레이아웃 기술 언어'입니다.

지금까지 iPad는 하나의 해상도만 존재했으나 iPad Pro와, 멀티테스킹 기능이 추가됨으로 인해서 결국 iPad도 다양한 해상도를 대응해줘야 됩니다.

이러한 작업을 가능하게 해주는 기술이 AutoLayout입니다.

## 기존 좌표 기반 레이아웃의 문제점

* 슈퍼뷰의 크기 변화에 대응하기 어렵다.
* 기기별 화면 크기 변화의 대응이 어렵다.
* 언어별 문자열 크기 변화에 대응이 어렵다.

## Constraints

레이아웃 Constraints는 뷰 하나의 값에 대한 제약사항이다. 예를 들어,

* 임의의 뷰의 중심은 X 방향으로 슈퍼 뷰의 중심과 같아야 한다.
* 임의의 뷰의 바닥면은 Y 방향으로 슈퍼 뷰의 바닥면에서 20 포인트 만큼 이동한 자리에 있어야 한다.
* 임의의 뷰의 Width는 150 포인트이어야 한다.
* 임의의 뷰의 Height는 80 포인트이어야 한다.

이 정도의 제약사항이 있다면 우리는 슈퍼뷰의 크기 변화에 상관없이 임의의 버튼의 위치와 크기를 정확히 지정할 수 있다.

## Constraints를 만드는 방법

코드, 비주얼 레이아웃 언어 그리고 스토리 보드의 비주얼 레이아웃 툴이라는 메뉴를 사용해서 Constraints를 만들 수 있다.

* **Constraints 추가하기**
	* Align 항목
		* Align은 오브젝트들의 정렬을 위한 Constraint를 추가할 때 사용한다.
		* 두 개 이상의 뷰가 수직방향을 기준으로 같은 위치에 있어야 한다거나, 두 뷰의 왼쪽면이 동일한 위치에 있도록 하는 등의 정렬이 필요할 때 Align 메뉴를 사용해서 Constraint를 추가한다.

		* ![Align](https://lh3.googleusercontent.com/-_yC9GiRqkA4/Vpz5F8C8gqI/AAAAAAAAAQ8/VQ2L8eVLUt8/s0/Align.png "Align.png")

	* Pin 항목
		* Pin은 공간을 위한 Constraint를 추가할 때 사용한다. 뷰의 크기를 확보하거나 다른 뷰와의 거리를 확보할 때 Pin 메뉴를 이용해 Constraint를 만든다.
		* 슈퍼뷰에서의 위치를 정할 때도 Pin을 사용한다.
		* ![Pin](https://lh3.googleusercontent.com/-jrSqefrmTDo/Vpz6ot-BHOI/AAAAAAAAARM/cvio3UA4to4/s0/Pin.png "Pin.png")

	* Resolve AutoLayout Issue 메뉴
		* Resolve Auto Layout Issue 메뉴는 레이아웃의 문제점을 해결하기 위한 기능을 제공한다.
		* 사용자가 지정한 위치와 뷰에 더해진 Constraint가 서로 맞지 않을 때는 부정렬(misplacement)이 발생하게 되며, 사용자가 만든 레이아웃 컨스트레인트가 불충분하면 애매모호한(ambigous) 레이아웃이 생기게 된다. 이런 상황을 해결하기 위한 기능을 제공하는 메뉴이다.
		* ![Resolve AutoLayout Issue](https://lh3.googleusercontent.com/-P_Gr-f_N_tU/Vpz7RYH58cI/AAAAAAAAARY/OubWrFw_cqs/s0/Resolve.png "Resolve.png")

	* Ctrl-드래그 
		* Ctrl-드래그는 Xcode에서 오랫동안 '연결'을 의미해 왔다. 이제 스토리보드의 Scene 내에서 오브젝트간 Ctrl-드래그시에는 두 오브젝트 사이에 만들 수 있는 Constraint를 보여주는 Contextual 메뉴를 보여준다.
		* 드래그의 방향에 따라 다른 종류의 Constraint를 보여주며, Shift키를 누르고 선택하면 동시에 여러개의 Constraint를 추가할 수 있다.
		* ![Ctrl + Drag](https://lh3.googleusercontent.com/-s5km1jUSdLw/Vpz9ZSB85QI/AAAAAAAAARs/ZYRlymfeuHg/s0/CtrlDrag.png "CtrlDrag.png")

* **Assistant Editor**

AutoLayout을 이용해 레이아웃 디자인을 하는 동안은, 오른쪽 영역을 Automatic이 아닌 Preview로 설정하자. Preview를 통해 우리의 뷰 디자인을 바로 확인할 수 있다. 특히 + 버튼을 누르면 다양한 디바이스 해상도를 추가할 수 있어서 AutoLayout을 사용하는 목적에 맞게 다양한 슈퍼뷰 크기에 따른 레이아웃 변화를 확인할 수 있다.

![Assistant Editor](https://lh3.googleusercontent.com/-HcH3yW8hYmQ/Vp0JxLBDPMI/AAAAAAAAASM/VnGwu7OmVS0/s0/AssistantEditor.png "AssistantEditor.png")

## 참고자료
[Auto Layout Guide](https://developer.apple.com/library/prerelease/ios/documentation/UserExperience/Conceptual/AutolayoutPG/index.html#//apple_ref/doc/uid/TP40010853-CH7-SW1)

## 예제 1.

* 레이아웃 요청사항
	* 화면의 아래쪽 중앙에 'More' 버튼을 위치시켜 주세요.
	* 슈퍼뷰의 아래면과 'More' 버튼의 아래면의 여백은 표준 여백을 사용합니다.

* 애매모호성(Ambiguity)과 Misplacement(부정렬)을 해결해보세요.
> **애매모호성(Ambiguity)과 Misplacement(부정렬)**
> 
> 하나의 Constraint를 추가했을 때, 우리가 지정한 하나의 Constraint만으로는 위치를 정확히 지정할 수 없어서 모든 것이 주황색으로 표시되고 부족한 정보에 해당하는 부분은 좌상단인 원점을 기준으로 임의로 배치해 버리는 것을 말한다.


## 예제 2.

* 레이아웃 요청사항
	* 스토리 보드에 동일한 크기의 버튼 3개를 페이지 하단 중앙에 배치해 주세요.
	* 버튼간의 간격은 동일해야 합니다.