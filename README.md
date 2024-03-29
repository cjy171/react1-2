# 최진영 202230337

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
