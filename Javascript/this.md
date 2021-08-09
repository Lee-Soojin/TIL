# this

JavaScript에서 this는 class를 사용하고 배울때마다 헷갈렸던 개념이다. 밑에 기록해두고 까먹지 않아야겠다! 😆

this는 부르는 위치에 따라 바뀐다. 즉 함수를 호출한 방법에 의해 결정된다.

- ES5 -> 함수를 어떻게 호출했는지 상관없이 this 값을 설정할 수 있는 **bind** 도입
- ES2015 -> 스스로 this 바인딩을 제공하지 않는 **arrow function**을 추가

웹 브라우저에서 기본으로 window 객체가 전역 객체이다.

```js
console.log(this); // window

a = "hi";
console.log(window.a); // hi
```

## Function.prototype.bind

bind는 내부적으로 사용할 this를 고정시킨다.

```js
class Play {
  game = "call of duty";
  campaign() {
    console.log(this);
  }
}

const player = new Play();
const startGame = player.campaign.bind(player);
startGame(); // Play
```

```js
const startGame = player.campaign;
startGame(); // undefined
```

위의 예제에서 bind를 이용하면 Play 클래스를 호출해 만든 player라는 변수가 **this**가 된다.

```js
function.prototype.bind(something);
```

something 자리에 오는 것이 this가 되도록 고정시켜주는 것이 bind의 기능이다.

bind()가 호출되면 새로운 함수를 생성한다.

## 화살표 함수 ( arrow function )

```js
class Play {
  game = "call of duty";
  campaign = () => {
    console.log(this);
  };
}

const player = new Play();
const startGame = player.campaign.bind(player);
startGame(); // Play
```

화살표 함수는 this를 가지지 않고 생성될 때 this가 결정된다. 화살표 함수를 사용하면 bind를 이용해 this를 바인딩하지 않아도 된다. 화살표 함수의 this는 상위 스코프의 this를 가리키는 것이다.
