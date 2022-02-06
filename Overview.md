# Svelte Overview

## 1. What is svelte?

- 반응형 웹 애플리케이션 및 인터페이스를 생성하는 컴파일러
- 웹사이트의 작은 파트 혹은 전체에 사용될 수 있음(SPA; Single Page Application)

## 2. 그래서 Vue, React 등등과 같은 프레임워크와 다른 점이 무엇인데?

- 스벨트는 `프레임워크가 아닌, 컴파일러`
- 빌드 단계에서 코드를 컴파일해서 페이지에 바닐라 자바스크립트로 작성된 단일 번들 bundle.js에 넣어줌
- 다른 별도의 라이브러리나 스크립트가 실행에 필요하지 않음
- 종종 결과들이 웹사이트에서 더 빠르게 렌더링될 수 있음

## 3. 확인해야 할 부분!!

1. 선수지식
- HTML
- CSS
- JS
2. 사전 설치
- Node.js 버전 8이상 설치💥💥💥💥💥💥💥
(Node.js를 따로 공부할 필요까지는 없고, 설치만 해도 됨)

[Let's Move to download!](https://nodejs.org/en/download/)

** ENOENT: no such file or directory, open 'D:\VirtualBox_share_folder\svelte\
lesson2\package.json'

▶ WebStorm 터미널에서 / 혹은 vs code 터미널에서

```
PS D:\VirtualBox_share_folder\svelte\lesson2> npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (lesson2) save
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to D:\VirtualBox_share_folder\svelte\lesson2\package.json:

{
  "name": "save",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
}


Is this OK? (yes)
npm notice
npm notice New major version of npm available! 7.20.0 -> 8.4.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v8.4.1
npm notice Run npm install -g npm@8.4.1 to update!
npm notice

removed 223 packages, changed 19 packages, and audited 39 packages in 5s

1 moderate severity vulnerability

To address all issues, run:
  npm audit fix

Run `npm audit` for details.
PS D:\VirtualBox_share_folder\svelte\lesson2> npm -v
8.4.1

```
위와 같이 npm init 후 npm install을 진행!
https://xenostudy.tistory.com/520 (package.json 생성은 npm init!)

 
