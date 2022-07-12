# 객체를 만드는 방법

1. 객체 리터럴 이용

- 리터럴은 사람이 이해할 수 있는 문자나 약속된 기호를 사용해 값을 생성하는 표기법이다.
- 객체 리터럴은 중괄호를 사용해 프로퍼티를 정의하여, 객체를 만들 수 있다.

```js
const person = {
  name: "Lee",
  address: "Seoul",
  phone: "010-1234-1234",
};
```

2. 생성자를 이용

- new연산자를 통해 Object객체의 생성자 함수를 호출한다.

```js
const person = new Object();

person.name = "Lee";
person.address = "Seoul";
person.phone = "010-1234-1234";

console.log(person); // {name:'Lee', address:'Seoul',phone:'010-1234-1234'}
```

- 직접 생성자 함수를 만들고 이것을 통해 객체를 생성할 수 있다.

```js
const Person = function (name, address, phone) {
  this.name = name;
  this.address = address;
  this.phone = phone;
};

const person = new Person("Lee", "Seoul", "010-1234-1234");
console.log(person); // {name:'Lee', address:'Seoul', phone:'010-1234-1234'}
```
