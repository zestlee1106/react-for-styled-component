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
