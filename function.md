# 자바스크립트의 함수를 정의하는 방법

1. 함수 선언식

- function을 이용하여 함수를 생성한다.

```js
function sayName(name) {
  console.log(name);
}

sayName("Kim"); // 'Kim'
```

2. 함수 표현식

- 함수 표현식은 일반적으로 변수를 선언하는 리터럴 방식이다.

```js
const sayName = function (name) {
  console.log(name);
};

sayName("Kim"); // 'Kim'
```

3. Fucntion 객체를 이용

- new 키워드를 이용하여 함수를 만드는 방법이다.

```js
const sayName = new Function("name", "console.log(name)");

sayName("Kim"); // 'Kim'
```

4. 익명함수 사용

- 익명 함수는 함수를 만들어 재사용하는 것이 목적이 아니라, 다른 함수간의 충돌을 막기 위해 사용한다고 한다.

```js
(function (name) {
  console.log(name);
})("Kim"); // 'Kim'
```

# 생각해 볼 점

- 1,2 번의 경우는 일반적을 많이 쓰이고 당연하다고 느낀다.
- 3번의 경우는 많이 쓰지 않은다고 하고, 보기에도 뭔가 별로 일 것이라는 느낌이 든다.
- 4번의 경우는 실무에서 권장되지 않을 것 같은데 쓰는 경우가 있는지 궁금하다.
