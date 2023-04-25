---
layout: post
title:  "[Next.js|프로젝트] style"
date:   2023-04-25
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### 1. HTML태그 내부에 style 설정

```
<Link style={{}} / >
```
### 2. modules 사용하기

* FILENAME.module.css 파일 create
* css 코드를 작성
* 사용하고자 하는 .js / .tsx 파일에서 `import styles from "./FILENAME.module.css` 해준다.
*  html 태그에 `className={styles.클래스}`

+)  html 태그에 className을 설정해주면, 브라우저에는 태그들별 무작위 이름으로 설정된다.

즉, 클래스 이름의 충돌을 막아준다.

[ 단 점 ] 파일을 두 개 생성해야한다. className을 직접 찾아야한다.

### 3. styled jsx

* only NextJS

```
<style jsx>{`nav{background-color: black;}`}</style>
```

* import 할 필요도 없고 return 속에서 사용 가능하다. 
* 스타일의 적용 범위를 오직 해당 컴포넌트 내부로 한정한다.

```
 <nav>
      <Link href="/" className={router.pathname === "/" ? "active" : ""}>
        Home
      </Link>
      <Link
        href="/about"
        className={router.pathname === "/about" ? "active" : ""}
      >
        about
      </Link>
      <style jsx>
        {`
        nav{background-color: tomato; }
          .active {
            background-color: red;
            color: pink;
            text-decoration: none;
          }
        `}
      </style>
    </nav>
```

이런 식으로 코드를 작성하게 될 경우, nav 태그의 background-color는 바뀌지만 .active 클래스에 따른 스타일 변화가 일어나지 않는다.

이유는 style jsx에서 지정한 클래스 이름은 최종 렌더링된 HTML 코드에 적용되는 고유한 해시 클래스 이름으로 대체돼서 Link 컴포넌트의 className 속성을 변경하여도 해당 클래스의 스타일이 적용되지 않을 수 있다.

따라서 a태그에 직접 style class를 넣어주면 되지만, 

최신 next.js에서는 Link 내부에 a 태그를 자동으로 넣어주기 때문에 사용할 수가 없다.

따라서 문제를 해결하려면 Link 컴포넌트의 legacyBehavior prop을 사용하여 a 태그를 사용할 수 있도록 설정하면 된다. 

이 방법은 Next.js의 이전 버전과 호환되도록 제공되며, 최신 버전에서는 사용하지 않는 것이 좋다고한다...

```
import Link from "next/link";
import { useRouter } from "next/router";

export default function NavBar() {
  const router = useRouter();
  return (
    <nav>
      <Link href="/" legacyBehavior>
        <a className={router.pathname === "/" ? "active" : ""}>Home</a>
      </Link>
      <Link href="/about" legacyBehavior>
        <a className={router.pathname === "/about" ? "active" : ""}>about</a>
      </Link>
      <style jsx>
        {`
          nav {
            background-color: tomato;
          }
          .active {
            color: pink;
            text-decoration: none;
          }
        `}
      </style>
    </nav>
  );
}
```

이렇게 코드를 작성해주면

![image](https://user-images.githubusercontent.com/88815795/234188423-a5c33d0f-436f-4a04-bb57-5bac9c6e38f3.png)
![image](https://user-images.githubusercontent.com/88815795/234188621-308fdf61-b94b-451f-8def-fd52a3ec3d30.png)

잘 작동된다~

### 4. Global style 설정하기

* `<style jsx global>` 로 설정하기
* App component, 모든 페이지를 랜더링하게하는 기본 프레임워크를 커스터마이징한다. 
 - pages폴더 하위에  _app.js를 만든다. (about랜더링 전에 app.js를 랜더링한다.)
 
 ```
 export default function App({Component, pageProps}){
 return 
   <div>
    <NavBar />
    <Comonent {...pageProps} / >
    <style jsx global>{`
      a{
        color: white;
      }</style>
   </div>;
 
 }
 ```
 
 이렇게 작성하면, Component 자리에 우리가 pages에 만든 파일들을 넣어 랜더링하게 된다. 
 
* styles 파일에 존재하는 global css 파일에 커스텀을 통해 아래의 코드마저도 지울 수 있다.
* _app.tsx에 `import "../styles/globals.css";` 해주면 적용이 된다. 

```
<style jsx global>{`
      a{
        color: white;
      }</style>
```

