# MVC

![mvc](https://user-images.githubusercontent.com/20768506/107139587-b4bc9700-695f-11eb-8280-239c4d3021fa.png)

### 동작

1. 유저의 액션이 컨트롤러로 들어온다.
2. 컨트롤러는 사용자의 액션을 확인하고 모델을 변경한다.
3. 컨트롤러는 모델을 나타낼 뷰를 결정한다.
4. 뷰는 모델을 화면에 그린다.

### 특징

- 컨트롤러와 뷰는 1:N
- 컨트롤러는 뷰를 선택할 뿐 관여하지 않아야 한다(뷰는 컨트롤러를 몰라야 함)

### 장점

- 단순함

### 단점

- 모델과 뷰가 서로 의존적임

# MVP

![mvp](https://user-images.githubusercontent.com/20768506/107139592-b9814b00-695f-11eb-8130-1af81391aacc.png)

### 동작

1. 유저의 액션이 뷰로 들어온다.
2. 뷰는 프레젠터에 데이터를 요청한다.
3. 프레젠터는 모델에 데이터를 요청한다.
4. 모델은 프레젠터가 요청한 데이터를 전달한다.
5. 프레젠터는 뷰에게 데이터를 전달한다.
6. 뷰는 프레젠터에서 온 데이터를 화면에 그린다.

### 특징

- 프레젠터와 뷰는 1:1
- 뷰와 모델의 인스턴스를 프레젠터에서 가지고 있다.
- Cocoa-MVC와 Android-MVC는 *(MVC가 아닌)* MVP와 가장 유사함

### 장점

- 뷰와 모델의 의존성이 없음.

### 단점

- 뷰와 프레젠터 사이의 의존성이 높아짐*(우리가 아는 그 Massive-ViewContoller)*

# MVVM

![mvvm](https://user-images.githubusercontent.com/20768506/107139596-bc7c3b80-695f-11eb-9779-4b790167d895.png)


### 동작

1. 유저의 액션이 뷰로 들어온다.
2. 뷰는 뷰모델에 액션을 전달한다: **커맨드패턴**
3. 뷰모델은 모델에 데이터를 요청한다.
4. 모델은 뷰모델이 요청한 데이터를 전달한다.
5. 뷰모델은 모델에서 온 데이터를 가공하여 전달한다.
6. 뷰는 뷰모델의 데이터를 화면에 그린다: **데이터바인딩**

### 특징

- 커맨드패턴과 데이터바인딩을 통해 구현됨
- 뷰모델과 뷰는 1:N

### 장점

- 커맨드패턴과 데이터바인딩을 이용하여 뷰와 뷰모델 사이의 의존성이 없음.

### 단점

- 뷰모델의 설계가 어려움