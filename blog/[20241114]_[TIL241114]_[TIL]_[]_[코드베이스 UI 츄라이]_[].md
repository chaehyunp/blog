
UIKit을 사용하면 자동으로 storyboard 파일이 생성된다.
하지만, 스토리보드 없이도 오직 코드로만 UI를 작업할 수 있다.

1️⃣ 스토리보드를 과감하게 삭제해주자

<img width="298" alt="과감하게메인지우기" src="https://github.com/user-attachments/assets/783993b8-3b76-4e88-86d8-2606428e1d4b">

</br>

스토리보드만 지운다고 끝이 아니다. </br>
2️⃣ Main.storyboard와 링크된 것들을 끊어주어야 한다.

<img width="931" alt="링크된것도모두삭제메인검색" src="https://github.com/user-attachments/assets/3e747076-7c6b-4671-9cd7-25e99bf21cc0">

`info.plist` 파일에서 'main'을 검색하고 Storyboard Name을 선택한 후 백스페이스바를 누르면 지울 수 있다.

<img width="913" alt="빌드세팅에도지워주기" src="https://github.com/user-attachments/assets/0ad5db68-1460-4b5d-b1dc-f5ad31decee2">

BuildSetting에도 있다. 마찬가지로 검색해서 지워주자.

<img width="402" alt="짠" src="https://github.com/user-attachments/assets/ee8093a2-3998-4546-8096-7500c24695d4">

Storyboard Name과는 다르게 해당 항목이 사라지는 것은 아니고 값만 지워진다. Main만 안나오면 👌

</br>

마지막으로,</br>
3️⃣ SceneDelegate에 시작점을 설정해주어야 한다.
<img width="981" alt="신딜리게이트에서시작점설정" src="https://github.com/user-attachments/assets/aa2f59ef-bb2f-4697-bb6f-3e3f2aebb2c4">

이 부분에 시작점을 알려주는 코드를 작성해주어야 한다.

```swift
class SceneDelegate: UIResponder, UIWindowSceneDelegate {

		// UIWindow : 앱에 반드시 한 개 이상 필요한 근본이 되는 뷰, 이 위에 뷰가 쌓이기 시작함 
    var window: UIWindow?

		// 앱 시작시 세팅해주는 코드를 작성
    func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        // UIWindow 객체 생성, window가 optional이므로 nil값일 경우 리턴
        guard let windowScene = (scene as? UIWindowScene) else { return }
        let window = UIWindow(windowScene: windowScene)
        
        // window에게 루트뷰 지정
        window.rootViewController = ViewController()
        
         // 이 메서드를 반드시 작성해주어야 윈도우가 활성화!
        window.makeKeyAndVisible()
        self.window = window
    } 

    ...
}
```

작성을 완료했다면 에러 없이 잘 실행되는지 런 돌려보자.



에러없이 잘 구동되었다면 코드베이스로 UI 준비갈완료 🫧

<img width="60%" center alt="신딜리게이트에서시작점설정" src="https://github.com/user-attachments/assets/e416174e-b94f-442a-abe0-5ed4740c0518">
