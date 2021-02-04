![800x0](https://user-images.githubusercontent.com/20768506/106916853-004a2780-674b-11eb-848c-f2e560eff226.jpg)
[책 설명](http://www.yes24.com/Product/Goods/96193044)


# 목차
1. 출생
2. 학습
3. 취업
4. 은퇴

*마치 사람처럼 표현했다.*

# 1. 출생
## -er로 끝나는 이름을 사용하지 말 것.
- 클래스는 객체의 어머니다.
- 클래스는 객체의 팩토리다.
- 팩토리 패턴은 객체를 생성하는 `new` 연산자를 대신할 수 있는 강력한 옵션이지만 개념적으로 유사하다.
- 객체지향언어에서 클래스란 객체의 웨어하우스다. (객체를 꺼내거나 반환할 수 있는 위치에 있다는 뜻)
- 클래스를 객체의 템플릿으로 설명하는 것은 클래스를 수동적이고 멍청한(!) 코드 덩어리로 격하시키는 것.
- 클래스는 무엇을 하는지(what he does)가 아니라 무엇인지(what he is)를 생각해야 한다.

## 생성자 하나를 주 생성자로 만들 것.
- 올바른 클래스 설계는 많은 생성자와 적은 메서드로 이루어져있다.
    - 메서드 2-3개에 생성자 5-10개의 비율이 적당(비과학적)
    - 생성자가 많을 수록 클래스를 편하게 쓸 수 있다.
    ```swift
    Cash(30)
    Cash("$29.95")
    Cash(29.95)
    Cash(29.95f)
    Csh(29.95, "USD")
    ```
    - 메서드가 많아질수록 SRP는 위반하기 쉽지만, 생성자가 많아질수록 유연성이 향상된다.
- 초기화 로직을 하나의 생성자에만 두고, 그 외의 생성자들은 주 생성자를 호출하게 한다.
    ```swift
    class Cash {
        private var dollars: Int?

        init(dlr: Float) {
            Cash(dlr: Int(dlr))
            // Int()의 return 값은 옵셔널이므로 추가적인 작업이 필요합니다. 다만 여기선 개념설명에 의의를 두므로 생략합니다.
        }

        init(dlr: String) {
            Cash(dlr: dlr)
        }

        // 주 생성자
        // ...의 위치는 상관없지만 생성자의 맨 처음이나 맨 끝에 두도록 합니다.
        init(dlr: Int) {
            dollars = dlr
        }
    }
    ```
- 메서드 오버로딩을 지원하는 언어로 전향하라.
    - 자바스크립트의 경우 아규먼트로 map을 전달하는 방법이 있긴 있다.

## 생성자에 코드를 넣지 말 것.
- 객체 초기화 단계에는 코드가 없어야(code-free)하고 파라미터를 건드려선 안된다.
    - 필요하다면 파라미터를 캡슐화하라: 다른 타입의 객체나 가공하지 않은 형식(raw form)으로
    - 최적화가 쉽고 코드의 실행속도가 더 빨라진다. (객체를 만들때마다 호출될 것이므로)
- 객체를 실제로 사용하는 시점까지 객체의 변환 작업을 연기하라.
- 1. 객체를 인스턴스화하고 2. 객체가 작업을 하게 하라. 이 두 단계가 겹쳐서는 안 된다.
- 분리한 작업을 반복해서 하지 않으려면 데코레이터 패턴을 사용하라.
    - 최초 작업한 결과를 캐싱한다.
    ```swift
    class StringAsInteger: Number {
        var num: Int
        init(txt: String) {
            num = Int(txt)
        }

        func intValue() { return num }
    }

    class CachedNumber {
        var origin: Number
        var cached: [Int] = []

        init(num: Number) {
            origin = num
        }

        func intValue() -> Int {
            if cached.isEmpty() {
                cached.append(origin.intValue())
            } 
            return cached[0]
        }
    }

    // 호출부
    var integer = StringAsInteger(txt: "123")
    var num = CachedNumber(num: integer)

    num.intValue() // Int 형변환
    num.intVlaue() // Int 형변환이 일어나지 않음
    ```
- 작업이 단 한번만 일어나는게 확실하더라도 생성자의 작업을 메서드에 양보한다.
    - 당신은 이 클래스가 미래에 어떻게 변할지, 어떻게 리팩토링될지 알지 못한다.
    - 어떠한 경우에도 일관성을 유지하라.
    ```swift
    // 아래 코드는 매우 추상적이지만 가장 잘 표현되어있다.
    var app = App(data: Data(), screen: Screen())
    app.run()
    ```
    - 위 코드는 `app`을 생성하는 동안 `app`이 어떤 일도 처리하지 않는다.
    - `run()` 시점에 필요한 때와 필요한 곳에서 필요한 작업을 수행한다.