# call

- 함수를 호출하는 메서드이다.
- 그런데 함수를 호출할 때, 어디에서 호출했느냐와 관계없이 this를 지정할 수 있다.
- 함수를 호출하면서 call을 사용하고 this로 사용할 객체를 넘기면 해당 함수가 주어진 객체의 메서드인 것처럼 사용할 수 있다.

```js
const kim = {
  name: "Minsu",
};
const Lee = {
  name: "Minjung",
};
function sayHi() {
  console.log(`Hi ${this.name}`);
}

sayHi(); // 'Hi '
sayHi.call(kim); //'Hi Minsu'
sayHi.call(Lee); //'Hi Minjung'

function update(birthYear, occupation) {
  this.birthYear = birthYear;
  this.occupation = occupation;
}

update.call(kim, 1949, "singer");
console.log(kim); //{name: 'Minsu',birthYear: 1949,occupation: 'singer'}
```

# apply

- apply는 함수 매개변수를 처리하는 방법을 제외하면 call과 완전히 같다.
- call은 일반적인 함수와 마찬가지로 매개변수를 직접 받지만, apply는 매개변수를 배열로 받는다.
- 그렇기 때문에 apply는 매개변수가 배열인 경우 자주 쓰인다. Math.max()나 Math.min()과 같은 경우에 말이다.

```js
const arr = [1, 2, 3, 4, 5, 6, 7];

Math.max.apply(null, arr); // 7
Math.min.apply(null, arr); // 1
```

# bind

- bind는 함수의 this를 묶는다. 즉, 함수의 this 값을 영구히 고정시킨다.

```js
const updateKim = update.bind(Kim);
updateKim(2001, "dancer");
console.log(kim);
//{name:'Minsu',birthYear: 2001,occupation: 'dancer'}

updateKim.call(Lee, 2000, "fighter");
console.log(kim);
//{name:'Minsu',birthYear: 2000,occupation: 'fighter'}
//Lee는 변하지 않는다.
```

# 생각할 점

- 재미있는 것들이긴 한데... 실제 코드에서 어떤 상황에서 어떻게 쓰이는지 예시들을 더 보고 싶다.
