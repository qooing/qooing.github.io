---
title: "[React 정복기 #02] 5분 완성! Vite로 가장 빠른 리액트 개발 환경 구축하기"
date: 2026-02-13T09:00:00+09:00
draft: false
categories: ["React Tutorial"]
tags: ["React", "JavaScript", "Virtual DOM", "Component", "Declarative", "Frontend", "Web Development"]
author: "Qooing"
description: "Vite로 React 개발환경을 설정하고, React 앱을 만들어봅니다."
---

![Vite](/images/react/vite.png)

안녕하세요, **Qooing**입니다! 👋

지난 시간에는 "리액트가 무엇이고, 왜 써야 하는가?"에 대한 근본적인 철학을 알아보았습니다.
이제 이론은 충분합니다! 오늘부터는 본격적으로 우리가 만들 **'Smart To-Do Planner'** 를 위한 작업실을 꾸며보겠습니다.

"개발 환경 설정... 듣기만 해도 머리 아픈데요?"
걱정 마세요. 오늘 소개할 **Vite(비트)** 라는 도구를 사용하면 컵라면이 익기도 전에 모든 세팅이 끝납니다. 자, 터미널을 열고 바로 시작해 볼까요?

---

## 1. 프론트엔드 개발의 엔진: Node.js 설치

리액트 개발을 하려면 가장 먼저 **Node.js**가 컴퓨터에 깔려 있어야 합니다.
*"어? 저는 프론트엔드(화면) 개발을 할 건데, 왜 백엔드(서버) 기술인 Node.js를 깔아야 하죠?"*

리액트는 우리가 작성한 코드를 브라우저가 이해할 수 있도록 압축하고, 변환하고, 하나로 묶어주는 작업(빌드)이 필요합니다. 이 복잡한 공장을 돌려주는 '엔진' 역할을 Node.js가 해주기 때문입니다.

### **🛠️ 설치 및 확인 방법**

1. 터미널(Mac은 Terminal, Windows는 명령 프롬프트나 PowerShell)을 엽니다.
2. 아래 명령어를 입력해 보세요.
```bash
node -v

```

