# static

static은 property나 method에 사용할 수 있다. static을 이용하여 정적 메소드, 프로퍼티를 정의하는 것이다.

```ts
class PizzaMaker {
  static Bread() {
    return "Preparing Bread for pizza";
  }
  static Cheeze() {
    return this.Bread() + "add some cheeze";
  }
}
```

위와 같이 정적 메소드인 Bread를 다른 정적 메소드인 Cheeze에서 불러오려면 **this**를 사용해야 한다.

```ts
class Static {
  constructor() {
    console.log(Static.first());

    console.log(this.constructor.first());
  }

  static first() {
    return "first static method";
  }
}
```

위의 경우는 다른 method에서 static method를 호출하는 경우이다.

- classname.static_method_name()
- this.constructor.static_method_name()

이러한 두 방법으로 static method를 불러올 수 있다.
