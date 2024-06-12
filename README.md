# 최진영 202230337

## 6월 12일 강의

####  CSS란?
- CSS는 Cascading Style Sheets의 약자로 스타일링을 위한 언어입니다.
- Cascadig이란 계단식이라는 뜻으로 한 엘리먼트에 여러 스타일이 적용될 경우 스타일간의 충돌을 막기 위해 계단식으로 스타일을 적용시키는 규칙을 갖고 있습니다.
- 즉 하나의 스타일이 여러 개의 엘리먼트에 적용될 수도 있고, 하나의 엘리먼트에도 여러 개의 스타일이 적용될 수도 있습니다.
- 엘리먼트에 스타일이 적용되는 규칙을 selector(선택자)라고 합니다. CSS는 이 선택자와 스타일로 이루어 집니다.
- 이번 장에서는 선택자와 스타일을 카테고리별로 나누어 학습합니다.

#### CSS문법과 선택자
- 선택자를 먼저 쓰고 다음에 적용할 스타일을 중괄호 안에 세미콜론으로 구분하여 하나씩 작성합니다.
- 선택자는 HTML 엘리먼트를 직접 넣어도 되고, 엘리먼트이 조합 혹은 class형태로 작성 가능합니다.
- 스타일은 property(속성)과 key value(키 값)로 이루어지며, 이들은 콜론(:)으로 구분하고, 각 스타일은 세미콜론(;)으로 구분합니다.

#### 레이아웃과 관련된 속성
- 화면에 엘리먼트를 어떻게 배치할 것인지를 정의합니다.
- 가장 중요한 속성은 display입니다.
- 모든 엘리먼트는 기본 display 속성을 갖고 있지만 이 기본값을 변경해 줄 수 있습니다.
```
div {
    display: none | block | inline | flex;
}
```
-none은 존재는 하지만 화면에 보이지 않는 것으로, 자바스크립트를 넣을 때 많이 사용합니다.
- block은 세로로 정렬되며, with의 height를 갖을 수 있다. 크기와 상관없이 한 줄을 점유합니다.
- inline은 가로로 정렬되며, with의 height를 갖을 수 없다. 컨텐츠의 크기만큼 공간을 점유합니다.
- inline-block는 기본적으로 inline의 특성을 갖지만, with와 height 등 block의 특성을 사용할 수 있습니다.
- 대표적인 block과 inline 태그는 다음과 같습니다.
- Block: `<div>` `<table>` `<h1>` ~ `<h6>` `<p>` `<form>` `<ul>` `<O>` `<i>` `<d>` `<dt>` `<dd>` `<pre>` 등
- inline: `<span>` `<a>` `<br›` `<em>` `<strong>` `<input>` `<label>` `<img>`
- flex는 컨테이너의 형태로 엘리먼트를 관리합니다. `Mozila` 참고
- 최근 들어서는 Grid를 많이 사용합니다. Flex가 1차원 적이라면 Grid는 2차원 적으로 관리가 가 능하기 때문입니다. `Mozilla` 참고

#### Styled-components
- CSS 문법을 그대로 사용하면서 결과물을 스타일링된 컴포넌트 형태로 만들어 주는 오픈소스 라이브러리입니다.
- 컴포넌트의 개념을 사용하고 있어 리액트 개발에 많이 사용합니다.
1. tyled-components 설치하기
    -  npm install -save styled-components
    - 교재에는 위와 같이 나와 있지만 npm v5 부터는 사용하지 않아도 됩니다. 자동 추가!
    - 440페이지 코드 처럼 import해서 사용하면 됩니다.
2. styled-components 기본 사용법
    - 태그드 템플릿 리터럴을 사용하여 구성 요소의 스타일을 지정합니다.
    - 태그드 템플릿 리터럴은 자바스크립트에서 제공하는 문법 중 하나로 리터럴을 템플릿 현태로 사용하는 것입니다.




## 6월 11일 강의

#### [3] Containment와 Specialization을 같이 사용하기
- Containment를 위해서 props.children을 사용하고, Specialization을 위해 직접 정의한 props를 사용하면 됩니다.
- Dialog컴포넌트는 이전의 것과 비슷한데 Containment를 위해 끝부분에 props.children을 추가했습니다.
- Dialog를 사용하는 SignUpDialog는 Specialization을 위해 props인 title, message에 값을 넣어주고 있고, 입력을 받기위해 `<input>`과 `<button>`을 사용합니다. 이 두 개의 태그는 모두 props.children으로 전달되어 다이얼로그에 표시됩니다.
- 이러한 형태로 Containment와 Specialization을 동시에 사용할 수 있습니다.

#### 상속에 대해 알아보기
- 합성과 대비되는 개념으로 상속(ingeritance)이 있습니다.
- 자식 클래스는 부모 클래스가 가진 변수나 함수 등의 속성을 모두 갖게 되는 개념입니다.
- 하지만 리액트에서는 상속보다는 합성을 통해 새로운 컴포넌트를 생성합니다.

#### 컨텍스트란 무엇인가?
- 기존의 일반적인 리액트에서는 데이터가 컴포넌트의 props를 통해 부모에서 자식으로 단방향으로 전달되었습니다.
- 컨텍스트는 리액트 컴포넌트들 사이에서 데이터를 기존의 props를 통해 전달하는 방식 대신 '컴포넌트 트리를 통해 곧바로 컴포넌트에 전달하는 새로운 방식'을 제공합니다.
- 이것을 통해 어떤 컴포넌트라도 쉽게 접근할 수 있습니다.
- 컨텍스트를 사용하면 일일이 props로 전달할 필요 없이 그림처럼 데이터를 필요로 하는 컴포넌트에 곧바로 데이터를 읽을 수 있습니다.

