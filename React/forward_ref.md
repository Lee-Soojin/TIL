# Forward Ref

fowarding ref 를 사용하면 부모 component에서 자식 component의 ref에 관여할 수 있다.

```js
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="FancyButton">
    {props.children}
  </button>
));

// You can now get a ref directly to the DOM button:
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;
```

FancyButton 은 forwardRef를 이용해 전달된 ref를 얻고 렌더링 되는 DOM button으로 전달한다.

_단계_

- React.createRef를 호출해 ref 생성 후 ref 변수에 할당한다. \*이 ref는 FancyButton의 ref로 전달되어진다.
- ref는 fowardRef의 두번째 인자로 전달되어진다.
- 이 ref를 button 에서 ref로 전달한다.
- 이제 ref.current는 DOM Node인 button을 가리키게 된다.

---

**HOC에서의 ref는?**

HOC에서 ref를 추가할 경우 래핑 된 component가 아닌 가장 바깥쪽 컨테이너의 component를 참조한다.

```js
function logProps(WrappedComponent) {
  class LogProps extends React.Component {
    componentDidUpdate(prevProps) {
      console.log("old props:", prevProps);
      console.log("new props:", this.props);
    }

    render() {
      return <WrappedComponent {...this.props} />;
    }
  }
  class FancyButton extends React.Component {
    focus() {
      // ...
    }

    // ...
  }

  return LogProps;
}
export default logProps(FancyButton);
```

실제로는 FancyButton의 ref가 LogProps component에 첨부된다는 것이다.

```js
function logProps(Component) {
  class LogProps extends React.Component {
    componentDidUpdate(prevProps) {
      console.log("old props:", prevProps);
      console.log("new props:", this.props);
    }

    render() {
      const { forwardedRef, ...rest } = this.props;

      return <Component ref={forwardedRef} {...rest} />;
    }
  }

  return React.forwardRef((props, ref) => {
    return <LogProps {...props} forwardedRef={ref} />;
  });
}
```

다행히 위와 같이 React.forwardRef API를 사용하여 내부 Component인 FancyButton에 대한 ref를 전달할 수 있다.

참고 : [React 공식 문서] <https://ko.reactjs.org/docs/forwarding-refs.html#gatsby-focus-wrapper>
