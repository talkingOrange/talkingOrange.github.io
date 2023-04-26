---
layout: post
title:  "[Next.js|프로젝트] Fetching Data "
date:   2023-04-26
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### API key 구하기

* 우선 나는 API를 직접 설계하기 이전에 Next.js로 fetching하는 방법을 학습하기 위해 공개 API key를 가지고 구현 연습을 먼저 할 것이다.

https://www.themoviedb.org/settings/api

1. API key 변수에 담아주기 

`const API_KEY = "c508d3f9c129f19eb7e9e48763e6024a";`

2. data fetch 해주기

```
  const [movies, setMovies] = useState();
  useEffect(() => {
    (async () => {
      const { results } = await (
        await fetch(
          `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`
        )
      ).json();
      setMovies(results);
    })();
  }, []);
```

3. return 으로 map을 돌려서 results 값들 나타내기 (movies에 담아져있음)

+) ?는 null일 때에는 map함수를 실행하지 않는 것임.

```
{movies?.map((movie) => (
        <div key={movie.id}>
          <h4>{movie.original_title}</h4>
        </div>
      ))}
```

4. 아직 movies에 값이 없을 때, Loading을 불러준다.
    {!movies && <h4>Loading...</h4>}
    
    

[ 전체 코드 ]

```
import Seo from "@/components/Seo";
import { useEffect, useState } from "react";

const API_KEY = "c508d3f9c129f19eb7e9e48763e6024a";

export default function Home() {
  const [movies, setMovies] = useState();
  useEffect(() => {
    (async () => {
      const { results } = await (
        await fetch(
          `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`
        )
      ).json();
      setMovies(results);
    })();
  }, []);
  return (
    <div>
      <Seo title="Home" />
      {!movies && <h4>Loading...</h4>}
      {movies?.map((movie) => (
        <div key={movie.id}>
          <h4>{movie.original_title}</h4>
        </div>
      ))}
    </div>
  );
}
```

![image](https://user-images.githubusercontent.com/88815795/234571641-086a5eef-7a17-4956-8cc0-ff7ce8880e4d.png)



### API key 숨기기

[ redirect 알기 ]
1. next.config.js 파일 찾기
2. async redirects() 에 배열을 리턴해주는데 배열 안에는 source(사용자가 입력한 주소), destination(그걸 받으면 보낼 주소)를 입력해준다.

```
module.exports = {
  reactStrictMode: true,
  async redirects() {
    return [
      {
        source: "/old-blog/:path*",
        destination: "/new-sexy-blog/:path*",
        permanent: false,
      },
    ];
  },
```

- 이러면, 사용자가 ~/old-blog/123/path~ 를 작성했을 때, ~/new-sexy-blog/123/path~로 이동시킨다.


[ rewrite 알기 ]

```
async rewrites() {
    return [
      {
        source: "/api/movies",
        destination: `https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`,
      },
    ];
  },
```

redirect 시키는데 url은 안 바뀐다.

그래서 redirect는 사용자가 자기가 친 url이 다른 곳으로 이동했다는 것을 눈으로 볼 수 있지만,

rewrite를 사용하면 사용자는 자기가 친 url로 이동했다고 생각한다. 

3. .env 파일을 만들고 API_KEY=값을 넣어준다.
4. .gitignore 파일에 .env 파일을 추가하여 깃에 올라가지 않도록 막는다.
5. 데이터를 fetch하던 코드를 source로 설정한 코드로 변경해준다.