#### 언제 컨텍스트를 사용해야 할까?
- 여러 컴포넌트에서 자주 필요로 하는 데이터는 로그인 여부, 로그인 정보, UI 테마, 현재 선택된 언어 등이 있습니다.
- props를 통해 데이터를 전달하는 기존 방식은 실제 데이터를 필요로 하는 컴포넌트까지의 깊이가 깊어질 수록 복잡해 집니다.
- 또한 반복적인 코드를 계속해서 작성해 주어야 하기 때문에 비효율적이고 가독성이 떨어집니다.
- 컨텍스트를 사용하면 이러한 방식을 깔끔하게 개선할 수 있습니다.

#### 컨텍스트를 사용하기 전에 고려할 점
- 컨텍스트는 다른 레벨의 많은 컴포넌트가 특정 데이터를 필요로 하는 경우에 주로 사용합니다.
- 하지만 무조건 컨텍스트를 사용하는 것이 좋은 것은 아닙니다.
- 왜냐하면 컴포넌트와 컨텍스트가 연동되면 재사용성이 떨어지기 때문입니다.
- 따라서 다른 레벨의 많은 컴포넌트가 데이터를 필요로 하는 경우가 아니면 props를 통해 데이터를 전달하는 컴포넌트 합성 방법이 더 적합합니다.

- 실제 user와 avatarSize를 사용하는 것은 Avatar 컴포넌트 뿐인데 여러 단계에 걸쳐 props를 전달하고 있습니다.
- 이런 경우 컨텍스트를 사용하지 않고 문제를 해결할 수 있는 방법은 Avatar 컴포넌트를 변수에 저장하여 직접 넘겨주는 것입니다.
- 이렇게 하면 중간 단계의 컴포넌트들은 user와 avatarSize에 대해 몰라도 됩니다.
- 하지만 데이터가 많아질수록 상위 컴포넌트가 점점 더 복잡해지기 때문에 모든 상황에서 좋은 것은 아니다.
- 이런 경우 하위 컴포넌트를 여러 개의 변수로 나눠서 전달하면 됩니다.
- 하지만 어떤 경우에는 하나의 데이터에 다양한 레벨에 있는 중첩된 컴포넌트들의 접근이 필요할 수 있습니다.
- 이런 경우라면 컨텍스트가 유리합니다.
- 컨텍스트는 해당 데이터와 데이터의 변경사항을 모두 하위 컴포넌트들에게 broadcast해주기 때문입니다.
- 컨텍스트를 사용하기에 적합한 데이터의 대표적인 예로는 '지역 정보', 'UI테마' 그리고 '캐싱된 데이터' 등이 있습니다.

#### 컨텍스트 API
- 이 파트에서는 리액트에서 제공하는 컨텍스트 API를 통해 컨텍스트를 어떻게 사용하는지에 대해 알아봅니다.

##### [1] React.createContext
- 컨텍스트를 생성하기 위한 함수입니다.
- 파라메타에는 기본값을 넣어주면 됩니다.
- 하위 컴포넌트는 가장 가까운 상위 레벨의 Provider로 부터 컨텍스트를 받게 되지만, 만일 Provider를 찾을 수 없다면 설정한 기본값을 사용하게 됩니다.

```
const MyContent = React.creatContext(기본값);
```
##### [2] Context.Provider
- Context.Provider 컴포넌트로 하위 컴포넌트들을 감싸주면 모든 하위 컴포넌트들이 해당 컨텍스트의 데이터에 접근할 수 있게 됩니다.
```
MyContext.Provider value={/* some value */}
```
- Provider컴포넌트에는 value라는 prop이 있고, 이것은 Provider컴포넌트 하위에 있는 컴포넌트에게 전달됩니다.
- 하위 컴포넌트를 consumer컴포넌트라고 부릅니다.

##### [3] Class.ContextType
- Provider 하위에 있는 클래스 컴포넌트에서 컨텍스트의 데이터에 접근하기 위해 사용합니다.
- Class 컴포넌트는 더 이상 사용하지 않으므로 참고만 합니다.

##### [4] Context.Consumer
- 함수형 컴포넌트에서 Context.Consumer를 사용하여 컨텍스트를 구독할 수 있습니다.
```
 <MyContext.Consumer>
    {value => /* 컨텍스트의 값에 따라서 컴포넌트들을 렌더링 */ }
</MyContext.Consumer>
```
- 컴포넌트의 자식으로 함수가 올 수 있는데 이것을 function as a child라고 부릅니다.
- Context.Consumer로 감싸주면 자식으로 둘어간 함수가 현재 컨텍스트릐 value를 받아서 리액트 노드로 리턴합니다.
- 함수로 전달되는 value는 Provider의 value prop과 동일합니다.

##### [5] Context.displayName
- 컨텍스트 객체는 displayName이라는 문자열 속성을 갖습니다.
- 크롬의 리액트 개발자 도구에서는 컨텍스트의 Provider나 Consumer를 표시할 때 displayName을 함께 표시해 줍니다.
```
const MyContext = React.createContext( /* some value */ );
MyContext.displayName = 'MyDisplayName';

// 개발자 도구에 "MyDisplayName.Provider"로 표시됨
<MyContext.Provider>

// 개발자 도구에 "MyDisplayName.Consumer"로 표시됨
<MyContext.Consumer>
```

