# 생성자 함수에 의한 객체 생성

- Object 생성자 함수:
  new 연산자와 함께 Object 생성자 함수를 호출하면 빈 객체를 생성하여 반환한다.

```js
// 빈 객체의 생성
const person = new Object();

// 프로퍼티 추가
person.name = "April";
person.sayHello = function () {
  console.log("Hi! My name is " + this.name);
};

console.log(person); // {name: "April", sayHello: ƒ}
person.sayHello(); // Hi! My name is April
```

- 생성자 함수(constructor)란?
  new 연산자와 함께 호출하여 객체(인스턴스)를 생성하는 함수. 생성자 함수에 의해 생성된 객체를 인스턴스(instance)라 한다.

- 생성자 함수

1. 객체 리터럴에 의한 객체 생성 방식의 문제점
   객체 리터럴에 의한 객체 생성 방식은

단 하나의 객체만 생성한다.

따라서 동일한 프로퍼티를 갖는 객체를 여러 개 생성해야 하는 경우

매번 같은 프로퍼티를 기술해야 하기 때문에 비효율적이다.

2.생성자 함수에 의한 객체 생성 방식의 장점
생성자 함수에 의한 객체 생성 방식은

마치 객체(인스턴스)를 생성하기 위한 템플릿(클래스)처럼 생성자 함수를 사용하여

프로퍼티 구조가 동일한 객체 여러개를 간편하게 생성할 수 있다.

```js
function Circle(radius) {
  // 생성자 함수 내부의 this는 생성자 함수가 생성할 인스턴스를 가리킨다
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

const circle1 = new Circle(5); //  반지름이 5인 Circle 객체 생성
const circle2 = new Circle(10); // 반지름이 10인 Circle 객체 생성

console.log(circle1.getDiameter()); // 10
console.log(circle2.getDiameter()); // 20
```

3. 생성자 함수의 인스턴스 생성과정
   생성자 함수의 역할은 프로퍼티 구조가 동일한 인스턴스를 생성하기 위한 템플릿(클래스)으로서 동작하여 인스턴스를 생성하는 것과 생성된 인스턴스를 초기화(인스턴스 프로퍼티 추가 및 초기값 할당)하는 것이다.

new 연산자와 함께 생성자 함수를 호출하면 자바스크립트 엔진은 다음과 같은 과정을 거쳐 암묵적으로 인스턴스를 생성하고 인스턴스를 초기화한 후 암묵적으로 인스턴스를 반환한다.

1. 인스턴스 생성과 this 바인딩

- 암묵적으로 빈 객체가 생성된다.

- (아직 완성되진 않았지만) 이 빈 객체가 생성자 함수가 생성한 인스턴스다.

2. 인스턴스 초기화

- 생성자 함수에 기술되어 있는 코드가 한 줄씩 실행되어

- this에 바인딩되어 있는 인스턴스를 초기화한다.

3. 인스턴스 반환

생성자 함수 내부의 모든 처리가 끝나면 완성된 인스턴스가 바인딩된 this가 암묵적으로 반환한다.
