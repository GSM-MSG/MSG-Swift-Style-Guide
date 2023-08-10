# MSG Swift Style Guide
코드를 이해하고 작성하는 데에, 더 도움을 주고 명확하게 소통하기 위한 MSG의 Swift Style Guide입니다.
코드 리뷰때에서 아래 내용을 바탕으로 신명나게 지적해주세요!
구성원들의 의사결정에 따라 수시로 변경될 수 있습니다.

## 목표
스타일 가이드를 준수함으로써
- 보다 쉽게 읽고 익숙하지 않은 코드를 이해할 수 있도록 합니다.
- 코드를 보다 쉽게 유지 관리
- 간단한 프로그래머 오류 감소
- 코드 작성 시 인지 부하 감소

간결함이 주 목표가 아닙니다.
코드는 다른 좋은 코드 품질(가독성, 단순성, 명확성 등)이 동일하게 유지되거나 개선될 경우에만 보다 간결하게 만들어야 합니다.

## Guide
- 해당 스타일 가이드에 없는 내용은 https://swift.org/documentation/api-design-guidelines/ 를 따릅니다.
- 모든 규칙을 구체화하기 위해 노력합니다.
- 예외사항은 거의 두지 않아야 하고, 있더라도 정당성이 높아야합니다.

## 목차
- [MSG Swift Style Guide](#msg-swift-style-guide)
  - [목표](#목표)
  - [Guide](#guide)
  - [목차](#목차)
  - [Code Layout](#code-layout)
    - [Basic](#basic)
      - [한 줄은 120자를 넘지 않아야한다.](#한-줄은-120자를-넘지-않아야한다)
      - [들여쓰기 및 indent는 4개의 space를 사용한다.](#들여쓰기-및-indent는-4개의-space를-사용한다)
      - [줄 끝에는 공백을 제거한다.](#줄-끝에는-공백을-제거한다)
      - [MARK 구문은 위와 공백을 추가한다.](#mark-구문은-위와-공백을-추가한다)
      - [Scope의 끝에는 빈 줄을 제거한다.](#scope의-끝에는-빈-줄을-제거한다)
      - [Scope의 시작에는 빈 줄을 제거한다.](#scope의-시작에는-빈-줄을-제거한다)
      - [Scope와 Scope 사이에는 공백을 추가한다.](#scope와-scope-사이에는-공백을-추가한다)
      - [들여쓰기 방식은 K\&R 스타일을 따른다.](#들여쓰기-방식은-kr-스타일을-따른다)
      - [공백줄은 1줄까지만 허용한다.](#공백줄은-1줄까지만-허용한다)
      - [공백은 1칸까지만 허용한다.](#공백은-1칸까지만-허용한다)
      - [선언부 앞의 주석은 Doc주석으로 작성한다.](#선언부-앞의-주석은-doc주석으로-작성한다)
      - [guard의 else는 가독성을 해치지 않거나 120줄을 넘지 않으면 같은 줄에 작성한다.](#guard의-else는-가독성을-해치지-않거나-120줄을-넘지-않으면-같은-줄에-작성한다)
      - [namespace는 오직 enum으로만 만든다.](#namespace는-오직-enum으로만-만든다)
      - [extension에서 접근제어자를 설정할때는 선언이 아닌 extension에 설정한다.](#extension에서-접근제어자를-설정할때는-선언이-아닌-extension에-설정한다)
      - [FileHeader는 제거한다.](#fileheader는-제거한다)
      - [let, var를 바인딩할 때는 hoist 형태로 바인딩한다](#let-var를-바인딩할-때는-hoist-형태로-바인딩한다)
      - [파일의 끝에는 빈 공백줄을 추가한다.](#파일의-끝에는-빈-공백줄을-추가한다)
      - [파라미터에 Protocol을 받을때는 필요하지 않다면 Generic 대신 some을 사용한다.](#파라미터에-protocol을-받을때는-필요하지-않다면-generic-대신-some을-사용한다)
      - [고차함수를 사용할 때 KeyPath로 접근할 수 있다면 KeyPath를 사용한다.](#고차함수를-사용할-때-keypath로-접근할-수-있다면-keypath를-사용한다)
      - [중괄호 주위에 공백을 준다.](#중괄호-주위에-공백을-준다)
      - [식별자 바로 뒤에 콜론 : 을 배치하고 그 뒤에 공백을 넣는다.](#식별자-바로-뒤에-콜론--을-배치하고-그-뒤에-공백을-넣는다)
      - [가독성을 위해 함수의 리턴 화살표 양쪽에 공백을 둔다.](#가독성을-위해-함수의-리턴-화살표-양쪽에-공백을-둔다)
      - [TODO와 FIXME는 Warning을 발생시켜야 한다.](#todo와-fixme는-warning을-발생시켜야-한다)
    - [Functions](#functions)
      - [메서드 내의 공백은 기능을 분리해야 하지만 섹션이 너무 많으면 종종 여러 메서드로 리팩토링해야한다.](#메서드-내의-공백은-기능을-분리해야-하지만-섹션이-너무-많으면-종종-여러-메서드로-리팩토링해야한다)
      - [함수 정의 시 매개변수나 호출 시 인수는 같은 줄에 놓거나, 줄 당 하나만 있게한다. 여러 줄로 만든다면, 각각 새 줄에 놓고 들여쓰기를 추가한다.](#함수-정의-시-매개변수나-호출-시-인수는-같은-줄에-놓거나-줄-당-하나만-있게한다-여러-줄로-만든다면-각각-새-줄에-놓고-들여쓰기를-추가한다)
      - [함수 매개변수에 closure 가 2개 이상 존재하는 경우 내려쓰기를 한다.](#함수-매개변수에-closure-가-2개-이상-존재하는-경우-내려쓰기를-한다)
    - [Operators](#operators)
      - [infix 연산자는 양쪽에 하나의 공간이 있어야 한다.](#infix-연산자는-양쪽에-하나의-공간이-있어야-한다)
  - [Naming](#naming)
    - [Format](#format)
      - [타입(struct, class, enum)과 protocol 이름은 PascalCase를 사용하고, 그 외에는 lowerCamelCase 를 사용한다.](#타입struct-class-enum과-protocol-이름은-pascalcase를-사용하고-그-외에는-lowercamelcase-를-사용한다)
      - [Bool타입은 is, has 와같이 Bool타입임을 분명히하는 접두사를 붙여서 사용합니다.](#bool타입은-is-has-와같이-bool타입임을-분명히하는-접두사를-붙여서-사용합니다)
      - [약어로 시작하는 경우 소문자로 표기하고, 그 외의 경우에는 항상 대문자로 표기한다.](#약어로-시작하는-경우-소문자로-표기하고-그-외의-경우에는-항상-대문자로-표기한다)
      - [이름이 모호할 경우 이름 타입에 대한 힌트를 포함한다.](#이름이-모호할-경우-이름-타입에-대한-힌트를-포함한다)
      - [Action 함수의 네이밍은 '동사 + 목적어'의 형태를 사용한다.](#action-함수의-네이밍은-동사--목적어의-형태를-사용한다)
      - [Delegate method를 만들 때 이름 없는 첫 번째 매개 변수가 delegate source가 되어야 한다.](#delegate-method를-만들-때-이름-없는-첫-번째-매개-변수가-delegate-source가-되어야-한다)
      - [함수 이름 앞에는 되록 get과 같은 광범위한 의미를 지닌 단어의 사용을 지양한다.](#함수-이름-앞에는-되록-get과-같은-광범위한-의미를-지닌-단어의-사용을-지양한다)
      - [뷰(UIView 및 하위 타입)타입 변수의 이름을 지을 때 타입 이름을 뒤에 붙여준다.](#뷰uiview-및-하위-타입타입-변수의-이름을-지을-때-타입-이름을-뒤에-붙여준다)
      - [테스트 이름을 한글로 작성하는 것을 허용한다.](#테스트-이름을-한글로-작성하는-것을-허용한다)
  - [Style](#style)
    - [Basic](#basic-1)
      - [쉽게 타입이 추론될 수 있다면 타입을 포함하지 않는다.](#쉽게-타입이-추론될-수-있다면-타입을-포함하지-않는다)
      - [언어에 의해 요구되거나 모호함을 피하기 위한 경우가 아니라면 self를 사용하지 않는다.](#언어에-의해-요구되거나-모호함을-피하기-위한-경우가-아니라면-self를-사용하지-않는다)
      - [closure 에서 weak self 는 `self` 혹은 `owner` 로 바인딩한다.](#closure-에서-weak-self-는-self-혹은-owner-로-바인딩한다)
      - [tuple 멤버의 이름을 지정하여 더욱 명확하게 표시한다.](#tuple-멤버의-이름을-지정하여-더욱-명확하게-표시한다)
      - [불필요한 괄호는 생략한다.](#불필요한-괄호는-생략한다)
      - [String은 +를 사용하여 연산하는 것을 지양한다.](#string은-를-사용하여-연산하는-것을-지양한다)
    - [Closures](#closures)
      - [파라미터와 리턴 타입이 없는 closure 정의시에는 () -\> Void를 사용한다.](#파라미터와-리턴-타입이-없는-closure-정의시에는----void를-사용한다)
      - [사용되지 않은 closure 매개변수의 이름을 placeholder(\_)로 지정한다.](#사용되지-않은-closure-매개변수의-이름을-placeholder_로-지정한다)
      - [closure 매개변수가 마지막 끝에 하나 있다면 가능한 한 trailing closure 구문을 사용한다.](#closure-매개변수가-마지막-끝에-하나-있다면-가능한-한-trailing-closure-구문을-사용한다)
    - [Properties](#properties)
      - [연산 속성이 읽기전용이라면 get 절을 생략한다.](#연산-속성이-읽기전용이라면-get-절을-생략한다)
      - [Array와 Dictionary\<T: U\> 보다는 \[T\], \[T: U\] 와 같은 syntax sugar를 사용한다.](#array와-dictionaryt-u-보다는-t-t-u-와-같은-syntax-sugar를-사용한다)
    - [Optional](#optional)
      - [가능한 한 ? 로 선언한다.](#가능한-한--로-선언한다)
      - [Optional 변수의 값은 가능한 한 옵셔널 바인딩으로 얻는다.](#optional-변수의-값은-가능한-한-옵셔널-바인딩으로-얻는다)
      - [값을 사용할 필요가 없다면 옵셔널 바인딩을 사용하지 않고 nil을 체크한다.](#값을-사용할-필요가-없다면-옵셔널-바인딩을-사용하지-않고-nil을-체크한다)
  - [Patterns](#patterns)
    - [Basic](#basic-2)
      - [강제 언랩핑 옵션을 사용하지 않고 가능하면 init 타임에 속성을 초기화하는 것을 선호한다.](#강제-언랩핑-옵션을-사용하지-않고-가능하면-init-타임에-속성을-초기화하는-것을-선호한다)
      - [`init()`에서 의미 있는 작업이나 time-intensive 작업을 수행하는 것을 피한다.](#init에서-의미-있는-작업이나-time-intensive-작업을-수행하는-것을-피한다)
      - [scope 시작 부분에 guard 사용을 선호한다.](#scope-시작-부분에-guard-사용을-선호한다)
      - [`if` 문 보다는 `guard` 문을 사용하여 중첩을 최소화한다.](#if-문-보다는-guard-문을-사용하여-중첩을-최소화한다)
      - [여러 종료지점에서 정리 코드가 필요한 경우 defer block을 사용하는 것을 고려한다.](#여러-종료지점에서-정리-코드가-필요한-경우-defer-block을-사용하는-것을-고려한다)
      - [접근 제어는 가능한 한 엄격한 수준이어야 한다.](#접근-제어는-가능한-한-엄격한-수준이어야-한다)
      - [가능한 한 전역 함수를 정의하지 않는다.](#가능한-한-전역-함수를-정의하지-않는다)
      - [public 또는 internal 상수 및 함수를 네임스페이스로 묶고 싶을 때는 case 없는 enum을 사용한다.](#public-또는-internal-상수-및-함수를-네임스페이스로-묶고-싶을-때는-case-없는-enum을-사용한다)
      - [네임스페이스 없이 전역 상수와 함수를 만들지 않는다. 명료함을 위해서라면 네임스페이스를 제한없이 중첩한다.](#네임스페이스-없이-전역-상수와-함수를-만들지-않는다-명료함을-위해서라면-네임스페이스를-제한없이-중첩한다)
      - [가능한 한 immutable 값을 선호한다.](#가능한-한-immutable-값을-선호한다)
      - [Type method는 기본적으로 static 으로 정의한다.](#type-method는-기본적으로-static-으로-정의한다)
      - [클래스는 기본적으로 final로 정의한다.](#클래스는-기본적으로-final로-정의한다)
    - [Objects](#objects)
      - [디미터 법칙을 따른다.](#디미터-법칙을-따른다)
      - [객체의 상태는 숨기고 행동만 외부에 공개한다.](#객체의-상태는-숨기고-행동만-외부에-공개한다)
      - [메서드의 이름은 '어떻게'가 아니라 클라이언트가 '무엇'을 원하는지를 드러내도록 짓는다.](#메서드의-이름은-어떻게가-아니라-클라이언트가-무엇을-원하는지를-드러내도록-짓는다)
    - [Types](#types)
      - [타입의 특성을 고려하여 `class` 와 `struct`, `actor` 를 적절하게 선택한다.](#타입의-특성을-고려하여-class-와-struct-actor-를-적절하게-선택한다)
  - [File](#file)
      - [extension 파일 이름은 {타입}+{extension}.swift 로 명명한다.](#extension-파일-이름은-타입extensionswift-로-명명한다)
  - [Programming Recommendations](#programming-recommendations)
      - [일반적인 변수, 함수의 선언 순서는 아래와 같다.](#일반적인-변수-함수의-선언-순서는-아래와-같다)


## Code Layout

### Basic

#### 한 줄은 120자를 넘지 않아야한다.

#### 들여쓰기 및 indent는 4개의 space를 사용한다.

#### 줄 끝에는 공백을 제거한다.

#### MARK 구문은 위와 공백을 추가한다.

- GOOD 👏
```swift

// MARK: - Layout
func setLayout() {}

// MARK: Reusable
extension AStore {
    ...
}
```

- BAD 👎
```swift

// MARK: - Layout

func setLayout() {}
// MARK: Reusable
extension AStore {
    ...
}
```

#### Scope의 끝에는 빈 줄을 제거한다.

- GOOD 👏
```swift
override func viewDidLoad() {  
    super.viewDidLoad()
}
```

- BAD 👎
```swift
override func viewDidLoad() {  
    super.viewDidLoad()

}
```

#### Scope의 시작에는 빈 줄을 제거한다.

- GOOD 👏
```swift
extension ViewController {
    func asdf() {}
}
```

- BAD 👎
```swift
extension ViewController {

    func asdf() {}
}
```

#### Scope와 Scope 사이에는 공백을 추가한다.

#### 들여쓰기 방식은 [K&R](https://ko.wikipedia.org/wiki/%EB%93%A4%EC%97%AC%EC%93%B0%EA%B8%B0_%EB%B0%A9%EC%8B%9D#K.26R_style) 스타일을 따른다.

#### 공백줄은 1줄까지만 허용한다.

- GOOD 👏
```swift
func asdf() {
    let asdf = ""

    print(asdf)
}
```

- BAD 👎
```swift
func asdf() {
    let asdf = ""


    print(asdf)
}
```

#### 공백은 1칸까지만 허용한다.

#### 선언부 앞의 주석은 Doc주석으로 작성한다.

#### guard의 else는 가독성을 해치지 않거나 120줄을 넘지 않으면 같은 줄에 작성한다.

#### namespace는 오직 enum으로만 만든다.

#### extension에서 접근제어자를 설정할때는 선언이 아닌 extension에 설정한다.

#### FileHeader는 제거한다.

#### let, var를 바인딩할 때는 hoist 형태로 바인딩한다

- GOOD 👏
```swift
switch case let .foo(a, b):
    ...
```

- BAD 👎
```swift
switch case .foo(let a, let b):
    ...
```

#### 파일의 끝에는 빈 공백줄을 추가한다.

#### 파라미터에 Protocol을 받을때는 필요하지 않다면 Generic 대신 some을 사용한다.

- GOOD 👏
```swift
func foo<T: AProtocol>(bar: T) {}
```

- BAD 👎
```swift
func foo(bar: some AProtocol) {}
```

#### 고차함수를 사용할 때 KeyPath로 접근할 수 있다면 KeyPath를 사용한다.

- GOOD 👏
```swift
let foo = bar.map(\.name)
```

- BAD 👎
```swift
let foo = bar.map { $0.name }
```

#### 중괄호 주위에 공백을 준다.

- GOOD 👏
```swift
foo.filter{ true }.map{ $0 }
```

- BAD 👎
```swift
foo.filter{true}.map{$0}
```

#### 식별자 바로 뒤에 콜론 : 을 배치하고 그 뒤에 공백을 넣는다.

- GOOD 👏
```swift
let foo: String
struct Foo: Bar {}
```

- BAD 👎
```swift
let foo : String
let bar :String
struct Foo : Bar {}
```

#### 가독성을 위해 함수의 리턴 화살표 양쪽에 공백을 둔다.

- GOOD 👏
```swift
func foo() -> String {}
```

- BAD 👎
```swift
func foo()->String {}
```

#### TODO와 FIXME는 Warning을 발생시켜야 한다.

- GOOD 👏
```swift
func foo() {
    #warning("TODO: 추가 로직")
}

#warning("FIXME: 파라미터 이름 변경 예정")
func bar(param: String) {}
```

- BAD 👎
```swift
func foo() {
    // TODO: 추가 로직
}

// FIXME: 파라미터 이름 변경 예정
func bar(param: String) {}
```

### Functions

#### 메서드 내의 공백은 기능을 분리해야 하지만 섹션이 너무 많으면 종종 여러 메서드로 리팩토링해야한다.

#### 함수 정의 시 매개변수나 호출 시 인수는 같은 줄에 놓거나, 줄 당 하나만 있게한다. 여러 줄로 만든다면, 각각 새 줄에 놓고 들여쓰기를 추가한다.

- GOOD 👏
```swift
func reticulateSplines(
  spline: [Double],
  adjustmentFactor: Double,
  translateConstant: Int,
  comment: String
) -> Bool {
  // reticulate code goes here
}

let actionSheet = UIActionSheet(
  title: "정말 계정을 삭제하실 건가요?",
  delegate: self,
  cancelButtonTitle: "취소",
  destructiveButtonTitle: "삭제해주세요"
)
```

- BAD 👎
```swift
func reticulateSplines(spline: [Double], adjustmentFactor: Double, translateConstant: Int, comment: String) -> Bool {
  // reticulate code goes here
}

let actionSheet = UIActionSheet(title: "정말 계정을 삭제하실 건가요?", delegate: self, cancelButtonTitle: "취소", destructiveButtonTitle: "삭제해주세요")
```

#### 함수 매개변수에 closure 가 2개 이상 존재하는 경우 내려쓰기를 한다.

- GOOD 👏
```swift
UIView.animate(
    withDuration: 0.25,
    animations: {
        // doSomething()
    },
    completion: { finished in
        // doSomething()
    }
)
```

- BAD 👎
```swift
UIView.animate(
    withDuration: 0.25, animations: {
        // doSomething()
    },
    completion: { finished in
        // doSomething()
    }
)
```

### Operators

#### infix 연산자는 양쪽에 하나의 공간이 있어야 한다.
- 이 규칙은 범위 연산자에는 적용되지 않는다(예: 1...3) 및 postfix 또는 접두사 연산자 (예: guest? , -1)
- 많은 연산자가 있는 문장을 시각적으로 그룹화하기 위해 공백의 폭을 다양하게 하기 보다는 괄호를 선호한다.

- GOOD 👏
```swift
let capacity = 1 + 2
let capacity = currentCapacity ?? 0
let mask = (UIAccessibilityTraitButton | UIAccessibilityTraitSelected)
let capacity = newCapacity
let latitude = region.center.latitude - (region.span.latitudeDelta / 2.0)
```

- BAD 👎
```swift
let capacity = 1+2
let capacity = currentCapacity   ?? 0
let mask = (UIAccessibilityTraitButton|UIAccessibilityTraitSelected)
let capacity=newCapacity
let latitude = region.center.latitude - region.span.latitudeDelta/2.0
```

---

## Naming

명명은 기본적으로 [Swift API Design Guidelines](https://swift.org/documentation/api-design-guidelines/)의 가이드를 따른다. 위 문서의 내용을 여기에 정리할 수 도 있고, 새로운 가이드라인을 추가할 수도 있다.

### Format

#### 타입(struct, class, enum)과 protocol 이름은 PascalCase를 사용하고, 그 외에는 lowerCamelCase 를 사용한다.

- 예외: 동일한 이름의 속성이나 메서드가 더 높은 액세스 수준을 가진 경우, private 속성에 밑줄 접두사를 붙일 수 있다.

- GOOD 👏
```swift
protocol SpaceThing {
 // ...
}

class SpaceFleet: SpaceThing {

 enum Formation {
   // ...
 }

 class Spaceship {
   // ...
 }

 var ships: [Spaceship] = []
 static let worldName: String = "Earth"

 func addShip(_ ship: Spaceship) {
   // ...
 }
}

let myFleet = SpaceFleet()
```

#### Bool타입은 is, has 와같이 Bool타입임을 분명히하는 접두사를 붙여서 사용합니다.
- 이것은 변수가 다른 타입이 아닌 Bool이라는 것을 분명히 한다.

#### 약어로 시작하는 경우 소문자로 표기하고, 그 외의 경우에는 항상 대문자로 표기한다.

- GOOD 👏
```swift
let html: String
let userID: String
class URLConvertible {}
```

- BAD 👎
```swift
let HTML: String
let userId: String
class UrlConvertible {}
```

#### 이름이 모호할 경우 이름 타입에 대한 힌트를 포함한다.

- GOOD 👏
```swift
let titleText: String
let cancelButton: UIButton
```

- BAD 👎
```swift
let title: String
let cancel: UIButton
```

#### Action 함수의 네이밍은 '동사 + 목적어'의 형태를 사용한다.
- 주어가 **명확**하다면 생략할 수 있다.
- 대표적인 동사로 Tap은 버튼이 눌린 행위, Gesture는 특정 제스쳐가 발생했을 때의 행위, Scroll은 스크롤이 발생했을 때의 행위이다.
- will~은 특정 행위가 일어나기 직전이고, did~는 특정 행위가 일어난 직후다.
- should~은 일반적으로 Bool을 리턴하는 함수에 사용한다.

- GOOD 👏
```swift
func backButtonDidTap() {
  // ...
}
```

- BAD 👎
```swift
func back() {
  // ...
}
func tapBack() {
  // ...
}
```

#### Delegate method를 만들 때 이름 없는 첫 번째 매개 변수가 delegate source가 되어야 한다.

- GOOD 👏
```swift
func namePickerView(_ namePickerView: NamePickerView, didSelectName name: String)
func namePickerViewShouldReload(_ namePickerView: NamePickerView) -> Bool
```

- BAD 👎
```swift
func didSelectName(namePicker: NamePickerViewController, name: String)
func namePickerShouldReload() -> Bool
```

#### 함수 이름 앞에는 되록 get과 같은 광범위한 의미를 지닌 단어의 사용을 지양한다.
- 다른 개발자가 읽었을 때 한 번에 이해할 수 있을 만한 함수의 액션을 나타내는 단어를 사용합니다.

- GOOD 👏
```swift
func fetchUserInfo() {
...
}
```

- BAD 👎
```swift
func getUser() {
...
}
```

#### 뷰(UIView 및 하위 타입)타입 변수의 이름을 지을 때 타입 이름을 뒤에 붙여준다.
- 타입 이름을 줄이지 않는다.
  - 예외: `UICollectionViewCell`, `UITableViewCell` 의 경우는 너무 길기 때문에 Cell만 활용하는 것을 허용한다.

#### 테스트 이름을 한글로 작성하는 것을 허용한다.
- 한글로 작성하면 올바른 테스트인지 판단하기가 더 쉽다.

---

## Style

### Basic

#### 쉽게 타입이 추론될 수 있다면 타입을 포함하지 않는다.

#### 언어에 의해 요구되거나 모호함을 피하기 위한 경우가 아니라면 self를 사용하지 않는다.

#### closure 에서 weak self 는 `self` 혹은 `owner` 로 바인딩한다.

#### tuple 멤버의 이름을 지정하여 더욱 명확하게 표시한다.
- 튜플의 필드가 3개이상이라면 struct를 사용하는 것을 권장하고 4개라면 필수적으로 struct로 변경한다.

- GOOD 👏
```swift
func whatever() -> (width: Int, height: Int) {
 return (width: 4, height: 4)
}

let rect = whatever()
rect.width
rect.y
```

- BAD 👎
```swift
func whatever() -> (Int, Int) {
 return (4, 4)
}

let rect = whatever()
rect.0
rect.1
```

#### 불필요한 괄호는 생략한다.

- GOOD 👏
```swift
if userCount > 0 { ... }
switch someValue { ... }
let evens = userCounts.filter { number in number % 2 == 0 }
let squares = userCounts.map { $0 * $0 }
```

- BAD 👎
```swift
if (userCount > 0) { ... }
switch (someValue) { ... }
let evens = userCounts.filter { (number) in number % 2 == 0 }
let squares = userCounts.map() { $0 * $0 }
```

#### String은 +를 사용하여 연산하는 것을 지양한다.
- 컴파일 시간에 영향을 주는 주요 원인이므로 지양한다.

- GOOD 👏
```swift
let firstName = "김"
let secondName = "이름"
let wholeName = "\(firstName)\(secondName)"
```

- BAD 👎
```swift
let firstName = "김"
let secondName = "티드"
let wholeName = firstName+secondName
```

### Closures

#### 파라미터와 리턴 타입이 없는 closure 정의시에는 () -> Void를 사용한다.
- 가독성과 일관성을 위하여 () -> Void로 정의한다.

- GOOD 👏
```swift
let completion: () -> Void
```

- BAD 👎
```swift
let completion: () -> ()
let completion: (Void) -> (Void)
```

#### 사용되지 않은 closure 매개변수의 이름을 placeholder(_)로 지정한다.
- 어떤 매개변수가 사용되고 어떤 매개변수가 사용되지 않는지 명확히 함으로써 closure를 읽을 때 필요한 인지 오버헤드가 감소한다.

- GOOD 👏
```swift
someAsyncThing() { _, _, arg3 in
  print(arg3)
}
```

- BAD 👎
```swift
someAsyncThing() { arg2, arg2, arg3 in
  print(arg3)
}
```

#### closure 매개변수가 마지막 끝에 하나 있다면 가능한 한 trailing closure 구문을 사용한다.
- 둘 이상이라면 평범하게 사용한다.

- GOOD 👏
```swift
UIView.animate(withDuration: 1.0) {
    self.myView.alpha = 0
}

UIView.animate(withDuration: 1.0, animations: {
 self.myView.alpha = 0
}, completion: { finished in
 self.myView.removeFromSuperview()
})
```

- BAD 👎
```swift
UIView.animate(withDuration: 1.0, animations: {
 self.myView.alpha = 0
})

UIView.animate(withDuration: 1.0, animations: {
 self.myView.alpha = 0
}) { f in
 self.myView.removeFromSuperview()
}
```

### Properties

#### 연산 속성이 읽기전용이라면 get 절을 생략한다.

#### Array<T>와 Dictionary<T: U> 보다는 [T], [T: U] 와 같은 syntax sugar를 사용한다.

### Optional

#### 가능한 한 ? 로 선언한다.
- 예외: 단위 테스트에서는 ! 로 선언하는 것이 허용된다.

#### Optional 변수의 값은 가능한 한 옵셔널 바인딩으로 얻는다.
- !를 사용한 강제 언래핑은 앱 크래시의 가능성이 있기 때문이다.

#### 값을 사용할 필요가 없다면 옵셔널 바인딩을 사용하지 않고 nil을 체크한다.

---

## Patterns

### Basic

#### 강제 언랩핑 옵션을 사용하지 않고 가능하면 init 타임에 속성을 초기화하는 것을 선호한다.

- GOOD 👏
```swift
class MyClass: NSObject {

  init() {
    someValue = 0
    super.init()
  }

  var someValue: Int
}
```

- BAD 👎
```swift
class MyClass: NSObject {

  init() {
    super.init()
    someValue = 5
  }

  var someValue: Int!
}
```

#### `init()`에서 의미 있는 작업이나 time-intensive 작업을 수행하는 것을 피한다.
- 데이터베이스 연결 열기, 네트워크 요청, 디스크에서 대량의 데이터 읽기 등의 작업을 수행하지 않는다. 객체를 사용할 준비가 되기 전에 이러한 작업을 수행해야 하는 경우 start() 메서드과 같은 것을 만든다.

#### scope 시작 부분에 guard 사용을 선호한다.
- 모든 guard 문을 상단에 모아놓는 것이 비즈니스 로직과 섞일때 code block에 대해 추론하는 것이 더 쉽다.

#### `if` 문 보다는 `guard` 문을 사용하여 중첩을 최소화한다.
- 탈출 조건에서 throws나 return 문 등을 실행하거나 옵셔널 바인딩을 해야할 때 guard 문을 사용하면 중첩도를 줄여서 가독성과 유지보수성을 높일 수 있다.

#### 여러 종료지점에서 정리 코드가 필요한 경우 defer block을 사용하는 것을 고려한다.

#### 접근 제어는 가능한 한 엄격한 수준이어야 한다.
- 그런 행동이 필요하지 않는 한 open보다는 public, fileprivate보다는 private 쪽을 선호한다.

#### 가능한 한 전역 함수를 정의하지 않는다.
- 타입 정의부안에서 메서드를 정의하는 것을 선호한다.

#### public 또는 internal 상수 및 함수를 네임스페이스로 묶고 싶을 때는 case 없는 enum을 사용한다.

#### 네임스페이스 없이 전역 상수와 함수를 만들지 않는다. 명료함을 위해서라면 네임스페이스를 제한없이 중첩한다.

#### 가능한 한 immutable 값을 선호한다.
- 새 컬렉션에 추가하는 대신 map 과 compactMap 을 사용한다. 변경 가능한 컬렉션에서 요소를 제거하는 대신 filter를 사용한다.


#### Type method는 기본적으로 static 으로 정의한다.
- 메소드를 재정의가 필요한 경우에 class 키워드를 사용한다.

#### 클래스는 기본적으로 final로 정의한다.
- 클래스를 재정의해야하는 경우에는 final 키워드를 생략한다.

### Objects

#### 디미터 법칙을 따른다.
- 디미터 법칙을 따르는 코드는 메시지 전송자가 수신자의 내부 구현에 결합되지 않는다.
- 디미터 법칙을 위반한 코드를 수정하는 일반적인 방법은 `묻지 말고 시켜라`를 따르는 것이다.

#### 객체의 상태는 숨기고 행동만 외부에 공개한다.
- E.g. 속성은 private으로 만들어서 직접 접근하지 않고, 메서드만 사용한다.

#### 메서드의 이름은 '어떻게'가 아니라 클라이언트가 '무엇'을 원하는지를 드러내도록 짓는다.

### Types

#### 타입의 특성을 고려하여 `class` 와 `struct`, `actor` 를 적절하게 선택한다.
- struct는 value sementics, class와 actor는 reference sementics를 가지고 있다.
- 상황에 따라 적절한 타입을 선택한다.

## File

#### extension 파일 이름은 {타입}+{extension}.swift 로 명명한다.

## Programming Recommendations

#### 일반적인 변수, 함수의 선언 순서는 아래와 같다.
- Property Wrapper 변수
- 상수
- 변수
- 연산 프로퍼티
- 생성자 및 소멸자
- override 함수
- public 함수
- private 함수
- extension
