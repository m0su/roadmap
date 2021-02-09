![image](https://user-images.githubusercontent.com/20768506/107121088-e720b280-68d3-11eb-8699-d6be7cd6f0cf.png)

당연히 [공식문서](https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1622921-application)에 잘 정리가 되어있다.

# AppDelegate.swift
### 앱 상태 변화에 따른 메소드
- `application(_:willFinishLaunchingWithOptions:)`: 앱이 실행되면서 런치 프로세스가 시작되자마자 실행되는 메소드
    - 상태에 대한 정보가 없는 상태
- `application(_:didFinishLaunchingWithOptions:)`: 앱이 실행된 직후, 런치 프로세스와 앱의 실행 준비가 **거의** 완료되었을 때 실행되는 메소드.
    - 프로젝트를 새로 생성하면 기본적으로 작성되어있는 메소드.
    - *위대하신 애플께서 almost란 표현을 쓴 것은 연구해볼만하다*
- `applicationDidBecomeActive(_:)`: 앱이 `Active`상태가 된 직후 호출
- `applicationWillResignActive(_:)`: 앱이 `Inacitve`상태가 되기 직전 호출
- `applicationDidEnterBackground(_:)`: 앱이 `background`상태가 된 직후 호출
- `applicationWillEnterForeground(_:)`: 앱이 `foreground`상태가 되기 직전 호출
- `applicationWillTerminate(_:)`: 앱이 종료되기 직전 호출


# SceneDelegate.swift