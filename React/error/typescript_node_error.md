# Error: Cannot find module '@types/node/package.json'

```
**Error: Cannot find module '@types/node/package.json'**
```

위와 같은 에러가 발생하였다.
나는 TypeScript를 이용해
'1-2-function.ts'라는 파일을
**ts-node 1-2-function.ts** 라는 명령어를 이용해 실행 중이었다. 그리고 저러한 에러가 발생하였다. 그리하여 서치한 결과

```
npm i -g @types/node
```

위와 같이 @types/node를 글로벌하게 설치하여 문제를 해결할 수 있었다.
이렇게 사소한 문제들이 가끔 골치를 아프게 한다. 😹
