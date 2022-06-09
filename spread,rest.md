# spread

- Spread 라는 단어의 의미는 펼치다, 퍼뜨리다 이다.

- 이 문법을 이용하면, 객체 혹은 배열을 펼칠 수 있다. (객체나 배열을 통채로 끌고와서 사용 가능!)

- 기존의 것은 건들이지 않고 새로운 객체를 만들 때 사용한다.

```js
const person = {
  name: "Kim",
};
const king = {
  ...person,
  job: "king",
};

console.log(king); //{ name: 'Kim', job: 'king' }
```

# rest

Rest 파라미터(나머지 매개변수) 구문을 구조 분해 할당 문법과 같이 사용하면 나머지 (객체, 배열)을 rest에 담아서 추출할 수 있다.
Rest 파라미터(나머지 매개변수) 구문을 사용하면 함수에서 정해지지 않은 수의 매개변수를 배열로 받을 수 있다.

- rest의 생김새가 spread와 비슷하지만 역할은 매우 다르다.

- rest는 객체, 배열, 함수의 매개변수에서 사용가능하다.

- rest는 객체와 배열에서 사용할 때는 구조 분해 할당 문법과 함께 사용된다.

- 사용할 때는 주로 rest 라는 키워드를 사용하게 되는데 추출값의 이름이 꼭 rest 일 필요는 없다.

```js
const person = {
  name: "Kim",
};
const king = {
  ...person,
  job: "king",
};
const { name, ...rest } = king;
console.log(name); // "Kim"
console.log(rest); // { job: 'king' }
```

함수에서 rest를 사용해보자

```js
function sum(...rest) {
  return rest;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // [ 1, 2, 3, 4, 5, 6 ]
```

위의 코드처럼 받아온 파라미터들이 요소로 이루어진 배열이 리턴된다. 이를 통해 잘 더해 보자

```js
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // 21
```

# 생각해볼 점

- spread의 경우 매우 자주 쓰는 문법이라서 앞으로 재미있게 써볼 예정이다.
- 그런데 rest의 경우 실제로 자주 쓸일이 있을지 모르겠다. 의도적으로라도 써봐야겠다.
