오늘은 Storyboard 없이 개발하는 방법에 대해 알아볼거에요. 



### 스토리보드 없이 사용하는것의 장점은?

1. 뷰가 많아져도 랙이 없어요.
2. 뷰 제약사항이 비교적 가독성이 좋아져요.
3. 대부분 애플 개발자문서는 코드로 되어있어 사용하기 편해요.
4. 가독성이 좋아 현업하기 좋은 것 같아요.
5. 코드를 많이 쳐서 전문가 같아 보여요..

제가 느낀건 이정도 있는 것 같아요 ㅋㅋ 그럼 스토리보드 없이 개발하는 방법에 대해 알려드릴게요.



### 사용방법

> 1. 스토리보드 삭제
> 2. Main Interface 안의 내용 삭제
> 3. SceneDelegate 내용 수정
> 4. Plist안에 스토리보드 내용 삭제

1. #### 스토리보드 삭제해주세요.

![Screen Shot 2020-07-01 at 7.11.34 PM](/Users/uk/Desktop/Screen Shot 2020-07-01 at 7.11.34 PM.png)

2. #### Main Interface 안의 내용을 삭제해주세요.

![Screen Shot 2020-07-01 at 7.11.53 PM](/Users/uk/Desktop/Screen Shot 2020-07-01 at 7.11.53 PM.png)

3. #### SceneDelegate 내용을 수정해주세요.

```swi
...

func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        
        guard let windowScene = (scene as? UIWindowScene) else { return }
        window = UIWindow(frame: windowScene.coordinateSpace.bounds)
        window?.windowScene = windowScene
        let navigationVC = UINavigationController(rootViewController: ViewController())
        // 첫 페이지 설정
        window?.rootViewController = navigationVC
        window?.makeKeyAndVisible()
    }
```

4. #### Plist를 수정해주세요.

![Screen Shot 2020-07-01 at 7.14.50 PM](/Users/uk/Desktop/Screen Shot 2020-07-01 at 7.14.50 PM.png)

위 빨간박스인 스토리보드 관련부분을 지워줍시다.

![Screen Shot 2020-07-01 at 7.15.05 PM](/Users/uk/Desktop/Screen Shot 2020-07-01 at 7.15.05 PM.png)

지우면 이렇게 남겠죠??

5. #### 기본적인 ViewController를 작성해줍니다.

저는 알아보기 쉽게 배경을 노란색으로 바꿔볼게요.

```swift
//  ViewController.swift
import UIKit

class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }
    
    override func loadView() {
        let view = UIView()
        view.backgroundColor = .yellow
        self.view = view
    }
}
```

#### 

이렇게 작성하시고 빌드를 해보면 ..

![Screen Shot 2020-07-01 at 7.27.04 PM](/Users/uk/Desktop/Screen Shot 2020-07-01 at 7.27.04 PM.png)

잘 나오네요.. 위에 흰색부분은 신델리게이트에서 네비게이션 컨트롤러를 임베디드 시켜줬기 때문에 생긴 네비게이션 바 입니다. 이렇게 코드를 통해서 뷰를 짜면 있어보이기도 하고.. 가독성도 좋은 것 같아요.



### 마지막으로..

저는 처음에 스토리보드를 사용해서 앱개발 하는걸 배웠었는데, 유튜브에서 강의해주시는 분들은 대부분 코드를 사용해서 개발을 하시더라구요.. 코드를 사용해서 뷰를 만들면 뭔가 키보드를 많이 두들겨서 멋있어 보였어요 =_=.. 그래서 혹시 코드를 사용해서 뷰를 짜보시고 싶으신 분들에게 도움이 되셧으면 좋겠습니다. 확실히 코드로 뷰를 짜면 가독성도 늘어나고, 코드로 짜면 명확하기 때문에 배운 내용을 정리해두기도 좋은 것 같아요.