#### 여러 개의 컨텍스트 사용하기
- 여러 개의 컨텍스트를 동시에 사용하면 Context.provder를 중첩해서 사용합니다.
- 예제에서는 ThemeContext와 UserContext를 중첩해서 사용하고 있습니다.
- 이런 방법으로 여러 개의 컨텍스트를 동시에 사용할 수 있습니다.
- 하지만 두 개 또는 그 이상의 컨텍스트 값이 자주 함께 사용될 경우 모든 값을 한 번에 제공해 주는 별도의 render prop 컴포넌트를 직접 만드는 것을 고려하는 것이 좋습니다.

#### useContext
- 함수형 컴포넌트에서 컨텍스트를 사용하기 위해 컴포넌트를 매번 Consumer컴포넌트로 감싸주는 것보다 더 좋은 방법이 있습니다. 바로 7장에서 배운 Hook입니다.
- useContext() 훅은 React.createContext() 함수 호출로 생성된 컨텍스트 객체를 인자로 받아서 현재 컨텍스트의 값을 리턴합니다.
```
function MyComponent(props) {
    const value = useContext(MyContext);

    return (
        ...
    )
}
```
- 이 방법도 가장 가까운 상위 Provider로 부터 컨텍스트의 값을 받아옵니다.
- 만일 값이 변경되면 useContext() 훅을 사용하는 컴포넌트가 재렌더링 됩니다.
- 또한 useContext() 훅을 사용할 때에는 파라미터로 컨텍스트를 넣어줘야 한다는 것을 기억해야 합니다.





## 6월 5일 강의
#### Shared State
- Shared state는 state의 공유를 의미합니다.
- 같은 부모 컴포넌트의 state를 자식 컴포넌트가 공유해서 사용하는 것입니다.

    - Calculator.jsx

        ```
        import { useState } from "react"
        import TemperatureInput from "./TemperatureInput"

        export default function Calculator() {
        return (
            <>
            <TemperatureInput scale='c' />
            <TemperatureInput scale='f' />
            </>
        )
        }

        function toCelsius(fahrenheit) {
        return (
            (fahrenheit-32) * 1.8
        )
        }

        function toFahrenheit(celsius) {
        return (
            (celsius * 1.8) +32
        )
        }

        function tryConvert(temperature, convert) {
        const input = parseFloat(temperature)
        if(Number.isNaN(input)) {
            return('')
        }
        const output = convert(input)
        const rounded = Math.round(output * 1000) / 1000  
        return (rounded.toString())
        }
        ```


    - TemperatureInput.jsx
        ```
        import { useState } from "react"

        export default function TemperatureInput(props) {
        const scaleNames = {
            c: '섭씨',
            f: '화씨'
        }
        const [temperature, setTemperature] = useState()
        const handleChange = (e) => {
            setTemperature(e.target.value)
        }
        return (
            <fieldset>
            <legend>섭씨온도를 입력해주세요(단위:{scaleNames[props.scale]}) :</legend>
            <input value={temperature} onChange={handleChange} />
            </fieldset>
        )
        }
        ```

##### 정리하면
- 상위 컴포넌트인 Calculator에서 온도와 단위를 state로 갖고,
- 두 개의 하위 컴포넌트는 각각 섭씨와 화씨로 변환된 온도와 단위, 그리고 온도를 업데이트하기 위한 함수를 props로 갖고 있습니다.

#### 합성
- 합성(Composition)은 '여러 개의 컴포넌트를 합쳐서 새로운 컴포넌트를 만드는 것입니다.
- 조합 방법에 따라 합성의 사용 기법은 다음과 같이 나눌 수 있습니다.

### [1] Containment (담다, 포함하다, 격리하다)
- 특정 컴포넌트가 하위 컴포넌트를 포함하는 형태의 합성 방법이다.
- 컴포넌트에 따라서는 어떤 자식 엘리먼트가 들어올 지 미리 예상할 수 없는 경우가 있습니다.
- 범용적인 '박스' 역할을 하는 Sidebar혹은 Dialog와 같은 컴포넌트에서 특히 자주 볼 수 있습니다.
- 이런 컴포넌트에서는 children prop을 사용하여 자식 엘리먼트를 출력에 그대로 전달하는 것이 좋습니다.
- 이때 children prop은 컴포넌트의 props에 기본적으로 들어있는 children속성을 사용합니다.
- 다음과 같이 props.children을 사용하면 해당 컴포넌트의 하위 컴포넌트가 모두 children으로 들어오게 됩니다.
```
function FancyBorder(props) {
    return (
        <div className={'FancyBorder FancyBorder-' + props.color}>
            {props.children}
        </div>
    );
}
```
- children은 다음 구조에서 세 번째 들어가는 파라미터 입니다.
- 파라미터가 배열로 되어있는 이유는 여러 개의 하위 컴포넌트를 가질 수 있기 때문입니다.
- children이 배열로 되어있는 것은 여러 개의 하위 컴포넌트를 위한 것입니다.

#### React.CreateElement()에 관하여
- jsx를 사용하지 않는 경우의 props전달 방법입니다.
> 정확히 말하면 JSX를 사용하지 않고 리액트로 엘리먼트를 생성하는 방법입니다.

- FancyBorder를 사용한 예제입니다.
```
return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">어서오세요.</h1>
      <p className="Dialog-message">우리 사이트 방문을 환영합니다.</p>
    </FancyBorder>
  )
```

- 리액트에서는 props.children을 통해 하위 컴포넌트를 하나로 모아서 제공해 줍니다.
- 만일 여러 개의 children 집합이 필요한 경우는 별도로 props를 정의해서 각각 원하는 컴포넌트를 넣어줍니다.
- 예와 같이 SplitPane은 화면을 왼쪽과 오른쪽으로 분할해 주고, App에서는 SplitPane을 사용해서 left, right 두 개의 props를 정의하고 있습니다.
- 즉, App에서 left, right를 props를 받아서 화면을 분할하게 됩니다. 이처럼 여러 개의 children 집합이 필요한 경우 별도의 props를 정의해서 사용합니다.

