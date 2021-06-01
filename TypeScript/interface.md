# Interface 인터페이스

인터페이스는 타입 체크를 위해 사용되며 변수, 함수, 클래스에 사용할 수 있습니다.

## 변수 interface

```ts
function Cake(topping: { fruits: number; cream: string }) {
  console.log(
    `${fruits}개의 과일이 올라간 ${cream} 크림 케이크를 만드는 중입니다. `
  );
}

let topping = {
  fruits: 4,
  cream: milk,
};

Cake(topping);
```

위에 Cake를 만드는 Cake라는 함수가 있고 props로 topping 오브젝트가 들어가 있습니다. 위와 같이 fruits, cream 두개로 이루어진 topping에 다른 여러 종류의 토핑들이 들어갈 경우 코드의 가독성이 좋지 않고 지저분한 코드가 완성될 것입니다.

따라서 이때 우리는 interface를 사용할 수 있습니다.

```ts
interface Topping {
  fruits: number;
  cream: string;
}

function Cake(topping: Topping) {
  console.log("케이크 만드는 중... 🍰");
}
```

이렇게 interface를 이용하면 훨씬 가독성 좋고 깔끔한 코드를 완성할 수 있습니다.

## interface의 선택적 property

interface의 property 중 optional로 지정하고 싶은 property에는 ? 물음표를 붙이면 됩니다.

```ts
interface Pizza {
  ketchup: number;
  pickle: number;
  vegetable: string;
  olive?: boolean;
}
```

위와 같이 olive에 ?를 붙여서 optional로 만들어줄 수 있습니다.

## 함수 interface

```ts
interface sumFunc {
  (num1: number, num2: number): void;
}

const Sum: sumFunc = (num1: number, num2: number): void => {
  console.log(`num1+ num2 = ${num1 + num2}`);
};
```

함수 interface는 parameter , return type을 정의해주어야 한다.

## 클래스 interface

```ts
interface Item {
    name: string;
    skill: string;
    damage: number;
    createItem(name: string, skill: string, damage: number):void;
}

class Game implements Item {
    constructor {
        public name: string;
        public skill: string;
        public damage: number;
    }

    function createItem (name: string, skill: string, damage: number):void {
        this.name = name;
        this.skill = skill;
        this.damage = damage;
        console.log(`명칭: ${name} 스킬: ${skill} 치명타: ${damage}`)
    }
}

const game = new Game();
game.createItem('thunder', 'wind', 30);
```

클래스에 implements를 이용하여 interface를 선언할 수 있습니다. 해당 클래스는 선언된 interface 를 반드시 구현해야 합니다.
