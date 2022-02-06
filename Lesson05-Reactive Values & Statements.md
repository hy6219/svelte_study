# Lesson05-Reactive Values & Statements

## 1. Practice01- $: value3 = `${value1} {value2}`

1. 기존의 name 변수 대신 성(lastname)과 이름(firstname)으로 이름을 구성해보자
```html
<script>

let  firstname = "jisoo";//이름

let  lastname = "jeong";//성

(중략)
</script>
```

2. 사용자로부터 성과 이름에 대해서 각각을 입력받고 표시할 input 을 준비

```html
<script>

let  firstname = "jisoo";//이름

let  lastname = "jeong";//성

let  beltColour = "black";

let  btnClickCnt = 0;

  

const  handleClick = ()=>{

++btnClickCnt;

beltColour = btnClickCnt%2==1?"black":"blue";

};

  

const  handleInput = (e)=>{

beltColour = e.target.value;

};

</script>

  

<main>

<h1>{firstname}  {lastname}</h1>

<p  style="color:{beltColour}">{beltColour} belt</p>

<!--사용자 입력받기-->

<!--value,bind:value : 양방향 바인딩-->

<input  type="text"  bind:value="{firstname}">

<input  type="text"  bind:value = "{lastname}">

<input  type="text"  bind:value="{beltColour}">

</main>
```

3. `reactive value`로써 fullname을 준비하는데, 이는 [데이터 값/상태에 따라 즉각적으로 변화하는 값](https://svelte.dev/tutorial/reactive-declarations)을 의미한다

- 먼저 `$: 변수명 = ~` (js template literal 등을 활용해서 그 값을 넣어주어도 좋다) 를 스크립트 내부에 넣어주자

```html
<script>
$: fullname = `${firstname}  ${lastname}`;
</script>

```
- 기존에 h1 태그 내부를 아래와 같이 변경해주자
```html
<main>
<h1>{fullname}</h1>
</main>
```
이렇게 되면, 값(상태)이 변경됨에 따라 즉각적으로 적용되는 것도, 그리고 그 적용된 값을 활용해서 복합적인 작업을 진행할 수 있는 것도 확인해보았다(fullname=firstname+lastname)

## 2. Practice02 - `$: console.log(~)`

이번에는 console.log로 시도해보자
```html
<script>
$: console.log(beltColour);
</script>
```
![](https://github.com/hy6219/svelte_study/blob/main/reactive_values_statements_log.PNG?raw=true)

그러면 위와 같이 입력한 컬러문자열에 따라, 지워지는 상태에 따라 로그가 출력되는 모습을 확인해볼 수 있다

## 3. Practice03- code block

- reactive variable을 응용해서 여러 작업을 하나로 묶어서 시도해볼 수도 있다
```html
<script>
$:{

console.log(`beltColour: ${beltColour}`);

console.log(`fullname : ${fullname}`);

}
</script>
```

그리고 이렇게 되면 `모두(both)가 아닌, 위의 두 변수 중 하나만 변경되면  코드블럭 내 코드가 실행`되어 콘솔에 로그가 찍히는 모습을 확인해볼 수 있다

