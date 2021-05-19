# 이벤트 위임

## 📌버블링과 캡처링

### **1. 버블링**

**버블링**이란 물 속의 거품이 아래에서 올라오는 모습처럼 부모요소를 거슬러 올라가며 *이벤트 핸들러*가 동작하는 모습에 의해 이름 지어졌다.

```html
<div onclick="divClick()">
  <section onclick="sectClick()">
    <p onclick="pClick()"></p>
  </section>
</div>
```

위 코드의 경우 p가 click 되면 p에 할당된event handler가 동작하고 이어서 부모 요소인 section 그리고 div 순서로 event handler가 동작한다. 이 onclick handler는 상위 document 객체를 만날때까지 동작한다. 이것이 바로 버블링이다.

💡 **거의 모든 이벤트들이 버블링이 발생한다. 하지만 focus 등 버블링이 발생하지 않는 이벤트도 존재한다.**

```html
<div onclick="alert('bubble')">
  <p onclick="alert('p clicked')"></p>
</div>
```

버블링을 중단하려면 'event.stopPropagation()'을 이용하면 된다.

### **2. 캡처링**

버블링이 이벤트가 상위요소로 전파되는 거라면 캡처링은 이벤트가 **하위요소**로 전파되는 것이다.

캡처링은 addEventListener에서 capture option을 true로 설정하면 동작한다.

```js
elem.addEventListener(...,{capture:true})
// elem.addEventListener(...,true)와 동일함

```

버블링과 달리 상위에서 부터 하위요소로 이벤트 핸들러가 거슬러 내려가면서 동작한다고 보면 된다.

---

## _이벤트 위임 Event Delegation_

캡처링과 버블링을 활용해 이벤트 위임을 할 수 있다.
부모 요소에 공통 이벤트 핸들러를 두어 부모 요소부터 그 안의 하위 요소들까지 같은 이벤트 핸들러를 할당해 주는 것이다.

**event.target**을 이용하여 실제 event target을 알아낼 수 있다.

```js
div.onCLick = (event) => {
  let target = event.target;
  if (target.tagName === "img") {
    console.log("img clicked");
  }
};
```

위와 같이 if문 안에서 target의 tagName을 지정해 조건을 부여한다. 그리하여 event target이 해당 조건에 성립하면 if 문 안의 동작이 실행되는 것이다.

이렇게 이벤트 위임을 활용하면 여러 요소에 같은 이벤트 핸들러를 일일이 부여하지 않아도 된다. 부모 요소에 한번 할당하면 하위 요소들 전체에 같은 이벤트 핸들러가 할당이 되는 대단한 일을 해내는 것이 event delegation인 것이다!
이러한 event delegation은
언제든지 이벤트 핸들러를 할당받을 하위요소를 추가하고 제거할 수 있다는 장점도 있다.
