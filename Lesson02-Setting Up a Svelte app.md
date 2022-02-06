# Lesson02-Setting Up a Svelte app

## 1. Start

VS Code에서 진행해보자(터미널)
[svelte 환경 구축](https://velog.io/@thyoondev/Svelte-VSCode%EC%97%90%EC%84%9C-%EC%8A%A4%EB%B2%A8%ED%8A%B8-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0)
1. 먼저 degit을 설치하고
```
> npm install -g degit
```

`-g` : global 옵션

2. bundler를 선택해서 받자

- [Rollup bundler](https://github.com/sveltejs/template)
- [Webpack bundler](https://github.com/sveltejs/template-webpack)
중 하나 선택

영상에서는 `degit sveltejs/template myproject` 와 같이 진행하고 있어서, 나는 Rollup bundler를 선택해서 진행해서 동일하게 진행했다

```
npx degit sveltejs/template svelte-app
cd svelte-app
```

3. 모듈설치
```
npm install
```

4. 개발환경으로 실행해주기(Rollup)

```
npm run dev
```

```
PS D:\VirtualBox_share_folder\svelte\lesson2\svelte-app> npm run dev

> svelte-app@1.0.0 dev
> rollup -c -w

rollup v2.67.0
bundles src/main.js → public\build\bundle.js...
LiveReload enabled
created public\build\bundle.js in 579ms

[2022-02-06 11:12:19] waiting for changes...

> svelte-app@1.0.0 start
> sirv public --no-clear "--dev"


  Your application is ready~! 🚀

  ➡ Port 8080 is taken; using 11029 instead

  - Local:      http://localhost:11029
  - Network:    Add `--host` to expose

────────────────── LOGS ──────────────────
```

이렇게 진행하고 나서 VS code 프로젝트 구조를 보면 아래와 같은 템플릿에서 제공되는 구조 및 파일들로 구성되어 있는 것을 확인해볼 수 있다

![svelte rollup template](https://github.com/hy6219/svelte_study/blob/main/svelte_rollupbundler_template.PNG?raw=true)

- `package-lock.json` : 필요한 의존성들을 모두 관리, 추적(dependencies)

다시한번 개발환경으로 시작시켜보면 아래와 같은 모두의 시작, "hello world"가 화면에 보인다
![](https://github.com/hy6219/svelte_study/blob/main/start_with_svelte.PNG?raw=true)

이렇게 보여지는 것은 App.svelte에 존재하는 내용 및 스타일 부분의 영향이다!

그리고 스프링부트에서는 변경되는 기능이 있으면 재시작해서 확인하고는 했는데,
아래처럼 `Hello {name}!` 를 `Hello {name} svelte!`  로 바꾸면 화면에 바로 보여지는 것을 확인해볼 수 있다!😍(귀엽다)

```svelte
<script>

export  let  name;

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

