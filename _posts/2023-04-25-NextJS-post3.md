---
layout: post
title:  "[Next.js|프로젝트] 3. Routing"
date:   2023-04-25
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### Routing

* routing에 있어서 `<a href="/">` 태그를 사용하게 된다면, 페이지를 새로고침하며 페이지를 이동하게 된다. 
* NextJs가 클라이언트 사이드 네비게이션을 제공해준다.

```
import Link from "next/link";

export default function NavBar() {
  return (
    <nav>
      <Link href="/">
        <a>Home</a>
      </Link>
      <Link href="/about">
        <a>about</a>
      </Link>
    </nav>
  );
}
```

* 이렇게 작성하면, `Invalid <Link> with <a> child` 라는 오류가 발생하는데 NextJS 13번전에서는 link 태그가 a로 저절로 렌더링 하기 때문이다.

```
<Link href="/"> Home </Link>
```

이렇게 작성해주면 되겠다.

### useRouter

NextJs가 지원해주는 것으로
`import {useRouter} from "next/router"`
해주고 `const router = useRouter();` 선언함으로써 사용이 가능하다.

이는 location에 대한 정보를 알려주는데, react.js의 useloaction과 같은 기능을 한다고 느꼈다.

```
import Link from "next/link";
import { useRouter } from "next/router";

export default function NavBar() {
  const router = useRouter();
  return (
    <nav>
      <Link
        href="/"
        style={{ color: router.pathname === "/" ? "red" : "blue" }}
      >
        Home
      </Link>
      <Link
        href="/about"
        style={{ color: router.pathname === "/about" ? "red" : "blue" }}
      >
        about
      </Link>
    </nav>
  );
}
```
