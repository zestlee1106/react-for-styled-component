# Styled Component 에 대해서 공부해 보자

- html 의 스타일이 길어지면 점점 읽기가 힘들어진다.
- class 로 나눠줄 수는 있겠지만, 이것도 한계가 있다
- 이를 해결하기 위해서 나온 것이 바로 Styled Component 이다
- `styled-components` 를 import 한 후, styled.태그명`` 이라고 한 뒤 백틱 안에다 원하는 스타일을 넣으면  
  설정한 컴포넌트명으로 jsx 내에서 컴포넌트를 사용할 수 있다
- 이것은 중복되는 컴포넌트를 줄일 때 효과적으로 쓰일 수 있다

## 스타일을 확장하기

- 중복되는 스타일들을 줄이기 위해서, Style Component 를 extend 할 수도 있다
- `styled.div` 대신 `styled(기존컴포넌트명)` 을 하면, Style Component 를 extend 하여 코드 중복을 줄일 수 있다

## 스타일 컴포넌트에 attribute 넣기

- as 를 사용해서 html 태그를 변경할 수 있다
- 같은 attribute 를 같은 스타일에 여러개 넣어야 할 경우가 생길 수 있다
- `styled.div.attrs({required: true})` 이런 식으로 객체 형태로 넣으면 된다

## animation 사용하기

- 여느 css 처럼 animaiton 을 넣을 수 있다
- styled-components 의 keyframes 를 import 한 후, keyframes`` 이렇게 애니메이션 객체를 만들어 주고
- 사용할 Style Component 에서 animation: 만든 객체 로 써주면 만든 animation 이 동작한다

## Styled Component 내부 태그들 스타일 주기

- Style Component 를 scss 처럼 활용이 가능하다
- Styled Component 에서 아래처럼 내부 태그들 스타일 지정이 가능하고,  
  심지어는 scss 처럼 pseudo selector 도 &:active 로 지정이 가능하다

```javascript
const Box = styled.div`
  height: 200px;
  span {
    font-size: 36px;
    &:hover {
      font-size: 40px;
    }
  }
`;
```

### Styled Component 내부의 Styled Component 에 스타일 지정하기

- styled component 내부에 styled component 를 넣고 그 컴포넌트를 지정해서 스타일을 주고 싶을 수도 있다
- 그럴 땐 위해서 Styled Component 를 새로 만들고, 기존 Styled Component 에서 pseudo selector 를 쓰면 된다.

```javascript
const Emoji = styled.span`
  font-size: 36px;
`;
const Box = styled.div`
  ${Emoji}:hover {
    font-size: 98px;
  }
`;
function App() {
  return (
      <Box>
        <Emoji as="p">🤔</Emoji>
      </Box>
      <Emoji>👍</Emoji>
  );
}
```

- 위처럼 되어있을 때, Box 안에 있는 Emoji 는 hover 스타일이 먹지만, 밖에 있는 Emoji 는 hover가 먹지 않는다

### Theme 을 추가해 주기

- 다크모드, 라이트모드가 필요하다면 ThemeProvider 를 사용하면 된다.
- index.js 에서 App 을 ThemeProvider 로 감싸면 되고, theme props 로 스타일을 넘겨주면 된다
- 그럼 app 안에서는 해당 값으로 스타일을 받아와서 쓸 수 있다
