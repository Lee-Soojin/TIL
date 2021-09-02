# Constructor ( 생성자 )

## constructor ?

**constructor** 메서드는 class 내에서 객체를 생성하고 초기화하기 위한 메서드이다.

```js
class User {
  constructor(name) {
    this.name = name;
  }
}
const user1 = new User();
```

클래스 당 하나의 constructor 메서드를 가질 수 있다. constructor 는 **super**를 이용하여 상위 클래스의 생성자 메서드를 호출할 수 있다.

```js
class Player extends User {
  constructor(id) {
    super(id);
    this.name = "Bob";
  }
}
```

Player class 는 User class 를 상속 받는다. super를 이용하여 User 클래스의 constructor 함수를 호출하여 id 값을 넘겨준다.

### ❗ 생성자 함수 사용시 지켜야할 것

- 함수 이름은 반드시 대문자로 시작
- new를 이용해 생성

---

## **new**를 이용한 함수 생성

- 빈 객체 { } 를 만들어 this에 할당한다.
- this가 만들어진 객체를 가리키게 한다. ( default this는 window이다. new를 사용하지 않을 경우 this는 window를 가리킨다.)
- 함수 본문을 실행한다.
- 함수에서 해당 객체(class)를 반환한다.

## 생성자 함수

constructor function 즉 **생성자 함수**는 일반 함수와 기능이 다를 바 없다. 여러개의 동일한 프로퍼티를 가지는 객체를 생성하기 위해서 필요하다.
this.프로퍼티 형식으로 프로퍼티를 명시할 수 있다.
