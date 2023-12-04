# Tutorial

## 1. npm 초기화
`npm init -y`

## 2. typescript 설치
`npm install --save-dev typescript`

- typescript 패키지와 cli인터페이스인 ts-node 패키지와 구분하는 것이 좋다.
- ts-node는 typescript를 컴파일하지 않고, 간단히 실행할 수 있게 해주므로
  - 컴파일 전에 코드를 실행해보고 싶을때 사용한다. 
  - 컴파일 전, 후 가리지 않고 자주 확인하므로 마치 묶음처럼 사용되는 경우가 많다.

## 3. typescript config 파일 설정
`npx tsc --init`

- tsconfig.json 파일이 생성된다.

## 4. babel 설치
`npm install --save-dev @babel/core @babel/preset-env @babel/preset-react @babel/preset-typescript`
  
  - typescript로 개발을 착수하고, React를 사용하고, 그다음 babel을 통해 컴파일하는 일련의 '절차'에 고려해 설치했다.
  - `@babel/core`는 Babel 컴파일러의 핵심 패키지
  - `@babel/preset-env`는 환경에 맞게 ECMAScript 2015+ 버전의 코드를 변환해주는 Babel 프리셋(최종형태)
  - @babel/preset-react는 React의 JSX 문법을 JavaScript로 변환해주는 Babel 프리셋
  - @babel/preset-typescript는 TypeScript 코드를 JavaScript로 변환해주는 Babel 프리셋

여기서 컴파일하는 주체와 목적이 중요한데 쉽게 헷갈리는 부분은 다음과 같다.
  - typescript를 통해 컴파일 하지 않을 예정이다.
  - typescript는 React를 사용하기 위해 설치했다.
  - React는 Javascript의 라이브러리이다. 
  - typescript + React로 개발을 착수하고 최종형태는 babel이 컴파일하게 되는 구조이다.
  - **babel 컴파일러와 typescript 컴파일러는 역할은 같지만 해당 예제프로젝트에서는 typescript 컴파일러를 사용하지 않는다.**

## 5. babel config 파일 생성
디렉토리에서 .babelrc, babel.config.js 둘중 하나를 선택해서 생성

  - 예제상으로는 지난번과 다르게 rc파일을 생성했다.
  - 담겨진 내용은 preset(프리셋), pre set 이므로 말그대로 사전 설정을 뜻한다.
```
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react",
    "@babel/preset-typescript"
  ]
}
```
  - 해당 설정에서 "presets"라는 key의 배열 순서가 상당히 중요한데,
  - typescript를 사용하고 React를 사용하고 babel을 통해 컴파일하는 구조이므로
  - typescript를 먼저 컴파일하고 React를 컴파일하고 babel을 통해 최종 컴파일을 하게 된다.
  - typescript를 가지고 React를 작성하고, 작성된 React는 preset-env를 통해 최종 컴파일된다.

