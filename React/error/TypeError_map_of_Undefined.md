# TypeError: map of Undefined

card maker 프로젝트를 만들다가 위와 같은 에러가 발생하였다.

```js
{
  cham.map((champion) => (
    <img
      className={styles.champion_img}
      src={require(`../../image/chamImage/${champion}.png`).default}
      alt="champion"
    />
  ));
}
```
