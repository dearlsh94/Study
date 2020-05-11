# React Hook

- React 16.8 버전에서 추가



## Functional / Class Component

- [함수형 컴포넌트와 클래스, 어떤 차이가 존재할까?](https://overreacted.io/ko/how-are-function-components-different-from-classes/)

### Functional Component

- **state 및 lifecycle API 사용 불가** - Hooks 를 통해 보완!
- **rendering 된 값들을 유지**
- 성능 향상 (작은 메모리 자원과 배포 크기, 빠른 속도)
- 코드 재사용 가능
- 코드 길이 감축

### Class Component

- **state 및 lifecycle API 사용 가능**
- render, constructor, binding, this 등 코드 사용에 제약 존재
- 내부 코드 길이가 길어짐



## React Hook

- Functional Component 에서 state 관리 및 lifecycle API의 기능을 구현 가능하게 해줌.
- hook 의 재사용으로 코드 품질 향상
- React 내장 hook 및 Custom hook 사용 가능
- 한 컴포넌트에서 여러개의 State나 Effect Hook  사용 가능
- React 는 hook 이 호출되는 순서에 의존
  - hook 의 호출 순서는 렌더링 마다 동일

### useState()

- state 상태 관리 지원 hook

- [state 변수, 해당 변수를 갱신할 수 있는 함수] 의 쌍으로 반환

  - 배열 구조 분해 문법
  - 2개의 아이템 쌍이 들어있는 배열 반환

- useState 의 매개변수는 state의 초기 값으로 숫자, 문자 타입 지원

- 예시

  - ```react
    import React, { useState } from "react";
    ...
      const [color, setColor] = useState("black");
      const [count, setCount] = useState(0);
      const [list, setList] = useState([{title: 't', content: 'c'}]);
    ...
        <p>now color is {color}</p>
        <button onClick={() => setColor("blue")}>
    	  Change to Blue
        </button>
    ```

### useEffect()

- side effect 수행 hook
- componentDidMount + componentDidUpdate + componentWillUnmount

> ***Side Effect***
>
> 화면이 렌더링 된 이후 비동기로 처리 되어야 하는 부수적인 효과.
>
> ex) 외부 API를 통해 데이터를 가져올 때 화면 렌더링 후 비동기로 데이터를 가져오는 것

- Clean-Up을 이용하지 않는 Effects 예시

  - componentDidMount, componentDidUpdate

  - ```react
    import React, { useEffect } from 'react';
    ...
      const [count, setCount] = useState(0);
      useEffect(() => {
        document.title = `now {count}`;
      });
    ...
    ```

- Clean-Up을 이용하는 Effects 예시

  - componentDidMount에서 실행 후 componentWillUnmount 에서 Clean-Up

  - ```react
    import React, { useEffect } from 'react';
    ...
      const [isOnline, setIsOnline] = useState(null);
      useEffect(() => {
        ...
        return function cleanup() {
          ...
        };
      });
    ...
    ```

- 특정 값이 리렌더링 시 변경되지 않을 때 Effects 생략 예시

  - count 변경 시에만 Effect 재실행

    ```react
    ...
      useEffect(() => {
        document.title = `now {count}`;
      }, [count]);
    ```

> 빈 배열([])을 인수로 넘기면 prop이나 state에 의존하지 않으므로 이후 재실행 되지 않는다.



## 규칙

- `eslint-plugin-react-hooks` ESLint 플러그인을 통해 규칙 강제
  - CreateReactApp에 기본적으로 포함
  - `$npm i eslint-plugin-react-hooks`
- 최상위에서만 Hook 호출 가능
  - Hook 의 정확한 상태 유지를 위함
  - 반복문, 조건문, 중첩된 함수 내에서는 사용 불가
    - hook 의 호출 순서가 바뀔 위험이 존재
    - hook 내부에서 조건문을 사용하여 처리
- React Functional Component 또는 Custom Hook 에서 Hook 호출
  - 일반적인 JavaScript 함수에서 호출 금지



