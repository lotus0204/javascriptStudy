# 스코프란?

모든 식별자(변수 이름, 함수 이름, 클래스 이름 등)는 자신이 선언된 위치에 의해 다른 코드가 식별자 자신을 참조할 수 있는 유효 범위가 결정된다. 이를 스코프라고 한다. 즉 스코프는 식별자가 유효한 범위를 말한다.

# 코드의 문맥과 환경

"코드가 어디서 실행되며 주변에 어떤 코드가 있는지"를 렉시컬 환경 이라고 부른다. 즉, 코드의 문맥은 렉시컬 환경으로 이뤄지고, 이를 구현한 것이 실행 컨텍스트이며, 모든 코드는 실행 컨텍스트에서 평가되고 실행된다. 스코프는 실행 컨텍스트와 깊은 관련이 있다.

# 스코프 체인

스코프는 함수의 중첩에 의해 계층적인 구조를 갖는다. 이렇게 스코프가 계층적으로 연결된 것을 스코프 체인이라고 한다. 변수를 참조할 때 자바스크립트 엔진은 스코프 체인을 통해 변수를 참조하는 코드의 스코프에서 시작하여 상위 스코프 방향으로 이동하며 선언된 변수를 검색한다. 절대 하위 스코프로 내려가면서 식별자를 검색하는 일은 없다. 이를 통해 상위 스코프에서 선언한 변수를 하위 스코프에서도 참조할 수 있다.

# 렉시컬 스코프

함수를 어디서 정의했는지에 따라 함수의 상위 스코프를 결정하는것을 렉시컬 스코프라 한다.자바스크립트는 렉시컬 스코프를 따르므로
함수를 어디서 호출했는지가 아니라,
함수를 어디서 정의했는지에 따라 상위 스코프를 결정한다.
함수가 호출된 위치는 상위 스코프 결정에 어떠한 영향도 주지 않는다.
즉, 함수의 상위 스코프는 언제나 자신이 정의된 스코프다.

```js
var x = 1;

function foo() {
  var x = 10;
  bar();
}

function bar() {
  console.log(x);
}

foo(); // 1
bar(); // 1
```

위 코드에서 bar 함수는 전역에서 정의 되었다. 따라서 bar함수는 전역 코드가 실행되기 전에 먼저 평가되어 함수 객체를 생성한다. 이때 생성된 bar 함수 객체는 자신이 정의된 스코프인 전역 스코프를 기억한다. 그래서 bar 함수가 호출되면 호출된 곳이 어디인지 관계없이 언제나 자신이 기억하고 있는 전역 스코프를 상위 스코프로 사용한다. 따라서 위 예제에서 1이 두 번 출력된다.

# 생각할 점

- 실제로 코드를 읽으며 생각할 때, 스코프와 스코프 체인에 대한 이해가 잘 되어 있어야 코드를 잘 읽을 수 있을 것 같다.
- 이 부분은 개념도 중요하지만 실제로 이를 활용해여 코드를 잘 읽는 연습이 더 중요해 보인다.