### [2] Specialization (특수화, 전문화)
- 웰컴다이얼로그는 다이얼로그의 특별한 케이스입니다.
- 범용적인 개념을 구별이 되게 구체화하는 것을 특수화라고 합니다.
- 객체지향 언어에서는 상속을 사용하여 특수화를 구현합니다.
- 리액트에서는 합성을 사용하여 특수화를 구현합니다.
- 다음 예와 같이 특수화는 범용적으로 쓸 수 있는 컴포넌트를 만들어 놓고 이를 특수한 목적으로 사용하는 합성 방식입니다.
```
function Dialog(props) {
    return (
        <FancyBorder color="blue">
            <h1 className="Dialog-title">
                {props.title}
            </h1>
            <p className="Dialog-message">
                {props.messgae}
            </p>
        </FancyBorder>
    );
}


export default function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">어서오세요.</h1>
      <p className="Dialog-message">우리 사이트 방문을 환영합니다.</p>
    </FancyBorder>
  )
}
```



## 5월 29일 강의
#### Select 태그
- select태그도 taxtarea와 동일합니다.
```
    <select>
        <option value="apple">사과</option>
        <option value="banana">바나나</option>
        <option selected value="grape">포도</option>
        <option value="watermelon">수박</option>
    </select>
```
#### File input 태그
- File input 태그는 그 값이 읽기 전용이기 때문에 리액트에서는 비제어 컴포넌트가 됩니다.
> `<input type="file" />`

#### Input Null Value
- 제어 컴포넌트에 value prop을 정해진 값으로 넣으면 코드를 수정하지 않는 한 입력값을 바꿀 수 없습니다.
- 만약 value prop 은 넣되 자유롭게 입력할 수 있게 만들고 싶다면 값이 undefined 또는 null을 넣어주면 됩니다.
```
    ReactDOM.render(<input value ="hi" />, rootNode);

    setTimeout(function() {
        ReactDOM.render(<input value={null} />, rootNode);
    }, 1000);
```

#### (실습)사용자 정보 입력받기
```
import { useState } from "react";

export default function SignUp() {
  const [name, setName] = useState()
  const [gender, setGender] = useState('여자') // 초기값을 '여자'로 설정
  const [document, setDocument] = useState()
  const [haveBreakfest, setHaveBreakfest] = useState(true)

  const handleChangeName = (e) => {
    setName(e.target.value)
  }

  const handleChangeGender = (e) => {
    setGender(e.target.value)
  }

  const handleChangeDocument = (e) => {
    setDocument(e.target.value)
  }

  const handleChangeHaveBreakfest = (e) => {
    setHaveBreakfest(e.target.checked)
  }

  const handleSubmit = (e) => {
    alert(`이름: ${name}, 성별: ${gender}, 문서: ${document}, 아침식사: ${haveBreakfest}`)
    e.preventDefault()
  }


  return (
    <form onSubmit={handleSubmit}>
      <label>
        이름:
        <input type="text" value={name} onChange={handleChangeName} placeholder="이름을 입력해주세요."/>
      </label>
      <br />
      <label>
        성별:
        <select value={gender} onChange = {handleChangeGender}>
          <option value="남자">남자</option>
          <option value="여자">여자</option>
        </select>
      </label>
      <br />
      <label>
        문서:
        <textarea value={document} onChange={handleChangeDocument}></textarea>
      </label>
      <br />
      <lavel>
        아침식사:
        <input type="checkbox" checked={haveBreakfest} onClick={handleChangeHaveBreakfest} />
      </lavel>
      <br />
      <button type="submit">제출</button>
    </form>
  )
}
```

#### props
- BoilingVerdict.jsx
```
export default function BoilingVerdict(props) {
  if(props.delsius >= 100) {
    return <p>물이 끓습니다.</p>
  } else if(props.foo <= 0) {
    return <p>물이 끓지 않습니다.</p>
  }
}
```

- App.js
```
import './App.css';
import BoilingVerdict from './BoilingVerdict';

function App() {
  return (
    <>
      <BoilingVerdict celsius="100" foo="-3" />
    </>
  );
}

export default App;
```



## 5월 22일 강의
#### 리스트의 키
- 리스트에서 키는 "리스트에서 아이템을 구별하기 위한 고유한 문자열" 입니다.
- 이 키는 리스트에서 어떤 아이켐이 추가 또는 제거 되었는지 구분하기 위해 사용합니다.
- 키는 같은 리스트에 있는 엘리먼트 사이에서만 고유한 값이면 됩니다.


### ch_11 폼
#### 폼이란
- 폼은 일반적으로 사용자로부터 입력을 받기 위한 양식에서 많이 사용됩니다.
#### 제어 컴포넌트
- 제어 컴포넌트는 사용자가 입력한 값에 접근하고 제어할 수 있도록 해주는 컴포넌트입니다.



## 5월 8일 강의
#### Arguments 전달하기
- 함수를 정의할 때는 파라미터 혹은 매개변수, 함수를 사용할 때는 아귀먼트 혹은 인수라고 부릅니다.
- 이벤트 핸들러에 매개변수를 전달해야 하는 경우도 많습니다.
```
<button onClick={(event)=> this.deleteItem(id, event)}>삭제하기</button>
<button onClick={this.deleteItem.bind(this, id)}>삭제하기</button>
```
- 위의 코드는 모두 동일한 역할을 하지만 한나는 화살표 함수를, 다른 하나는 bind를 사용했습니다.
- event라는 매개변수는 리액트의 이벤트 객체를 의미합니다.
- 두 방법 모두 첫 번째 매개변수는 id 이고 두 번째 매개변수로 event가 전달 됩니다.
- 첫 번째 코드는 명시적으로 event를 매개변수로 넣어 주었고, 두 번째 코드는 id 이후 두번째 매개변수로 event가 자동 전달 됩니다.

