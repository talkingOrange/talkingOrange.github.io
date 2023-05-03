---
layout: post
title:  "[Next.js|프로젝트] 9. 다크모드 적용하기 "
date:   2023-05-03
categories: NextJS
---

# Next.js로 포트폴리오 만들기

--- 

### Installation

[참고 사이트](https://github.com/pacocoursey/next-themes)

1. 다크모드 라이브러리를 설치해준다. 

`npm install next-themes`

2. package-lock.json 에 추가되었는지 확인해준다. 

3. dark 모드 기능을 구현하는 컴포넌트를 만들고 코드를 작성해준다.

```
import { useTheme } from "next-themes";
import { useState } from "react";

export default function DarkModeBtn() {
  const { theme, setTheme } = useTheme();
  const [isDarkMode, setIsDarkMode] = useState<boolean>(true);

  function handleModeBtn() {
    setIsDarkMode(!isDarkMode);
    isDarkMode ? setTheme("light") : setTheme("dark");
  }

  return (
    <div>
      <button onClick={handleModeBtn}>Mode Change</button>
    </div>
  );
}
```

* useTheme을 import해서 사용해주면 되는데, 나는 useState를 추가로 구현하여 return 코드를 간결하게 만들어주었다.

### 결과물

![image](https://user-images.githubusercontent.com/88815795/235824874-610b8e12-b3e0-4eb9-aff4-4e45058b6c6b.png)
![image](https://user-images.githubusercontent.com/88815795/235824881-5eca1746-1486-42de-8dea-f94eb714066b.png)
