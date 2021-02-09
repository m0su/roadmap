# [App Architect](https://github.com/m0su/roadmap/blob/main/iOS/iOS%20Tecgnologies/App%20Architect.md)
## 왜 나타났을까?
- 프로젝트의 덩치가 커지면서 디버깅이 복잡해지기 시작함
- 객체들의 역할 나누기를 통해 프로그램 복잡도를 낮출 필요.
- 런타임 에러를 잡기 위핸 테스트의 용이성
- 사용이 편하고 유지보수 비용이 적을 것.
    - 코드의 길이가 짧으면서 설명이 필요 없는 코드


## MVx 패턴들
```
MVC -> MVP -> MVVM -> VIPER -> RIBs -> VIP ...
```
MVx 패턴들은 **대략** 아래로 구분된다.
- Model: 데이터
- View: 화면, UI
- Controller/Presenter/ViewModel: Model과 View의 연결점

### 종류
- MVC: 컨트롤러가 뷰에 관여하지 않긴 하지만 뷰와 모델이 서로 의존적임
    - 서로가 독립적이지 않아 재사용성이 떨어짐.
- MVP: CocoaMVC가 여기에 해당되며 뷰와 모델을 독립적으로 다룸.
    - 프레젠터가 뷰와 강한 의존성을 갖게 되어 뷰와 프레젠터의 분리가 어려움 -> 재사용과 테스트가 어려움
    - 프레젠터의 역할이 너무 많음 *(Massive-ViewController라고 조롱)*
    - iOS 개발에서 MVC라고 함은 MVP를 뜻함.
        - `View+ViewController`가 뷰에 속함
- MVVM

# App Life-cycle

# View-ViewController Programming

# Multi-touch Event Handling