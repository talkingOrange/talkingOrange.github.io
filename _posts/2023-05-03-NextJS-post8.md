---
layout: post
title:  "[Next.js|프로젝트] TailwindCss 적용하기 "
date:   2023-05-03
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### Installation

참고 사이트 : https://tailwindcss.com/docs/installation

1. tailwindcss를 설치해준다. 

`npm install -D tailwindcss`

2. package-lock.json 에 추가되었는지 확인해준다. 

3. tailwind.config.js가 추가되었는지 확인하고, content 문구가 있는지 확인한다.

```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

4. styles/global.css 파일에 다음 문구를 붙여준다.

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### tailblocks 이용

참고 사이트 : https://tailblocks.cc/

1. 사이트에 방문하여 원하는 스타일을 선택하고 css보기를 누른다.

2. css를 원하는 페이지의 return 값에 넣어준다.


### 결과물

![image](https://user-images.githubusercontent.com/88815795/235819475-efb3732d-6da5-43ce-9266-475fdbd93e95.png)


