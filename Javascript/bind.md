# bind

bind() 메소드를 호출하면 새로운 바인딩한 함수가 생성된다. 바인딩한 함수는 특이 함수 객체라고 한다. 

### **bind의 반환값**

지정한 this의 값 및 초기 인수를 사용해 변경한 **원본 함수의 복제본**

```js
let user = {
  name: "Bob",
  login() {
    console.log(`user: ${this.name} login`);
  },
};

setTimeout(user.login, 1000);
```

위의 setTimeout에서 `this.name`에 'Bob'이 출력되지 않고 'undefined'가 출력된다. 이는 `user` 객체에서 `user.login()`함수가 분리되어서 전달되기 때문이다. setTimeout에서 `this`는 `window`가 되므로 `name` 객체가 undefined로 나오는 것이다.

이런 상황을 해결하는 방법은 두가지가 있다.

## Arrow function

```js
setTimeout(() => user.login(), 1000);
```

위와 같이 작성하면 login함수 안의 name에 'Bob'이 잘 전달되어 출력된다.

하지만 setTimeout에 지정한 1초가 지나기 전에 user가 변경될 경우 변경된 객체의 메서드를 호출하게 되는 문제가 있다.

## bind

```js
let boundFunc = func.bind(context);
```

func.bind(context)는 this가 context로 고정된 함수 func를 반환한다. 그리하여 boundFunc를 호출하면 this가 고정된 func를 호출할 수 있는 것이다.

```js
let user = {
  name: "Bob",
};

function login() {
  console.log(this.name);
}

let User = login.bind(user);
User();
```

login.bind(user) 는 login의 this를 user로 바인딩한 것이다. 인수는 login함수에 그대로 전달이 된다.
