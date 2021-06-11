# Interface & Type Alias

## Interface

인터페이스는 같은 이름으로 선언하여도 컴파일 시, 합쳐지므로 **확장성**이 좋다.

```ts
interface ClickInterface {
  enter: number;
  mouse: number;
}

interface ClickInterface {
  spacebar: number;
}
```

위와 같이 ClickInterface라는 인터페이스를 같은 이름으로 두번 선언하면

```ts
interface ClickInterface {
  enter: number;
  mouse: number;
  spacebar: number;
}
```

결론적으론 위와 같이 합쳐진 인터페이스가 된다.

```ts
interface ClickInteface extends InputInterface {
  ctrlBtn: number;
}
```

위와 같이 extends를 이용하여 기존의 인터페이스를 확장할 수 있다.

---

## Type Alias

인터페이스와 달리 타입은 같은 이름을 중복 사용이 불가능하다. 또한 type alias는 extends 또는 implements 될 수 없다.

```ts
type ClickType = {
  enter: number;
  mouse: number;
};
```

```ts
type SpaceClickType = ClickType & { spacbar: number };
```

위와 같이 intersection으로 새로운 타입을 선언하여 구현할 수 있다.

일반적으로 interface를 많이 사용하지만 union, tuple 등이 필요한 경우 type alias를 사용한다.
