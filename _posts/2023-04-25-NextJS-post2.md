---
layout: post
title:  "[Next.js|프로젝트] 2. Next.js와 React.js의 차이"
date:   2023-04-25
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### 정적 랜더링 ( pre-rendering )

* next.js는 페이지들이 미리 랜더링 된다. 실제 HTML을 불러온다. 
* react.js는 client side render로 브라우저가 자바스크립를 가져와서 모든 UI를 만든다. 

따라서 속도가 빠르지 않은 상태에서 페이지를 불러오면 HTML -> 흰 화면 -> 자바스크립트 요청 -> 서서히 UI가 나타나는 현상이 일어난다. 

모든 것을 fetch한 후에야 화면이 보인다는 것이다. 
* react.js와 next.js는 API를 불러오는 과정은 둘 다 느릴 수 있지만, 처음 페이지를 랜더링 할 때, UI가 나타나는 속도에서 차이가 발생한다. 
