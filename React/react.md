# React 공부 기록

_21.05.03_

- image src 작성시

```js
<image src={require('./image1.png')}>
```

위와 같이 작성하면 사진이 정상적으로 들어가지 않는다.

```js
<image src={require('./image1.png').default}>
```

뒤에 .default를 추가해주면 사진이 잘 나타나게 된다.

- 사진 여러장을 불러올 경우

참고: Youtube <Multiple Images in ONE IMPORT | ReactJS> [link here]('https://youtu.be/gEMAZSO85KY')
