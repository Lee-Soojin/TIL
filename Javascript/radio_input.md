# < input type="radio" >

```js
<input type="radio">
```

슬라이드 형식의 css를 구현하려다가 radio type의 input을 접하게 되었다! 😃

---

- radio type의 input은 동시에 하나의 radio button만 선택이 가능하고 선택된 경우 속을 채우거나 강조 표시가 된다.

```js
<div>
  <input type="radio" id="huey" name="drone" value="huey"
         checked>
  <label for="huey">Huey</label>
</div>
```

- 한 radio button을 누르면 원래 select 되어있던 radio button이 deselect된다.

- radio group은 원하는 수만큼 생성할 수 있다. 그리고 unique한 **name**을 가져야 한다.

- radio button을 선택시 input 안의 value가 전달되어진다.

```js
<input type="radio" id="contactChoice1"
     name="contact" value="email" checked>
```

- 위의 예시처럼 *checked*를 부여하면 *checked*가 부여된 input의 radio button이 클릭되어진 상태가 **default**가 된다.

💡 *checked*를 여러 input에 부여하면 가장 나중에 부여되어진 input이 default로 select되어진다. 이는 radio button은 한번에 하나만 선택되어지기 때문에 나타나는 현상이다.

CSS 작성시 기본 스타일을 없애고 새로 스타일링하려면 **appearance : none**을 지정하면 된다.

참고: [MDN 문서]<'https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input/radio'>