3. `v24.13.0` 처럼 버전 숫자가 나온다면 이미 설치되어 있는 것입니다. 통과!
4. 만약 "명령어를 찾을 수 없습니다"라는 에러가 뜬다면, [Node.js 공식 홈페이지](https://nodejs.org/ko)에 접속하여 **LTS 버전(안정적이고 가장 많이 쓰이는 버전)** 을 다운로드해 설치해 주세요.

---

## 2. 생산성 200% 향상: VS Code 확장 프로그램 세팅

본격적인 프로젝트 생성에 앞서, 우리의 주력 무기인 **VS Code(Visual Studio Code)** 를 튜닝해 보겠습니다. 이 두 가지만 설치해도 코딩이 훨씬 즐거워집니다.
![prettier](/images/react/vscode_prettier_plugin.png)
![ES7+ React/Redux/React-Native snippets](/images/react/vscode_es7_react_redux_reactnative_snippets_plugin.png)

* **Prettier - Code formatter:** 띄어쓰기, 줄바꿈 등 코드를 저장할 때마다 아주 예쁘게 자동 정렬해 줍니다. (필수 중의 필수!)
* **ES7+ React/Redux/React-Native snippets:** `rfce`라는 마법의 단어 네 글자만 치면, 리액트 컴포넌트의 기본 뼈대를 1초 만에 자동으로 완성해 주는 도구입니다.

---

## 3. 프로젝트 생성: 왜 CRA 대신 Vite인가?

예전에는 리액트를 시작할 때 `Create React App (CRA)`이라는 도구를 썼습니다. 하지만 프로젝트 덩치가 커지면 서버를 켜는 데만 수십 초가 걸리는 치명적인 단점이 있었죠.

그래서 최근에는 프랑스어로 '빠르다'는 뜻을 가진 **Vite**가 대세로 자리 잡았습니다. 정말 빛의 속도로 켜집니다.

### **🛠️ 5분 만에 프로젝트 띄우기**

터미널을 열고, 프로젝트를 만들고 싶은 폴더(예: 바탕화면)로 이동한 뒤 아래 명령어를 차례대로 입력하세요.

```bash
# 1. 'todo-app'이라는 이름의 리액트 프로젝트를 생성합니다.
npm create vite@latest todo-app -- --template react

# 2. 방금 만든 프로젝트 폴더 안으로 이동합니다.
cd todo-app

# 3. 프로젝트 구동에 필요한 부품(의존성 패키지)들을 설치합니다.
npm install

# 4. 드디어 개발 서버를 실행합니다!
npm run dev

```

#### **💡 명령어 해설**

* `npm install`을 치면 `node_modules`라는 엄청나게 무거운 폴더가 생깁니다. 이건 리액트가 돌아가는 데 필요한 외부 도서관(라이브러리)들을 몽땅 다운받아 온 것입니다.

터미널에 `http://localhost:5173/` 이라는 로컬 주소가 뜨면 성공입니다!
`Ctrl` (또는 `Cmd`) 키를 누른 채로 해당 주소를 클릭해 보세요.

![Vite+React](/images/react/hello_react.png)

---

## 4. 폴더 구조 파헤치기 & 첫 코드 수정

VS Code로 우리가 만든 `todo-app` 폴더를 열어보세요. 복잡해 보이지만, 지금은 딱 3가지만 알면 됩니다.

1. **`index.html`**: 웹사이트의 뼈대입니다. 여기에 `<div id="root"></div>`라는 빈 상자가 하나 있는데, 리액트가 그린 모든 화면이 이 상자 안으로 들어갑니다.
2. **`src/main.jsx`**: 리액트의 진입점입니다. "App이라는 그림을 저 root 상자 안에 그려라!"라고 명령을 내리는 곳이죠.
3. **`src/App.jsx` ⭐️ (가장 중요)**: 우리가 실질적으로 코드를 짜고 화면을 꾸밀 메인 스케치북입니다.

### **🛠️ 나만의 앱으로 바꿔보기**

`src/App.jsx` 파일을 열어서, 기존 코드를 싹 지우고 아래처럼 작성해 보세요.

```jsx
// src/App.jsx

import React from 'react';
import './App.css'; // 기본 스타일 적용

function App() {
  return (
    <div className="container">
      <h1>안녕, 리액트! 🚀</h1>
      <p>오늘부터 Smart To-Do Planner를 만듭니다.</p>
    </div>
  );
}

export default App; // 다른 곳에서 이 컴포넌트를 쓸 수 있게 내보냄

```

코드를 작성하고 **저장(Ctrl + S)** 을 누르는 순간! 브라우저를 다시 새로고침할 필요도 없이 화면이 즉시 바뀐 것을 볼 수 있습니다.

![Hello react](/images/react/hello-react-2.png)

개발자가 코드를 수정하면 즉각적으로 화면에 반영해 주는 기능, 이것이 바로 Vite가 자랑하는 강력한 **HMR(Hot Module Replacement)** 기능입니다. 코딩할 맛이 나죠?

---

## 🚀 마치며

축하합니다! 완벽한 개발 환경을 세팅하고 나만의 첫 번째 리액트 화면까지 띄우셨습니다.

오늘 우리는:

1. **Node.js**로 코드를 돌릴 엔진을 준비했고
2. **Vite**를 이용해 눈 깜짝할 새에 프로젝트를 세팅했으며
3. **App.jsx**를 수정해 화면이 실시간으로 변하는 마법을 경험했습니다.

이제 도화지는 준비되었습니다. 다음 시간에는 리액트만의 독특한 문법, HTML과 자바스크립트의 혼종인 **JSX 문법**에 대해 완벽하게 파헤쳐 보겠습니다.

다음 포스팅도 기대해 주세요! 

