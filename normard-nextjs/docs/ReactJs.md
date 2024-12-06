# ReactJS
React 처럼 단일 페이지 어플리케이션(SPA) 의 장점
- 사용자 경험을 향상시킨다. 전체 페이지를 로드할 필요가 없어 더 빠르다.
- 서버의 부하를 감소시킨다.
  - 페이지의 일부만 동적으로 갱신되기 때문에 서버의 부하가 줄고, 페이지 로드 시간이 단축된다.
- 코드를 효율적으로 구성할 수 있다. 컴포넌트 기반으로 애플리케이션을 쪼개기 때문에 유지보수가 편하다.

> 리액트는 라이브러리고, 뷰,앵귤러,NextJS 는 프레임워크 이다 <br>

> JSX 파일은 html,css,js 를 하나로 결합할 수 있는 구문을 제공한다.

### 가상 DOM 과 동시성 렌더링
리액트는 가상 Dom 을 사용한다 <br>
트리 구조로된 Dom 이 렌더링 될 때 화면의 DOM 과 동일한 가상 Dom 을 메모리 상에 만들고 마지막에 실제 DOM 으로 넘기면 연산의 효율성을 높인다 <br>

리액트18 버전부터는 동시성 렌더링 기능을 도입하였다 <br>
JS 는 기본적으로 단일 스레드를 사용하기 때문에 비동기가 불가능했지만, 리액트는 단일 스레드 안에서 여러 렌더링 작업을 <br>
작은 단위로 나누고 작업들 간의 우선 순위를 정하여 화면에 보여준다 <br>

[동시성 렌더링 사용 방법]
```jsx
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

[리액트 프로젝트 생성]
```jsx
npx create-next-app@latest
```

위 명령어는 리액트 프로젝트를 생성하면 자동으로 Next 프레임워크가 포함된 프로젝트가 생성된다 <br>

만약 Next 를 제외한 리액트만 사용한다면  vite 빌드 도구를 사용하는 것이다
```jsx
nppm create vite@latest
```

### useEffect()
보통 페이지가 처음 로드될 때, 혹은 어떤 값이 바뀔 때 필요한 작업을 수행할 때 사용한다 <br>
즉 어떤 일이 일어났을 때 실행할 일을 미리 정해 두는 것이다 <br>

### useState()
useState 는 값을 보관하는 일종의 장소라고 생각하면 된다 <br>
```jsx
const [count, setCount] = useState(0);
```

위 코드는 상태가 count 이고 상태를 바꾸는 함수는 setCount 이다 <br>
count 의 처음 상태값은 '0' 이다 <br>
```jsx
import {useState, useEffect} from "react";

function Exmaple() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        console.log('count 값이 바뀌었다')
    }, [count]); // count 가 바뀔 때 마다 실행
    
    return (
        <div>
            <p>현재 count 값 : {count} </p>
            <button onClick={() => setCount(count+1)}>Count 증가</button>
        </div>
    )
}
```

### useRef()
렌더링에 필요하지 않은 값을 참조할 수 있는 ReactHook <br>
Java 로 따지면 '전역변수' 라고 생각하면 된다 <br>



위 코드를 보면 이해에 도움이 될 것이다 <br>