#### 조건부 렌더링
```
    function Greeting(props) {
        const isLoggedIn = props.isLoggedIn;
        if(isLoggedIn) {
            return <UserGreeting />;
        }
        return <GuestGreeting />;
    }
```
#### 엘리먼트 변수
- 렌더링해야 될 컴포넌트를 변수처럼 사용하는 방법이 엘리먼트 변수입니다.
```
    let button;
    if(isLoggedIn {
        button = <LoggoutButton onClick={handleLogutClick} />;
    }) else {
        button = <LoginButton onClick={handleLogutClick} />;
    }

    return (
        <div>
            <Greeting isLoggedIn = {isLoggedIn} />
            {button}
        </div>
    )
```

#### 인라인 조건
- 필요한 곳에 조건문을 직접 넣어 사용하는 방법

1. 인라인 if
- if문을 직접 사용하지 않고, 동일한 효과를 내기 위해 &&논리 연산자를 사용합니다.
- &&는 and연자로 모든 조건이 참일때만 참이 됩니다.
- 첫 번 조건이 거짓이면 두번째 조건은 판단할 필요가 없습니다. 단축평가.
```
    true && expression -> expression
    false && expression -> false

    {unreadMessages.length > 0 &&
        <h2>
            현재 {unreadMessages.length}개의 읽지 않은 메세지가 있습니다.
        </hr>
    }
```
- 판단만 하지 않는 것이고, 결과 값은 그대로 리턴

```
    <>
        {count && <h1>현재 카운트: {count}</h1>}
    </>
```
 2. 인라인 if-else
 - 조건문 ? 참일 경우 : 거짓일 경우
 - 삼항 연산자를 이용합니다.
 - 문자열이나 엘리먼트를 넣어서 사용할 수도 있습니다.





## 5월 1일 강의
#### 훅의 규칙
- 첫 번째 규칙은 무조건 최상위 레벨에서만 호출해야 한다는 것입니다.
- 따라서 반복문이나 조건문 또는 중첩된 함수들 안에 훅을 호출하면 안 됩니다.
- 이 규칙을 따라서 훅은 컴포넌트가 렌더링 될 때마다 같은 순서로 호출되어야 합니다.
- 페이지 230의 코드는 조건에 따라 호출되기 때문에 잘못된 코드입니다.
```
    function MyComponent(props) {
        const [name, setName] = useState('Inje');

        if(name !== '' ) {
            useEffect(() => {
                ...
            });
        }

        ...
    }
```
- 두 번째 규칙으니 함수형 컴포넌트에서만 훅을 호출해야 한다는 것입니다.
- 따라서 일반 자바스크립트 함수에서 훅을 호출하면 안 됩니다.
- 훅은 함수형 컴포넌트 혹은 직접 만든 커스텀 훅에서만 호출할 수 있습니다.
- 필요하다면 직접 훅을 만들어 쓸 수 있는데, 이것을 커스텀 훅이라고 합니다.

- 한가지 주의할 점은 일반 컴포넌트와 마찬가지로 다른 혹을 호출하는 것은 무조건 커스텀 훅의 최상위 레벨에서만 가능합니다.
- 이름은 use로 시작하도록 합니다. 그렇지 않으면 다른 훅을 불러올 수 없습니다.

#### 이벤트 처리하기
- DOM에서 클릭 이벤트를 처리하는 예제 코드
```
<button onclick="activate()">
    Activate
</button>
```
- React에서 클릭 이벤트를 처리하는 예제 코드
```
<button onClick={activate}>
    Activate
</button>
```
- 둘의 차이점은 첫째, 이벤트 이름이 onclick에서 onClick으로 변경. 둘째, 전달하려는 함수는 문자열에서 함수 그대로 전달

- 이벤트가 발생했을 때 해당 이벤트를 처리하는 함수를 "이벤트 핸들러" 라고 합니다. 또는 이벤트가 발생하는 것을 계속 듣고 있다는 의미로 "이벤트 리스너" 라고 부르기도 합니다.

- 이벤트 핸들러 추가하는 방법은?
- 버튼을 클릭하면 이벤트 핸들러 함수인 handleClick()함수를 호출하도록 되어 있습니다.
- bind를 사용하지 않으면 this.HandleClick은 글로벌 스코프에서 호출되어, undefined으로 사용할 수 없기 때문입니다.
- bind를 사용하지 않으려면 화살표 함수를 사용하는 방법도 있습니다.
- 하지만 클래스 컴포넌트는 이제 거의 사용하지 않기 때문에 이 내용은 참고만 합니다.
```

class Toggle extends React.Component {
    constructor(props) {
        super(props);

        this.state = { isToggleOn: true };

        // callback에서 `this`를 사용하기 위해서는 바인딩을 필수적으로 해줘야 합니다.
        this.handleClick = this.handleClick.bind(this);
    }

    handleClick() {
        this.setState(prevState => ({
            isToggleOn: !prevState.isToggleOn
        }));
    }

    render() {
        return(
            <button onClick={this.handleClick}>
                {this.state.isToggleOn ? '켜짐' : '꺼짐'}
            </button>
        );
    }
}

```



