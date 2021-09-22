# 변수 선언 / 호이스팅 / TDZ

변수는 var, let, const 를 이용하여 선언할 수 있다.

## 변수의 생성 단계

1. 선언 : 실행 컨텍스트의 변수 객체에 등록한다. 이 변수 객체는 스코프가 참조하는 대상이 된다.

2. 초기화 : 변수 객체에 등록된 변수를 위해 메모리 공간을 확보한다. 할당된 메모리에 undefined로 초기화 된다.

3. 할당 : undefined로 초기화 되어있는 메모리에 새로운 값을 할당한다.

## var

```js
var user = "Mark";
console.log(user); // Mark

var user = "JayB";
console.log(user); // JayB
```

var는 한번 선언된 변수를 다시 선언할 수 있다.

```js
console.log(user);
var user = "Mark";
```

var는 선언하기 전에 사용할 수 있다.

```js
var user;
console.log(user);
user = "Mark";
```

var는 변수 선언 전에 변수 선언과 초기화 단계가 동시에 이루어진다.
위와 같이 user 변수가 최상위로 끌어올려진 것처럼 동작한다. 즉 **호이스팅**이 일어나는 것이다. 따라서 var는 선언하기 전에 사용할 수 있는 것이다.

### hoisting 호이스팅

**var** 변수 선언과 함수 선언문에서 호이스팅이 발생한다.
var 변수, 함수 선언만 위로 끌어올려지고 var 할당은 끌어올려지지 않는다. 실제로 코드가 끌어올려지는 것이 아니라 끌어올려진 것처럼 실행되는 것이 **호이스팅**이다.
코드 실행 전 이미 var 변수, 함수 선언이 메모리에 저장되어 있다. 그리하여 참조,호출이 먼저 나와도 오류 없이 동작한다.

자바스크립트의 모든 선언에는 **호이스팅**이 발생한다.
**var**는 선언과 함께 **undefined**로 초기화된다. 하지만 **let, const**는 **초기화되지 않은 상태**로 선언만 메모리에 저장되어 참조 에러가 발생하는 것이다.

---

## let

```js
let user = "Mark";
console.log(user); // Mark

let user = "JayB";
console.log(user); // Error!

// 'user' has already been declared
```

let은 var과 달리 중복 선언이 불가능하다.

```js
let user = "Mark";
console.log(user); // Mark

user = "JayB";
console.log(user); // JayB
```

## 변수 재선언은 불가능하나 재할당은 가능하다.

## const

```js
const user = "Mark";
console.log(user); // Mark

const user = "Yugyeom"; // Error!

user = "JayB";
// Error!
```

const도 재선언이 불가능하다. 그리고 let과 달리 재할당도 불가능하다.

---

## TDZ (Temporal Dead Zone)

**TDZ**는 스코프의 시작부터 초기화 시작까지의 구간을 말한다.

```js
const number = 1;
console.log(number); // 1
```

변수를 선언하고 초기화하면 변수에 접근할 수 있다.

```js
number;
const number = 1;
```

선언 전에 number 변수에 접근하면
`const number = 1`전의 `number` 변수 줄은 TDZ에 있는것이다.

TDZ에 있는 변수에 접근할 경우 아래와 같은 Reference Error가 발생한다.

`Reference Error: Cannot access'number' before initialization`

### let

let은 선언 전 줄까지 TDZ의 영향을 받는다.
그러므로 let 변수는 선언 후에 사용해야 한다.

```js
number;
let number; // Reference Error!

number = 1;
```

### const

```js
id; // Reference Error!
const id = "angel123";
```

const 변수는 선언 및 초기화 줄 전까지 TDZ 영역에 있다. 그러므로 const 변수는 선언 후에 사용해야 한다.

### class

```js
const student = new User("Mark");
// Reference Error !

class User {
  constructor(name) {
    this.name = name;
  }
}
```

class 는 선언 전에 사용할 수 없다.

```js
class User {
  constructor(name) {
    this.name = name;
  }
}

const student = new User("Mark");
console.log(student);
```

클래스를 선언하고 사용하면 에러가 발생하지 않는다.
