# Lesson 04- User Input & Data Binding

😁 강의가 설명도 쉽고 재생시간도 짧아서 입문하기 너무 좋고 재미있는 강의인것 같다!
혹시 스벨트 입문용 강의를 찾으신다면 [The Net Ninja](https://youtu.be/n8Kk7uvsx9A) 님 강의 강추!! 😀

저번 스벨트 강의에서 맛보기를 하면서 느낀거지만, 세상은 넓고, 엄청난 분도 많은 것 같다. 그리고 스벨트 아직까지 재미있는 것 같다!(아직 깊게 파고들지 않은 1인이라서 그런 것일 가능성이 매우매우 높을 것 같다)

## 1. 사용자로부터 입력받기

1. `App.svelte`에서 `<main></main>` 부분에 `input` 태그를 추가해주자

```svelte
<main>

<h1>Hello {name}!</h1>

<p>{beltColour} belt</p>

<button  on:click="{handleClick}">update belt colour</button>

<!--사용자 입력받기-->

<input  type="text">

</main>
```

2. 이번에는 입력에 따른 이벤트를 핸들링해주기 위해서 `on:input` 을 맛보자

```svelte
<main>

<h1>Hello {name}!</h1>

<p>{beltColour} belt</p>

<button  on:click="{handleClick}">update belt colour</button>

<!--사용자 입력받기-->

<input  type="text"  on:input="{handleInput}">

</main>
```
3. (메서드 내용은 변경가능)handleInput은 이벤트 파라미터를 받아서 진행하는데, 지금은 이 메서드가 붙은 곳이 input:text이기 때문에, 이점을 이용해서 입력값을 가져오고!! 그 값을 beltColour에 넣어주도록 해보자

```svelte
<script>
const  handleInput = (e)=>{

beltColour = e.target.value;

};
</script>
```
그러면 아래와 같이 사용자가 입력하는 값에 따라 화면에 보다 역동적으로 표시되는 것을 확인해볼 수 있다

![Svelte-User Input](https://github.com/hy6219/svelte_study/blob/main/svelte_user_input.gif?raw=true)


## 2. two-way binding

위에서의 결함은 버튼을 눌렀을 때, input 부분에 값이 표시되지 않는 점인데
이번에는 이를 값이 변경될때마다 보다 역동적으로 input 요소에도 내용이 표시될 수 있도록
진행해보도록 하겠다

1️⃣ `value 옵션 활용`
1. input 태그에 `value={적용해줄(추적할) 값이 담긴 변수}` 옵션 추가

```svelte
<main>

<h1>Hello {name}!</h1>

<p>{beltColour} belt</p>

<button  on:click="{handleClick}">update belt colour</button>

<!--사용자 입력받기-->

<input  type="text"  on:input="{handleInput}"  value="{beltColour}">

</main>
```
그러면 이제는 버튼을 누를 때마다 변경된 값도 input 부분에 표시되는 것을 확인해볼 수 있다!

2️⃣ `bind:value` 옵션 활용

이번에는 `bind:value` 옵션을 활용해서 양방향 바인딩을 진행해보자
```svelte
<main>

<!--(중략)-->
<input  type="text"  bind:value="{beltColour}">

</main>
```

![bind:value, two-way binding](https://github.com/hy6219/svelte_study/blob/main/svelte_value_bindvalue_two-way-binding.gif?raw=true)

그러면 이번에는 beltColour, 처음에 있었던 input, 버튼이 모두 값이 동기화되는 것을 확인해볼 수 있다

상황에 따라서는 처음에 접했던 one-way binding을 사용하기도 하지만, 지금처럼 two-way binding을 사용하기도 한다

## 3. 입력된 값에 따라 스타일 변경하기

이번에는 사용자로부터 받은 입력값이나 버튼클릭으로 인해 변경된 beltColour값에 따라 스타일을 변경해보자
```html
<p  style="color:{beltColour}">{beltColour} belt</p>
```
```svelte
<main>

<h1>Hello {name}!</h1>

<p  style="color:{beltColour}">{beltColour} belt</p>

<button  on:click="{handleClick}">update belt colour</button>

<!--사용자 입력받기-->

<!--value : 양방향 바인딩-->

<input  type="text"  on:input="{handleInput}"  value="{beltColour}">

<input  type="text"  bind:value="{beltColour}">

</main>
```

그러면 입력한 색상이름에 맞게 "{beltColour} belt" 부분의 색상이 변경되는 것을 확인해볼 수 있다
