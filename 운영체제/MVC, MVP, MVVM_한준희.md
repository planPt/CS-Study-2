# MVC, MVP, MVVM

## MVC

Model, View, Controller

Model : 데이터 계층 -> 뷰나 컨트롤러를 모른다.

View : 사용자에게 보여지는 화면 , UI

- 데이터나 함수같은 로직은 없어야 한다.

Controller : 모델과 뷰를 이어준다.

장점은 서로 분리되어서 유연성이 증가한다.

단점은 뷰와 모델 사이의 의존성이 높아진다.  
-> 모델이랑 뷰가 증가할 수록 컨트롤러가 점점 커지고 복잡해진다.

HTML 웹 구현에서의 예시?

- View : 사용자 화면 -> Css

- Controller : JavaScript

- Model : 이미지파일(원본), 로컬 문서 등..

인풋이 컨트롤러로

## MVP

Model, View, Presenter

Presenter : Controller가 교체되었다.

- 뷰와 프레젠터는 일대일 관계이다.

MVC패턴에서의 의존성을 보완했다.

인풋이 뷰에

프레젠터가 뷰와 모델 모두를 업데이트한다.

## MVVM

Model, View, View Model

컨트롤러가 View Model 로 바뀌었다

- 뷰모델 : 뷰를 나타내기위한 모델이면서 뷰를 위한 데이터를 처리한다.

CPU /메모리 /하드디스크 느낌..?

[디자인 패턴 MVC, MVVM 비교](https://donggyu9410.medium.com/%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-mvc-mvvm-%EB%B9%84%EA%B5%90-1a4e6c1c860a#:~:text=MVC%20%ED%8C%A8%ED%84%B4%EC%9D%98%20%EB%8B%A8%EC%A0%90%EC%9D%80,%EC%9C%A0%EC%A7%80%EB%B3%B4%EC%88%98%EA%B0%80%20%EC%96%B4%EB%A0%A4%EC%9B%8C%EC%A7%91%EB%8B%88%EB%8B%A4.)

데이터가 모델이라 모델이 없을 수가 없다.

웹이나 앱을 생각하면서 공부하기

어떤식으로 개발이 될 지

데이터가 모델이라 M은 항상 들어간다.
