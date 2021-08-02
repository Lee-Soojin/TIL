# 추상 클래스 ( Abstract Claas )

추상 클래스를 정의할 때 class 앞에 abstract를 표기한다.

```ts
abstract class Greet {
  protected abstract callName(name: string): void;

  public shout(): string {
    return "hi!";
  }
}
```

추상 메소드를 정의할 때도 abstract를 붙이면 된다. 추상 메소드는 정의만 하고 메소드의 동작은 추상 클래스를 상속하는 클래스에서 구현한다.

추상 클래스는 인스턴스 생성이 불가능하다. 추상 클래스를 상속받은 클래스의 인스턴스 생성은 가능하다.

```ts
abstract class Greet {
  protected abstract callName(name: string): void;

  public shout(): string {
    return "hi!";
  }
}

class Hello extends Greet {
  protected callName(name: string): void {
    console.log(`${name}!!`);
  }
}

const sayHi = new Hello();
```

이와 같이 추상 클래스의 추상 메소드는 상속받은 클래스에 구현이 되어야 한다. 그렇지 않을 경우 error가 발생한다.
또한 추상클래스를 상속받은 클래스는 new 를 이용한 인스턴스 생성이 가능하다.