## 4월 17일 강의
1. 훅이란 
- 클래스형 컴포턴트에서는 생성자에서 state를 정의하고, setState()함수를 통해 state를 업데이트 합니다.
- 예전에 사용하던 함수형 컴포넌트는 별도로 state를 정의하거나, 컴포넌트의 생명주기에 맞춰서 어떤 코다가 실행되도록 할 수 없었습니다.
- 함수형 컴포넌트에서도 state나 생명주기 함수의 기능을 사용하게 해주기 위해 추가된 기능이 바로 훅Hook입니다.
- 함수형 컴포넌트도 훅을 사용하여 클래스형 컴포넌트의 기능을 모두 동일하게 구현할 수 있게 되었습니다.
- Hook이란 'state와 생명주기 기능에 갈고리를 걸어 원하는 시점에 정해진 함수를 실행되도록 만든 함수'를 의미합니다.
- 훅의 이름은 모두 'use'로 시작합니다.
- 사용자 정의 훅을 만들 수 있으며, 이 경우에 이름은 자유롭세 할 수 있으나 'use'로 시작할 것을 권장한다.
- useState는 함수형 컴포넌트에서 state를 사용하기 위한 Hook입니다.
- 다음 예제는 버튼을 클릭하 때마다 카운트가 증가하는 함수형 컴포넌트입니다.
- 하지만 증가는 시킬 수 있지만 증가할 때마다 재 렌더링은 일어나지 않습니다.
- 이럴 때 state를 사용해야 하지만 함수형에는 없기 때문에 useState()를 사용합니다.


#### useEffect
- useState와 함께 가장 많이 사용하는 Hook입니다.
- 이 함수는 사이드 이펙트를 수행하기 위한 것입니다.
- 영어로 side effect는 부작용을 의미합니다. 일반적으로 프로그래밍에서 사이트 이펙트는 '개발자가 의도하지 않은 코드가 실행되면서 버그가 발생하는 것'을 말합니다.
- 하지만 리액트에서는 효과 또는 영향을 뜻하는 effect의 의미에 가깝습니다.
- 예를 들면 서버에서 데이터를 받아오거나 수동으로 DOM을 변경하는 등의 작업을 의미합니다.
- 이 작업을 이펙트라고 부르는 이유는 이 작업들이 다른 컴포넌트에 영향을 미칠 수 있으며, 렌더링 중에는 작업이 완료될 수 없기 때문입니다. 렌더링이 끝난 이후에 실행되어야 하는 작업들입니다.
- 클래스 컴포넌트의 생명주기 함수와 같은 기능을 하나로 통합한 기능을 제공합니다.
- 결국 sideEffect는 렌더링 외에 실행해야 하는 부수적인 코드를 말합니다.
- useEffect()함수는 다음과 같이 사용합니다.
- 첫 번째 파라미터는 이펙트 함수가 들어가고, 두 번째 파라미터로는 의존성 배열이 들어갑니다.
- 의존성 배열은 이펙트가 의존하고 있는 배열로, 배열 안에 있는 변수 중에 하나라도 값이 변경되었을 때 이펙트 함수가 실행됩니다.
- 이펙트 함수는 처음 컴포넌트가 렌더링 된 이후, 그리고 재 렌더링 이후에 실행됩니다.
- 만약 이펙트 함수가 마운트와 언마운트 될 때만 한 번씩 실행되게 하고 싶으면 빈 배열을 넣으면 됩니다. 이 경우 props나 state에 있는 어떤 값에도 의존하지 않기 때문에 여러 번 실행되지 않습니다.

#### useMemo
- useMemo()혹은 Meoized value를 리턴하는 훅입니다.
- 이전 계산값을 갖고 있기 때문에 연산량이 많은 작업의 반복을 피할 수 있습니다.
- 이 훅은 렌더링이 일어나는 동안 실행됩니다.
- 따라서 렌더링이 일어나는 동안 실행되어서는 안 될 작업을 넣으면 안됩니다.
- 예를 들면 useEffect에서 실행되어야 할 사이드 이팩트 같은 것입니다.

#### useRef
- useRdf() 훅은 래퍼런스를 사용하기 위한 훅입니다.
- 래퍼런스란 특정 컴포넌트에 접근할 수 있는 객체을 의미합니다.
- useRef() 훅은 바로 이 레퍼런스 객체를 반환합니다.
- 레퍼런스 객체에는 .current라는 속성이 있는데, 이것은 현재 참조하고 있는 엘리먼트를 의미합니다.
- 


## 4월 3일 강의

3. props의 사용법
- JSX에서는 key-value쌍으로 props를 구성한다
    * Profile 컴포넌트로 name, intoduction, viewCount props를 전달한다.
    * 이때 전달되는 props는 다음과 같은 자바스크립트 객체입니다.
    * JSX에서는 중괄호를 사용하면 JS코드를 넣을 수 있다고 배웠습니다.
    * 다음 코드처럼 props를 통해서 value를 할당 할 수도 있고, 직접 중괄호를 사용하여 할당할 수도 있다.
    * JSX를 사용하지 않는 경우 props의 전달 방법은 createElement()함수를 사용하는 것입니다.
    * createElement()함수의 두번째 매개변수 가 바로 props이다.

컴포넌트 만들기
1. 컴포넌트의 종류
    * 리액트 초기 버전을 사용할 때는 클래스형 컴포넌트를 주로 사용했습니다.
    * 이후 Hook이라는 개념이 나오면서 최근에는 함수형 컴포넌트를 주로 사용합니다.
    * 예전에 작성된 코드나 문서들이 클래스형 컴포넌트를 사용하고 있기 때문에,
    * 클래스형 컴포넌트와 컴포넌트의 생명주기에 관해서도 공부해 두어야 합니다.
2. 함수형 컴포넌트
    * Welcome컴포넌트는 props를 받아, 받은 props중 name키의 값을 "안녕,"뒤에 넣어 반환합니다.
