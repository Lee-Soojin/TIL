# React 공부 기록

_📝21.05.03_

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

---

_📝21.05.07_

- React.js 랑 Firebase Realtime Database 사용하기

참고한 유용한 링크 : <https://www.educative.io/edpresso/firebase-as-simple-database-to-react-app>

firebase -> Database -> real time database 의 경로로 실시간 데이터에 접근하고 싶다면 *ref*를 이용하면 된다.
