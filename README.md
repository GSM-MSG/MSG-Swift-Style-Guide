# MSG Swift Style Guide
코드를 이해하고 작성하는 데에, 더 도움을 주고 명확하게 소통하기 위한 MSG의 Swift Style Guide입니다.
코드 리뷰때에서 아래 내용을 바탕으로 신명나게 지적해주세요!
구성원들의 의사결정에 따라 수시로 변경될 수 있습니다.

## 목차
- [MSG Swift Style Guide](#msg-swift-style-guide)
  - [목차](#목차)
  - [Naming](#naming)
    - [디렉토리](#디렉토리)
    - [파일명](#파일명)
    - [class & struct](#class--struct)
    - [함수](#함수)
    - [변수](#변수)
    - [상수](#상수)
    - [enum](#enum)
    - [약어](#약어)
  - [Formatting](#formatting)
    - [최대 줄길이](#최대-줄길이)
    - [들여쓰기](#들여쓰기)
    - [띄어쓰기](#띄어쓰기)
    - [줄바꿈](#줄바꿈)
    - [빈 줄](#빈-줄)
    - [Switch](#switch)
  - [class & struct](#class--struct-1)
  - [Closure](#closure)
  - [프로그래밍 권장 사항](#프로그래밍-권장-사항)

## Naming
### 디렉토리
- 디렉토리 이름은 대문자로 시작하는 단어로 설정합니다.
- 해당 디렉토리에 비슷한 기능을 하는 파일들이 들어있다면 단어의 끝에 복수로 `s`를 붙여줍니다.
  - **GOOD👏**
    ```swift
    - Domains, Entities, Views
    ```

  - **BAD👎**
    ```swift
    - Domain, Entity, View
    ```

### 파일명
- 파일명은 `UpperCamelCase`를 사용합니다.
- 파일명은 줄여서 사용하지 않습니다.
- ViewController, View, ViewModel, Reactor 등 매칭되는 **접두사(prefix)**를 사용합니다.
  - **GOOD👏**
    ```swift
    - HomeViewController.swift
    - HomeViewModel.swift
    ```

  - **BAD👎**
    ```swift
    - HomeVC.swift
    - HomeVM.swift
    ```

### class & struct
- class 및 struct의 이름은 `UpperCamelCase`를 사용합니다.

### 함수
- 함수 이름에는 `lowerCamelCase`를 사용합니다.
- 함수 이름 앞에는 되록 `get`과 같은 광범위한 의미를 지닌 단어의 사용을 지양합니다.
  - 다른 개발자가 읽었을 때 한 번에 이해할 수 있을 만한 함수의 액션을 나타내는 단어를 사용합니다.
  - **GOOD👏**
    ```swift
    func fetchUserInfo() {
    ...
    }
    ```

  - **BAD👎**
    ```swift
    func getUserInfo() {
    ...
    }
    ```

- Action 함수의 네이밍은 '주어 + 동사 + 목적어'의 형태를 사용합니다.
  - 대표적인 동사로 *Tap*은 버튼이 눌린 행위, *Gesture*는 특정 제스쳐가 발생했을 때의 행위, *Scroll*은 스크롤이 발생했을 때의 행위입니다.
  - *will~*은 특정 행위가 일어나기 직전이고, *did~*는 특정 행위가 일어난 직후입니다.
  - *should~*은 일반적으로 `Bool`을 리턴하는 함수에 사용합니다.

### 변수
- 변수 이름에는 `lowerCamelCase`를 사용합니다.
- 변수 타입 중 Bool타입은 is 와같은 be동사를 접두사를 붙여서 사용합니다.
- 배열 혹은 리스트와 같이 복수의 의미를 담고있는 변수라면 끝에 **s**를 붙여서 사용합니다.
  - **GOOD👏**
    ```swift
    var images: [Message] = []
    var title: String = ""
    var isValid: Bool = false
    ```

  - **BAD👎**
    ```swift
    var image: [Message] = []
    var valid: Bool = false
    ```

### 상수
- 상수 이름에는 `lowerCamelCase`를 사용합니다.
- 변수 타입 중 Bool타입은 is 와같은 be동사를 접두사를 붙여서 사용합니다.
- 배열 혹은 리스트와 같이 복수의 의미를 담고있는 변수라면 끝에 **s**를 붙여서 사용합니다.
  - **GOOD👏**
    ```swift
    let horizontalMargin: CGFloat = 40
    ```

  - **BAD👎**
    ```swift
    let HORIZONTAL_MARGIN: CGFloat = 40
    ```

### enum
- 열거형 enum 변수들은 `lowerCamelCase`를 사용합니다.
  - **GOOD👏**
    ```swift
    enum MessageType {
      case text
      case image
      case video
    }
    ```

  - **BAD👎**
    ```swift
    enum MessageType {
      case TEXT
      case IMAGE
      case VIDEO
    }
    ```

### 약어
- 약어로 시작하는 변수의 경우 소문자로 시작합니다.
- 약어로 시작하는 class, struct, enum의 경우 대문자료 사용합니다.
- 변수, 클래스 등의 중간에 약어가 들어가는 경우 대문자를 사용합니다.
  - **GOOD👏**
    ```swift
    let html: String
    let userID: String
    class URLConvertible {}
    ```

  - **BAD👎**
    ```swift
    let HTML: String
    let userId: String
    class UrlConvertible {}
    ```

## Formatting
### 최대 줄길이
- 한줄 최대 길이는 **100**자로 설정합니다.
- XCode > Preferences > Text Editing > Display > Page guide at column에서 설정할 시 편합니다.

### 들여쓰기
- 들여쓰기는 4 spaces로 설정합니다.
- XCode > Preferences > Text Editing > Indentation에서 설정 가능합니다.

### 띄어쓰기
- 콜론(:) 뒤에는 띄어쓰기를 사용합니다.
  - **GOOD👏**
    ```swift
    let userID: String
    ```

  - **BAD👎**
    ```swift
    let userID : String
    ```

- 삼항연산자의 경우 (:)의 앞에도 띄어쓰기를 사용합니다.
  - **GOOD👏**
    ```swift
    isLike ? "heart.fill" : "heart"
    ```

  - **BAD👎**
    ```swift
    isLike ? "heart.fill": "heart"
    ```

- 함수를 정의할 때 파라미터 뒤(,)에는 띄어쓰기를 사용합니다
  - **GOOD👏**
    ```swift
    func sum(x: Int, y: Int) -> Int
    ```

  - **BAD👎**
    ```swift
    func sum(x: Int,y: Int) -> Int
    ```

- 연산자 앞뒤로 공백을 추가해서 사용합니다.
  - **GOOD👏**
    ```swift
    let x = 1 + 2
    ```

  - **BAD👎**
    ```swift
    let x = 1+2
    ```

### 줄바꿈
- 함수의 파라미터 혹은 이름이 길어져 100글자를 넘어갈 경우 다음과 같이 줄바꿈합니다
  - **GOOD👏**
    ```swift
    func animationController(
        forPresented presented: UIViewController,
        presenting: UIViewController,
        source: UIViewController
    ) -> UIViewControllerAnimatedTransitioning? {
    ...
    }
    ```

  - **BAD👎**
    ```swift
    func animationController(forPresented presented: UIViewController, presenting: UIViewController, source: UIViewController) -> UIViewControllerAnimatedTransitioning? {
    ...
    }
    ```
  
- 함수를 호출하는 코드가 최대 길이를 초과하는 경우에는 파라미터 이름을 기준으로 줄바꿈합니다.
  - **GOOD👏**
    ```swift
    self.navigationController?.pushViewController(
      viewController, 
      animated: true
    )
    ```

  - **BAD👎**
    ```swift
    self.navigationController?.pushViewController(viewController, animated: true)
    ```

  **단, 파라미터에 클로저가 2개 이상 존재하는 경우에는 무조건 내려쓰기합니다.**
  - **GOOD👏**
    ```swift
    UIView.animate(
        withDuration: 0.25,
        animations: {
        ...
       },
       completion: { finished in
         ...
        }
    )
    ```
  - **BAD👎**
    ```swift
    UIView.animate(withDuration: 0.25, animations: { 
        ...
    }, completion: { finished in
        ... 
    }
    ```

- 배열의 컨텐츠를 정의할 때 길이가 길어진다면 다음과 같이 줄바꿈합니다.
  - **GOOD👏**
    ```swift
    self.addSubViews([
      titleLabel,
      titleButton,
      nextButton
    ])
    ```

  - **BAD👎**
    ```swift
    self.addSubViews([titleLabel, titleButton,
      nextButton])
    ```

- 변수의 네이밍과 타입명이 길어서 정의하는데 100자가 넘어간다면 다음과 같이 줄바꿈 합니다.
  - **GOOD👏**
    ```swift
    private var myPageTableViewDataSource = 
      RxTableViewSectionedReloadDataSource<MyPageSecionModel>()
    ```

  - **Bad👎**
    ```swift
    private var myPageTableViewDataSource = RxTableViewSectionedReloadDataSource<MyPageSecionModel>()
    ```

- if let 구문이 길어질 경우에는 쉼표 이후에 줄바꿈을 합니다.
  - **GOOD👏**
    ```swift
    if let user = user,
      let compete = compete {
    ...
    }
    ```

  - **BAD👎**
    ```swift
    if let user = user, let compete = compete {
    ...
    }
    ```

- `guard let ... else` 는 한줄에 표시합니다.
  - **GOOD👏**
    ```swift
    guard let user = optionalUser else { return }
    ```
  
  - **BAD👎**
    ```swift
    guard let user = optionalUser
    else { return }
    ```

- `guard let` 구문이 길 경우에는 줄바꿈하고 한 칸 들여씁니다. `else`는 `guard`와 같은 들여쓰기를 적용합니다.
  - **GOOD👏**
    ```swift
    guard 
        let user = optionalUser,
        let compete = optionalCompete
    else {
        return
    }
    ```
  
  - **BAD👎**
    ```swift
    guard let user = optionalUser, let compete = optionalCompete else { return }
    ```

### 빈 줄
- 빈 줄에는 공백이 포함되지 않도록 합니다.
- 모든 파일은 빈 줄로 끝나도록 합니다.
- MARK 구문 위와 아래에는 공백이 필요합니다.
  - **GOOD👏**
     ```swift
    // MARK: - Layout

    override func layoutSubviews() {
    ...
    }

    // MARK: - Actions

    func menuButtonDidTap() {
    ...
    }
    ```

  - **BAD👎**
    ```swift
    // MARK: - Layout
    override func layoutSubviews() {
    ...
    }
    // MARK: - Actions
    func menuButtonDidTap() {
    ...
    }


### Switch
- switch문 안의 case문은 줄바꿈 후 내용을 정의합니다.
- case문들 사이에는 한 줄 공백을 추가합니다.
  - **GOOD👏**
    ```swift
    switch user.status {
    case .success:
      ...

    case .failure:
      ...
    }
    ```

  - **BAD👎**
    ```swift
    switch user.status {
    case .success:
      ...
    case .failure: ...
    }
    ```

- switch문 내부의 case에 파라미터가 있을 경우 let을 **맨 앞**에 위치 시킵니다.
  - **GOOD👏**
    ```swift
    switch user.status {
    case let .success(res):
    ...
    case let .failure(error):
    ...
    }
    ```

  - **BAD👎**
    ```swift
    switch user.status {
    case .success(let res):
    ...
    case .failure(let error):
    ...
    }
    ```

## class & struct
- 더이상 상속이 발생하지 않는 클래스는 항상 `final` 키워드로 선언합니다.
- 클래스와 구조체 내부에서는 `self`를 명시적으로 사용합니다.
- 단, 파라미터에 사용할 경우 `self`를 사용하지 않습니다.
  - **GOOD👏**
    ```swift
    class ViewController: UIViewController {
        override func viewDidLoad() {
            super.viewDidLoad()
            self.fetchData(user: userName)
        }
    }
    ```
  - **BAD👎**
    ```swift
    class ViewController: UIViewController {
        override func viewDidLoad() {
            super.viewDidLoad()
            fetchData(user: self.userName)
        }
    }
    ```

- 프로토콜을 채택할 경우, 가급적 `extension`을 사용합니다.
  - **Good👏**
    ```swift
    class ViewController: UIViewController {
    ...
    }
     
    extension ViewController: UITableViewDelegate {
    ...
    }
    ```

  - **Bad👎**
    ```swift
    class ViewController: UIViewController, UITableViewDelegate {
    ...
    }
    ```

## Closure
- 파라미터와 리턴 타입이 없는 Closure 정의시에는 `() -> Void`를 사용합니다.
  - **GOOD👏**
    ```swift
    let completionBlock: (() -> Void)?
    ```

  - **BAD👎**
    ```swift
    let completionBlock: (() -> ())?
    let completionBlock: ((Void) -> (Void))?
    ```

- 클로저 내의 파라미터에는 괄호를 사용하지 않습니다.
  - **GOOD👏**
    ```swift
    let closure = { arg1, arg2 in
    ...
    }
    ```

  - **BAD👎**
    ```swift
    let closure = { (arg1, arg2) in
    ...
    }
    ```

- Closure 정의시 가능한 경우 타입 정의를 생략합니다.
  - **GOOD👏**
    ```swift
    let closure = { arg1 in
    ...
    }
    ```
  
  - **BAD👎**
    ```swift
    let closure = { (arg1: String) in
    ...
    }
    ```

- 사용하지 않는 클로저 파라미터는 `_`로 선언합니다.
  - **GOOD👏**
    ```swift
    let closure = { _, arg2 in
        print(arg2)
    }
    ```

  - **BAD👎**
    ```swift
    let closure = { (arg1, arg2) in
        pring(arg2)
    }
    ```

- Closure 호출시 또다른 유일한 Closure를 마지막 파라미터로 받는 경우, 파라미터 이름을 생략합니다.
  - **GOOD👏**
    ```swift
    UIView.animate(withDuration: 0.5) {
    ...
    }
    ```

  - **BAD👎**
    ```swift
    UIView.animate(withDuration: 0.5, animations: { () -> Void in
    ...
    })
    ```
## 주석
- 문서화를 할 경우 `///`을 사용합니다.
  - **GOOD👏**
    ```swift
    /// 사용자 프로필을 그려주는 뷰
    class ProfileView: UIView {

      /// 사용자 닉네임을 그려주는 라벨
      var nameLabel: UILabel!
    }
    ```

  - **BAD👎**
    ```swift
    // 사용자 프로필을 그려주는 뷰
    class ProfileView: UIView {

        // MARK: 사용자 닉네임을 그려주는 라벨
        var nameLabel: UILabel
    }
    ```

- `// MARK: -` 또는 `// MARK:`를 사용해서 연관된 코드를 구분짓습니다.
- `// MARK: -`는 대제목, `// MARK:`는 소제목격으로 구분짓습니다.
  - **GOOD👏**
    ```swift
    // MARK: - Properties
    private let profileImageView = UIImageView()

    // MARK: - init
    init() {
    ...
    }
    ```

  - **BAD👎**
    ```swift
    // MARK: Properties
    private let profileImageView = UIImageView()
    
    // MARK: init
    init() {
    ...
    }
    ```

## 프로그래밍 권장 사항
- 상수를 정의할 때에는 `enum`를 만들어 비슷한 상수끼리 모아둡니다. 재사용성과 유지보수 측면에서 큰 향상을 가져옵니다. `struct` 대신 `enum`을 사용하는 이유는, 생성자가 제공되지 않는 자료형을 사용하기 위해서입니다.
- 
  ```swift
  final class ProfileViewController: UIViewController {

      private enum Metric {
          static let profileImageViewLeft: CGFloat = 10
          static let profileImageViewRight: CGFloat = 10
          static let nameLabelTopBottom: CGFloat = 8
          static let bioLabelTop: CGFloat = 6
      }

      private enum Font {
          static let nameLabel = UIFont.boldSystemFont(ofSize: 14)
          static let bioLabel = UIFont.boldSystemFont(ofSize: 12)
      }

      private enum Color {
          static let nameLabelText = UIColor(hex: 0x000000)
          static let bioLabelText = UIColor(hex: 0x333333)
      }

  }
  ```

    이렇게 선언된 상수들은 다음과 같이 사용될 수 있습니다.

    ```swift
    self.profileImageView.frame.origin.x = Metric.profileImageViewLeft
    self.nameLabel.font = Font.nameLabel
    self.nameLabel.textColor = Color.nameLabelText
    ```

- 일반적인 변수, 함수의 선언 순서는 아래와 같습니다.
  - 상수
  - 변수
  - 생성자 및 소멸자
  - override 함수
  - public 함수
  - private 함수