3. 클래스형 컴포넌트
    * Welcome컴포넌트는 React.Component class로 부터 상속을 받아 선언합니다.
4. 컴포넌트 이름
    * 이름은 항상 대문자로 시작
    * 왜냐하면 리액트는 소문자로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문입니다. html tag.
    - 컴포넌트 파일 이름과 컴포넌트의 이름은 같게 합니다.

5. 컴포넌트의 렌더링
    * 렌더링 과정은 다음 코드
    ```
    function Welcome(props) {
        return <h1>안녕, {props.name}</h1>;
    }

    const element = <Welcome name="인제" />;
    ReactDOM.render(
        element,
        document.getElementById('root')
    );
    ```

    - 컴포넌트 합성
        * 컴포넌트 합성은 여러 개의 컴포넌트를 합쳐서 하나의 컴포넌트를 만드는 것입니다.
        리액트는 컴포넌트 안에 또 다른 컴포넌트를 사용할 수 

    - 컴포넌트 추출
        * 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 나눌 수도 있습니다.
        * 큰 컴포넌트에서 일부를 추출해서 새로운 컴포넌트를 만드는 것입니다.
        * 실무에서는 처음부터 1개의 컴포넌트에 하나의 기능만 사용하도록 설계하는 것이 좋습니다.


### state
1. state란?
    * State는 리액트 컴포넌트의 상태를 의미합니다.
    * 상태의 의미는 정상인지 비정상인지가 아니라 컴포넌트의 데이터를 의미합니다.
    * 정확히는 컴포넌트의 변경가능한 데이터를 의미합니다.
    * State가 변하면 다시 렌더링이 되기 때문에 렌더링과 관련된 값만 state에 포함시켜야 합니다.

2. state의 특징
    * 리액트 만의 특별한 형태가 아닌 단지 자바스크립트 객체일 뿐이다.
    ```
        class LikeButton extends React.Component {
            constructor(props) {
                super(props);
            }
            this.state = {
                name: 'choi'
            };
        }
    ```
    * state는 변경은 가능하다고 했지만 직접 수정해서는 안됩니다.

### 생명주기
- 생명주기는 컴포넌트의 생성 시점, 사용 시점, 종료 시점을 나타냄
- constructor가 실행 되면서 컴포넌트가 생성됩니다.
- 생성 직후 componentDIdMount() 함수가 호출됩니다.
- 컴포넌트가 소멸되기 전까지 여러 번 렌더링 합니다.
- 렌더링은 props, setState(), forceUpdate()에 의해 상태가 변경되면 이루어집니다.
- 그리고 렌더링이 끝나면 componentDinUpdate()함수가 호출됩니다.
- 마지막으로 컴포넌트가 언마운트 되면 componentWillUnmount()함수가 호출됩니다.

    


## 3월 27일 강의

JSX의 역할
- JSX는 내부적으로 XML/HTML 코드를 자바스크립트로 변환합니다.
- REACT가 createElement함수를 사용하여 자동으로 자바스크립트로 변환해 줌
- 만일 JS로 작업할 경우 직접 createElement함수를 사용해야 합니다.
```
class Hello extends React.Component {
    reader() {
        retrun <div>Hello {this.props.tomcat}</div>;
    }
}

ReactDOM.reader(
    <Hello toMhat="World"/>,
    document.getElementById("root")
);
```
```
React.createElement(
    type,
    [props],
    [...children]
)
```

JSX의 장점
-코드가 간결해 짐
-가독성이 향상 됨

JSX 사용법
- 모든 자바스크립트 문법을 지원합니다.
- 자바 스크립트 문법에 XML과 HTML을 섞어서 사용
- 아래 코드의 2번 라인처럼 섞어서 사용하는 것입니다.
- 만일 html이나 xml에 자바스크립트 코드를 사용하고 싶으면 {}괄호를 사용
```
const name = "소플";
const element = <h1>안녕, {name}</h1>;

ReactDOM.render(
    element,
    document.getElementByEd('root')
);
```

엘리먼트
1. 엘리먼트의 정의
    - 엘리먼트는 리액트 앱을 구성하는 요소를 의미합니다.
    - 앨리먼트는 리액트 앱의 가장 작은 빌딩 블록들
    - 웹사이트의 경우는 DOM 엘리먼트이며, HTML요소를 의미합니다.

그렇다면 리액트 엘리먼트와 DOM엘리먼트는 어떤 차이가 있을까요?
- 리액트 엘리먼트는 Virtual DOM의 형태를 취하고 있습니다.
- DOM 엘리먼트는 페이지의 모든 정보를 갖고 있어 무겁습니다.
- 반면 리액트 엘리먼트는 변화한 부분만 갖고 있어 가볍습니다.

2. 엘리먼트의 생김새
    - 리액트 엘리먼트는 자바스크립트 객체의 형태로 존재합니다.
    - 컴포넌트(Button 등), 속성(color 등) 및 내부의 모든 children을 포함하는 일반 JS객체입니다.
    - 이 객체는 마음대로 변경할 수 없는 불변성을 갖고 있습니다.

버튼을 나타내기 위한 앨리먼트의 예를 보겠습니다.
```
{
    type: 'button',
    props: {
        color: 'green',
        children: 'Hello, element!'
    }
}
```
내부적으로 자바스크립트 객체를 만드는 역할을 하는 함수가 createElement()입니다.
- 첫 번째 매개변수가 type입니다. 이 곳에 태그가 들어가면 그대로 표현하고, 만일 리액트 컴포넌트가 들어가면 이 것을 분해해 결국 태그로 만들게 됩니다.
- 두 번째 매개변수인 props는 속성을 나타냅니다.

