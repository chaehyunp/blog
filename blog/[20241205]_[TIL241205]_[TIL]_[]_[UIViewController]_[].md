## UIViewController
- UIKit 앱의 뷰 계층을 관리하는 개체
- 한 개의 페이지는 반드시 한 개의 UIViewController를 가지고 내부에 UIKit의 UI클래스들을 배치하여 화면을 구성

## ViewController 생명주기
#### iOS의 대표 생명주기 2가지
1. App Lifecycle
2. ViewController Lifecycle  
1️⃣. init: 생성자  
2️⃣. loadView: UIViewController를 생성하면 반드시 하나의 뷰를 갖는데, 뷰가 메모리에 올라가기 전 사전 작업을 이때 진행됨  
3️⃣. viewDidLoad: 뷰가 메모리에 올라감, **메모리에 올라가기 위한 한 번만 호출**   
4️⃣. viewWillApear: 뷰가 메모리에 로드가 된 후 유저에게 보이기 직전, **여러 번 호출이 가능**(다른 화면에 갔다가 돌아오면 호출됨)  
5️⃣. viewIsApearing: 뷰가 유저에게 나타내고 있는 중...  
6️⃣. viewDidApear: 뷰가 유저에게 보여지는 상태  
7️⃣. viewWillDisappear: 뷰가 책임을 다 하고 사라질 것  
8️⃣. viewDidDisapear: 뷰가 사라짐  
9️⃣. deinit: 소멸자 