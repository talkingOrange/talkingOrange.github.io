---
layout: post
title:  "[Next.js|프로젝트] layout 패턴, public "
date:   2023-04-26
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### layout 패턴

1. Layout.js 생성
2. Layout 함수 생성
3. NavBar과 children return
* children? props. 하나의 컴포넌트 안에 또 다른 컴포넌트를 넣는다.

```
//_app.tsx
import Layout from "../components/Layout";
import { AppProps } from "next/app";
import "../styles/globals.css";

export default function App({ Component, pageProps }: AppProps) {
  return (
    <div>
      <Layout>
        <Component {...pageProps} />
      </Layout>
    </div>
  );
}

```


```
//Layout.tsx
import NavBar from "@/components/NavBar";
import React, { ReactNode } from "react";

interface LayoutProps {
  children: ReactNode;
}

export default function Layout({ children }: LayoutProps) {
  return (
    <>
      <NavBar />
      <div>{children}</div>
    </>
  );
}

```

* Layout Component는 children이란 prop을 가진다.
* _app.tsx는 아주 큰 react.js 컴포넌트라서 layout 컴포넌트에 수정을 가한다.


### public 파일 관리
public에 있는 파일들은 사용할 때 .../ 이런 상대 경로 없이 src="/vercel.svg" 이렇게 써주면 됨.