3. 엘리먼트의 측징
리액트 엘리먼트의 가장 큰 특징은 불변성입니다.
즉, 한 번 생성된 엘리먼트의 childrend이나 속성(attributes)을 바꿀 수 없습니다.

엘리먼트 렌더링하기
Root DOM node
다음 html코드는 id 값이 root인 div 태그로 단순하지남 리액트에 필수로 들어가는 아주 중요한 코드입니다.
이 div태그 안에 리액트 엘리먼트가 렌더링 되며, 이 것을 Root DOM node라고 합니다.
```
<div id="root"></div>
```
엘리먼트를 렌더링하기 위해서는 다음과 같은 코드가 필요합니다.
```
const element = <h1>안녕 리액트</h1>;
ReactDOM.renderI
```

렌더링 된 엘리먼트 업데이트하기
- 다음 코드느 tick()함수를 정의하고 있습니다.
- 이 함수는 현재 시간을 포함한 element를 생성해서 root div에 렌더링해줍니다.
- 그런데 라인 12를 보면 setInterval()함수를 이용해서 위에서 정의한 tick()를 1초에 한 번씩 호출하고 있습니다.
- 결국 1초에 한 번씩 element를 새로 만들고 그것을 교체하는 것입니다.
```
function tick(){
    const element = {
        <div>
            <h1>안녕 리액트</h1>
            <h2>현재 시간: {new Date().toLocaleTimeString()}</h2>
        </div>
    };

    ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);
```

컴포넌트
- 2장에서 설명한 바와 같이 리액트는 컴포넌트 기반의 구조를 같습니다.
- 컴포넌트 구조라는 것은 컴포넌트가 모여 큰 컴포넌트를 구성하고, 다시 이런 컴포넌트들이 모여서 전체 페이지를 구성한다는 것을 의미함
- 컴포넌트는 재사용이 가능하기 때문에 전체 코드의 양을 줄일 수 있어 개발 시간과 유지 보수 비용도 줄일 수 있습니다.
- 컴포넌트는 자바스크립트 함수처럼 입력과 출력이 있다는 면에서는 유사합니다.
- 다만 입력은 props가 담당하고, 출력은 리액트 엘리먼트의 형태로 출력됩니다.
- 엘리먼트를 필요한 만큼 만들어 사용한다는 면에서는 객체 지향의 개념과 비슷합니다.

1. Props의 개념
- props는 prop의 준말입니다.
- 이 props가 바로 컴포넌트의 속성입니다.
- 컴포넌트에 어떤 속성, props를 넣느냐에 따라서 속성이 다른 엘리먼트가 출력됩니다.
- props는 컴포넌트에 전달 할 다양한 정보를

2. Props의 특징
- 읽기 전용입니다. 변경할 수 없다는 의미
- 속성이 다른 엘리먼트를 생성하려면 새로운 props를 컴포넌트에 전달하면 됩니다.

Pure함수 vs Impure함수
- Pure함수는 인수로 받은 정보가 함수 내부에서도 변하지 않는 함수입니다.
- Impure함수는 인수로 받은 정보가 함수 내부에서 변하는 함수 입니다.
```
// Pure 함수
// input을 변경하지 않으며 같은 input에 대해서 항상 같은 output을 리턴
function sum(a,b) {
    return a + b;
}
```

```
// inpure 함수
// input을 변경함
function withdray(account, amount) {
    account.total -= amount;
}
```



## 3월 20일 강의
내용
다양한 자바 스크립트 UI 프레임워크 : Stack Overflow Trends

리액트 개념 정리
- 복잡한 사이트를 쉽고 빠르게 만들고, 관리하기 위해 만들어진 것이 리액트
- 다른 표현으로는 SPA를 쉽고 빠르게 만들 수 있도록 해주는 도구

1.2 리액트의 장점
1.  빠른 업데이트와 렌더링 속도
    * 이것을 가능하게 하는 것이 바로 Virtual DOM입니다.
    * DOM이란 XML, HTML 문서의 각 항목을 계층으로 표현하여 생성, 변형, 삭제할 수 있도록 돕는 인터페이스입니다. 이것은 W3C의 표준입니다.
    * Virtual DOM은 DOM 조작이 비효율적인 이유로 속도가 느리기 때문에 고안된 방법입니다.
    * DOM은 동기식, Virtual DOM은 비동기식 방법으로 렌더링을 합니다.
2. 컴포넌트 기반 구조
    * 리액트의 모든 페이지는 컴포넌트로 구성됩니다.
    * 하나의 컴포넌트는 다른 여러 개의 컴포넌트의 조합으로 구성할 수 있습니다.
    * 그래서 리액트의 개발을 하다 보면 레고 블록을 조립나는 것처럼 컴포넌트를 조합해서 웹사이트를 개발하게 됩니다.
3. 재사용성
    * 반복적인 작업을 줄여주기 때문에 생산성을 높여 줍니다.
    * 또한 유지보수가 용이합니다.
    * 재사용이 가능 하려면 해당 모듈의 의존성이 없어야 합니다.
4. 든든한 지원군
 메타(구 페이스북)에서 오픈소스 프로젝트로 관리하고 있어 계속 발전되고 있습니다.
5. 활발한 지식 공유 & 커뮤니티
6. 모바일 앱 개발기능
    * 리액트 네이티브라는 모바일 환경 UI프레임워크를 사용하면 크로스 플랫폼(cross-platform) 모바일 앱을 개발할 수 있습니다.
 1.3 리액트의 단점
 1. 방대한 학습량
    * 자바스크립트를 공부한 경우 빠르게 학습 가능
 2. 높은 상태 관리 복잡도

## 3월 13일 강의
내용
```
```
~~내용~~
