# Lesson06-Loops

1. 스크립트 내부에 `people`이라는 객체배열을 준비해주자

```html
<script>

let  people = [

{name :  'yoshi',belt_colour:'black',age:25,id:1},

{name :  'mario',belt_colour:'blue',age:45,id:2},

{name :  'luigi',belt_colour:'orange',age:35,id:3}

];

</script>
```
- id값은 스벨트 루프 내에서 활용하기 간편할 용도로 이용할 것이다

2. 간단하게 각 배열 요소값을 출력해보자

```html
<main>

<div>

<h4>{people[0].name}</h4>

<p>{people[0].belt_colour}</p>

</div>

<div>

<h4>{people[1].name}</h4>

<p>{people[1].belt_colour}</p>

</div>

<div>

<h4>{people[2].name}</h4>

<p>{people[2].belt_colour}</p>

</div>

</main>
```

그러면 당연히 화면에서는 각 인덱스에 해당되는 사람의 이름과 벨트색상 값을 보여줄 것이다

3. `2`를 조금 더 효율적으로 진행하기 위해서 반복문을 진행해주기 `{#each 복수(다량데이터변수) as 단수(복수 내 데이터 각각)} ~ {/each}`

이는 자바의 향상된 for 문과 같다

```java
for(Person p : people)
```

```html
<main>
{#each  people  as  person}

<h4>{person.name}</h4>

<p>{person.age}</p>

<p>{person.belt_colour}</p>

{/each}
</main>
```

이렇게 되면 아까보다 더 효율적으로 많은 데이터에 접근해서 화면에 보여줄 수 있는 것을
확인해볼 수 있다

화면에는 아래처럼
```
yoshi

25

black

mario

45

blue

luigi

35

orange
```
가 보일 것이다

## Advanced-Unique key `id` 활용하기

앞서 id값을 활용해서 간편하게 이용해보자고 언급했다
이를 `{#each 복수 as 단수 (단수.unique key)}{/each}` 로 접근해보자
```html
<main>
{#each  people  as  person(person.id)}

<h4>{person.name}</h4>

<p>{person.age}</p>

<p>{person.belt_colour}</p>

{:else}

<p>There are no people to show...</p>

{/each}
</main>
```

이렇게 된다면, people 배열이 비어있으면(empty) "There are.."가 보여지게 된다
이는 svelte가 unique key와 함께 DOM 내부 요소를 인식할 수 있게 되기 때문에
각 person에 접근할 수 있기 때문이다(https://svelte.dev/tutorial/keyed-each-blocks)



