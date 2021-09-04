# DocumentFragment

## Document

Document는 브라우저가 불러온 웹페이지를 뜻한다. Document는 EventTarget, Node를 상속한다.

---

## DocumentFragment

**DocumentFragment**는 부모가 없는 아주 작은 document객체를 나타낸다. 이는 문서 트리 구조의 일부가 아니다. Node, ParentNode를 상속한다.

`<template>` 요소는 `HTMLTemplateElement.cotent` 속성에 `DocumentFragment`를 포함한다. 빈 `DocumentFragment`는 `document.createDocumentFragment()` 메서드나 생성자를 이용해 만들 수 있다.

---

## 용도

일반적인 용도는 DocumentFragment를 생성하고 그 안에 DOM 하위 트리를 조립한 다음 Node 인터페이스 메서드를 이용하여 DOM에 삽입하는 것이다.

ex )

```js
const number = [1, 2, 3, 4, 5];
const fragment = new DocumentFragment();
number.forEach((num) => {
  const li = document.createElement("li");
  li.innerHTML = num;
  fragment.appendChild(li);
});
```

위와 같이 new로 DocumentFragment를 생성해 appendChild를 이용하여 DOM에 li를 삽입할 수 있다.
