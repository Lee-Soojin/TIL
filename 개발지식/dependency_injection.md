# DI 의존성 주입 ( Dependency Injection)

### 의존성

```ts
class User {
  name: string;
}

class Record {
  character = new User();
}
```

위의 예시 코드에서 Record class는 User class와 의존관계가 생긴다. Record class에서 변수로 User class를 사용함으로서 의존관계가 성립된 것이다.

### 주입

```ts
class User {
  constructor(name: string) {
    console.log(`Hi ${name}!`);
  }
}

const bob = new User("Bob");
```

위처럼 bob이라는 변수로 User 객체를 외부에서 생성해 넣어주는 것이 주입하는 것이다.

### 의존성 주입

new 를 통해 직접 객체를 생성하면 그 클래스에 의존하게 된다. 따라서 객체를 직접 만드는게 아닌 객체의 밖에서 객체를 생성해 주입해주는 방식이 **의존성 주입**이다.

의존성 주입을 이용하면 가독성이 좋아지고 코드 재사용성이 높아진다. 또한 종속적인 코드의 수도 줄일 수 있고 객체 간 의존관계를 설정할 수 있다.
