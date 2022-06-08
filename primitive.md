# 원시 타입

- 원시 타입은 변경 불가능한 값이다.
- 원시 값을 변수에 저장하면 확보된 메모리 공간에 실제 값이 저장된다.
- 원시 값을 갖는 변수를 다른 변수에 할당하면 원본의 원시 값이 복사되어 전달된다.(값에 의한 전달)
- string, number, bigint, boolean, undefined, symbol이 있다.

```js
var name = "Kim";
var copy = name; // copy 변수를 위해 만들어진 메모리 공간에
// name 변수의 값 'Kim'이 복사되어 저장된다.

console.log(name); // 'Kim'
console.log(copy); // 'Kim'

name = "Lee"; // name 변수와 copy 변수의 값은 다른 메모리 공간에 저장되어 있는 별개의 값이다.
// 따라서 name 변수의 값을 변경해도 copy 변수의 값에는 영향을 전혀 주지 않는다.

console.log(name); // 'Lee'
console.log(copy); // 'Kim'
```

# 객체 타입

- 객체 타입의 값은 변경이 가능하다.
- 객체를 변수에 할당하면 확보된 메모리 공간에 참조 값이 저장된다.
- 객체를 가리키는 변수를 다른 변수에 할당하면 원본의 참조 값이 복사되어 전달된다.(참조에 의한 전달)
- 원시 타입을 제외한 모든 타입이 참조 타입, 즉 객체이다.

```js
var person = {
  name: "Kim",
};

var copy = person;

copy.name = "Lee";
person.address = "Seoul";

console.log(person); //{name:'Lee', address:'Seoul'}
console.log(copy); //{name:'Lee', address:'Seoul'}
```

# 추가

- 변경 가능한 값이라는 말은 메모리에 있는 값이 변할 수 있다는 것이다.
- 변경 불가능하다는 이야기는 메모리에 있는 값이 변할 수 없다는 것이다.
- 재할당하면 변경 가능한 것처럼 보이지만 아니다. => 원시 타입을 재할당 하면 새로운 메모리 공간에 재할당한 값이 저장되고, 원래 값은 없어지지 않는다. 그래서 변경 불가능한 것이다.
- 객체의 경우 원시 값과 달리 변경 가능한 값인 이유는 객체를 생성하고 관리하는 방식은 매우 복잡하며 비용이 많이 들기 때문에 메모리를 효율적으로 사용하기 위해 그렇게 설계를 하였기 때문이다.

# 깊은 복사와 얕은 복사

- 깊은 복사는 실제 값을 복사하는 것이고, 얕은 복사는 참조값(주소)를 복사하는 것이다.
- 원시 타입에 대해서는 실제 값을 복사하는 '깊은 복사'가 일어난다.
- 일반적으로 객체 타입에 대해서는 참조값(주소)를 복사하는 '얕은 복사'가 일어난다.
- 객체의 얕은 복사는 보통 slice()나 assign()을 통해 한다.

```js
const object = {
  a: "a",
  number: {
    one: 1,
    two: 2,
  },
};

const copy = Object.assign({}, object);
copy.number.one = 3;
console.log(object === copy); // false
console.log(object.number.one === copy.number.one); // true
```

# 객체의 깊은 복사

- 실제로 객체를 깊은 복사를 하고 싶을 여지가 많다고 생각한다.
- 왜냐하면 값을 복사해서 쓰는 경우, 원래 값에는 영향을 미치고 싶지 않기 때문에 값을 복사해서 쓸 가능성이 높기 때문이다.
- JSON.parse && JSON.stringify를 이용하여 깊은 복사를 한다.
- JSON.stringify()는 객체를 json 문자열로 변환하는데 이 과정에서 원본 객체와의 참조가 모두 끊어진다.
- 객체를 json 문자열로 변환 후, JSON.parse()를 이용해 다시 원래 객체(자바스크립트 객체)로 만들어준다.
