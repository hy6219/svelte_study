# Lesson03 - Svelte Basics : 데이터를 넣는 방법, 이벤트를 다루는 방법을 맛보기!

- App.svelte : 스벨트의 루트 컴포넌트
(컴포넌트 , 가상 DOM 등 개념적인 부분은 차차 정리하자)

## 1. Svelte 컴포넌트 구성

`App.svelte`를 보면 스벨트의 컴포넌트 구성이 어떻게 되어 있는지 흐름을 알 수 있다

- script : 로직(js)
- main : html
- style : css

## 2. Main.js && 화면에 보여지는 값을 적용하는 방법

- 애플리케이션을 시작하게 하는 역할
```js
import  App  from  './App.svelte';

  

const  app = new  App({

target:  document.body,

props: {

name:  'world'

}

});

  

export  default  app;
```
- App.svelte를 `App` 이라는 객체에 담아두고
- `target:document.body` 에서 App.svelte의 `<main></main>` 부분의 내용을 읽어들여와서 index.html의 body 태그에 매칭해주고
- `props` 속성 하위에 `App.svelte 에서 사용되는 name(App.svelte - export name)에 "world" 값을 매칭`(만약, App.svelte에서 `export let name`이 아닌 `let name`으로 두었다면, `undefined` 로 보여질 것 - "A")
```svelte
<script>

let  name;

</script>

  

<main>

<h1>Hello {name} svelte!</h1>

<p>Visit the <a  href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

</main>

  

<style>

main {

text-align: center;

padding: 1em;

max-width: 240px;

margin: 0  auto;

}

  

h1 {

color: #ff3e00;

text-transform: uppercase;

font-size: 4em;

font-weight: 100;

}

  

@media (min-width: 640px) {

main {

max-width: none;

}

}

</style>
```
- 위에서 설정된 json 객체를 추출해줌

- 스벨트가 한번 실행되면 /public/build 하위에 bundle.js, bundle.css 등으로 생겨나는데 이러한 파일들이 /public/index.html 내부에서 연결되어 있어서 화면에 렌더링될 수 있는 것이다!!

🤠 위의 "A" 부분에서 export를 지웠는데, 그러면 만약 값을 넣어주고 싶다면? 아래처럼 `script 내부에서 값을 지정해주고, main 태그 내부에서 {변수명}`으로 지정해준다면 어떻게 될까?

```svelte
<script>

let  name = "world!";

</script>

  

<main>

<h1>Hello {name} svelte!</h1>

<p></p>

<p>Visit the <a  href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

</main>

  

<style>

main {

text-align: center;

padding: 1em;

max-width: 240px;

margin: 0  auto;

}

  

h1 {

color: #ff3e00;

text-transform: uppercase;

font-size: 4em;

font-weight: 100;

}

  

@media (min-width: 640px) {

main {

max-width: none;

}

}

</style>
```

그러면 화면에 "HELLO WORLD! SVELTE!"라고 보이는 것을 알 수 있다!

마찬가지로, App.svelte 내부에서 `let 변수=값`을 하나 더 추가하고, `<main></main> 내부에서 그 변수명을 {변수명}처럼 언급`해주면 그 변수에 할당된 값이 화면에 출력되는 것을 볼 수 있다

아래에는 위의 헬로월드 밑에 "black belt"가 표시되는 것을 확인해볼 수 있다

```svelte
<script>

let  name = "world!";

let  beltColour = "black";

</script>

  

<main>

<h1>Hello {name} svelte!</h1>

<p>{beltColour} belt</p>

<p>Visit the <a  href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

</main>

  

<style>

main {

text-align: center;

padding: 1em;

max-width: 240px;

margin: 0  auto;

}

  

h1 {

color: #ff3e00;

text-transform: uppercase;

font-size: 4em;

font-weight: 100;

}

  

@media (min-width: 640px) {

main {

max-width: none;

}

}

</style>
```

## 3. 버튼 클릭 이벤트 맛보기

1. `<main></main> 내부에 <button></button> 추가`

```svelte
<main>

<h1>Hello {name} svelte!</h1>

<p>{beltColour} belt</p>

<p>Visit the <a  href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

<button>update belt colour</button>

</main>
```
2. `1`에서 추가한 버튼 내부에 `on:click={함수명}`을 추가해주기
```svelte
<main>

<h1>Hello {name} svelte!</h1>

<p>{beltColour} belt</p>

<p>Visit the <a  href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

<button  on:click="{handleClick}">update belt colour</button>

</main>
```

3. 클릭 이벤트를 핸들링할 함수를 `<script></script>` 내부에 준비해주기

```svelte
<script>

let  name = "world!";

let  beltColour = "black";

  

const  handleClick = ()=>{

beltColour = "orange";

};

</script>

  

<main>

<h1>Hello {name} svelte!</h1>

<p>{beltColour} belt</p>

<p>Visit the <a  href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

<button  on:click="{handleClick}">update belt colour</button>

</main>

  

<style>

main {

text-align: center;

padding: 1em;

max-width: 240px;

margin: 0  auto;

}

  

h1 {

color: #ff3e00;

text-transform: uppercase;

font-size: 4em;

font-weight: 100;

}

  

@media (min-width: 640px) {

main {

max-width: none;

}

}

</style>
```
위와 같이 진행해주면 아래처럼 버튼을 클릭했을 때 `black belt`라고 되어 있던 텍스트가 `orange belt`로 변경되는 모습을 확인해볼 수 있다

![Svelte 클릭 이벤트😍](https://github.com/hy6219/svelte_study/blob/main/svelte_basics_click_event.gif?raw=true)

이러한 흐름이 스벨트의 구문이다!(syntax)

