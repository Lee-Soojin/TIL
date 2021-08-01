# getter 와 setter

참고 : <https://ko.javascript.info/property-accessors>

getter 와 setter는 접근자 프로퍼티의 메소드이다.

```js
let user = {
    get fullName() {

    }

    set fullName(name) {

    }
}
```

**getter** 메서드는 user.fullName 을 이용해 **프로퍼티를 읽으려 할 경우 실행**된다. **setter**는 user.fullName = name 으로 **프로퍼티에 값을 할당할때 실행**된다.

```js
let user = {
  firstname: "Leonard",
  lastname: "Hofstadter",
};
```

이 user라는 객체를 토대로 fullName이라는 프로퍼티를 추가해 보자

```js
let user = {
  firstname: "Leonard",
  lastname: "Hofstadter",

  get fullName() {
    return `${this.firstname} ${this.lastname}`;
  },
};

console.log(user.fullName);
// Leonard Hofstadter
```

외부에서는 접근자 프로퍼티 fullName을 일반 프로퍼티처럼 사용이 가능하다.
메소드로 선언되어 있으나 호출시에는 일반 프로퍼티에 접근하는 것처럼 user.fullName으로 호출한다.

현재 fullName은 getter 메서드만 가지고 있으므로

```js
user.fullName = "Sheldon Cooper";
```

이와 같이 할당하려고 하면 에러가 발생한다.

setter 메서드를 추가하면 할당이 가능하다.

```js

let user = {
    firstname: 'Leonard',
    lastname: 'Hofstadter',

    get fullName() {
     return `${this.firstname} ${this.lastname}`
    }

    set fullName(value) {
        [this.firstname, this.lastname] = value.split(" ");
    }
};

user.fullName = 'Leonard Hofstadter';

console.log(user.fullName);

```

이처럼 setter를 이용해 fullName에 할당을 해줄수 있다.

---

### **get** -> 인수가 없으며 프로퍼티를 읽을때 동작함

### **set** -> 인수를 하나 가지고 프로퍼티에 값을 쓸 때 호출됨
