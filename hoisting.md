# 호이스팅

- JavaScript에서 호이스팅(hoisting)이란, 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미한다.
- 즉 선언되어 있는 변수 혹은 함수 모두를 코드 상단으로 끌어 올려지는 것이다.

# 변수의 경우

- 자바스크립트에서 변수 선언을 하기 위해서 보통 var, let, const라는 키워드를 사용한다. 여기서는 var를 통해서만 알아보도록 하겠다.
- 변수 선언에는 크게 3가지 단계가 있다. 1. 선언 단계 2. 초기화 단계 3. 할당 단계이다.
- 선언 단계에서는 변수가 실행 컨텍스트의 변수 객체에 등록된다.
- 초기화 단계는 변수 객체에 등록된 변수에 대한 메모리 공간을 확보한다. 여기서 변수는 undefined로 초기화 된다.
- 할당 단계에서는 undefined로 초기화된 변수에 실제 값을 할당하게 된다.
- 변수가 선언되고 초기화 된 후, 호이스팅이 이루어진다. 그리고 할당 단계는 코드가 실행되는 런타임에 실시된다. 아래의 예시를 살펴보자.

```js
console.log(name); // undefinded

var name = "Kim"; // 변수 선언과 값의 할당

console.log(name); // 'Kim'
```

```js
console.log(name); //undefined

name = "Kim";
var name;

console.log(name); // 'Kim'
```

이 두 코드는 실제로 작동방식이 같다. 선언부가 런타임 이전에 먼저 실행되었기 때문에, 코드 상으로는 ‘Kim’의 할당이 먼저 일어났지만 실제로는 이미 name이라는 변수가 선언된 다음 값의 할당이 일어났다. 그래서 위의 코드와 아래의 코드는 같은 코드이다.

# 함수의 경우

- 함수는 보통 함수 선언식이나 함수 표현식을 통해 정의한다. 호이스팅의 경우 선언식과 표현식에서 적용되는 방식이 다르기 때문에 각각 알아보겠다.
- 먼저 선언식의 경우는 함수 선언식의 위치와 관계없이 호이스팅이 잘 일어난다. 아래의 코드로 확인해보자

```js
function outer(firstname) {
  // 함수선언문
  var result = inner(); // "선언 및 할당"
  console.log(typeof inner); // > "function"
  console.log("name is " + result); // > "name is inner value"

  function inner() {
    // 함수선언문
    return "inner value";
  }
}

outer(); // 함수 호출
```

- 표현식의 경우는 선언식과 다르다. 표현식의 경우에는 변수 선언과 비슷한 방식으로 이해할 수 있다. 아래의 코드를 살펴보자.

```js
function outer(firstname) {
  // 함수선언문
  console.log(inner); // > "undefined": 선언은 되어 있지만 값이 할당되어있지 않은 상황이다.
  var result = inner(); // > TypeError: inner is not a function
  console.log("name is " + result);

  var inner = function () {
    // 함수표현식
    return "inner value";
  };
}
outer();
```

- 차레로 살펴보면, outer 함수를 실행하면, 1. outer함수의 실행 컨텍스트에 inner와 result라는 변수가 undefined로 초기화된다. 따라서 2. console.log(inner)에서는 undefined가 콘솔에 찍힌다. 그리고 3. result라는 변수에 inner라는 함수의 결과값을 할당해야하는데 문제는 inner가 undefined이기 때문에 함수실행을 해주어도 이것이 함수인지 모르기 때문에 'TypeError: inner is not a function'라는 에러를 리턴하고 outer함수가 종료된다.

# 생각해볼 점

- 호이스팅을 활용하는 방식으로 코드를 작성하는 것은 좋아보이지 않는다. 왜냐하면 우리는 코드를 읽을 때 위애서 아래로 읽기 때문에, 호이스팅이 남발된 코드는 읽기가 매우 힘들 것 같다는 생각이 든다.
- 생각을 해봐도 호이스팅의 장점이 무엇인지 잘 모르겠어서 찾아보다가 사실인지는 알 수 없지만 다음과 같은 글을 보았다.
  "ES6를 어디에서든 쓸 수 있으려면 아직 시간이 더 필요하므로 ES5로 트랜스컴파일을 해야한다."
- 그런가 보다
